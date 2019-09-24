---
description: Imposta un intervallo di timeout in millisecondi. Viene usato per comunicare alle altre soluzioni (es, Analytics, Audience Manager, Target, ecc.) quanto tempo attendere una risposta dal servizio ID.
keywords: Servizio ID
seo-description: Imposta un intervallo di timeout in millisecondi. Viene usato per comunicare alle altre soluzioni (es, Analytics, Audience Manager, Target, ecc.) quanto tempo attendere una risposta dal servizio ID.
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# loadTimeout{#loadtimeout}

Imposta un intervallo di timeout in millisecondi. Viene usato per comunicare alle altre soluzioni (es, Analytics, Audience Manager, Target, ecc.) quanto tempo attendere una risposta dal servizio ID.

**Sintassi:** ` loadTimeout: *`intervallo in millisecondi`*`

Il valore predefinito è 30.000 millisecondi (30 secondi). Ti consigliamo caldamente di *non* modificare il valore predefinito.

>[!NOTE]
>
>Le chiamate al servizio ID sono sincronizzate con gli altri codici non Adobe presenti nella pagina. Di conseguenza, se si aumenta o diminuisce l'intervallo di timeout, la frequenza di rendering dei contenuti della pagina non viene modificata. Tuttavia, intervalli di timeout troppo lunghi possono influire sui tempi di caricamento della pagina, misurati da comuni strumenti di monitoraggio della rete, anche se la frequenza di rendering rimane inalterata.

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

