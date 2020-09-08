---
description: Con questa funzione puoi condividere l'Experience Cloud ID di un visitatore tra più domini quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
keywords: ID Service
seo-description: Con questa funzione puoi condividere l'Experience Cloud ID di un visitatore tra più domini quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
seo-title: appendVisitorIDsTo (Monitoraggio interdominio)
title: appendVisitorIDsTo (Monitoraggio interdominio)
uuid: 06b453ee-73c5-4625-82d9-877ad2b4f702
translation-type: ht
source-git-commit: 6e77622817d9881efd9039d9073ba4ae14e8e14e
workflow-type: ht
source-wordcount: '446'
ht-degree: 100%

---


# appendVisitorIDsTo (Monitoraggio interdominio) {#appendvisitoridsto-cross-domain-tracking}

Con questa funzione puoi condividere l&#39;Experience Cloud ID di un visitatore tra più domini quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.

Sommario:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Tieni traccia dei visitatori su più domini quando i browser bloccano i cookie di terze parti </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Aggiungi l'esempio di codice ID visitatore </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) e supporto per l'SDK </a> </li> 
</ul>

## Tieni traccia dei visitatori su più domini quando i browser bloccano i cookie di terze parti {#section-7251d88befd440b4b79520e33c5aa44a}

Il servizio ID scrive un cookie di prime e terze parti nel browser quando una persona visita il sito (consulta [Cookie e il servizio Experience Cloud Identity](../../introduction/cookies.md)). Il cookie di prima parte contiene il MID, un ID univoco che identifica quel visitatore specifico. Il cookie di terza parte contiene un altro ID usato dal servizio ID per generare il MID. Quando un browser blocca il cookie di terza parte, il servizio ID non può:

* Rigenerare l’ID univoco per quel visitatore del sito quando si sposta su un altro dominio.
* Tenere traccia dei visitatori su domini diversi di proprietà della tua organizzazione.

Per risolvere questo problema, implementa ` Visitor.appendVisitorIDsTo( *`url`*)`. Questa proprietà consente al servizio ID di tenere traccia dei visitatori su più domini anche se il loro browser blocca i cookie di terze parti. Ecco come funziona:

* Quando un visitatore esplora gli altri domini, l&#39;` Visitor.appendVisitorIDsTo( *`url`*)` aggiunge il MID come parametro di query nell&#39;URL reindirizzandolo dal dominio originale al dominio di destinazione.
* Invece di inviare ad Adobe la richiesta dell&#39;ID di quel visitatore, il codice del servizio ID sul dominio di destinazione estrae l&#39;identificatore MID dall&#39;URL. Questa richiesta include l’ID del cookie di terza parte, che in questo caso non è disponibile.
* Il codice del servizio ID sulla pagina di destinazione usa il MID passato per tenere traccia del visitatore.

Per informazioni dettagliate consulta l’esempio di codice.

## Aggiungi l&#39;esempio di codice ID visitatore {#section-62d55f7f986542b0b9238e483d50d7b0}

L&#39;esempio seguente può aiutarti a iniziare con ` Visitor.appendVisitorIDsTo( *`url`*)`. Se viene implementato correttamente, il codice JavaScript sarà simile a quello di questo esempio.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
```

## Dynamic Tag Management (DTM) e supporto per l&#39;SDK {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Supporto per </th> 
   <th colname="col2" class="entry"> Consulta </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/it/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Imposta la funzione appendVisitorIDTo in DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://docs.adobe.com/content/help/it-IT/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Metodi del servizio ID Android </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://docs.adobe.com/content/help/it-IT/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> Metodi del servizio ID iOS </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

