---
description: Questa funzione è stata progettata in particolare per aiutare i clienti A4T a risolvere problemi relativi all'utilizzo degli ID su app oppure siti/schermate a pagina singola.
keywords: Servizio ID
seo-description: Questa funzione è stata progettata in particolare per aiutare i clienti A4T a risolvere problemi relativi all'utilizzo degli ID su app oppure siti/schermate a pagina singola.
seo-title: resetState
title: resetState
uuid: ed 7 be 76 d-a 7 ee -4 e 51-b 26 c -456 ff 85 fd 096
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# resetState{#resetstate}

Questa funzione è stata progettata in particolare per aiutare i clienti A4T a risolvere problemi relativi all&#39;utilizzo degli ID su app oppure siti/schermate a pagina singola.

## Casi d&#39;uso {#section-840b88a5cdb042488b340cad5d7b22a5}

Come cliente A 4 T che usa il servizio ID, potresti voler usare la `visitor.resetState()` funzione quando devi:

* Trasmettere un Supplemental Data ID (SDID) o qualsiasi altro ID da una pagina o una schermata a un&#39;altra mediante un rendirizzamento. Normalmente, il servizio ID non trasmetterà questo ID senza questa funzione.
* Usare il codice che aggiorna esclusivamente sezioni specifiche di una pagina o di un&#39;app mediante chiamate Ajax e vuoi tenere traccia di quelle azioni. Ad esempio, supponiamo che tu abbia una pagina in cui solo facendo clic su un oggetto si carica o si modifica una sezione speciale. In questo caso, il servizio ID non può richiedere un ID diverso a meno che la pagina sia ricaricata. Tuttavia, con `visitor.resetState()`, potete richiedere un nuovo ID a queste condizioni.

Vedi gli esempi di codice seguenti.

## Sintassi {#section-9e63503e178f4be28ac850abf44d6d91}

**Sintassi:**` visitor.resetState( *`state`*);`

## Esempi di codice {#section-d75b211bb4ea473887eb284de2ad838b}

L&#39;implementazione del servizio ID influisce sul modo in cui questa funzione verrebbe usata. Per gli esempi fare riferimento alla tabella seguente.

**Implementazione lato server**

Un&#39;implementazione lato server è rivolta ai clienti A 4 T con implementazioni lato server e lato client di [!DNL Target], [!DNL Analytics]e il servizio ID. Se hai impostato il servizio ID con questo metodo, tutto ciò che devi fare è aggiungere `visitor.resetState()` alla pagina. Le chiamate al servizio ID restituiranno automaticamente un nuovo ID e lo stato del server.

**Implementazione non standard** (con ID)

Se hai impostato il servizio ID con un&#39;[implementazione non standard](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113), devi configurare un oggetto variabile per mantenere l&#39;SDID (o altri ID) che desideri trasmettere con `visitor.resetState()`. Come mostrato di seguito, questo includerebbe l&#39;[ID organizzazione](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) e l&#39;ID che desideri trasmettere. Il codice sarà simile all&#39;esempio di seguito.

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**Implementazione non standard** (senza passare un ID)

In questo caso, `visitor.resetState()` può essere utilizzato per generare un nuovo ID. Questo può essere utile in un&#39;app a pagina singola quando un utente naviga su una nuova schermata senza riaggiornare la pagina e tu hai bisogno di un nuovo ID.

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

**Dynamic Tag Manager (DTM)**

Attualmente, non esiste un percorso di configurazione DTM per `visitor.resetState()`.
