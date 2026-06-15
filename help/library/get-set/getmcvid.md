---
description: getMarketingCloudVisitorID restituisce l'ID visitatore Experience Cloud.
keywords: Servizio ID
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
TQID: https://experienceleague.adobe.com/Ltpdq4dlGbJ8h0vAZBD52Pq7gLaurxSDYqETkLqQfDw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 118
ht-degree: 100%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID restituisce l&#39;ID visitatore Experience Cloud.

**Sintassi:** `var *`nome variabile`* = visitor.getMarketingCloudVisitorID()`

In genere questa funzione viene utilizzata con soluzioni personalizzate che richiedono la lettura dell’ID visitatore. Non viene utilizzata da un’implementazione standard. `getMarketingCloudVisitorID` funziona anche con le funzioni di callback per leggere gli [!DNL Analytics] ID di e inviarli al sistema o all&#39;applicazione.

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
>Se sei un [!DNL Analytics] cliente, rintraccia e invia [!DNL Analytics] l&#39;ID di alla tua funzione. Ad esempio, potresti volere utilizzare entrambi gli identificatori per il passaggio dell&#39;ID visitatore in un elemento nascosto a un&#39;applicazione server che utilizza l&#39;API di inserimento dati. In tal caso, devi raccogliere e restituire gli ID visitatore di [!DNL Experience Cloud] e di [!DNL Analytics]. Consulta [Ottieni ID visitatore Analytics](../../library/get-set/getanalyticsvisitorid.md).

