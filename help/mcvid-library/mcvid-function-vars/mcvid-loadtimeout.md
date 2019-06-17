---
description: Imposta un intervallo di timeout in millisecondi. Viene usato per comunicare alle altre soluzioni (es, Analytics, Audience Manager, Target, ecc.) quanto tempo attendere una risposta dal servizio ID.
keywords: Servizio ID
seo-description: Imposta un intervallo di timeout in millisecondi. Viene usato per comunicare alle altre soluzioni (es, Analytics, Audience Manager, Target, ecc.) quanto tempo attendere una risposta dal servizio ID.
seo-title: loadTimeout
title: loadTimeout
uuid: f 627 e 044-bd 73-49 a 4-8 a 90-6 d 19 aa 566751
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# loadTimeout{#loadtimeout}

Imposta un intervallo di timeout in millisecondi. Viene usato per comunicare alle altre soluzioni (es, Analytics, Audience Manager, Target, ecc.) quanto tempo attendere una risposta dal servizio ID.

**Sintassi:**` loadTimeout: *`intervallo in millisecondi`*`

Il valore predefinito è 30.000 millisecondi (30 secondi). Ti consigliamo caldamente di *non* modificare il valore predefinito.

>[!NOTE]
>
>Le chiamate al servizio ID sono asincrone in relazione ad altri codice non Adobe sulla pagina. Di conseguenza, se si aumenta o diminuisce l&#39;intervallo di timeout, la frequenza di rendering dei contenuti della pagina non viene modificata. Tuttavia, intervalli di timeout troppo lunghi possono influire sui tempi di caricamento della pagina, misurati da comuni strumenti di monitoraggio della rete, anche se la frequenza di rendering rimane inalterata.

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

