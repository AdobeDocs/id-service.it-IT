---
description: Flag booleano facoltativo che disabilita la sincronizzazione degli ID.
keywords: Servizio ID
seo-description: Flag booleano facoltativo che disabilita la sincronizzazione degli ID.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8 bea 1 de 8-53 c 8-4 a 15-bcf 5-f 0869763 a 32 e
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# disableIdSyncs{#disableidsyncs}

Flag booleano facoltativo che disabilita la sincronizzazione degli ID.

>[!NOTE]
>
>Questa configurazione è `idSyncDisableSyncs` stata ed è stata rinominata `disableIdSyncs` nella release v 18 del 2018 di v 3.0.

**Sintassi:**`disableIdSyncs: true|false` (impostazione predefinita `false`).

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

