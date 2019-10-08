---
description: getMarketingCloudVisitorID restituisce l'ID visitatore Experience Cloud.
keywords: Servizio ID
seo-description: getMarketingCloudVisitorID restituisce l'ID visitatore Experience Cloud.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
translation-type: tm+mt
source-git-commit: 4a5fbc971dc950c65e5c8f92dffdfe5dde528b54

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID restituisce l'ID visitatore Experience Cloud.

**Sintassi:** ` var *`nome variabile`* = visitor.getMarketingCloudVisitorID()`

Di solito, questo metodo viene usato con soluzioni personalizzate che richiedono la lettura dell'ID visitatore. Non viene utilizzata per l'implementazione standard. `getMarketingCloudVisitorID` funziona anche con le funzioni di callback per leggere gli [!DNL Analytics] ID di e inviarli al sistema o all'applicazione.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Se sei un [!DNL Analytics] cliente, rintraccia e invia [!DNL Analytics] l'ID di alla tua funzione. Ad esempio, potresti volere utilizzare entrambi gli identificatori per il passaggio dell'ID visitatore in un elemento nascosto a un'applicazione server che utilizza l'API di inserimento dati. In tal caso, devi raccogliere e restituire gli ID visitatore di [!DNL Experience Cloud] e di [!DNL Analytics]. Consulta [Ottieni ID visitatore Analytics](../../library/get-set/getanalyticsvisitorid.md).

