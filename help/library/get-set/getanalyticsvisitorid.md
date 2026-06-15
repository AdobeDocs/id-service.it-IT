---
description: Restituisce l’ID Analytics legacy (se presente) memorizzato nel cookie s_vi prima dell’implementazione di Experience Cloud Identity Service. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.
keywords: Servizio ID
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
TQID: https://experienceleague.adobe.com/xJRR3qXoJpCnyFqKuEZqvEs0MpPCCA0brWOT6WbngX4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 306
ht-degree: 97%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Restituisce l’ID Analytics legacy (se presente) memorizzato nel cookie s_vi prima dell’implementazione di Experience Cloud Identity Service. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.

**Sintassi** `var analyticsID = visitor.getAnalyticsVisitorID()`

In genere questa funzione viene utilizzata con soluzioni personalizzate che richiedono la lettura dell’ID visitatore. Non viene utilizzata da un’implementazione standard. `getAnalyticsVisitorID` funziona anche con le funzioni di callback per leggere gli [!DNL Analytics] ID di e inviarli al sistema o all&#39;applicazione.

**Codice di esempio**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>Se sei un [!DNL Analytics] cliente, rintraccia e invia [!DNL Analytics]l&#39;ID di alla tua funzione. Ad esempio, potresti volere utilizzare entrambi gli identificatori per il passaggio dell&#39;ID visitatore in un elemento nascosto a un&#39;applicazione server che utilizza l&#39;API di inserimento dati. In tal caso, devi raccogliere e restituire gli ID visitatore di [!DNL Experience Cloud] e di [!DNL Analytics]. Consulta [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**Il parametro “aid” è un valore legacy**

Il `aid` parametro viene visualizzato in una stringa di interrogazione in base a due diversi set di condizioni.

**Caso 1**

Il parametro `aid` viene visualizzato in una stringa di interrogazione quando:

* Il servizio [!DNL Experience Cloud] ID è stato distribuito correttamente.
* L’utente che accede a un sito dispone di un ID [!DNL Analytics] precedente memorizzato nel cookie [s_vi](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=it#section-5d50a078de444d12b7d927d68ff3b679).

**Caso 2**

Il `aid` parametro viene visualizzato in una stringa di interrogazione quando l&#39;organizzazione utilizza un [periodo di tolleranza](https://experienceleague.adobe.com/it/docs/analytics/implementation/id/migration) prima di implementare completamente il servizio ID. Se un nuovo utente accede al sito e non utilizzi un periodo di tolleranza, il visitatore riceve il parametro `mid` (ID [!DNL Experience Cloud]).

>[!MORELIKETHIS]
>
>* [Cookie di Analytics](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-privacy.html?lang=it)

