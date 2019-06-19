---
description: Note sulla versione e aggiornamenti per la versione 2015.
keywords: Servizio ID
seo-description: Note sulla versione e aggiornamenti per la versione 2015.
seo-title: Note sulla versione 2015
title: Note sulla versione 2015
uuid: 49423699-1 e 0 f -49 e 4-9135-2 ae 84 b 4 f 92 df
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Note sulla versione 2015 {#release-notes}

Note sulla versione e aggiornamenti per la versione 2015.

## Versione 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Novembre 2015

Il Children&#39;s Online Privacy Protection Act (COPPA) proibisce la raccolta online di dati personali di bambini di età inferiore ai 13 anni senza disporre del consenso verificabile dei genitori. I clienti interessati dal COPPA possono aggiungere una variabile opzionale al codice del servizio [!DNL Experience Cloud] ID  che impedisce l’impostazione di cookie nel dominio di un browser di terze parti. Consultate [Supporto COPPA nel servizio Identità Experience Platform](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Per le versioni a partire dalla 1.5.3.

## Versione 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

Settembre 2015

* È stato corretto un bug del browser Safari che impediva il funzionamento della sincronizzazione dei servizi quando gli utenti impostavano il blocco dei cookie di terze parti. (AAM-20764)
* Le chiamate al servizio ID ora includono l&#39;ID versione nel `d_visid_ver=` parametro. L&#39;ID restituito aiuta i team interni a risolvere i problemi e a prestare assistenza. (AAM-20824)

## Versione 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

Agosto 2015

* È stato corretto un bug per impedire al servizio ID di richiedere un iframe se non sono presenti dati da sincronizzare o attivare. (AAM-20164)
* È stato risolto un bug che impediva al servizio ID di impostare correttamente un cookie per un dominio di livello superiore con più parti. Ad esempio, se hai un dominio come `my_company.co.uk`, in alcuni casi il servizio ID imposta solo un `co.uk` cookie. (AN-104683)

   Questo bug interessava solo alcuni clienti che soddisfacevano *tutti* i seguenti criteri:

   * Utilizzavano il servizio ID.
   * Hanno abilitato un [periodo di grazia](../reference/analytics-reference/grace-period.md) *o* utilizzano cookie di prime parti e gli utenti hanno bloccato i cookie di terze parti.

   * Avevano pagine con domini di livello superiore con più parti.

Alcune revisioni della documentazione effettuate in questa versione:

* [Metodi API e Libreria codici](../library/library.md#concept-ff27497375644a898d47984aefb21c97): Contenuto e testo riorganizzati. Nella maggior parte dei casi, per ciascun metodo è presente una propria pagina.
* [Requisiti per Experience Platform Identity Service](../reference/requirements.md): Contenuto rivisto e testo riorganizzato.

## Versione 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

Luglio 2015

Il servizio [!DNL Experience Cloud] ID supporta più ID e stati di autenticazione. Questa modifica rimuove anche il supporto obsoleto per le mappature DPID di [!DNL Audience Manager] agli ID utente utilizzate dalla funzione `setCustomerIDs`. Vedere [ID cliente e stati di autenticazione](../reference/authenticated-state.md)

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

È stata corretta la gestione del timeout delle richieste per AAM Blob e Location Hint. Ora, quando si verifica un timeout, il sistema lascia correttamente questi campi vuoti per la pagina corrente ed effettua tutti i callback. Il timeout viene trattato come una condizione di errore, pertanto viene ritentato nella pagina successiva. (AN-94473, AN-94474)

## Versione 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

Gennaio 2015

È stata rielaborata `<head>/<body>` la ricerca del tag di `<script>` tag della richiesta JSONP, oltre alla creazione del `<script>` tag per diverse implementazioni DOM (HTML vs XHTML) con possibili impostazioni di sensibilità maiuscole/minuscole. (AN-9355)
