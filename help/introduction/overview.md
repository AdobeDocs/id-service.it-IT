---
description: Il ruolo del servizio Experience Cloud Identity in Adobe Experience Cloud.
seo-description: Il servizio Experience Cloud ID (già servizio Visitor ID o Marketing Cloud ID) abilita il framework comune di identificazione per i servizi Experience Cloud come gli attributi del cliente e le audience.
seo-title: Panoramica del servizio Experience Cloud ID
title: Panoramica del servizio Experience Cloud ID
translation-type: tm+mt
source-git-commit: 6342ea02c74e6d1c96f987c5f2620246602ce6c5

---


# Panoramica del servizio Experience Cloud ID

The [!UICONTROL Experience Cloud Identity Service] enables the common identification framework for Experience Cloud Core Services (such as customer attributes and audiences) solutions in the Experience Platform Identity Service.

>[!NOTE]
>
> Puoi vedere i riferimenti al servizio ID come acronimi o nomi precedenti, ad esempio ECID, Marketing Cloud ID Service (MID) e Visitor ID Service. Si tratta del servizio Experience Cloud Identity. Potresti anche vedere il servizio [!UICONTROL identità della piattaforma]Experience. Per chiarire:

* [!UICONTROL Servizio]identità della piattaforma di esperienza: Il servizio che collega le identità. È il servizio di collegamento dei dispositivi per la gestione dell&#39;esperienza basata sulle persone.
* [!UICONTROL Servizio] Experience Cloud ID (ECID): L’ID univoco e permanente assegnato a un visitatore del sito. È un&#39;entità specifica che può essere utilizzata dal servizio Identità piattaforma.

Quando l&#39;organizzazione implementa il servizio ID, tale ID consente di identificare lo stesso visitatore del sito e i relativi dati in diverse soluzioni Experience Cloud.

![](assets/ecid.png)

Inoltre, il servizio ID può sostituire i diversi ID specifici di ogni soluzione (ad esempio, AID di Analytics). E tramite la funzionalità [ID cliente e stati di autenticazione](/help/reference/authenticated-state.md), il servizio ID ti permette di trasmettere gli ID dei tuoi clienti a Experience Cloud. Ricorda però che il servizio ID può essere utilizzato solo con le soluzioni per le quali hai effettuato la sottoscrizione. Se non hai sottoscritto altri prodotti, questo servizio non consente di utilizzarli.

Il servizio ID è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e futuri di Experience Cloud. Attualmente, il servizio ID supporta [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). È inoltre richiesto per partecipare ad Adobe Experience Cloud Device Co-op. Se non hai implementato il servizio ID, ti consigliamo di considerare fin d&#39;ora una strategia di migrazione. Per ulteriori informazioni sull’importanza e il ruolo del servizio ID, consulta l’articolo di blog [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/) (Perché considerare il servizio Experience Cloud Identity).

## Riepilogo delle funzioni

Riepilogando, il servizio ID:

* Crea una chiave o un ID comune che possono essere usati per collegare profili ed identità.
* Identifica in maniera univoca un dispositivo all&#39;interno di varie soluzioni.
* Imposta un cookie di prima parte nel dominio del cliente per garantire il monitoraggio del dominio stesso. Consulta per ulteriori informazioni, consulta il documento sui [cookie e il servizio](https://docs.adobe.com/content/help/en/id-service/using/intro/cookies.html) Experience Cloud Identity.
* Riceve alias e mappature ID dai clienti e dai partner Experience Cloud.
* Gestisce la sincronizzazione ID all&#39;interno di Experience Cloud.
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.

## Requisiti del servizio ID

La tua soluzione e altre librerie di codice Adobe devono soddisfare [alcuni requisiti](/help/reference/requirements.md) per poter utilizzare il servizio ID.

* [Cookie e il servizio Experience Cloud Identity](cookies.md): il servizio ID utilizza l’ID organizzazione, il cookie AMCV di Experience Cloud e un cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie permettono al servizio ID di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le varie soluzioni Experience Cloud.
* [Richiesta e impostazione degli ID da parte del servizio Experience Cloud Identity](id-request.md): panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l’assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.
* [Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza](match-rates.md): panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud Identity, inclusi Adobe Media Optimizer e il servizio ID.
