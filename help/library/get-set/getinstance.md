---
description: getInstance restituisce un ID visitatore per l'ID organizzazione Experience Cloud specificato. Questo è necessario per inizializzare l’ID visitatore fornito ad AppMeasurement tramite s.visitor.
keywords: Servizio ID
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '226'
ht-degree: 100%

---

# getInstance{#getinstance}

getInstance restituisce un ID visitatore per l&#39;ID organizzazione Experience Cloud specificato. Questo è necessario per inizializzare l’ID visitatore fornito ad AppMeasurement tramite s.visitor.

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
>*Non* creare un&#39;istanza della funzione Visitatore con `var visitor = new Visitor`. Devi usare la chiamata di funzione appropriata indicata qui. Si applica alla versione 3.0 o successiva della libreria del codice di [!UICONTROL VisitorAPI.js].

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

Se `getInstance` non rileva un&#39;istanza esistente, viene creata e restituita una nuova istanza. È simile alla [funzione `s_gi()`](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=it) in [!DNL AppMeasurement].

**Uso comune**

L&#39;API del servizio [!DNL Experience Cloud] ID conserva un elenco di tutte le istanze create per ciascun [!DNL Adobe Experience Cloud] ID organizzazione di. Se l&#39;applicazione che utilizza l&#39;API del servizio ID non utilizza un riferimento all&#39;istanza, l&#39;istanza può essere rilevata chiamando `getInstance`, senza bisogno di crearne una nuova. Questa funzione supporta anche più istanze per diverse organizzazioni all&#39;interno della stessa pagina Web o della stessa applicazione.

È utile per le applicazioni che non dispongono di una `init` fase chiara e che devono essere richiamate nell&#39;API del servizio ID in più posizioni. Puoi chiamare `getInstance` da tutte le posizioni, l&#39;istanza verrà creata dalla prima posizione in cui viene eseguito. L&#39;istanza esistente verrà restituita dalle chiamate successive.
