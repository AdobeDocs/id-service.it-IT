---
description: Flag booleano facoltativo che controlla il modo in cui Experience Platform Identity Service carica l'iframe di sincronizzazione ID.
keywords: Servizio ID
seo-description: Flag booleano facoltativo che controlla il modo in cui Experience Platform Identity Service carica l'iframe di sincronizzazione ID.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa 2 c 2 fa 4-2 cab -4 e 08-8 d 35-729 a 6 c 3 e 459 a
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Flag booleano facoltativo che controlla il modo in cui Experience Platform Identity Service carica l&#39;iframe di sincronizzazione ID.

**Sintassi:**` `Idsyncattachiframeonwindowload = true | false &quot; (predefinito is `false`.)

Quando `idSyncAttachIframeOnWindowLoad: true`, il servizio ID carica l&#39;iFrame di sincronizzazione ID al caricamento della finestra. Per impostazione predefinita, il servizio ID carica l&#39;iFrame di sincronizzazione con la massima velocità possibile, ma non al caricamento della finestra.

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

