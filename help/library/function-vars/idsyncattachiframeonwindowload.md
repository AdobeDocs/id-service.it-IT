---
description: Flag booleano facoltativo che controlla come il servizio Experience Cloud Identity carica l’iFrame di sincronizzazione ID.
keywords: Servizio ID
seo-description: Flag booleano facoltativo che controlla come il servizio Experience Cloud Identity carica l’iFrame di sincronizzazione ID.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Flag booleano facoltativo che controlla come il servizio Experience Cloud Identity carica l’iFrame di sincronizzazione ID.

**Sintassi:** ` `idSyncAttachIframeOnWindowLoad= true|false`` (l'impostazione predefinita è `false`).

Quando `idSyncAttachIframeOnWindowLoad: true`, il servizio ID carica l'iFrame di sincronizzazione ID al caricamento della finestra. Per impostazione predefinita, il servizio ID carica l'iFrame di sincronizzazione con la massima velocità possibile, ma non al caricamento della finestra.

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

