---
description: Flag booleano opzionale che impedisce al servizio Experience Cloud ID di restituire il cookie di terze parti demdex.net.
keywords: Servizio ID
seo-description: Flag booleano opzionale che impedisce al servizio Experience Cloud ID di restituire il cookie di terze parti demdex.net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7 ed 5 aa 16-44 ca -4702-878 a -1 a 208 ca 95270
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Flag booleano opzionale che impedisce al servizio Experience Cloud ID di restituire il cookie di terze parti demdex.net.

>[!NOTE]
>
>Questa configurazione è `idSyncDisable3rdPartySyncing` stata ed è stata rinominata `disableThirdPartyCookies` nella release v 18 del 2018 di v 3.0.

**Sintassi:**`disableThirdPartyCookies: true|false` (impostazione predefinita `false`). Per `VisitorAPI.js` la versione 1.5.3 o successiva.

Quando `disableThirdPartyCookies: true`, il servizio ID non restituisce il cookie di terze parti demdex. net (vedi [Cookie e il servizio](../../mcvid-introduction/mcvid-cookies.md) Experience Cloud ID). Se il browser del visitatore del sito contiene già questo cookie, il servizio ID non lo usa per creare un nuovo identificatore Experience Cloud ID (MID) o restituire un ID esistente. Piuttosto, il servizio ID crea un nuovo identificatore MID casuale nel cookie di prime parti. Una volta attivato, è possibile raccogliere i dati con il servizio ID e condividerlo tra diverse soluzioni Experience Cloud.

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

