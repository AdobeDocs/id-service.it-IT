---
description: Obbligatoria per i domini di livello superiore con più parti, se una delle ultime due parti dell’URL comprende più di due caratteri.
keywords: Servizio ID
title: cookieDomain
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 100%

---

# cookieDomain{#cookiedomain}

Obbligatoria per i domini di livello superiore con più parti, se una delle ultime due parti dell’URL comprende più di due caratteri.

**Sintassi:** `cookieDomain: "*`URL`*"` (Il prefisso `www` non è obbligatorio.)

**Caso d&#39;uso**

* Obbligatorio: `www.example.com.uk`
* Non obbligatorio: `www.example.co.uk`

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```
