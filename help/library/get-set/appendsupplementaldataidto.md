---
description: Questo metodo helper ti consente di aggiungere a un URL di reindirizzamento il codice Supplemental Data ID (SDID) sotto forma di parametro della stringa di interrogazione. È utile quando stai usando A4T e hai bisogno di mantenere il codice SDID da una pagina all'altra e di unire insieme le visite separate. Per utilizzare questa funzione, devi aver implementato il servizio ID con lo stesso ID organizzazione nei domini di origine e di destinazione.
keywords: ID Service
seo-description: Questo metodo helper ti consente di aggiungere a un URL di reindirizzamento il codice Supplemental Data ID (SDID) sotto forma di parametro della stringa di interrogazione. È utile quando stai usando A4T e hai bisogno di mantenere il codice SDID da una pagina all'altra e di unire insieme le visite separate. Per utilizzare questa funzione, devi aver implementato il servizio ID con lo stesso ID organizzazione nei domini di origine e di destinazione.
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 77%

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Questo metodo helper ti consente di aggiungere a un URL di reindirizzamento il codice Supplemental Data ID (SDID) sotto forma di parametro della stringa di interrogazione. È utile quando stai usando A4T e hai bisogno di mantenere il codice SDID da una pagina all&#39;altra e di unire insieme le visite separate. Per utilizzare questa funzione, devi aver implementato il servizio ID con lo stesso ID organizzazione nei domini di origine e di destinazione.

Sommario:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Sintassi ed esempio di codice </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Output di esempio </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Sintassi ed esempio di codice </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> Modifica del timeout del codice SDID con sdidParamExpiry </a> </li> 
</ul>

## Sintassi ed esempio di codice {#section-cbb0b2f73bcc418386796c24c01b2365}

**Sintassi:**` appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## Output di esempio  {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Come mostrato di seguito, l&#39;URL reindirizza il codice SDID visitatore, l&#39;ID organizzazione e la marca temporale UNIX nella chiamata alla pagina ricevente.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Modifica del timeout del codice SDID con sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

La configurazione [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) ti permette di ignorare l&#39;intervallo di scadenza del codice SDID predefinito quando trasmetti quell&#39;ID da una pagina all&#39;altra usando la funzione helper `appendSupplementalDataIDTo`. Per impostazione predefinita, il codice del servizio ID sulla pagina ricevente ha 30 secondi di tempo per ottenere il codice SDID dall&#39;URL inviato dalla pagina inviante. Se il codice del servizio ID sulla pagina ricevente non riesce a recuperare il codice SDID in meno di 30 secondi, richiede un nuovo codice SDID. Questa funzionalità è destinata principalmente ai clienti A4T che devono passare il codice SDID da una pagina all’altra e desiderano controllare questo intervallo di timeout.

Se hai bisogno di modificare il timeout del codice SDID predefinito, aggiungi `sdidParamExpiry` alla `Visitor.getInstance` funzione con la sintassi seguente:

**Sintassi:**` sdidParamExpiry: *`tempo in secondi`*`

**Esempio di codice**

Una volta configurato il tuo codice del servizio ID potrebbe assomigliare a questo esempio. Questo esempio imposta il timeout del codice SDID a 15 secondi.

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

