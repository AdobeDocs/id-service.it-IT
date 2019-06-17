---
description: Con questa funzione puoi condividere l'Experience Cloud ID di un visitatore tra più domini quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
keywords: Servizio ID
seo-description: Con questa funzione puoi condividere l'Experience Cloud ID di un visitatore tra più domini quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
seo-title: appendVisitorIDsTo (Monitoraggio interdominio)
title: appendVisitorIDsTo (Monitoraggio interdominio)
uuid: 06 b 453 ee -73 c 5-4625-82 d 9-877 ad 2 b 4 f 702
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# appendVisitorIDsTo (Monitoraggio interdominio){#appendvisitoridsto-cross-domain-tracking}

Con questa funzione puoi condividere l&#39;Experience Cloud ID di un visitatore tra più domini quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.

Sommario:

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Tieni traccia dei visitatori su più domini quando i browser bloccano i cookie di terze parti </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Aggiungi l'esempio di codice ID visitatore </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) e supporto per l'SDK </a> </li> 
</ul>

## Tieni traccia dei visitatori su più domini quando i browser bloccano i cookie di terze parti {#section-7251d88befd440b4b79520e33c5aa44a}

Il servizio ID scrive un cookie di prime e terze parti sul browser quando una persona visita il sito (consultate [Cookie e il servizio](../../mcvid-introduction/mcvid-cookies.md) Experience Cloud ID). Il cookie di prima parte contiene il MID, un ID univoco che identifica quel visitatore specifico. Il cookie di terza parte contiene un altro ID usato dal servizio ID per generare il MID. Quando un browser blocca questo cookie di terza parte, il servizio ID non è in grado di:

* Rigenerare l&#39;ID univoco per quel visitatore del sito quando il visitatore si sposta su un altro dominio.
* Tenere traccia dei visitatori su più domini diversi di proprietà della tua organizzazione.

Per risolvere questo problema, implementa ` Visitor.appendVisitorIDsTo( *`l&#39;URL`*)`. Questa proprietà consente al servizio ID di tenere traccia dei visitatori su più domini anche se il loro browser blocca i cookie di terze parti. Funziona in questo modo:

* Quando un visitatore arriva sugli altri domini, l&#39; ` Visitor.appendVisitorIDsTo( *`URL`*)` aggiunge il MID come parametro query nell&#39;URL reindirizzandolo dal dominio originale al dominio di destinazione.
* Invece di inviare ad Adobe la richiesta dell&#39;ID di quel visitatore, il codice del servizio ID sul dominio di destinazione estrae l&#39;identificatore MID dall&#39;URL. Questa richiesta include l&#39;ID del cookie di terza parte, che non è disponibile in questo caso.
* Il codice del servizio ID sulla pagina di destinazione usa quindi questo stesso identificatore MID per tenere traccia del visitatore.

Per maggiori dettagli vedi l&#39;esempio di codice.

## Aggiungi l&#39;esempio di codice ID visitatore {#section-62d55f7f986542b0b9238e483d50d7b0}

L&#39;esempio seguente può aiutarti a iniziare con ` Visitor.appendVisitorIDsTo( *`l&#39;URL`*)`. Se viene implementato correttamente, il codice JavaScript sarà simile a quello di questo esempio.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678 
<draft-comment>
  |TS=123675879 
</draft-comment>" 
 
//Redirect to the destination
```

## Dynamic Tag Management (DTM) e supporto per l&#39;SDK {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Supporto per </th> 
   <th colname="col2" class="entry"> Consulta  </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Imposta la funzione appendVisitorIDTo in DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/android/mc_methods.html" format="https" scope="external"> Metodi del servizio ID Android </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://marketing.adobe.com/resources/help/en_US/mobile/ios/mc_methods.html" format="https" scope="external"> Metodi del servizio ID iOS </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

