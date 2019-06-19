---
title: Metodi della libreria ECID in un world Safari ITP
seo-title: Metodi della libreria ECID in un world Safari ITP
description: Documentazione della libreria Adobe ECID (servizio ID).
seo-description: Documentazione della libreria Adobe ECID (servizio ID).
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Metodi della libreria ECID in un world Safari ITP

Poiché Safari ottimizza il monitoraggio tra più domini tramite ITP, Adobe deve mantenere le best practice per le librerie che supportano i clienti e la privacy e la scelta del consumatore.

Il 21 febbraio 2019 Apple ha annunciato l&#39;ultimo aggiornamento di ITP (Intelligent Tracking Prevention, Prevenzione intelligente del tracciamento). A differenza delle versioni precedenti incentrate su cookie di terze parti, questa versione fornisce nuove misure di prevenzione del tracciamento per i cookie di prime parti. Tutti i cookie persistenti di prime parti impostati tramite l&#39;API document. cookie, spesso noti come cookie &quot;lato client&quot;, vengono ridotti a 7 giorni. I cookie di terze parti continueranno a essere bloccati, come indicato nelle versioni precedenti di ITP. Per ulteriori dettagli su ITP 2.1 e l&#39;impatto delle soluzioni Adobe, leggi [l&#39;impatto di Safari ITP 2.1 su Adobe Experience Cloud e sui clienti della piattaforma Experience Cloud](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Domande frequenti su Adobe ECID per Safari ITP

**Perché il cookie AMCV, impostato dalla libreria Experience Cloud ID (ECID) in un dominio di terze parti dei clienti, interessato da ITP 2.1?**

Il cookie AMCV si basa attualmente sull&#39;API document. cookie e viene impostato tramite &quot;lato client&quot;. Safari favorisce i cookie impostati dal server di un cliente.

**Perché un cookie impostato tramite un server di tracciamento CNAME è un&#39;opzione migliore per il monitoraggio in Safari?**

Le regole di ITP consentono di fornire il controllo agli sviluppatori. Le implementazioni tramite i certificati CNAME non possono essere eseguite solo tramite javascript. Il programma di certificazione CNAME di Adobe (tracciamento lato server) è in linea con ITP ed è parte della strategia Adobe da molti anni. La libreria ECID sta rilasciando metodi che consentono di spostare le funzionalità della libreria ECID in un&#39;implementazione CNAME.

**Perché Adobe si concentra sulla libreria ECID quando altri metodi di tracciamento dei visitatori di Analytics vengono utilizzati oggi con CNAME?**

La libreria ECID, il cookie AMCV e l&#39;ECID (MID) iniziano come metodo per integrare tutte le soluzioni Adobe in un unico ID. Questo ID continuerà ad essere l&#39;ID a livello di cookie della priorità nella roadmap del prodotto Adobe ed è l&#39;ID cookie predefinito per Adobe Experience Platform.

**I CNAME consentono ai clienti di abilitare il tracciamento multidominio?**

Le stesse regole e battute esistenti in precedenza con CNAME continueranno a esistere. In alcuni casi, i nomi CNAME possono essere utilizzati in uno scenario multidominio. Se hai un sito di accesso principale in cui gli utenti possono essere identificati prima di visitare altri domini, un CNAME può abilitare il monitoraggio multidominio nei browser che non accettano i cookie di terze parti. Tuttavia, mentre CNAME può essere utile con più domini in alcuni scenari, il motivo per lo spostamento delle implementazioni ECID in CNAME è per identificazione permanente dei visitatori, non per il tracciamento di più domini. Per ulteriori informazioni su CNAME e su più domini, vedi [CNAME raccolta dati e monitoraggio](/help/reference/analytics-reference/cname.md)tra più domini.

