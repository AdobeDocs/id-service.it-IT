---
description: Note sulla versione e aggiornamenti per la versione 2015.
keywords: Servizio ID
title: Note sulla versione 2015
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 99%

---

# Note sulla versione 2015 {#release-notes}

Note sulla versione e aggiornamenti per la versione 2015.

## Versione 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Novembre 2015

Il Children&#39;s Online Privacy Protection Act (COPPA) proibisce la raccolta online di dati personali di bambini di età inferiore ai 13 anni senza disporre del consenso verificabile dei genitori. I clienti interessati dal COPPA possono aggiungere una variabile opzionale al codice del servizio [!DNL Experience Cloud] ID che impedisce l’impostazione di cookie nel dominio di un browser di terze parti. Consulta [Supporto per COPPA in Experience Cloud Identity Service](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Per le versioni a partire dalla 1.5.3.

## Versione 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

Settembre 2015

* È stato corretto un bug del browser Safari che impediva il funzionamento della sincronizzazione dei servizi quando gli utenti impostavano il blocco dei cookie di terze parti. (AAM-20764)
* Ora le chiamate al servizio ID includono l&#39;ID versione nel parametro `d_visid_ver=`. L’ID restituito aiuta i team interni a risolvere i problemi e a fornire assistenza. (AAM-20824)

## Versione 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

Agosto 2015

* È stato risolto un bug per impedire che il servizio ID richieda un iframe se non sono presenti dati da sincronizzare o attivare. (AAM-20164)
* È stato risolto un bug che impediva al servizio ID di impostare correttamente un cookie di dominio multiparte di livello più alto. Per esempio, per un dominio come `my_company.co.uk`, in alcuni casi il servizio ID imposterebbe un cookie solo in `co.uk`. (AN-104683)

  Questo bug interessava solo alcuni clienti che soddisfacevano *tutti* i seguenti criteri:

   * Uso del servizio ID.
   * Hanno abilitato un [periodo di grazia ](../reference/analytics-reference/grace-period.md)*o* utilizzano cookie di prime parti e gli utenti hanno bloccato i cookie di terze parti.

   * Avevano pagine con domini di livello superiore con più parti.

Le revisioni della documentazione in questa versione includono:

* [Metodi API e libreria dei codici](../library/library.md#concept-ff27497375644a898d47984aefb21c97): contenuto e testo riorganizzati. Nella maggior parte dei casi, per ciascun metodo è presente una propria pagina.
* [Requisiti di Experience Cloud Identity Service](../reference/requirements.md): contenuto rivisto e testo riorganizzato.

## Versione 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

Luglio 2015

Il servizio [!DNL Experience Cloud] ID supporta più ID e stati di autenticazione. Questa modifica rimuove anche il supporto obsoleto per le mappature [!DNL Audience Manager] DPID di agli ID utente utilizzate dalla `setCustomerIDs`funzione. Vedi [Impostazione degli ID cliente e degli stati di autenticazione](../reference/authenticated-state.md)

## Versione 1.4 {#section-f5c596f355b14da28f45c798df513572}

Maggio 2015

Nella versione 1.4, il metodo migliore per effettuare la configurazione consiste nel trasferire un oggetto config come secondo parametro alla funzione `Visitor.getInstance`.

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

Consulta [Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd).

## Versione 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

Febbraio 2015

È stata corretta la gestione del timeout per le richieste di Blob AAM e posizione hint. Ora, in caso di timeout, il sistema lascerà tali campi vuoti per la pagina corrente ed effettuerà tutti i callback. Il timeout viene trattato come una condizione di errore e verrà quindi ritentato nella pagina successiva. (AN-94473, AN-94474)

## Versione 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

Gennaio 2015

La ricerca del tag `<head>/<body>` è stata rielaborata per il contenitore di tag `<script>` della richiesta JSONP; è stata rielaborata anche la creazione del tag `<script>` per diverse implementazioni DOM (HTML vs XHTML) con impostazioni potenzialmente diverse per la distinzione tra maiuscole e minuscole. (AN-9355)
