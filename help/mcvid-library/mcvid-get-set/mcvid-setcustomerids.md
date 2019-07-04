---
description: setCustomerIDs imposta una o più coppie chiave/valore che definiscono gli ID cliente e i relativi stati di autenticazione.
keywords: Servizio ID
seo-description: setCustomerIDs imposta una o più coppie chiave/valore che definiscono gli ID cliente e i relativi stati di autenticazione.
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128ea2
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# setCustomerIDs{#setcustomerids}

setCustomerIDs imposta una o più coppie chiave/valore che definiscono gli ID cliente e i relativi stati di autenticazione.

**Sintassi:** `visitor.setCustomerIDs()`

Puoi impostare uno o più ID, come mostrato nel seguente codice di esempio. Vedi [ID cliente e stati di autenticazione](../../mcvid-reference/mcvid-authenticated-state.md) per ulteriori informazioni ed esempi.

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
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

