---
description: Restituisce l’ID Analytics legacy (se presente) memorizzato nel cookie s_vi prima dell’implementazione del servizio Experience Cloud Identity. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.
keywords: ID Service
seo-description: Restituisce l’ID Analytics legacy (se presente) memorizzato nel cookie s_vi prima dell’implementazione del servizio Experience Cloud Identity. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6bb8ddfc-9fc1-4105-b377-d9b4d247a0f8
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Restituisce l’ID Analytics legacy (se presente) memorizzato nel cookie s_vi prima dell’implementazione del servizio Experience Cloud Identity. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.

**Sintassi** `var analyticsID = visitor.getAnalyticsVisitorID()`

In genere, questa funzione viene utilizzata con soluzioni personalizzate che richiedono la lettura dell&#39;ID visitatore. Non viene utilizzato da un&#39;implementazione standard. `getAnalyticsVisitorID` funziona anche con le funzioni di callback per leggere gli [!DNL Analytics] ID di e inviarli al sistema o all&#39;applicazione.

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
* L’utente che accede a un sito dispone di un ID [!DNL Analytics] precedente memorizzato nel cookie [s_vi](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-analytics.html#section-5d50a078de444d12b7d927d68ff3b679).

**Caso 2**

Il `aid` parametro viene visualizzato in una stringa di interrogazione quando l&#39;organizzazione utilizza un [periodo di tolleranza](../../reference/analytics-reference/grace-period.md) prima di implementare completamente il servizio ID. Se un nuovo utente accede al sito e non utilizzi un periodo di tolleranza, il visitatore riceve il parametro `mid` (ID [!DNL Experience Cloud]).

>[!MORELIKETHIS]
>
>* [Cookie di Analytics](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-privacy.html)

