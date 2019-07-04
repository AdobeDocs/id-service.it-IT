---
description: getInstance restituisce un ID visitatore per l'ID organizzazione Experience Cloud specificato. Questo ID è richiesto per inizializzare l'ID visitatore fornito ad AppMeasurement tramite s.visitor.
keywords: Servizio ID
seo-description: getInstance restituisce un ID visitatore per l'ID organizzazione Experience Cloud specificato. Questo ID è richiesto per inizializzare l'ID visitatore fornito ad AppMeasurement tramite s.visitor.
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3d0-4aab-b935-566099bdab98
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getInstance{#getinstance}

getInstance restituisce un ID visitatore per l&#39;ID organizzazione Experience Cloud specificato. Questo ID è richiesto per inizializzare l&#39;ID visitatore fornito ad AppMeasurement tramite s.visitor.

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
>*Non* creare un&#39;istanza della funzione Visitatore con `var visitor = new Visitor`. Devi usare la chiamata di funzione appropriata indicata qui. Si applica alla [!DNL VisitorAPI.js] libreria di codici v3.0 o superiore.

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

Se `getInstance` non rileva un&#39;istanza esistente, viene creata e restituita una nuova istanza. È simile alla [`s_gi()` funzione ]( https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html) in [!DNL AppMeasurement].

**Uso comune**

L&#39;API del servizio [!DNL Experience Cloud] ID conserva un elenco di tutte le istanze create per ciascun [!DNL Adobe Experience Cloud] ID organizzazione di. Se l&#39;applicazione che utilizza l&#39;API del servizio ID non utilizza un riferimento all&#39;istanza, l&#39;istanza può essere rilevata chiamando `getInstance`, senza bisogno di crearne una nuova. Questa funzione supporta anche più istanze per diverse organizzazioni all&#39;interno della stessa pagina Web o della stessa applicazione.

È utile per le applicazioni che non dispongono di una `init` fase chiara e che devono essere richiamate nell&#39;API del servizio ID in più posizioni. Puoi chiamare `getInstance` da tutte le posizioni, l&#39;istanza verrà creata dalla prima posizione in cui viene eseguito. L&#39;istanza esistente verrà restituita dalle chiamate successive.
