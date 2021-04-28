---
description: Flag booleano opzionale che impedisce al servizio Experience Cloud Identity di restituire il cookie di terze parti demdex.net.
keywords: Servizio ID
seo-description: Flag booleano opzionale che impedisce al servizio Experience Cloud Identity di restituire il cookie di terze parti demdex.net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '157'
ht-degree: 100%

---

# disableThirdPartyCookies {#disablethirdpartycookies}

Flag booleano opzionale che impedisce al servizio Experience Cloud Identity di restituire il cookie di terze parti demdex.net.

>[!NOTE]
>
>Questa configurazione era `idSyncDisable3rdPartySyncing` ed è stata rinominata in `disableThirdPartyCookies` il 18 gennaio 2018 in occasione del rilascio della v3.0.

**Sintassi:** `disableThirdPartyCookies: true|false` (l&#39;impostazione predefinita è `false`). Per `VisitorAPI.js` versione 3.0.0 o successiva.

Quando `disableThirdPartyCookies: true`, il servizio ID non restituisce il cookie di terze parti demdex.net (vedi [Cookie e il servizio Experience Cloud Identity](../../introduction/cookies.md)). Se il browser del visitatore del sito contiene già questo cookie, il servizio ID non lo usa per creare un nuovo identificatore Experience Cloud ID (MID) o restituire un ID esistente. Il servizio ID crea un nuovo MID casuale nel cookie di prime parti. Una volta attivato, è possibile raccogliere i dati con il servizio ID e condividerlo tra diverse soluzioni Experience Cloud.

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
