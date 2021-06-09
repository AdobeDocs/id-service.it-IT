---
description: Il ruolo del servizio Experience Cloud Identity in Adobe Experience Cloud.
seo-description: Il servizio Experience Cloud Identity (già servizio Visitor ID o Experience Cloud ID) abilita il framework comune di identificazione dei servizi Experience Cloud, come gli attributi cliente e i tipi di pubblico.
seo-title: Panoramica del servizio Experience Cloud ID
title: Panoramica del servizio Experience Cloud ID
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: b907ffcbfbb8851ce6279b614dc58c22f2ce9907
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 100%

---

# Panoramica del servizio Experience Cloud ID

Il [!UICONTROL servizio Experience Cloud Identity] abilita il framework comune di identificazione dei servizi principali (come gli attributi cliente e i tipi di pubblico) e delle soluzioni Experience Cloud del servizio Experience Platform Identity.

>[!NOTE]
>
> È possibile che siano presenti termini relativi al servizio ID come acronimi o nomi precedenti, come ECID, servizio Experience Cloud ID (MID) e servizio Visitor ID. Si tratta del [!UICONTROL servizio Experience Cloud Identity]. È possibile che sia presente anche il [!UICONTROL servizio Experience Platform Identity]. Spiegazione:

* [!UICONTROL Servizio Experience Platform Identity]: il servizio che collega le identità. È il servizio di collegamento dispositivi per la gestione dell&#39;esperienza basata sulle persone.
* [!UICONTROL Servizio Experience Cloud ID] (ECID): l&#39;ID univoco e costante assegnato ai visitatori del sito. È un&#39;entità specifica che può essere utilizzata dal servizio Platform Identity.

Quando l’organizzazione implementa il servizio ID, questo ID consente di identificare lo stesso visitatore del sito e i relativi dati in diverse soluzioni Experience Cloud.

![](assets/ecid-new.png)

Inoltre, il servizio ID può sostituire i diversi ID delle singole soluzioni (ad esempio, AID di Analytics). Quindi, tramite la funzionalità [ID cliente e stati di autenticazione](/help/reference/authenticated-state.md), il servizio ID ti permette di trasmettere gli ID dei tuoi clienti a Experience Cloud. Tuttavia, il servizio ID funziona solo con le soluzioni alle quali sei abbonato. Se non ti sei registrato per altri prodotti, non sarà possibile accedere ad altri prodotti.

Il servizio ID è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e futuri di Experience Cloud. Attualmente, il servizio ID supporta [Analytics](http://www.adobe.com/it/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/it/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/it/marketing-cloud/testing-targeting.html). È inoltre richiesto per partecipare ad Adobe Experience Cloud Device Co-op. Se non hai implementato il servizio ID, ti consigliamo di considerare fin d&#39;ora una strategia di migrazione. Per ulteriori informazioni sull’importanza e il ruolo del servizio ID, consulta l’articolo di blog [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/) (Perché considerare il servizio Experience Cloud Identity).

## Riepilogo delle funzioni

In sintesi, il servizio ID svolge le seguenti funzioni:

* Crea una chiave o un ID comune che può essere utilizzato per collegare profili e identità.
* Identifica in modo univoco un dispositivo tra più soluzioni.
* Imposta un cookie di prima parte nel dominio del cliente per garantire il monitoraggio del dominio stesso. Consulta il documento su [cookie e servizio Experience Cloud Identity](./cookies.md) per ulteriori informazioni.
* Riceve alias e mappature ID dai clienti e dai partner Experience Cloud.
* Gestisce la sincronizzazione ID all&#39;interno di Experience Cloud.
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.

## Requisiti del servizio ID

La tua soluzione e altre librerie di codice Adobe devono soddisfare [alcuni requisiti](/help/reference/requirements.md) per poter utilizzare il servizio ID.

* [Cookie e il servizio Experience Cloud Identity](cookies.md): il servizio ID utilizza l’ID organizzazione, il cookie AMCV di Experience Cloud e un cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie permettono al servizio ID di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le varie soluzioni Experience Cloud.
* [Richiesta e impostazione degli ID da parte del servizio Experience Cloud Identity](id-request.md): panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l’assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.
* [Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza](match-rates.md): panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud Identity, inclusi Adobe Media Optimizer e il servizio ID.
