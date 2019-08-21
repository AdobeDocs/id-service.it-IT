---
description: getMarketingCloudVisitorID restituisce l'ID visitatore Experience Cloud.
keywords: Servizio ID
seo-description: getMarketingCloudVisitorID restituisce l'ID visitatore Experience Cloud.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID restituisce l&#39;ID visitatore Experience Cloud.

**Sintassi:** ` var *`nome variabile`* = visitor.getMarketingCloudVisitorID()`

Di solito, questo metodo viene usato con soluzioni personalizzate che richiedono la lettura dell&#39;ID visitatore. Non viene utilizzata per l&#39;implementazione standard. `getMarketingCloudVisitorID` funziona anche con le funzioni di callback per leggere gli [!DNL Analytics] ID di e inviarli al sistema o all&#39;applicazione.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingClouidID)
```

>[!TIP]
>
>Se sei un [!DNL Analytics] cliente, rintraccia e invia [!DNL Analytics] l&#39;ID di alla tua funzione. Ad esempio, potresti volere utilizzare entrambi gli identificatori per il passaggio dell&#39;ID visitatore in un elemento nascosto a un&#39;applicazione server che utilizza l&#39;API di inserimento dati. In tal caso, devi raccogliere e restituire gli ID visitatore di [!DNL Experience Cloud] e di [!DNL Analytics]. Consulta [Ottieni ID visitatore Analytics](../../library/get-set/getanalyticsvisitorid.md).

