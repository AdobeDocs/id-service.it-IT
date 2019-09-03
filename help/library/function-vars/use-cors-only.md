---
description: Flag booleano facoltativo che controlla in che modo il browser richiede le risorse dal servizio Experience Cloud Identity.
keywords: Servizio ID
seo-description: Flag booleano facoltativo che controlla in che modo il browser richiede le risorse dal servizio Experience Cloud Identity.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# useCORSOnly{#usecorsonly}

Flag booleano facoltativo che controlla in che modo il browser richiede le risorse dal servizio Experience Cloud Identity.

**Sintassi:**`useCORSOnly: true|false` (l'impostazione predefinita è `false`).

**Panoramica**

Se è impostato su `false`, il browser esegue verifiche sulle risorse con CORS o JSONP. Il servizio ID tenta sempre di richiedere le risorse prima con CORS. Se necessario, utilizza JSONP per i browser più datati che non supportano CORS. Se devi forzare il solo utilizzo di CORS, imposta `useCORSOnly:true` nella chiamata della funzione `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` in caso di requisiti di sicurezza rigidi. Abilita questa modalità solo se sei certo che tutti i tuoi visitatori usano browser che supportano CORS. L'esperienza utente non risente dell'uso di browser che non supportano CORS. Tuttavia, i browser senza supporto CORS non possono richiedere risorse o scambiare dati con [!DNL Adobe Experience Cloud].

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

