---
description: Restituisce l’ID di regione del servizio Experience Cloud Identity. Un ID di regione (o hint di posizione) è un identificatore numerico per la posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server ad Audience Manager è necessario disporre dell’ID di regione.
keywords: ID Service
seo-description: Restituisce l’ID di regione del servizio Experience Cloud Identity. Un ID di regione (o hint di posizione) è un identificatore numerico per la posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server ad Audience Manager è necessario disporre dell’ID di regione.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 100%

---


# getLocationHint {#getlocationhint}

Restituisce l’ID di regione del servizio Experience Cloud Identity. Un ID di regione (o hint di posizione) è un identificatore numerico per la posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server ad Audience Manager è necessario disporre dell’ID di regione.

**Sintassi:** ` var *`nome variabile`* = visitor.getLocationHint()`

Per un elenco degli ID di regione e delle posizioni corrispondenti, consulta [ID di regione DCS, posizioni e nomi host](https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

**Esempio di codice**

La funzione dell’hint di posizione legge l’ID di regione dal cookie AMCV. Se l’ID di regione è già impostato nel cookie AMCV, il callback avviene immediatamente. Se l’ID di regione non è impostato, la funzione attende una risposta dal server prima di passare l’ID di regione al callback. Il codice sarà simile all&#39;esempio di seguito.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

