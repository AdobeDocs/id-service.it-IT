---
description: Il servizio ID visitatore utilizza l’ID organizzazione IMS, il cookie AMCV di CX Enterprise e un cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie consentono al servizio ID visitatore di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le diverse soluzioni aziendali CX.
keywords: playstation;Servizio ID visitatore
title: Cookie e il servizio ID visitatore di Adobe
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
TQID: https://experienceleague.adobe.com/iLOFGQ9t-DqYfqOZs3K5yZI7903dMPEjANaJ7lH8K0o
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 990
ht-degree: 42%

---

# Cookie e il servizio ID visitatore di Adobe{#cookies-and-the-experience-cloud-id-service}

Il servizio ID visitatore utilizza l’ID organizzazione IMS, il cookie AMCV di CX Enterprise e un cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie consentono al servizio ID visitatore di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le diverse soluzioni aziendali CX.

## Informazioni sui cookie del servizio ID visitatore {#section-f438168beaec409ab8b2cc58bd021e26}

Il Servizio ID visitatore si basa sul corretto funzionamento dei cookie AMCV, AMCVS e demdex. Questi cookie sono solo file che memorizzano i dati utilizzati dal servizio ID visitatore. Questi cookie del Servizio ID visitatore non sono pericolosi, dannosi o diversi da altri cookie di prima parte o di terze parti memorizzati da un sito web o da un servizio in un browser, seguendo le stesse regole che disciplinano altri cookie di prima e terze parti. Per ulteriori informazioni sui cookie utilizzati dal servizio ID visitatori, consulta le sezioni seguenti.

### Quali sono le funzioni dei cookie del servizio ID visitatore

* Imposta e archivia un ID univoco per i visitatori del tuo sito (il MID).
* Mantenere questo ID univoco in modo che il Servizio ID visitatore possa raccogliere e condividere i dati con altre soluzioni CX Enterprise.
* Tracciare gli utenti nei vari domini. Tuttavia, questo richiede che tu sia il proprietario di questi altri domini e che su di essi sia distribuito il codice del servizio ID visitatore.

### Quali funzioni non possono essere svolte dai cookie del servizio ID visitatore

* Archiviare, trasmettere o eseguire virus del computer.
* Accedere o archiviare informazioni personali identificabili (PII) come il tuo indirizzo e-mail.
* Controllare l’hardware o il software del computer.
* Rendere i computer instabili o causare problemi di prestazione.
* Monitora gli utenti sui siti che non utilizzano il servizio ID visitatore.

## Cookie AMCV {#section-c55af54828dc4cce89f6118655d694c8}

I seguenti attributi del cookie impostati dal servizio ID visitatore.

**Nome**

Il nome del cookie AMCV deve rispettare la sintassi `AMCV_<variable name>@AdobeOrg`. Nel nome, gli elementi `<variable name>` sono segnaposto per parte dell&#39;ID organizzazione IMS. L&#39;ID viene inviato al DCS dalla funzione `Visitor.getInstance` nel codice del servizio ID visitatore.

Il nome completo del cookie deve essere simile al seguente:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenuto**

Il cookie AMCV contiene l&#39;identificatore ECID o MID. Il MID viene memorizzato in una coppia chiave/valore con sintassi `MCMID|<ECID>`.

La coppia chiave/valore completa deve essere simile alla seguente:

```
MCMID|20265673158980419722735089753036633573
```

Questo identificatore permanente consente la condivisione dei dati tra più soluzioni.

**Dominio**

Il cookie AMCV è impostato nel dominio di prima parte di un browser. Ciò significa che è impostato nel dominio del sito visualizzato al momento da un utente. Di conseguenza, il codice del servizio ID visitatore e altre librerie di codici CX Enterprise possono leggere il MID memorizzato nel cookie AMCV.

Tuttavia, poiché il cookie AMCV è impostato nel dominio di prima parte, non può essere utilizzato per tracciare e identificare gli utenti tra domini diversi. Al contrario, il Servizio ID visitatore si basa sull’ID organizzazione IMS e sull’ID demdex per restituire il MID corretto quando un visitatore del sito accede a un dominio diverso.

