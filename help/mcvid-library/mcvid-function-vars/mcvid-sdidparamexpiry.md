---
description: Questa configurazione ti permette di ignorare l'intervallo di scadenza del codice Supplemental Data ID (SDID) predefinito quando trasmetti quell'ID da una pagina all'altra usando la funzione helper appendSupplementalDataIDTo. Per impostazione predefinita, il codice del servizio ID sulla pagina ricevente ha 30 secondi di tempo per ottenere il codice SDID dall'URL inviato dalla pagina inviante. Se il codice del servizio ID sulla pagina ricevente non riesce a recuperare il codice SDID in meno di 30 secondi, richiede un nuovo codice SDID. Questa funzionalità è riservata principalmente ai clienti A4T che hanno necessità di trasferire il codice SDID da una pagina all'altra e vogliono controllare questo intervallo di timeout.
keywords: Servizio ID
seo-description: Questa configurazione ti permette di ignorare l'intervallo di scadenza del codice Supplemental Data ID (SDID) predefinito quando trasmetti quell'ID da una pagina all'altra usando la funzione helper appendSupplementalDataIDTo. Per impostazione predefinita, il codice del servizio ID sulla pagina ricevente ha 30 secondi di tempo per ottenere il codice SDID dall'URL inviato dalla pagina inviante. Se il codice del servizio ID sulla pagina ricevente non riesce a recuperare il codice SDID in meno di 30 secondi, richiede un nuovo codice SDID. Questa funzionalità è riservata principalmente ai clienti A4T che hanno necessità di trasferire il codice SDID da una pagina all'altra e vogliono controllare questo intervallo di timeout.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# sdidParamExpiry{#sdidparamexpiry}

Questa configurazione ti permette di ignorare l&#39;intervallo di scadenza del codice Supplemental Data ID (SDID) predefinito quando trasmetti quell&#39;ID da una pagina all&#39;altra usando la funzione helper appendSupplementalDataIDTo. Per impostazione predefinita, il codice del servizio ID sulla pagina ricevente ha 30 secondi di tempo per ottenere il codice SDID dall&#39;URL inviato dalla pagina inviante. Se il codice del servizio ID sulla pagina ricevente non riesce a recuperare il codice SDID in meno di 30 secondi, richiede un nuovo codice SDID. Questa funzionalità è riservata principalmente ai clienti A4T che hanno necessità di trasferire il codice SDID da una pagina all&#39;altra e vogliono controllare questo intervallo di timeout.

**Ignorare il timeout del codice SDID**

Se hai bisogno di modificare il timeout del codice SDID predefinito, aggiungi `sdidParamExpiry` alla `Visitor.getInstance` funzione con la sintassi seguente:

**Sintassi:**` sdidParamExpiry: *`tempo in secondi`*`

**Esempio di codice**

Una volta configurato il tuo codice del servizio ID potrebbe assomigliare a questo esempio. Questo esempio imposta il timeout del codice SDID a 15 secondi. Questa configurazione funziona con Metodo helper [appendSupplementalDataIDTo](../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

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

