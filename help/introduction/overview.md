---
description: Il ruolo di Experience Cloud Identity Service in Adobe Experience Cloud.
title: Panoramica di Experience Cloud Identity Service
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 100%

---

# Panoramica di Experience Cloud Identity Service

Experience Cloud Identity Service abilita la piattaforma di identificazione comune per i servizi applicativi di Experience Cloud. Puoi utilizzare Experience Cloud Identity Service per impostare l&#39;[ID Experience Cloud (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=it).

L’ECID è uno spazio dei nomi dell’identità condivisa utilizzato nelle applicazioni Adobe Experience Platform e Experience Cloud per monitorare il comportamento dei visitatori e garantire che ogni dispositivo abbia un identificatore univoco che possa persistere in più sessioni.

>[!TIP]
>
>Experience Cloud Identity Service, Experience Platform Identity Service e l’ECID sono tre entità **diverse**.

Experience Cloud Identity Service può sostituire diversi ID specifici dell’applicazione e utilizzare la funzione [ID cliente e stati di autenticazione](/help/reference/authenticated-state.md) che ti consente di trasmettere gli ID dei tuoi clienti a Experience Cloud.

>[!NOTE]
>
>Experience Cloud Identity Service funziona solo con i servizi applicativi di Experience Cloud a cui ti sei iscritto e non fornirà l’accesso ad altri servizi applicativi senza tale iscrizione.

Experience Cloud Identity Service supporta le seguenti applicazioni:

* [Adobe Analytics](https://business.adobe.com/it/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/it/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/it/products/target/adobe-target.html)

Il servizio ID è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e futuri di Experience Cloud. Attualmente, il servizio ID supporta [Analytics](http://www.adobe.com/it/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/it/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/it/marketing-cloud/testing-targeting.html). Se non hai implementato il servizio ID, ti consigliamo di considerare fin d&#39;ora una strategia di migrazione.

## Riepilogo delle funzioni

In sintesi, Experience Cloud Identity Service aiuta a:

* Identificare in modo univoco un visitatore su un dispositivo in più applicazioni.
* Imposta un cookie di prima parte nel dominio del cliente affinché sia possibile eseguire il tracciamento sullo stesso dominio. Per ulteriori informazioni, consulta il documento su [I cookie ed Experience Cloud Identity Service](./cookies.md).
* Riceve alias e mappature ID dai clienti e dai partner Experience Cloud.
* Gestisce la sincronizzazione ID all&#39;interno di Experience Cloud.
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.

## Requisiti di Experience Cloud Identity Service

Prima che tu possa utilizzare Identity Service, la tua soluzione e altre librerie di codice di Adobe devono soddisfare [alcuni requisiti](/help/reference/requirements.md).

* [I cookie ed Experience Cloud Identity Service](cookies.md): il servizio Experience Cloud Identity utilizza l’ID dell&#39;organizzazione, il cookie AMCV di Experience Cloud e un cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie permettono al Identity Service di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le varie soluzioni di Experience Cloud.
* [Richiesta e impostazione degli ID da parte di Experience Cloud Identity Service](id-request.md): panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l’assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.
* [Informazioni sulla sincronizzazione degli ID e sui tassi di corrispondenza](match-rates.md): panoramica dei processi di sincronizzazione ID e dei tassi di corrispondenza in Experience Cloud Identity Service, inclusi Adobe Media Optimizer e Identity Service.
