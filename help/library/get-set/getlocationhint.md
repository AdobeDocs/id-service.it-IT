---
description: Restituisce l’ID di regione di Experience Cloud Identity Service. Un ID di regione (o hint di posizione) è un identificatore numerico per la posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server ad Audience Manager è necessario disporre dell’ID di regione.
keywords: Servizio ID
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
TQID: https://experienceleague.adobe.com/Q58a-bmHINs-3mhlUarH8Ipo85tNhjTjMDSlZLFcHsw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 195
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

Restituisce l’ID di regione di Experience Cloud Identity Service. Un ID di regione (o hint di posizione) è un identificatore numerico per la posizione geografica di un particolare datacenter del servizio ID. Per effettuare chiamate API lato server ad Audience Manager è necessario disporre dell’ID di regione.

**Sintassi:** `var *`nome variabile`* = visitor.getLocationHint()`

Per un elenco degli ID di regione e delle posizioni corrispondenti, consulta [ID di regione DCS, posizioni e nomi host](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=it).

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

