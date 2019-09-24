---
description: Flag booleano facoltativo che disabilita la sincronizzazione degli ID.
keywords: Servizio ID
seo-description: Flag booleano facoltativo che disabilita la sincronizzazione degli ID.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# disableIdSyncs{#disableidsyncs}

Flag booleano facoltativo che disabilita la sincronizzazione degli ID.

>[!NOTE]
>
>Questa configurazione era `idSyncDisableSyncs` ed è stata rinominata in `disableIdSyncs` il 18 gennaio 2018 in occasione del rilascio della v3.0.

**Sintassi:**`disableIdSyncs: true|false` (l'impostazione predefinita è `false`).

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

