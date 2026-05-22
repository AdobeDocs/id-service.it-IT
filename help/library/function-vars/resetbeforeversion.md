---
description: Questa configurazione consente di cancellare Experience Cloud ID (ECID) orfani o non aggiornati in base alla versione del servizio ID che si aggiorna.
keywords: Servizio ID
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
TQID: https://experienceleague.adobe.com/5aqi7F5QkybjotjVMJgDWCchFw1XOYa6qPOSUzDyeqE
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 87%

---

# resetBeforeVersion{#resetbeforeversion}

Questa configurazione consente di cancellare Experience Cloud ID (ECID) orfani o non aggiornati in base alla versione del servizio ID che si aggiorna.

Specificando la versione del servizio ID come valore della variabile `resetBeforeVersion` gli ECID superati verranno cancellati dagli ID lato client.

Alcune condizioni, ad esempio i timeout della sessione, potrebbero a volte causare la generazione di un ID lato client senza che il servizio ID ottenga in maniera corretta un ID lato server. Quando si verifica questa situazione, un ID lato client orfano viene tracciato dal servizio ID senza poter essere tracciato tra i domini o sincronizzato in modo appropriato con altre soluzioni. Il comportamento confronta la versione nel cookie AMCV attuale con il valore di `resetBeforeVersion`. Se il cookie non esiste o la versione del cookie è meno recente rispetto all&#39;ultima versione rilasciata di `resetBeforeVersion`, il cookie AMCV viene rimosso e il servizio ID richiede un nuovo ECID.

Per i visitatori che hanno cookie demdex di terze parti sul browser, l&#39;ECID viene controllato per verificare che sia stato generato correttamente usando l&#39;UUID nel cookie demdex. Se la verifica conferma la corretta generazione, il nuovo ECID sarà lo stesso e il visitatore verrà considerato come nuovo. Se per qualche motivo l’ECID da eliminare non era stato generato utilizzando il cookie demdex o se non è presente alcun cookie demdex, il visitatore riceverà un nuovo ECID e sarà considerato come nuovo visitatore.

**Sintassi:** `resetBeforeVersion = "3.3"`

**Esempio di codice**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```

