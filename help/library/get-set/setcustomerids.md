---
description: setCustomerIDs imposta una o più coppie chiave/valore che definiscono gli ID cliente e i relativi stati di autenticazione.
keywords: Servizio ID
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# setCustomerIDs{#setcustomerids}

setCustomerIDs imposta una o più coppie chiave/valore che definiscono gli ID cliente e i relativi stati di autenticazione.

**Sintassi:** `visitor.setCustomerIDs()`

Puoi impostare uno o più ID, come mostrato nel seguente codice di esempio. Consulta [ID cliente e stati di autenticazione](../../reference/authenticated-state.md) per ulteriori informazioni ed esempi.

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```
