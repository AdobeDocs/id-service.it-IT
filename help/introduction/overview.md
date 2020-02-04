---
description: Il ruolo del servizio Experience Cloud Identity in Adobe Experience Cloud.
seo-description: Il servizio Experience Cloud Identity abilita il framework comune di identificazione dei servizi di base e delle soluzioni Experience Cloud, nonché degli attributi cliente e tipi di pubblico.
seo-title: Panoramica del servizio ID
title: Panoramica
uuid: null
translation-type: tm+mt
source-git-commit: 6c314656c134a697540c289560c67ca3ab88bc63

---


# Panoramica

Il servizio Experience Cloud Identity abilita il framework comune di identificazione per i servizi di base, le soluzioni e gli attributi cliente e pubblico di Experience Cloud nel servizio Platform Identity. (Potresti trovare riferimenti a nomi o acronimi precedenti, ad esempio servizio Experience Cloud ID, ECID, servizio Marketing Cloud ID, MID e servizio Visitor ID). Il servizio Identity funziona tramite l’assegnazione di un ID univoco persistente a un visitatore del sito. Quando l&#39;organizzazione implementa il servizio ID, tale ID consente di identificare lo stesso visitatore del sito e i relativi dati in diverse soluzioni Experience Cloud.

![](assets/ecid.png)

Inoltre, il servizio ID può sostituire i diversi ID specifici di ogni soluzione (ad esempio, AID di Analytics). E tramite la funzionalità [ID cliente e stati di autenticazione](/help/reference/authenticated-state.md), il servizio ID ti permette di trasmettere gli ID dei tuoi clienti a Experience Cloud. Ricorda però che il servizio ID può essere utilizzato solo con le soluzioni per le quali hai effettuato la sottoscrizione. Se non hai sottoscritto altri prodotti, questo servizio non consente di utilizzarli.

Il servizio ID è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e futuri di Experience Cloud. Attualmente, il servizio ID supporta [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). È inoltre richiesto per partecipare ad Adobe Experience Cloud Device Co-op. Se non hai implementato il servizio ID, ti consigliamo di considerare fin d&#39;ora una strategia di migrazione. Per ulteriori informazioni sull’importanza e il ruolo del servizio ID, consulta l’articolo di blog [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/) (/ (Perché considerare il servizio Experience Cloud Identity).

## Riepilogo delle funzioni

Riepilogando, il servizio ID:

* Crea una chiave o un ID comune che possono essere usati per collegare profili ed identità.
* Identifica in maniera univoca un dispositivo all&#39;interno di varie soluzioni.
* Imposta un cookie di prima parte nel dominio del cliente per garantire il monitoraggio del dominio stesso. Consulta Experience Cloud.
* Riceve alias e mappature ID dai clienti e dai partner Experience Cloud.
* Gestisce la sincronizzazione ID all&#39;interno di Experience Cloud.
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.

## Requisiti del servizio ID

La tua soluzione e altre librerie di codice Adobe devono soddisfare [alcuni requisiti](/help/reference/requirements.md) per poter utilizzare il servizio ID.

* [Cookie e il servizio Experience Cloud Identity](cookies.md): il servizio ID utilizza l’ID organizzazione, il cookie AMCV di Experience Cloud e un cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie permettono al servizio ID di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le varie soluzioni Experience Cloud.
* [Richiesta e impostazione degli ID da parte del servizio Experience Cloud Identity](id-request.md): panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l’assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.
* [Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza](match-rates.md): panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud Identity, inclusi Adobe Media Optimizer e il servizio ID.