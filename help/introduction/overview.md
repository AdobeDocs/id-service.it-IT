---
description: Il ruolo del servizio Experience Cloud Identity in Adobe Experience Cloud.
title: Panoramica del servizio Experience Cloud Identity
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 100%

---

# Panoramica del servizio Experience Cloud Identity

Il servizio Experience Cloud Identity abilita la piattaforma di identificazione comune per i servizi applicativi di Experience Cloud. Puoi utilizzare il servizio Experience Cloud Identity per impostare l&#39;[ID Experience Cloud (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=it).

L’ECID è uno spazio dei nomi dell’identità condivisa utilizzato nelle applicazioni Adobe Experience Platform e Experience Cloud per monitorare il comportamento dei visitatori e garantire che ogni dispositivo abbia un identificatore univoco che possa persistere in più sessioni.

>[!TIP]
>
>Il servizio Experience Cloud Identity, il servizio Experience Platform Identity e l’ECID sono tre entità **diverse**.

Il servizio Experience Cloud Identity può sostituire diversi ID specifici dell’applicazione e utilizzare la funzione [ID cliente e stati di autenticazione](/help/reference/authenticated-state.md) che ti consente di trasmettere gli ID dei tuoi clienti a Experience Cloud.

>[!NOTE]
>
>Il servizio Experience Cloud Identity funziona solo con i servizi applicativi di Experience Cloud a cui ti sei iscritto e non fornirà l’accesso ad altri servizi applicativi senza tale iscrizione.

Il servizio Experience Cloud Identity supporta le seguenti applicazioni:

* [Adobe Analytics](https://business.adobe.com/it/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/it/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/it/products/target/adobe-target.html)

Il servizio ID è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e futuri di Experience Cloud. Attualmente, il servizio ID supporta [Analytics](http://www.adobe.com/it/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/it/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/it/marketing-cloud/testing-targeting.html). Se non hai implementato il servizio ID, ti consigliamo di considerare fin d&#39;ora una strategia di migrazione.

## Riepilogo delle funzioni

In sintesi, il servizio Experience Cloud Identity aiuta a:

* Identificare in modo univoco un visitatore su un dispositivo in più applicazioni.
* Imposta un cookie di prima parte nel dominio del cliente affinché sia possibile eseguire il tracciamento sullo stesso dominio. Per ulteriori informazioni, consulta il documento su [Cookie e servizio Experience Cloud Identity](./cookies.md).
* Riceve alias e mappature ID dai clienti e dai partner Experience Cloud.
* Gestisce la sincronizzazione ID all&#39;interno di Experience Cloud.
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.

## Requisiti del servizio Experience Cloud Identity

Prima che tu possa utilizzare il servizio Identity, la tua soluzione e altre librerie di codice di Adobe devono soddisfare [alcuni requisiti](/help/reference/requirements.md).

* [Cookie e il servizio Experience Cloud Identity](cookies.md): il servizio Experience Cloud Identity utilizza l’ID dell&#39;organizzazione, il cookie AMCV di Experience Cloud e un cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie permettono al servizio Identity di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le varie soluzioni di Experience Cloud.
* [Richiesta e impostazione degli ID da parte del servizio Experience Cloud Identity](id-request.md): panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l’assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.
* [Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza](match-rates.md): panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud Identity, inclusi Adobe Media Optimizer e il servizio Identity.
