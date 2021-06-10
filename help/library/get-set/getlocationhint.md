---
description: Restituisce l’ID di regione del servizio Experience Cloud Identity. Un ID di regione (o hint di posizione) è un identificatore numerico per la posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server ad Audience Manager è necessario disporre dell’ID di regione.
keywords: Servizio ID
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

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
