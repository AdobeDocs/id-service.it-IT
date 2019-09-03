---
description: Restituisce l’ID di regione del servizio Experience Cloud Identity. L'ID di regione (o hint di posizione) è l'identificatore numerico della posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server all'Audience Manager hai bisogno dell'ID regione.
keywords: Servizio ID
seo-description: Restituisce l’ID di regione del servizio Experience Cloud Identity. L'ID di regione (o hint di posizione) è l'identificatore numerico della posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server all'Audience Manager hai bisogno dell'ID regione.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# getLocationHint{#getlocationhint}

Restituisce l’ID di regione del servizio Experience Cloud Identity. L'ID di regione (o hint di posizione) è l'identificatore numerico della posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server all'Audience Manager hai bisogno dell'ID regione.

**Sintassi:** ` var *`nome variabile`* = visitor.getLocationHint()`

Per un elenco degli ID regioni e delle posizioni corrispondenti, consulta [ID regioni DCS, posizioni e nomi host](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html).

**Esempio di codice**

La funzione di hint posizione legge l'ID di regione dal cookie AMCV. Se l'ID di regione è già impostato nel cookie AMCV, il callback avviene subito. In caso contrario, la funzione attende una risposta dal server prima di passare l'ID di regione al callback. Il codice sarà simile all'esempio di seguito.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

