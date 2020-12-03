---
description: Questa variabile consente di ignorare la durata predefinita del cookie AMCV.
keywords: ID Service
seo-description: Questa variabile consente di ignorare la durata predefinita del cookie AMCV.
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625-ac3f-69ac259377a3
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '62'
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