Ulteriori domande frequenti verranno aggiunte qui, man mano che vengono rilasciate altre modifiche ITP. Per ulteriori domande, visita [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## Modifiche, metodi e configurazioni di ITP

Quando vengono creati metodi aggiuntivi per il monitoraggio in Safari, questi verranno aggiunti come riferimento a questa pagina.

>[!NOTE]*ECID* = *MID* = *MCID* in tutte le documentazione di seguito.

Consultate di seguito per ulteriori sforzi relativi all&#39;utilizzo della libreria ITP e ECID.

## Utilizza la libreria ECID e il tracciamento CNAME per estendere la scadenza degli ID visitatore

ITP 2.1 ostacola la scrittura dei cookie lato client, il che compromette la capacità di fornire informazioni accurate sul tracciamento dei visitatori ai clienti. Pertanto, nei server di tracciamento CNAME di Adobe viene introdotta una modifica per memorizzare l&#39;Experience Cloud ID (ECID) del visitatore in un cookie first party.

Questa modifica è utile solo per i clienti ECID che utilizzano un CNAME di Analytics nel contesto di prime parti. Se sei un cliente Analytics che al momento non usa un CNAME, o anche un cliente non Analytics, sei comunque idoneo per il record CNAME. Contatta l&#39;Assistenza clienti o il rappresentante commerciale di riferimento per avviare il processo di registrazione di un [CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html).

Aggiornamento alla libreria ECID v. 4.3.0 + per sfruttare questa modifica.

**Progettazione**

Quando viene effettuata una richiesta ID a demdex. net e viene recuperato un ECID, se un server di monitoraggio è impostato nella libreria ECID, viene effettuata una richiesta ID al dominio del cliente. Questo endpoint legge il param ecid dalla stringa query e imposta un nuovo [cookie](/help/introduction/cookies.md) che comprende solo l&#39;ECID e una data di scadenza due anni futura. Ogni volta che questo endpoint viene chiamato in questo modo, il `s_ecid` cookie viene riscritto con una data di scadenza due anni dall&#39;ora della chiamata. La libreria ECID deve essere aggiornata alla versione 4.3.0 per recuperare il valore di questo cookie.

Questo nuovo `s_ecid` cookie segue lo stesso stato di rinuncia del cookie AMCV. Se il codice ecid viene letto dal `s_ecid` cookie, demdex viene sempre chiamato per recuperare lo stato di rinuncia più recente per quell&#39;ID e archiviato nel cookie AMCV.

Inoltre, se il consumatore ha rinunciato al tracciamento di Analytics tramite questo [metodo](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html), `s_ecid` questo cookie verrà eliminato.

Il nome del server di tracciamento deve essere fornito alla libreria visitorjs quando si inizializza la libreria utilizzando trackingserver o trackingserversecure. Deve corrispondere alla configurazione trackingserver nelle configurazioni di Analytics.

Se scegli di non sfruttare questo metodo, aggiungi la seguente configurazione alla tua implementazione della libreria ECID: Discardtrackingserverecid. Quando questa configurazione è impostata su true, la libreria Visitatore non legge l&#39;identificatore MID impostato dal server di tracciamento iniziale.

![](assets/itp-proposal-v1.png)

## Usa metodo appendvisitoridsto per il monitoraggio tra domini (all&#39;interno dei più domini della tua società)

Questa funzione consente di condividere l&#39;ECID di un visitatore tra domini diversi quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in visitorapi. js versione 1.7.0 o successiva (ma non nella versione 1.10.0).

**Progettazione**

* Quando un visitatore arriva sugli altri domini, la funzione Visitor. appendvisitoridsto (url) restituisce un URL con ECID aggiunto come parametro di query.

   Utilizzate questo URL per reindirizzare dal dominio originale al dominio di destinazione.

* Invece di inviare una richiesta ad Adobe per l&#39;ID di quel visitatore, il codice del servizio ID sul dominio di destinazione estrae il codice ECID dall&#39;URL.

   Questa richiesta include l&#39;ID del cookie di terza parte, che non è disponibile in questo caso.

* Il codice del servizio ID nella pagina di destinazione utilizza il file ECID passato per tenere traccia del visitatore.

   >[!NOTE]
   >Se la pagina di destinazione dispone già di un ECID dalle visite precedenti, la decisione di sovrascrivere il cookie esistente è controllata da questa configurazione overwritecrossdomainmcidandaid. Per informazioni dettagliate su questa configurazione, consultate [overwritecrossdomainmcidandaid](/help/library/function-vars/overwrite-visitor-id.md).
   >
   >Per maggiori dettagli su questo metodo, consulta la pagina [appendvisitoridsto (Cross](/help/library/get-set/appendvisitorid.md) Domain Tracking).
