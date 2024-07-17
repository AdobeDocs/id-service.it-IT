---
description: Versioni future, aggiornamenti o modifiche a Experience Cloud Identity Service.
keywords: Servizio ID
title: Note sulla versione 2019
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
source-git-commit: 503683b66b6022b7c1fecbfb197fe17e05ae9c64
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 100%

---

# Note sulla versione 2019 di Experience Cloud {#release-notes}

Versioni future, aggiornamenti o modifiche a Experience Cloud Identity Service.

## Versione 4.4.1

Aggiungi approvazione pre-consenso tramite casella di controllo per l’analisi dei supporti in ECID Launch Extension.

**Correzioni**

* Problema con l’estensione di lancio ECID: parsing della stringa di input per preOptInApprovals.
* Calo della prestazione quando trackingServer è in uso.

## Versione 4.4 {#version-4point4}

**Nuova funzionalità**

[Supporto di hashing SHA-256 per setCustomerIDs](/help/reference/hashing-support.md). Il servizio Experience Cloud ID (ECID) supporta l’algoritmo di hashing SHA-256 che consente di ricevere gli ID o indirizzi e-mail dei clienti e di inoltrare gli ID con hashing.

**Correzioni e miglioramenti**

* È stato effettuato un aggiornamento della configurazione per `cookieDomain`. La libreria ECID ora filtra la stringa vuota `cookieDomain` in `initConfig` e utilizza il dominio del cookie di livello principale, restituito dal metodo getDomain.
* È stato corretto un bug correlato a `getVisitorValues` in `localVisitor`.
* È stato corretto un bug a causa del quale si verificava un’incoerenza per il valore MCOPTOUT nel browser Safari, restituito dal metodo `getVisitorValue`.
* Abbiamo aggiornato la libreria Opt-in aggiungendo `optIn.off` per annullare l’iscrizione agli eventi.
* È stato corretto un bug correlato alla funzione setTimeout, che in alcuni siti dei clienti causava la violazione della CSP (Content Security Policy) da parte di `setTimeout`.

## Versione 4.3 {#version-4point3}

**Supporto per ITP 2.1**. Se un server di tracciamento è impostato in un CNAME di prima parte, viene inserito un nuovo cookie (s_ecid) con il valore ECID. La libreria ECID fa riferimento a tale valore in modo che l’ID venga mantenuto oltre il limite di 7 giorni. Consulta [Metodi della libreria ECID in ambito Safari ITP](/help/reference/ecid-library-methods.md).

**Correzione di bug nella configurazione di secureCookie.**

## Versione 4.1

Aggiornamento `publishDestinations` per nuova modifica API. Con questo aggiornamento le informazioni della pagina possono essere esposte durante la sincronizzazione ID, se si desidera.

## Versione 4.2

Supporto per il plug-in Audience Manager per IAB TCF, disponibile tramite l’oggetto Opt-in ECID.

**Correzioni**

* IAB + OptIn non riesce a ottenere il MID per i clienti di ritorno.
* Risoluzione di un bug della configurazione opt-in doesOptInApply in DTM.
* La rinuncia ECID disattiva le sincronizzazioni ID.

## Versione 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servizio Opt-in**. Opt-in è un&#39;estensione di Experience Cloud ID (ECID) che consente di controllare se (e quali) librerie di Experience Cloud possono creare dei cookie sulle pagine Web per i visitatori. Usando [Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it), è possibile semplificare la raccolta dei consensi dei visitatori per la soluzione Experience Cloud consentendo ad Analytics, Target, Audience Manager e a tutte le altre soluzioni Experience Cloud di partecipare al sistema di gestione dei consensi.

## Versione 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descrizione |
|---|---|
| Il flag `disableIdSyncs` non funziona quando viene passata una stringa. | Corretto. Ora i valori impostati sul `disableidSyncs` parametro per la `getInstance` funzione vengono rispettati. |
| iFrames di terze parti non ricevono l’ECID | È stato corretto ECID su Safari Mobile e ECID in diversi iFrame che non funzionavano. |
