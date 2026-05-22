---
title: Metodi della libreria ECID in ambito Safari ITP
description: Documentazione della libreria Adobe ECID (servizio ID).
exl-id: ac1d1ee1-2b5f-457a-a694-60bb4c960ae7
TQID: https://experienceleague.adobe.com/GwI5LkCBXGiKyfjGm6bOqbyGbHQ2GwW64PeyLIrl3Ck
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 833
ht-degree: 93%

---

# Metodi della libreria ECID in ambito Safari ITP

>[!NOTE]
>
>Sono stati introdotti aggiornamenti per riflettere le ultime modifiche a ITP rilasciate il 12 novembre 2020 nell’ambito della versione del sistema operativo Big Sur.

Poiché Safari ottimizza il monitoraggio tra domini diversi tramite ITP, Adobe deve mantenere le best practice per le librerie che supportano i clienti, nonché la privacy e le scelte dei consumatori.

A partire dal 10 novembre 2020, tutti i cookie persistenti di prime parti impostati tramite l’API document.cookie, spesso noti come cookie &quot;lato client&quot;, e i cookie impostati tramite le implementazioni CNAME di prime parti nei browser Safari e iOS mobile hanno una scadenza limitata a sette giorni. I cookie di terze parti continueranno a essere bloccati, come indicato nelle versioni precedenti di ITP. Per ulteriori dettagli su ITP 2.1 e sull’impatto delle soluzioni Adobe, consulta [L’impatto di Safari ITP 2.1 sui clienti Adobe Experience Cloud ed Experience Platform](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Modifiche, metodi e configurazioni relative a ITP

Quando vengono creati metodi aggiuntivi per il monitoraggio in Safari, questi verranno aggiunti come riferimento a questa pagina.

>[!NOTE]
>
>*ECID* = *MID* = *MCID* in tutta la documentazione di seguito.

Di seguito sono riportate tutte le iniziative relative all&#39;utilizzo della libreria ECID e ITP.

## Comportamento corrente della libreria ECID con ITP e WebKit di Apple

ITP 2.1 ostacola la possibilità di scrivere cookie lato client, il che ostacola la possibilità di fornire ai clienti informazioni accurate relative al monitoraggio dei visitatori. Pertanto, nei server di tracciamento CNAME di Adobe viene introdotta una modifica per memorizzare l’Experience Cloud ID (ECID) del visitatore in un cookie di prima parte.

Questa modifica è utile solo per i clienti ECID che utilizzano un CNAME di Analytics nel contesto di prima parte. Se sei un cliente di Analytics che al momento non usa un CNAME, o anche se non sei un cliente di Analytics, sei comunque idoneo per il record CNAME. Per avviare il processo di registrazione per un [CNAME](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-first-party.html?lang=it), contatta l’Assistenza clienti o il rappresentante di riferimento per il tuo account.

Aggiornamento alla libreria ECID v. 4.3.0 + per trarre vantaggio da questa modifica.

Di seguito vengono illustrati il comportamento della libreria ECID con ITP 2.1 e le ultime modifiche apportate da Apple nell’ambito della versione Big Sur.

**Progettazione**

Quando viene effettuata una richiesta ID a demdex.net e viene recuperato un ECID, se un server di monitoraggio è impostato nella libreria ECID, viene effettuata una richiesta ID al dominio del cliente. Questo endpoint legge il parametro ecid dalla stringa query e imposta un nuovo [cookie](/help/introduction/cookies.md) che comprende solo l&#39;ECID e una data di scadenza di due anni nel futuro. Ogni volta che l&#39;endpoint viene chiamato in questo modo, il cookie `s_ecid` viene riscritto con una data di scadenza di due anni dalla data di tale chiamata. La libreria ECID deve essere aggiornata alla versione 4.3.0 per recuperare il valore di questo cookie.

>[!IMPORTANT]
>
>Come parte degli aggiornamenti di Big Sur, anche un cookie `s_ecid` impostato tramite CNAME è soggetto alla scadenza di sette giorni.

Questo nuovo cookie `s_ecid` segue lo stesso stato di rinuncia del cookie AMCV. Se il codice ECID viene letto dal cookie `s_ecid`, demdex viene sempre chiamato per recuperare lo stato di rinuncia più recente per tale ID e archiviato nel cookie AMCV.

Inoltre, se il tuo utente ha rinunciato al tracciamento da parte di Analytics tramite questo [metodo](https://experienceleague.adobe.com/docs/analytics/implementation/js/opt-out.html?lang=it), questo cookie `s_ecid` verrà eliminato.

Il nome del server di tracciamento deve essere fornito alla libreria VisitorJS quando questa viene inizializzata utilizzando `trackingServer` o `trackingServerSecure`. Questo deve corrispondere alla configurazione del `trackingServer` nelle configurazioni di Analytics.

Se scegli di non sfruttare questo metodo, aggiungi la seguente configurazione alla tua implementazione della libreria ECID: `discardtrackingServerECID`. Quando questa configurazione è impostata su true, la libreria Visitatore non legge il MID impostato dal server di tracciamento di prima parte.

![](assets/itp-proposal-v1.png)

## Utilizza il metodo appendVisitorIDsTo per il monitoraggio tra più domini (all&#39;interno dei diversi domini della tua azienda)

Con questa funzione puoi condividere l&#39;ECID di un visitatore tra più domini quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in VisitorAPI.js versione 1.7.0 o successiva (ma non nella versione 1.10.0).

**Progettazione**

* Quando un visitatore arriva ai tuoi altri domini, Visitor.appendVisitorIDsTo(url) restituisce un URL con ECID aggiunto come parametro di query.

  Utilizza questo URL per reindirizzare dal dominio originale al dominio di destinazione.

* Invece di inviare ad Adobe la richiesta dell&#39;ID di quel visitatore, il codice del servizio ID sul dominio di destinazione estrae l&#39;identificatore ECID dall&#39;URL.

  Questa richiesta include l’ID del cookie di terza parte, che in questo caso non è disponibile.

* Il codice del servizio ID sulla pagina di destinazione usa quindi questo stesso identificatore ECID per tenere traccia del visitatore.

  >[!NOTE]
  >Se la pagina di destinazione dispone già di un ECID da precedenti visite, la decisione di sovrascrivere il cookie esistente è controllata da questa configurazione overwriteCrossDomainMCIDAndAID. Per informazioni dettagliate su questa configurazione, consulta [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md).
  >
  >Per maggiori dettagli su questo metodo, consulta la pagina di riferimento [appendVisitorIDsTo (Monitoraggio interdominio)](/help/library/get-set/appendvisitorid.md).

