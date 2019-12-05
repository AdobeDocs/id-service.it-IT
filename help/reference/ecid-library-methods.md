---
title: Metodi della libreria ECID in ambito Safari ITP
seo-title: Metodi della libreria ECID in ambito Safari ITP
description: Documentazione della libreria Adobe ECID (servizio ID).
seo-description: Documentazione della libreria Adobe ECID (servizio ID).
translation-type: ht
source-git-commit: 8f4175b942ed4228ccd1f96791aa668be8aff95d

---


# Metodi della libreria ECID in ambito Safari ITP

Poiché Safari ottimizza il monitoraggio tra domini diversi tramite ITP, Adobe deve mantenere le best practice per le librerie che supportano i clienti, nonché la privacy e le scelte dei consumatori.

Il 21 febbraio 2019 Apple ha annunciato l'ultimo aggiornamento di ITP (Intelligent Tracking Prevention). A differenza delle versioni precedenti incentrate su cookie di terze parti, questa versione fornisce nuove misure di prevenzione del monitoraggio per i cookie di prima parte. Tutti i cookie persistenti di prima parte impostati tramite l'API document.cookie, spesso noti come cookie "lato client", hanno una scadenza massima di 7 giorni. I cookie di terze parti continueranno a essere bloccati, come indicato nelle versioni precedenti di ITP. Per ulteriori dettagli su ITP 2.1 e sull’impatto delle soluzioni Adobe, consulta [L’impatto di Safari ITP 2.1 sui clienti Adobe Experience Cloud ed Experience Platform](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Domande frequenti su Adobe ECID per Safari ITP

**Perché il cookie AMCV, impostato dalla libreria Experience Cloud ID (ECID) in un dominio di prima parte dei clienti, è interessato da ITP 2.1?**

Il cookie AMCV si basa attualmente sull'API document.cookie e viene impostato tramite "lato client". Safari favorisce i cookie impostati dal server di un cliente.

**Perché un cookie impostato tramite un server di monitoraggio CNAME è un'opzione migliore per il monitoraggio in Safari?**

Le regole di ITP consentono agli sviluppatori di riprendere il controllo. Le implementazioni tramite i certificati CNAME non possono essere eseguite solo tramite JavaScript. Il programma di certificazione CNAME di Adobe (monitoraggio lato server) è in linea con ITP ed è parte della strategia Adobe da molti anni. Attualmente, la libreria ECID rilascia metodi che consentono di spostare le funzionalità della libreria ECID in un'implementazione CNAME.

**Perché Adobe si concentra sulla libreria ECID quando attualmente con i CNAME vengono utilizzati altri metodi di monitoraggio dei visitatori di Analytics?**

La libreria ECID, il cookie AMCV ed ECID (ovvero MID) avevano come scopo iniziale quello di fornire un metodo per integrare tutte le soluzioni Adobe in un unico ID. Questo ID continuerà a essere l'ID prioritario a livello di cookie nella roadmap del prodotto Adobe ed è l'ID cookie predefinito per Adobe Experience Platform.

**I CNAME consentono ai clienti di abilitare il monitoraggio tra più domini?**

Le stesse regole e avvertenze che esistevano in precedenza con i CNAME esistono ancora. In alcuni casi, i nomi CNAME possono essere utilizzati in uno scenario con più domini. Se utilizzi un sito di accesso principale per l'identificazione degli utenti prima che visitino altri domini, un CNAME consente il monitoraggio tra più domini nei browser che non accettano i cookie di terze parti. Tuttavia, mentre i CNAME possono essere utili in caso di più domini in alcuni scenari, la ragione per il passaggio di ECID alle implementazioni CNAME è l'identificazione persistente dei visitatori, non il monitoraggio tra più domini. Per ulteriori informazioni su CNAME e sugli scenari con più domini, consulta [CNAME per raccolta dati e monitoraggio tra più domini](/help/reference/analytics-reference/cname.md).

In questa sezione verranno aggiunte nuove risposte alle domande più frequenti man mano che verranno rilasciate altre modifiche in merito a ITP. Per ulteriori informazioni, visita [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## Modifiche, metodi e configurazioni relative all'ITP

Quando vengono creati metodi aggiuntivi per il monitoraggio in Safari, questi verranno aggiunti come riferimento a questa pagina.

>[!NOTE] *ECID* = *MID* = *MCID* nell'intera documentazione di seguito.

Di seguito sono riportate tutte le iniziative relative all'utilizzo della libreria ECID e ITP.

## Utilizzo della libreria ECID e del monitoraggio CNAME per estendere la scadenza degli ID visitatore

ITP 2.1 ostacola la possibilità di scrivere cookie lato client, il che ostacola la possibilità di fornire ai clienti informazioni accurate relative al monitoraggio dei visitatori. Pertanto, nei server di monitoraggio CNAME di Adobe viene introdotta una modifica per memorizzare l'Experience Cloud ID (ECID) del visitatore in un cookie di prima parte.

Questa modifica è utile solo per i clienti ECID che utilizzano un CNAME di Analytics nel contesto di prima parte. Se sei un cliente di Analytics che al momento non usa un CNAME, o anche se non sei un cliente di Analytics, sei comunque idoneo per il record CNAME. Per avviare il processo di registrazione per un [CNAME](https://marketing.adobe.com/resources/help/it_IT/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html), contatta l’Assistenza clienti o il rappresentante di riferimento per il tuo account.

Esegui l'aggiornamento alla libreria ECID versione 4.3.0 o superiore per sfruttare questa modifica.

**Progettazione**

Quando viene effettuata una richiesta ID a demdex.net e viene recuperato un ECID, se un server di monitoraggio è impostato nella libreria ECID, viene effettuata una richiesta ID al dominio del cliente. Questo endpoint legge il parametro ecid dalla stringa query e imposta un nuovo [cookie](/help/introduction/cookies.md) che comprende solo l'ECID e una data di scadenza di due anni nel futuro. Ogni volta che l'endpoint viene chiamato in questo modo, il cookie `s_ecid` viene riscritto con una data di scadenza di due anni dalla data di tale chiamata. La libreria ECID deve essere aggiornata alla versione 4.3.0 per recuperare il valore di questo cookie.

Questo nuovo cookie `s_ecid` segue lo stesso stato di rinuncia del cookie AMCV. Se il codice ECID viene letto dal cookie `s_ecid`, demdex viene sempre chiamato per recuperare lo stato di rinuncia più recente per tale ID e archiviato nel cookie AMCV.

Inoltre, se il tuo utente ha rinunciato al tracciamento da parte di Analytics tramite questo [metodo](https://marketing.adobe.com/resources/help/it_IT/sc/implement/opt_out_link.html), questo cookie `s_ecid` verrà eliminato.

Il nome del server di monitoraggio deve essere fornito alla libreria VisitorJS quando si inizializza la libreria utilizzando trackingServer o trackingServerSecure. Questo deve corrispondere alla configurazione di trackingServer nelle configurazioni di Analytics.

Se scegli di non sfruttare questo metodo, aggiungi la seguente configurazione alla tua implementazione della libreria ECID: discardtrackingServerECID. Quando questa configurazione è impostata su true, la libreria Visitatore non legge il MID impostato dal server di monitoraggio di prima parte.

![](assets/itp-proposal-v1.png)

## Utilizza il metodo appendVisitorIDsTo per il monitoraggio tra più domini (all'interno dei diversi domini della tua azienda)

Con questa funzione puoi condividere l'ECID di un visitatore tra più domini quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in VisitorAPI.js versione 1.7.0 o successiva (ma non nella versione 1.10.0).

**Progettazione**

* Quando un visitatore arriva ai tuoi altri domini, Visitor.appendVisitorIDsTo(url) restituisce un URL con ECID aggiunto come parametro di query.

   Utilizza questo URL per reindirizzare dal dominio originale al dominio di destinazione.

* Invece di inviare ad Adobe la richiesta dell'ID di quel visitatore, il codice del servizio ID sul dominio di destinazione estrae l'identificatore ECID dall'URL.

   Questa richiesta include l'ID del cookie di terza parte, che non è disponibile in questo caso.

* Il codice del servizio ID sulla pagina di destinazione usa quindi questo stesso identificatore ECID per tenere traccia del visitatore.

   >[!NOTE]
   >Se la pagina di destinazione dispone già di un ECID da precedenti visite, la decisione di sovrascrivere il cookie esistente è controllata da questa configurazione overwriteCrossDomainMCIDAndAID. Per informazioni dettagliate su questa configurazione, consulta [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md).
   >
   >Per maggiori dettagli su questo metodo, consulta la pagina di riferimento [appendVisitorIDsTo (Monitoraggio interdominio)](/help/library/get-set/appendvisitorid.md).
