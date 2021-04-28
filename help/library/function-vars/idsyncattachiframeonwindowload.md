---
description: Flag booleano facoltativo che controlla come il servizio Experience Cloud Identity carica l’iFrame di sincronizzazione ID.
keywords: Servizio ID
seo-description: Flag booleano facoltativo che controlla come il servizio Experience Cloud Identity carica l’iFrame di sincronizzazione ID.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '95'
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad {#idsyncattachiframeonwindowload}

Flag booleano facoltativo che controlla come il servizio Experience Cloud Identity carica l’iFrame di sincronizzazione ID.

**Sintassi:** ` `idSyncAttachIframeOnWindowLoad= true false`` (l&#39;impostazione predefinita è `false`).

Quando `idSyncAttachIframeOnWindowLoad: true`, il servizio ID carica l&#39;iFrame di sincronizzazione ID al caricamento della finestra. Per impostazione predefinita, il servizio ID carica l’iFrame di sincronizzazione ID il più rapidamente possibile invece che al caricamento della finestra.

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
