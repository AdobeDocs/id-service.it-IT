---
description: Questa configurazione consente di cancellare Experience Cloud ID (ECID) orfani o non aggiornati in base alla versione del servizio ID che si aggiorna.
keywords: Servizio ID
seo-description: Questa configurazione consente di cancellare Experience Cloud ID (ECID) orfani o non aggiornati in base alla versione del servizio ID che si aggiorna.
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# resetBeforeVersion{#resetbeforeversion}

Questa configurazione consente di cancellare Experience Cloud ID (ECID) orfani o non aggiornati in base alla versione del servizio ID che si aggiorna.

Specificando la versione del servizio ID come valore della variabile `resetBeforeVersion` gli ECID superati verranno cancellati dagli ID lato client.

Alcune condizioni, ad esempio i timeout della sessione, potrebbero a volte causare la generazione di un ID lato client senza che il servizio ID ottenga in maniera corretta un ID lato server. Quando si verifica questa situazione, un ID lato client orfano viene tracciato dal servizio ID senza poter essere tracciato tra i domini o sincronizzato in modo appropriato con altre soluzioni. Il comportamento confronta la versione nel cookie AMCV attuale con il valore di `resetBeforeVersion`. Se il cookie non esiste o la versione del cookie è meno recente rispetto all&#39;ultima versione rilasciata di `resetBeforeVersion`, i cookie AMCV vengono rimossi e il servizio ID richiede un nuovo ECID.

Per i visitatori che hanno cookie demdex di terze parti sul browser, l&#39;ECID viene controllato per verificare che sia stato generato correttamente usando l&#39;UUID nel cookie demdex. Se la verifica conferma la corretta generazione, il nuovo ECID sarà lo stesso e il visitatore verrà considerato come nuovo. Se per qualche ragione l&#39;ECID che viene cancellato non è stato generato correttamente usando il cookie demdex o se non esiste alcun cookie demdex, il visitatore riceverà un nuovo ECID e verrà considerato come nuovo.

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

