---
description: Restituisce l'ID di regione del servizio Experience Cloud ID. L'ID di regione (o hint di posizione) è l'identificatore numerico della posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server all'Audience Manager hai bisogno dell'ID regione.
keywords: Servizio ID
seo-description: Restituisce l'ID di regione del servizio Experience Cloud ID. L'ID di regione (o hint di posizione) è l'identificatore numerico della posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server all'Audience Manager hai bisogno dell'ID regione.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc 312 b 7-d 270-4 a 5 c-a 2 bb -0 fbb 37 f 1 e 2 f 4
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# getLocationHint{#getlocationhint}

Restituisce l&#39;ID di regione del servizio Experience Cloud ID. L&#39;ID di regione (o hint di posizione) è l&#39;identificatore numerico della posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server all&#39;Audience Manager hai bisogno dell&#39;ID regione.

**Sintassi:**` var *`nome variabile`* = visitor.getLocationHint()`

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

