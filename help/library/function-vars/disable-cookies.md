---
description: Flag booleano facoltativo che impedisce al servizio ID visitatore di restituire il cookie di terze parti demdex.net.
keywords: Servizio ID visitatori
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 16%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Flag booleano facoltativo che impedisce al servizio ID visitatore di restituire il cookie di terze parti demdex.net.

>[!NOTE]
>
>Questa configurazione era `idSyncDisable3rdPartySyncing` ed è stata rinominata in `disableThirdPartyCookies` il 18 gennaio 2018 in occasione del rilascio della v3.0.

**Sintassi:** `disableThirdPartyCookies: true|false` (l&#39;impostazione predefinita è `false`). Per `VisitorAPI.js` versione 3.0.0 o successiva.

Quando `disableThirdPartyCookies: true`, il servizio ID visitatore non restituisce il cookie di terze parti demdex.net (vedi [Cookie e il servizio ID visitatore](../../introduction/cookies.md) ). Se il visitatore del sito dispone già del cookie nel proprio browser, il Servizio ID visitatore non lo utilizza per creare un nuovo ECID o restituire un ID esistente. Il Servizio ID visitatore crea un nuovo MID casuale nel cookie di prime parti. Una volta attivato, è possibile raccogliere i dati con il servizio ID visitatore e condividerlo tra diverse soluzioni CX Enterprise.

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

