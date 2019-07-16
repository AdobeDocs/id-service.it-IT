---
description: Restituisce l'ID della regione del servizio Identità Experience Platform. L'ID di regione (o hint di posizione) è l'identificatore numerico della posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server all'Audience Manager hai bisogno dell'ID regione.
keywords: Servizio ID
seo-description: Restituisce l'ID della regione del servizio Identità Experience Platform. L'ID di regione (o hint di posizione) è l'identificatore numerico della posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server all'Audience Manager hai bisogno dell'ID regione.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# getLocationHint{#getlocationhint}

Restituisce l&#39;ID della regione del servizio Identità Experience Platform. L&#39;ID di regione (o hint di posizione) è l&#39;identificatore numerico della posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server all&#39;Audience Manager hai bisogno dell&#39;ID regione.

**Sintassi:** ` var *`nome variabile`* = visitor.getLocationHint()`

Per un elenco degli ID di regione e delle posizioni corrispondenti, consulta [ID di regione DCS, posizioni e nomi host](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html).

**Esempio di codice**

La funzione di hint posizione legge l&#39;ID di regione dal cookie AMCV. Se l&#39;ID di regione è già impostato nel cookie AMCV, il callback avviene subito. In caso contrario, la funzione attende una risposta dal server prima di passare l&#39;ID di regione al callback. Il codice sarà simile all&#39;esempio di seguito.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

