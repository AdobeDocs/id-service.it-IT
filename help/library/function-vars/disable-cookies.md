---
description: Flag booleano opzionale che impedisce a Experience Cloud Identity Service di restituire il cookie di terze parti demdex.net.
keywords: Servizio ID
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 100%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Flag booleano opzionale che impedisce a Experience Cloud Identity Service di restituire il cookie di terze parti demdex.net.

>[!NOTE]
>
>Questa configurazione era `idSyncDisable3rdPartySyncing` ed è stata rinominata in `disableThirdPartyCookies` il 18 gennaio 2018 in occasione del rilascio della v3.0.

**Sintassi:** `disableThirdPartyCookies: true|false` (l&#39;impostazione predefinita è `false`). Per `VisitorAPI.js` versione 3.0.0 o successiva.

Quando `disableThirdPartyCookies: true`, il servizio ID non restituisce il cookie di terze parti demdex.net (vedi [I cookie ed Experience Cloud Identity Service](../../introduction/cookies.md)). Se il browser del visitatore del sito contiene già questo cookie, il servizio ID non lo usa per creare un nuovo identificatore Experience Cloud ID (MID) o restituire un ID esistente. Il servizio ID crea un nuovo MID casuale nel cookie di prime parti. Una volta attivato, è possibile raccogliere i dati con il servizio ID e condividerlo tra diverse soluzioni Experience Cloud.

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
