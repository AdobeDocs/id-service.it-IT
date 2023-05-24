---
description: Questa variabile consente di ignorare la durata predefinita del cookie AMCV.
keywords: Servizio ID
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 100%

---

# cookieLifetime{#cookielifetime}

Questa variabile consente di ignorare la durata predefinita del cookie AMCV.

Per impostazione predefinita, i cookie del servizio [!DNL Experience Cloud] ID scadono dopo 24 mesi. L&#39;intervallo di tempo deve essere impostato in secondi.

**Sintassi:** ` cookieLifetime: *`durata in secondi`*`

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```
