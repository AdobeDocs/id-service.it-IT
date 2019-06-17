---
description: Il servizio ID utilizza l'ID organizzazione, il cookie AMCV di Experience Cloud e il cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie permettono al servizio ID di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le varie soluzioni Experience Cloud.
keywords: playstation; Servizio ID
seo-description: Il servizio ID utilizza l'ID organizzazione, il cookie AMCV di Experience Cloud e il cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie permettono al servizio ID di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le varie soluzioni Experience Cloud.
seo-title: Cookie e il servizio Experience Cloud ID
title: Cookie e il servizio Experience Cloud ID
uuid: c 5 cbd 235-37 ee -4605-8792-b 1 a 991 e 190 ad
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Cookie e il servizio Experience Cloud ID{#cookies-and-the-experience-cloud-id-service}

Il servizio ID utilizza l&#39;ID organizzazione, il cookie AMCV di Experience Cloud e il cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie permettono al servizio ID di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le varie soluzioni Experience Cloud.

## I cookie del servizio ID {#section-f438168beaec409ab8b2cc58bd021e26}

Il servizio ID funziona correttamente se usa i cookie AMCV, AMCVS e demdex. Questi cookie sono semplicemente file che archiviano i dati usati dal servizio ID. Questi cookie del servizio ID non sono pericolosi, dannosi o diversi dagli altri cookie di prima parte o di terze parti memorizzati da un sito Web o da un servizio in un browser e seguono le stesse regole dei cookie di prima e terze parti. Per ulteriori informazioni sui cookie utilizzati dal servizio ID, fai riferimento alle seguenti sezioni.

**I cookie del servizio ID**

* Impostare e archiviare un ID univoco per i visitatori del tuo sito (il MID).
* Mantenere questo ID univoco permettendo al servizio ID di raccogliere e condividere i dati con altre soluzioni Experience Cloud.
* Tracciare gli utenti nei vari domini. Questa funzione richiede però la presenza di altri domini dotati di un codice del servizio ID.

** Ciò che le ookies del servizio ID non possono fare**

* Archiviare, trasmettere o eseguire virus sui computer.
* Accedere o archiviare informazioni personali identificabili (PII) come il tuo indirizzo e-mail.
* Controllare l&#39;hardware o il software dei computer.
* Creare instabilità nei computer o ridurne le prestazioni.
* Tracciare gli utenti su siti che non fanno uso del servizio ID.

## Cookie AMCV {#section-c55af54828dc4cce89f6118655d694c8}

I seguenti attributi del cookie impostato dal servizio ID.

**Nome**

Il nome del cookie AMCV segue la sintassi `AMCV_<variable name>@AdobeOrg`. Nel nome, `<variable name>` gli elementi sono segnaposto per parte dell&#39;ID organizzazione Experience Cloud. L&#39;ID viene inviato al DCS dalla funzione `Visitor.getInstance` nel codice del servizio ID.

Il nome completo del cookie deve essere simile al seguente:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenuto**

Il cookie AMCV contiene l&#39;ID o il MID del visitatore di Experience Cloud. The MID is stored in a key-value pair that follows this syntax, `mid|<Experience Cloud ID>`.

La coppia chiave/valore completa deve essere simile alla seguente:

```
mid|20265673158980419722735089753036633573
```

Questo identificatore costante consente la condivisione dei dati tra più soluzioni.

**Dominio**

Il cookie AMCV è impostato nel dominio di prima parte di un browser. Ciò significa che è impostato nel dominio del sito visualizzato al momento da un utente. Di conseguenza, il codice del servizio ID e altre librerie di codici Experience Cloud possono leggere il MID memorizzato nel cookie AMCV.

Tuttavia, poiché il cookie AMCV è impostato nel dominio di prime parti, non può essere utilizzato per monitorare e identificare gli utenti nei diversi domini. Quando un visitatore del sito accede a un dominio diverso, il servizio ID si basa invece sull&#39;ID organizzazione e sull&#39;ID demdex per restituire il MID corretto.

## Cookie AMCVS {#section-92a9454f1ac645948f9059b9fad928bf}

**Nome**

Il nome del cookie AMCVS segue la sintassi `AMCVS_####@AdobeOrg`. Nel nome, gli elementi #### devono essere sostituiti dall&#39;ID organizzazione Experience Cloud. Questo ID viene passato al DCS by `theVisitor.getInstance` funzione nel codice del servizio ID.

Il nome completo del cookie deve essere simile al seguente:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenuto**

Il cookie AMCVS serve da flag per indicare che la sessione è stata inizializzata. Il suo valore è sempre `1` e continua quando la sessione è terminata.

**Dominio**

Il cookie AMCVS è impostato nel dominio di prima parte di un browser. Ciò significa che è impostato nel dominio del sito visualizzato al momento da un utente.

![](assets/AMCVS-cookie.png)

## Cookie demdex {#section-7ff7d96d6e4141b08a84a75a63d7814c}

Nella seguente tabella sono elencati e definiti alcuni importanti attributi del cookie demdex.

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Attributo </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Nome</b> </p> </td> 
   <td colname="col2"> <p>Il nome del cookie è “demdex”. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Contenuto</b> </p> </td> 
   <td colname="col2"> <p>Il cookie demdex contiene l'ID demdex, generato dal DCS. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Dominio</b> </p> </td> 
   <td colname="col2"> <p>Il cookie demdex è impostato nel dominio demdex.net di terze parti del browser. Questo dominio è separato dal sito visitato al momento dall'utente. </p> <p>A differenza del cookie di prime parti, il cookie AMCV, il cookie demdex e l'ID restano costanti nei diversi domini. L'ID demdex e l'ID organizzazione sono i valori comuni che permettono al servizio ID di restituire e identificare il visitatore di un sito con l'ID visitatore corretto. </p> </td> 
  </tr> 
 </tbody> 
</table>

Per informazioni correlate, consultate [Informazioni sulle chiamate al dominio demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

## Generazione dell&#39;Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

L&#39;Experience Cloud ID (MID) viene derivato matematicamente dall&#39;ID organizzazione e dall&#39;ID demdex. Fintanto che questi ID restano costanti la generazione del MID corretto per un utente specifico è semplicemente un problema matematico. Utilizzando lo stesso ID organizzazione e lo stesso ID demdex, il valore MID è sempre lo stesso. In questo modo il servizio ID può tracciare i visitatori nei vari domini che controlli e che hai configurato con il codice del servizio ID.

Il servizio ID inizia a creare un MID non appena la tua pagina viene caricata. Durante il processo, il codice fornito dalla libreria di codici `visitorAPI.js` invia l&#39;ID organizzazione in una chiamata evento al servizio ID. Il servizio ID crea e restituisce il MID e un ID demdex, rispettivamente, nei cookie AMCV e demdex.

## Passaggi successivi {#section-8db1727a63bc4ff68b495f270315d453}

Scopri [in che modo il servizio Experience Cloud ID richiede e imposta gli ID…](../mcvid-introduction/mcvid-id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)