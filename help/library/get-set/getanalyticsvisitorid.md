---
description: Restituisce l'ID Analytics legacy (se presente) memorizzato nel cookie s_ vi prima dell'implementazione del servizio Experience Cloud ID. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.
keywords: Servizio ID
seo-description: Restituisce l'ID Analytics legacy (se presente) memorizzato nel cookie s_ vi prima dell'implementazione del servizio Experience Cloud ID. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Restituisce l&#39;ID Analytics legacy (se presente) memorizzato nel cookie s_ vi prima dell&#39;implementazione del servizio Experience Cloud ID. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.

**Sintassi** `var analyticsID = visitor.getAnalyticsVisitorID()`

Di solito, questa funzione viene usata con soluzioni personalizzate che richiedono la lettura dell&#39;ID visitatore. Non viene utilizzata per l&#39;implementazione standard. `getAnalyticsVisitorID` funziona anche con le funzioni di callback per leggere gli ID di [!DNL Analytics] e inviarli al sistema o all&#39;applicazione.

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
>If you&#39;re an [!DNL Analytics] customer, also check for and send the [!DNL Analytics] ID to your function. Ad esempio, potresti volere utilizzare entrambi gli identificatori per il passaggio dell&#39;ID visitatore in un elemento nascosto a un&#39;applicazione server che utilizza l&#39;API di inserimento dati. In this case, you should collect and return the [!DNL Experience Cloud] and [!DNL Analytics] visitor IDs. See [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**Il parametro “aid” è un valore legacy**

Il parametro `aid` viene visualizzato in una stringa di interrogazione in base a due diversi set di condizioni.

**Caso 1**

Il parametro `aid` viene visualizzato in una stringa di interrogazione quando:

* The [!DNL Experience Cloud] ID service is deployed correctly.
* L&#39;utente che accede a un sito dispone di un ID [!DNL Analytics] precedente memorizzato nel cookie [s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

**Caso 2**

You will see the `aid` parameter in a query string when your organization is using a [grace period](../../reference/analytics-reference/grace-period.md) before fully implementing the ID service. If the user visiting your site is new, and you&#39;re not using a grace period, the visitor will get the `mid` ( [!DNL Experience Cloud] ID) parameter.

>[!MORE_ LIKE_ THIS]
>
>* [Cookie di Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

