---
description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud ID per il 2018.
keywords: Servizio ID
seo-description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud ID per il 2018.
seo-title: Note sulla versione 2018
title: Note sulla versione 2018
uuid: 771 b 5 b 11-a 8 e 3-464 c-b 65 e-b 15135584 ace
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Note sulla versione 2018 {#release-notes}

Versioni future, aggiornamenti o modifiche al servizio Experience Cloud ID per il 2018.

## Versione 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descrizione dell'elemento </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Maggiore sicurezza per i cookie AMCV </p> </td> 
   <td colname="col2"> <p>Durante una scansione della sicurezza interna, è stato rilevato che quando si usa la libreria DTM, i cookie usati per la gestione della sessione non riescono a specificare gli attributi adeguati. Questo potrebbe comportare una condivisione involontaria delle informazioni dei cookie. Per risolvere questo problema è stata introdotta una configurazione che consente al cliente di impostare il cookie AMCV come sicuro. Consulta <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-securecookie.html" format="https" scope="external">secureCookie</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versione 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descrizione dell'elemento </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Maggiore sicurezza per i cookie AMCV </p> </td> 
   <td colname="col2"> <p>Durante una scansione della sicurezza interna, è stato rilevato che quando si usa la libreria DTM, i cookie usati per la gestione della sessione non riescono a specificare gli attributi adeguati. Questo potrebbe comportare una condivisione involontaria delle informazioni dei cookie. Per risolvere questo problema è stata introdotta una configurazione che consente al cliente di impostare il cookie AMCV come sicuro. Consulta secureCookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Il codice di integrazione e l'ID devono essere numeri o stringhe non vuote </p> </td> 
   <td colname="col2"> <p>È stato corretto un problema di convalida di “setCustomerIDs” quando i dati contengono un codice di integrazione o un ID che non è né un numero né una stringa non vuota. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS è disponibile nel repository Git pubblico </td> 
   <td colname="col2"> ECID JS è ora disponibile nel repository Git pubblico per tutti i clienti di Experience Cloud all'indirizzo https://github.com/Adobe-Marketing-Cloud/id-service/releases. </td> 
  </tr> 
 </tbody> 
</table>

## Versione 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descrizione dell'elemento </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Picco non realistico nel conteggio di visitatori univoci </p> </td> 
   <td colname="col2"> <p>Con il rilascio del servizio Experience Cloud ID 3.1.0, abbiamo riscontrato un problema che causava un picco non realistico nel conteggio dei visitatori univoci in seguito all'implementazione di tale versione. Questo comportamento si verifica solo nell'ultima versione di ECID (3.1.0) e solo se l'utente ha selezionato l'opzione “Consenti solo dal sito Web attuale” nelle impostazioni di privacy del browser Safari. La versione 3.1.2 corregge questo problema. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versione 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>Si consiglia di effettuare l&#39;aggiornamento dalla versione 3.1.0 alla versione più recente al primo momento. Consultare la descrizione della versione 3.1.2. L&#39;ultimo pacchetto è disponibile da Adobe Launch, DTM e AppMeasurement.

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descrizione dell'elemento </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cookie impostato su un dominio errato </p> </td> 
   <td colname="col2"> <p>È stato corretto un bug in cui il cookie Visitatore temporaneo impostava un cookie nel dominio del cookie "predefinito" anziché impostarlo nel dominio specificato nella configurazione (initConfig). </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versione 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descrizione dell'elemento </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Thread yielding per richieste di sincronizzazione ID multiple </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>Per i clienti che eseguono più sincronizzazioni di ID, in alcuni casi l'interfaccia utente si blocca a causa dei continui calcoli che la CPU deve elaborare. Stiamo pertanto introducendo la tecnica del thread yielding per separare le richieste di sincronizzazione ID di 100 msec l'una dall'altra. </p> <p>Questa modifica determinerà un miglioramento delle prestazioni per i clienti che usano Visitor 2.3.0+ e DIL 6.10+. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Possibilità di disattivare le chiamate di terze parti aggiunta </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>Adobe ha rinominato le configurazioni seguenti per consentire la disattivazione delle chiamate di sincronizzazione di terze parti. </p> <p>Da idSyncDisableSyncs a disableIdSyncs </p> <p>Da idSyncDisable3rdPartySyncing a disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Supporto per Internet Explorer </p> </td> 
   <td colname="col2"> <p>Il servizio ID non supporta più Internet Explorer 6, 7, 8 e 9. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Aggiornamento della documentazione getInstance </p> </td> 
   <td colname="col2"> <p>È stato aggiunto un avviso alla funzione Visitatore per non creare un'istanza di questa funzione con var visitor = new Visitor. </p> </td> 
  </tr> 
 </tbody> 
</table>

