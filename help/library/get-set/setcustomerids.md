---
description: setCustomerIDs imposta una o più coppie chiave/valore che definiscono gli ID cliente e i relativi stati di autenticazione.
keywords: Servizio ID
seo-description: setCustomerIDs imposta una o più coppie chiave/valore che definiscono gli ID cliente e i relativi stati di autenticazione.
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4 f 960 f 98-cec 2-4 db 6-84 ea -0259 e 2128 ea 2
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# setCustomerIDs{#setcustomerids}

setCustomerIDs imposta una o più coppie chiave/valore che definiscono gli ID cliente e i relativi stati di autenticazione.

**Sintassi:** `visitor.setCustomerIDs()`

Puoi impostare uno o più ID, come mostrato nel seguente codice di esempio. Vedi [ID cliente e stati di autenticazione](../../reference/authenticated-state.md) per ulteriori informazioni ed esempi.

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

