---
description: getInstance restituisce un ID visitatore per l'ID organizzazione Experience Cloud specificato. Questo ID è richiesto per inizializzare l'ID visitatore fornito ad AppMeasurement tramite s.visitor.
keywords: Servizio ID
seo-description: getInstance restituisce un ID visitatore per l'ID organizzazione Experience Cloud specificato. Questo ID è richiesto per inizializzare l'ID visitatore fornito ad AppMeasurement tramite s.visitor.
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3d0-4aab-b935-566099bdab98
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# getInstance{#getinstance}

getInstance restituisce un ID visitatore per l'ID organizzazione Experience Cloud specificato. Questo ID è richiesto per inizializzare l'ID visitatore fornito ad AppMeasurement tramite s.visitor.

**Sintassi**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*Non* creare un'istanza della funzione Visitatore con `var visitor = new Visitor`. Devi usare la chiamata di funzione appropriata indicata qui. Si applica alla libreria di codici [!UICONTROL VisitorAPI.js] v3.0 o superiore.

**ActionScript / Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

Se `getInstance` non rileva un'istanza esistente, viene creata e restituita una nuova istanza. This is similar to the [ `s_gi()` function ](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html) in [!DNL AppMeasurement].

**Uso comune**

L'API del servizio [!DNL Experience Cloud] ID conserva un elenco di tutte le istanze create per ciascun [!DNL Adobe Experience Cloud] ID organizzazione di. Se l'applicazione che utilizza l'API del servizio ID non utilizza un riferimento all'istanza, l'istanza può essere rilevata chiamando `getInstance`, senza bisogno di crearne una nuova. Questa funzione supporta anche più istanze per diverse organizzazioni all'interno della stessa pagina Web o della stessa applicazione.

È utile per le applicazioni che non dispongono di una `init` fase chiara e che devono essere richiamate nell'API del servizio ID in più posizioni. Puoi chiamare `getInstance` da tutte le posizioni, l'istanza verrà creata dalla prima posizione in cui viene eseguito. L'istanza esistente verrà restituita dalle chiamate successive.
