---
description: Con questa funzione puoi condividere l'Experience Cloud ID di un visitatore tra più domini quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
keywords: Servizio ID
title: appendVisitorIDsTo (Monitoraggio interdominio)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
source-git-commit: c035f0af76f70322e4d79ed842502b26c3f155ac
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 100%

---

# appendVisitorIDsTo (Monitoraggio interdominio){#appendvisitoridsto-cross-domain-tracking}

Con questa funzione puoi condividere l&#39;Experience Cloud ID di un visitatore tra più domini quando i browser bloccano i cookie di terze parti. Per usare questa funzione, devi avere implementato il servizio ID sui domini di sorgente e di destinazione. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.

Sommario:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Tieni traccia dei visitatori su più domini quando i browser bloccano i cookie di terze parti </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Aggiungi l'esempio di codice ID visitatore </a> </li> 
 </a> </li> 
</ul>

<!-- <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) and SDK Support -->

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

L’esempio seguente può aiutarti a iniziare con la funzione `appendVisitorIDsTo`:

>[!TIP]
>
>È possibile inserire questo codice nell’editor del codice personalizzato che fa parte dell’estensione Adobe Analytics o nella parte superiore di [AppMeasurement.js](https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=it).

```js
var adbeDomains = ["marketo.com", "figma.com", "workfront.com"];
var visitor = Visitor.getInstance("9E1005A551ED61CA0A490D45@AdobeOrg", {
  trackingServer: "sstats.adobe.com",
  trackingServerSecure: "sstats.adobe.com",
  marketingCloudServer: "sstats.adobe.com",
  marketingCloudServerSecure: "sstats.adobe.com"
});
adbeDomains.forEach(function(domain) {
  var domainRegex = RegExp(domain);
  if (!domainRegex.test(location.hostname)) {
    hrefSelector = '[href*="' + domain + '"]';
    document.querySelectorAll(hrefSelector).forEach(function(href) {
      href.addEventListener('mousedown', function(event) {
        var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(event.currentTarget.href)
        event.currentTarget.href = destinationURLWithVisitorIDs.replace(/MCAID%3D.*%7CMCORGID/, 'MCAID%3D%7CMCORGID');
      });
    });
  }
});
```

<!-- >[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with ` Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

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
``` -->

<!-- ## Dynamic Tag Management (DTM) and SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Set the appendVisitorIDTo Function in DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> -->
