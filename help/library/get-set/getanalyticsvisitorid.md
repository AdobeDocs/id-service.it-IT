---
description: Restituisce l'ID Analytics legacy (se presente) memorizzato nel cookie s_ vi prima dell'implementazione del servizio Experience Platform Identity Service. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.
keywords: Servizio ID
seo-description: Restituisce l'ID Analytics legacy (se presente) memorizzato nel cookie s_ vi prima dell'implementazione del servizio Experience Platform Identity Service. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Restituisce l&#39;ID Analytics legacy (se presente) memorizzato nel cookie s_ vi prima dell&#39;implementazione del servizio Experience Platform Identity Service. Se a un visitatore non è stato assegnato un ID Analytics, restituisce una stringa vuota.

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
>Se sei [!DNL Analytics] un cliente, controlla e invia l&#39; [!DNL Analytics] ID alla funzione. Ad esempio, potresti volere utilizzare entrambi gli identificatori per il passaggio dell&#39;ID visitatore in un elemento nascosto a un&#39;applicazione server che utilizza l&#39;API di inserimento dati. In tal caso, devi raccogliere e restituire [!DNL Experience Cloud] gli ID [!DNL Analytics] visitatore. Consulta [getmarketingcloudvisitorid](../../library/get-set/getmcvid.md).

**Il parametro “aid” è un valore legacy**

Il parametro `aid` viene visualizzato in una stringa di interrogazione in base a due diversi set di condizioni.

**Caso 1**

Il parametro `aid` viene visualizzato in una stringa di interrogazione quando:

* Il servizio [!DNL Experience Cloud] ID è stato distribuito correttamente.
* L&#39;utente che accede a un sito dispone di un ID [!DNL Analytics] precedente memorizzato nel cookie [s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

**Caso 2**

Il `aid` parametro viene visualizzato in una stringa query quando l&#39;organizzazione utilizza un periodo [di tolleranza](../../reference/analytics-reference/grace-period.md) prima di implementare completamente il servizio ID. Se l&#39;utente che accede al sito è nuovo e non utilizzi un periodo di tolleranza, il visitatore riceve il `mid` parametro [!DNL Experience Cloud] (ID).

>[!MORE_ LIKE_ THIS]
>
>* [Cookie di Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

