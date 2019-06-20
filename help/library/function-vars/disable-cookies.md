---
description: Flag booleano facoltativo che impedisce al servizio Experience Cloud ID di restituire il cookie demdex. net di terze parti.
keywords: Servizio ID
seo-description: Flag booleano facoltativo che impedisce al servizio Experience Cloud ID di restituire il cookie demdex. net di terze parti.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7 ed 5 aa 16-44 ca -4702-878 a -1 a 208 ca 95270
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Flag booleano facoltativo che impedisce al servizio Experience Cloud ID di restituire il cookie demdex. net di terze parti.

>[!NOTE]
>
>This configuration was `idSyncDisable3rdPartySyncing` and renamed to `disableThirdPartyCookies` in the January 18, 2018 release of v3.0.

**Sintassi:**`disableThirdPartyCookies: true|false` (impostazione predefinita `false`). For `VisitorAPI.js` v1.5.3, or greater.

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Cloud ID Service](../../introduction/cookies.md) ). Se il browser del visitatore del sito contiene già questo cookie, il servizio ID non lo usa per creare un nuovo identificatore Experience Cloud ID (MID) o restituire un ID esistente. Piuttosto, il servizio ID crea un nuovo identificatore MID casuale nel cookie di prime parti. Una volta attivato, è possibile raccogliere i dati con il servizio ID e condividerlo tra diverse soluzioni Experience Cloud.

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

