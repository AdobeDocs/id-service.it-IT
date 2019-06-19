---
description: getInstance restituisce un ID visitatore per l'ID organizzazione Experience Cloud specificato. Questo ID è richiesto per inizializzare l'ID visitatore fornito ad AppMeasurement tramite s.visitor.
keywords: Servizio ID
seo-description: getInstance restituisce un ID visitatore per l'ID organizzazione Experience Cloud specificato. Questo ID è richiesto per inizializzare l'ID visitatore fornito ad AppMeasurement tramite s.visitor.
seo-title: getInstance
title: getInstance
uuid: 259 b 88 a 6-e 3 d 0-4 aab-b 935-566099 bdab 98
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

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
>*Non* creare un&#39;istanza della funzione Visitatore con `var visitor = new Visitor`. Devi usare la chiamata di funzione appropriata indicata qui. Si applica alla libreria di codici [!DNL VisitorAPI.js] v3.0 o superiore.

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

Se `getInstance` non rileva un&#39;istanza esistente, viene creata e restituita una nuova istanza. Simile alla [`s_gi()` funzione ](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html) in [!DNL AppMeasurement].

**Uso comune**

L&#39;API del servizio [!DNL Experience Cloud] ID conserva un elenco di tutte le istanze create per ciascun [!DNL Adobe Experience Cloud] ID organizzazione. Se l&#39;applicazione che utilizza l&#39;API del servizio ID non utilizza un riferimento all&#39;istanza, l&#39;istanza può essere rilevata chiamando `getInstance`, senza bisogno di crearne una nuova. Questa funzione supporta anche più istanze per diverse organizzazioni all&#39;interno della stessa pagina Web o della stessa applicazione.

È utile per le applicazioni che non dispongono di una fase `init` chiara e che devono essere richiamate nell&#39;API del servizio ID in più posizioni. Puoi chiamare `getInstance` da tutte le posizioni, l&#39;istanza verrà creata dalla prima posizione in cui viene eseguito. L&#39;istanza esistente verrà restituita dalle chiamate successive.
