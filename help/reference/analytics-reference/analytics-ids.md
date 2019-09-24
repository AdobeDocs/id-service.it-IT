---
description: Il servizio Experience Cloud Identity sostituisce i metodi legacy di raccolta degli ID visitatore di Analytics.
keywords: Servizio ID
seo-description: Il servizio Experience Platform Identity sostituisce i metodi legacy di raccolta degli ID visitatore di Analytics.
seo-title: Impostazione degli ID di Analytics ed Experience Cloud
title: Impostazione degli ID di Analytics ed Experience Cloud
uuid: 421cf597-a3e0-4ca3-8ce8-d0c80cbb6aca
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Impostazione degli ID di Analytics ed Experience Cloud{#setting-analytics-and-experience-cloud-ids}

Il servizio Experience Cloud Identity sostituisce i metodi legacy di raccolta degli ID visitatore di Analytics.

Una volta implementato il servizio ID, il codice viene eseguito prima di AppMeasurement. Il servizio ID recupera gli ID di Experience Cloud e Analytics in modo che siano a disposizione quando AppMeasurement viene caricato.

Quando AppMeasurement viene caricato, i valori degli ID di Experience Cloud e Analytics vengono richiesti dal servizio ID e inviati alla raccolta dati a ogni chiamata del server. Poiché il servizio ID stabilisce l'ID del visitatore e lo trasmette semplicemente ad AppMeasurement, deve essere incluso e implementato in tutte le pagine prima del file JavaScript di AppMeasurement.

## Modifiche al processo ID di Analytics {#section-79bb86ae63f546419bb1a7ef5e710462}

La principale modifica relativa alla migrazione al servizio [!DNL Experience Cloud] ID riguarda la configurazione del cookie ID, che viene effettuata con JavaScript e non più nell'intestazione HTTP restituita dal server Web di raccolta dei dati. Per comprendere questa modifica, nelle prossime sezioni vengono descritti i due metodi di configurazione dei cookie.

**Intestazione HTTP**

La risposta HTTP da parte di un server Web imposta i cookie in un browser. Il `s_vi` cookie viene impostato in questo modo. Il `s_vi` cookie identifica i visitatori di Analytics. Una volta impostato, il cookie viene inviato insieme a tutte le richieste HTTP successive a tale server.

Quando viene inviata una richiesta al server di raccolta dati Adobe, l'intestazione viene controllata per verificare la presenza del cookie `s_vi`. Se il cookie è presente nella richiesta, viene utilizzato per identificare il visitatore. Se il cookie non è presente, il server genera un [!DNL Experience Cloud] ID univoco, lo imposta come cookie nell'intestazione della risposta HTTP e lo invia nuovamente insieme alla richiesta. Il cookie viene memorizzato nel browser e inviato di nuovo al server di raccolta dati al momento delle successive visite al sito. In questo modo il visitatore può essere identificato nel corso delle visite.

Alcuni browser tuttavia non accettano i cookie di terze parti (ad es. Apple Safari). Si tratta dei cookie impostati nel browser da domini diversi rispetto al sito Web corrente. Inoltre, Safari blocca i cookie in domini di terze parti se il visitatore non ha mai visitato tale dominio. Ad esempio, se accedi a `mysite.com` e il server di raccolta dati è `mysite.omtrdc.net` il cookie restituito nell'intestazione HTTP da `mysite.omtrdc.net` potrebbe essere rifiutato dal browser.

Per evitare questo problema, molti clienti hanno implementato record CNAME per i propri server di raccolta dati. Questa operazione può essere considerata efficace nell'ambito di una strategia di [implementazione dei cookie di prime parti](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/). Se viene configurato un record CNAME per mappare un nome host nel dominio del cliente al server di raccolta dati (ad es., mappatura di `metrics.mysite.com` a `mysite.omtrdc.net`), il cookie [!DNL Experience Cloud] ID viene memorizzato, perché il dominio di raccolta dati corrisponde al dominio del sito Web. Questa operazione aumenta la possibilità che il cookie del servizio ID venga memorizzato, ma comporta un sovraccarico maggiore, perché è necessario configurare i record CNAME e gestire i certificati SSL per i server di raccolta dati.

**JavaScript**

JavaScript è in grado di leggere e scrivere i cookie impostati nel dominio di prime parti (il dominio del sito Web corrente). Il servizio [!DNL Experience Cloud] ID utilizza questo metodo per impostare il cookie `AMCV_###@AdobeOrg`, che contiene tutti gli ID dei visitatori, pertanto il dominio del server di monitoraggio non deve più corrispondere al dominio del sito Web per memorizzare il cookie dell'ID visitatore. Nella maggior parte dei casi, questo è il metodo migliore per impostare il cookie del servizio ID, perché elimina il sovraccarico dei record CNAME e dei certificati SSL.

In alcuni casi, però, l'impostazione del cookie nell'intestazione HTTP è da preferire per il monitoraggio tra domini diversi. Questo metodo è descritto in [CNAME per raccolta dati e monitoraggio tra più domini](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d).

## ID di Analytics personalizzati {#section-b6a7bd19e9ff432390010062450808f6}

L'impostazione di un ID cliente usando `s.visitorID` è un metodo di identificazione degli utenti in Analytics. Tuttavia, le integrazioni in cui vengono esportati o importati i dati di Analytics tramite il servizio ID non funzioneranno quando un visitatore viene identificato tramite `s.visitorID`.

Sono inclusi, ma senza limitazioni, tipi di pubblico condivisi, Analytics for Target (A4T) e attributi cliente. Per queste integrazioni, l'impostazione di un ID Analytics personalizzato non è supportata.

## Ordine di identificazione degli ID visitatore in Analytics {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

Dopo aver implementato il servizio ID visitatore, i visitatori possono essere identificati in cinque modi in Analytics (le opzioni sono indicate nella tabella in ordine di preferenza):

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ordine </th> 
   <th colname="col2" class="entry"> Parametro query (metodo di raccolta) </th> 
   <th colname="col3" class="entry"> Presente se </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>s.visitorID è impostato </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>Il visitatore aveva un altro cookie s_vi prima dell'implementazione del servizio <span class="keyword">Experience Cloud</span> ID, oppure è stato configurato un.<a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">periodo di tolleranza</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid (cookie AMCV_ impostato dal servizio ID visitatore di Experience Cloud) </p> </td> 
   <td colname="col3"> <p>Il browser del visitatore accetta i cookie di prime parti </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (cookie di fallback in H.25.3 o successivo, o in AppMeasurement per JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Un browser non accetta cookie di terze parti e il server di tracciamento di Analytics è impostato come server di tracciamento terze parti. </p> <p> <p>Nota: <span class="codeph">fid</span> è un identificatore legacy e non viene utilizzato se hai implementato il servizio ID sul tuo sito. In questo caso, il <span class="codeph"> fid</span> non è necessario perché il <a href="../../introduction/cookies.md" format="dita" scope="local">cookie AMCV</a> di prime parti lo rende obsoleto. È stato mantenuto per supportare codice legacy e per motivi storici. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> Indirizzo IP, agente utente, indirizzo IP gateway</a> </p> </td> 
   <td colname="col3"> <p>Il browser del visitatore non accetta i cookie. </p> </td> 
  </tr> 
 </tbody> 
</table>

In molte situazioni potrebbero essere presenti due o tre ID diversi in una chiamata, ma Analytics utilizza il primo ID presente nell'elenco come ID ufficiale di [!DNL Experience Cloud]. Ad esempio, se imposti un ID visitatore personalizzato (incluso nel parametro di query “vid”), questo ID verrà usato prima degli altri ID visualizzati per lo stesso hit.

>[!MORE_LIKE_THIS]
>
>* [Ordine delle operazioni per gli ID di Analytics](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

