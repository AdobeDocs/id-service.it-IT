---
description: Flag booleano facoltativo che controlla in che modo il browser richiede le risorse dal servizio Experience Cloud Identity.
keywords: ID Service
seo-description: Flag booleano facoltativo che controlla in che modo il browser richiede le risorse dal servizio Experience Cloud Identity.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 66%

---


# useCORSOnly{#usecorsonly}

Flag booleano facoltativo che controlla in che modo il browser richiede le risorse dal servizio Experience Cloud Identity.

**Sintassi:**`useCORSOnly: true|false` (l&#39;impostazione predefinita è `false`).

**Panoramica**

Se è impostato su `false`, il browser esegue verifiche sulle risorse con CORS o JSONP. Tuttavia, il servizio ID tenta sempre di richiedere risorse prima con CORS. Viene ripristinato su JSONP nei browser meno recenti che non supportano CORS. Se devi forzare il solo utilizzo di CORS, imposta `useCORSOnly:true` nella chiamata della funzione `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` in caso di requisiti di sicurezza rigidi. Abilita questa modalità solo se sei certo che tutti i visitatori utilizzano browser che supportano CORS. L&#39;esperienza utente non viene modificata dai browser che non supportano CORS. Tuttavia, i browser senza supporto CORS non possono richiedere risorse o scambiare dati con [!DNL Adobe Experience Cloud].

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

