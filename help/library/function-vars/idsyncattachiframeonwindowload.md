---
description: Flag booleano facoltativo che controlla come Experience Cloud Identity Service carica l’iFrame di sincronizzazione ID.
keywords: Servizio ID
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Flag booleano facoltativo che controlla come Experience Cloud Identity Service carica l’iFrame di sincronizzazione ID.

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
