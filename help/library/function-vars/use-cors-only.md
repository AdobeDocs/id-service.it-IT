---
description: Flag booleano facoltativo che controlla in che modo il browser richiede le risorse da Experience Cloud Identity Service.
keywords: Servizio ID
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
TQID: https://experienceleague.adobe.com/QMYUbL2y8X5gSUcLmYnKZnp5mfEu7-uiogOx3rx2dkY
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 145
ht-degree: 87%

---

# useCORSOnly{#usecorsonly}

Flag booleano facoltativo che controlla in che modo il browser richiede le risorse da Experience Cloud Identity Service.

**Sintassi:** `useCORSOnly: true|false` (l&#39;impostazione predefinita è `false`).

**Panoramica**

Se è impostato su `false`, il browser esegue verifiche sulle risorse con CORS o JSONP. Tuttavia, il servizio ID cerca sempre di richiedere risorse prima con CORS. Nei browser più datati che non supportano CORS, viene ripristinato il formato JSONP. Se devi forzare il solo utilizzo di CORS, imposta `useCORSOnly:true` nella chiamata della funzione `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` in caso di requisiti di sicurezza rigidi. Abilita questa modalità solo se sei certo che tutti i visitatori utilizzano browser che supportano CORS. Sui browser che non supportano CORS, l’esperienza utente resta invariata. Tuttavia, i browser senza supporto CORS non possono richiedere risorse o scambiare dati con [!DNL Adobe Experience Cloud].

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