## Cookie AMCVS {#section-92a9454f1ac645948f9059b9fad928bf}

**Nome**

Il nome del cookie AMCVS deve rispettare la sintassi `AMCVS_####@AdobeOrg`. Nel nome, gli elementi #### sono segnaposto per parte dell’ID organizzazione IMS. L&#39;ID viene inviato al DCS dalla funzione `theVisitor.getInstance` nel codice del servizio ID visitatore.

Il nome completo del cookie deve essere simile al seguente:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenuto**

Il cookie AMCVS serve da flag per indicare che la sessione è stata inizializzata. Il suo valore è sempre `1` ed è discontinuo se la sessione è terminata.

**Dominio**

Il cookie AMCVS è impostato nel dominio di prima parte di un browser. Ciò significa che è impostato nel dominio del sito visualizzato al momento da un utente.

![](assets/AMCVS-cookie.png)

## Cookie demdex {#section-7ff7d96d6e4141b08a84a75a63d7814c}

Nella tabella seguente sono elencati e definiti alcuni attributi importanti del cookie demdex.

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
   <td colname="col2"> <p>Il cookie demdex contiene l’ID demdex, generato dal DCS. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Dominio</b> </p> </td> 
   <td colname="col2"> <p>Il cookie demdex è impostato nel dominio di terza parte demdex.net nel browser. Questo dominio è separato dal sito visitato attualmente da un utente. </p> <p>A differenza del cookie di prima parte, il cookie AMCV, il cookie demdex e l’ID restano costanti nei diversi domini. L’ID demdex e l’ID organizzazione IMS sono i valori comuni che consentono al servizio ID visitatore di restituire e identificare un visitatore del sito con l’ID visitatore corretto. </p> </td> 
  </tr> 
 </tbody> 
</table>

Per informazioni sulle divulgazioni relative a Demdex, visita [Divulgazioni sulla memorizzazione dei dispositivi di Audience Manager](https://aam-iab-tcf-vendor.s3.amazonaws.com/aam_device_storage_disclosures.json).

Per informazioni correlate, consulta la documentazione relativa alle [informazioni sulle chiamate al dominio Demdex](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=it).

## Generazione dell’ECID {#section-15f69c0bac394b4b9966a23fbc586d17}

L’ECID viene derivato matematicamente dall’ID organizzazione IMS e dall’ID demdex. Fintanto che questi ID restano costanti la generazione del MID corretto per un utente specifico è semplicemente un problema matematico. Con lo stesso ID organizzazione IMS e lo stesso ID demdex si ottiene ogni volta lo stesso valore MID. Questo consente al servizio ID visitatore di tenere traccia dei visitatori tra i domini che controlli e che hai configurato con il codice del servizio ID visitatore.

Il Servizio ID visitatore inizia a creare un identificatore MID durante il caricamento della pagina. Durante questo processo, il codice fornito dalla libreria di codici `VisitorAPI.js` invia l&#39;ID organizzazione IMS in una chiamata evento al servizio ID visitatore. Il Servizio ID visitatore crea e restituisce il MID e un ID demdex rispettivamente nei cookie AMCV e demdex.

## Flag per cookie

Nella tabella seguente vengono descritti i flag per i cookie CX Enterprise:

| Cookie (impostato da) | httpOnly | Secure | SameSite |
|--- |--- |--- |--- |
| demdex (risposta http) | No | Sì | “Nessuno” |
| AMCV (JavaScript) | No | Configurabile | Non impostato (impostazione predefinita Lax) |
| AMCVS (JavaScript) | No | Configurabile | Non impostato (impostazione predefinita Lax) |

*Nota: Per informazioni sulla configurazione del cookie AMCV e AMCVS con attributi sicuri, consulta l’argomento relativo a [secureCookie](../library/function-vars/securecookie.md).*

## Passaggi successivi {#section-8db1727a63bc4ff68b495f270315d453}

Consulta [Richiesta e impostazione degli ID da parte del servizio ID visitatori...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

