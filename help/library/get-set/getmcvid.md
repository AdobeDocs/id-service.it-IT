---
description: getMarketingCloudVisitorID restituisce l'ID visitatore Experience Cloud.
keywords: Servizio ID
seo-description: getMarketingCloudVisitorID restituisce l'ID visitatore Experience Cloud.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93 e 16220-b 5 b 3-4 d 81-9189-30031 bc 15129
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID restituisce l&#39;ID visitatore Experience Cloud.

**Sintassi:**` var *`nome variabile`* = visitor.getMarketingCloudVisitorID()`

Di solito, questo metodo viene usato con soluzioni personalizzate che richiedono la lettura dell&#39;ID visitatore. Non viene utilizzata per l&#39;implementazione standard. `getMarketingCloudVisitorID` funziona anche con le funzioni di callback per leggere gli ID di [!DNL Analytics] e inviarli al sistema o all&#39;applicazione.

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
>Se sei [!DNL Analytics] un cliente, controlla e invia l&#39; [!DNL Analytics] ID alla funzione. Ad esempio, potresti volere utilizzare entrambi gli identificatori per il passaggio dell&#39;ID visitatore in un elemento nascosto a un&#39;applicazione server che utilizza l&#39;API di inserimento dati. In tal caso, devi raccogliere e restituire [!DNL Experience Cloud] gli ID [!DNL Analytics] visitatore. Consulta [Ottieni ID visitatore Analytics](../../library/get-set/getanalyticsvisitorid.md).

