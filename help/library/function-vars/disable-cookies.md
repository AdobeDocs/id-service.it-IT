---
description: Flag booleano facoltativo che impedisce al servizio Experience Cloud Identity di restituire il cookie demdex. net di terze parti.
keywords: Servizio ID
seo-description: Flag booleano facoltativo che impedisce al servizio Experience Cloud Identity di restituire il cookie demdex. net di terze parti.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Flag booleano facoltativo che impedisce al servizio Experience Cloud Identity di restituire il cookie demdex. net di terze parti.

>[!NOTE]
>
>Questa configurazione era `idSyncDisable3rdPartySyncing` ed è stata rinominata in `disableThirdPartyCookies` il 18 gennaio 2018 in occasione del rilascio della v3.0.

**Sintassi:**`disableThirdPartyCookies: true|false` (l'impostazione predefinita è `false`). For `VisitorAPI.js` v3.0.0 or greater.

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Cloud Identity Service](../../introduction/cookies.md) ). Se il browser del visitatore del sito contiene già questo cookie, il servizio ID non lo usa per creare un nuovo identificatore Experience Cloud ID (MID) o restituire un ID esistente. Piuttosto, il servizio ID crea un nuovo identificatore MID casuale nel cookie di prime parti. Una volta attivato, è possibile raccogliere i dati con il servizio ID e condividerlo tra diverse soluzioni Experience Cloud.

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

