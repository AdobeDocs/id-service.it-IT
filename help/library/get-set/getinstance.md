---
description: getInstance restituisce un ID visitatore per l'ID organizzazione Experience Cloud specificato. Questo è necessario per inizializzare l’ID visitatore fornito ad AppMeasurement tramite s.visitor.
keywords: Servizio ID
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
TQID: https://experienceleague.adobe.com/XtjVkeuXAke6g-K8DNmq5kT6aUszrj6W0k9UM2NBBIA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 226
ht-degree: 96%

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
>*Non* creare un&#39;istanza della funzione Visitatore con `var visitor = new Visitor`. Devi usare la chiamata di funzione appropriata indicata qui. Si applica alla [!UICONTROL VisitorAPI.js] libreria di codici v3.0 o superiore.

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

Se `getInstance` non rileva un&#39;istanza esistente, viene creata e restituita una nuova istanza. È simile alla funzione [`s_gi()`](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=it) in [!DNL AppMeasurement].

**Uso comune**

L&#39;API del servizio [!DNL Experience Cloud] ID conserva un elenco di tutte le istanze create per ciascun [!DNL Adobe Experience Cloud] ID organizzazione di. Se l&#39;applicazione che utilizza l&#39;API del servizio ID non utilizza un riferimento all&#39;istanza, l&#39;istanza può essere rilevata chiamando `getInstance`, senza bisogno di crearne una nuova. Questa funzione supporta anche più istanze per diverse organizzazioni all&#39;interno della stessa pagina Web o della stessa applicazione.

È utile per le applicazioni che non dispongono di una `init` fase chiara e che devono essere richiamate nell&#39;API del servizio ID in più posizioni. Puoi chiamare `getInstance` da tutte le posizioni, l&#39;istanza verrà creata dalla prima posizione in cui viene eseguito. L&#39;istanza esistente verrà restituita dalle chiamate successive.

