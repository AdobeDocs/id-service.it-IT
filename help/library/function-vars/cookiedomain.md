---
description: Obbligatoria per i domini di livello superiore con più parti, se una delle ultime due parti dell'URL comprende più di due caratteri.
keywords: Servizio ID
seo-description: Obbligatoria per i domini di livello superiore con più parti, se una delle ultime due parti dell'URL comprende più di due caratteri.
seo-title: cookieDomain
title: cookieDomain
uuid: a57e5477-c07b-4d54-8aea-8e8b152f1423
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# cookieDomain{#cookiedomain}

Obbligatoria per i domini di livello superiore con più parti, se una delle ultime due parti dell'URL comprende più di due caratteri.

**Sintassi:** ` cookieDomain: " *`URL`*"` (Il prefisso `www` non è obbligatorio.)

**Caso d'uso**

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

