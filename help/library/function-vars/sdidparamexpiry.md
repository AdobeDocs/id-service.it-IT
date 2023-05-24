---
description: Questa configurazione ti permette di ignorare l'intervallo di scadenza del codice Supplemental Data ID (SDID) predefinito quando trasmetti quell'ID da una pagina all'altra usando la funzione helper appendSupplementalDataIDTo. Per impostazione predefinita, il codice del servizio ID sulla pagina ricevente ha 30 secondi di tempo per ottenere il codice SDID dall'URL inviato dalla pagina inviante. Se il codice del servizio ID sulla pagina ricevente non riesce a recuperare il codice SDID in meno di 30 secondi, richiede un nuovo codice SDID. Questa funzionalità è principalmente per i clienti A4T che devono passare il codice SDID da una pagina all’altra e desiderano controllare questo intervallo di timeout.
keywords: Servizio ID
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 100%

---

# sdidParamExpiry{#sdidparamexpiry}

Questa configurazione ti permette di ignorare l&#39;intervallo di scadenza del codice Supplemental Data ID (SDID) predefinito quando trasmetti quell&#39;ID da una pagina all&#39;altra usando la funzione helper appendSupplementalDataIDTo. Per impostazione predefinita, il codice del servizio ID sulla pagina ricevente ha 30 secondi di tempo per ottenere il codice SDID dall&#39;URL inviato dalla pagina inviante. Se il codice del servizio ID sulla pagina ricevente non riesce a recuperare il codice SDID in meno di 30 secondi, richiede un nuovo codice SDID. Questa funzionalità è principalmente per i clienti A4T che devono passare il codice SDID da una pagina all’altra e desiderano controllare questo intervallo di timeout.

**Ignorare il timeout del codice SDID**

Se hai bisogno di modificare il timeout del codice SDID predefinito, aggiungi `sdidParamExpiry` alla `Visitor.getInstance` funzione con la sintassi seguente:

**Sintassi:** ` sdidParamExpiry: *`tempo in secondi`*`

**Esempio di codice**

Una volta configurato il tuo codice del servizio ID potrebbe assomigliare a questo esempio. Questo esempio imposta il timeout del codice SDID a 15 secondi. Questa configurazione funziona con Metodo helper [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```
