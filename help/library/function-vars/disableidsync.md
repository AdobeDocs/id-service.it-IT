---
description: Flag booleano facoltativo che disabilita la sincronizzazione degli ID.
keywords: Servizio ID
title: disableIdSyncs
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# disableIdSyncs{#disableidsyncs}

Flag booleano facoltativo che disabilita la sincronizzazione degli ID.

>[!NOTE]
>
>Questa configurazione era `idSyncDisableSyncs` ed è stata rinominata in `disableIdSyncs` il 18 gennaio 2018 in occasione del rilascio della v3.0.

**Sintassi:** `disableIdSyncs: true|false` (l&#39;impostazione predefinita è `false`).

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
