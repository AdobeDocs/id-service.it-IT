---
description: Imposta un intervallo di timeout in millisecondi. Utilizzato per comunicare ad altre soluzioni (ad esempio Analytics, Audience Manager, Target, ecc.) quanto tempo attendere una risposta dal servizio ID.
keywords: Servizio ID
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# loadTimeout{#loadtimeout}

Imposta un intervallo di timeout in millisecondi. Utilizzato per comunicare ad altre soluzioni (ad esempio Analytics, Audience Manager, Target, ecc.) quanto tempo attendere una risposta dal servizio ID.

**Sintassi:** ` loadTimeout: *`intervallo in millisecondi`*`

Il valore predefinito è 30.000 millisecondi (30 secondi). Si consiglia vivamente di *non* modificare il valore predefinito.

>[!NOTE]
>
>Le chiamate al servizio ID sono sincronizzate con gli altri codici non Adobe presenti nella pagina. Di conseguenza, se si aumenta o diminuisce l’intervallo di timeout, la frequenza di rendering del contenuto della pagina non viene modificata. Tuttavia, intervalli di timeout lunghi possono influire sui tempi di caricamento delle pagine misurati da comuni strumenti di monitoraggio della rete, ma il tempo di rendering non cambia.

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```
