---
description: Il ruolo del servizio Experience Cloud Identity in Adobe Experience Cloud.
keywords: ID Service
seo-description: Il ruolo del servizio Experience Cloud Identity in Adobe Experience Cloud.
seo-title: Informazioni sul servizio ID
title: Panoramica
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: ec67177fc6491e4c8cea835d198574c9fdb4b01f
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 63%

---


# Informazioni sul servizio ID {#aboutidservice}

Il ruolo del servizio Experience Cloud Identity in Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Servizio Experience Cloud Identity: elemento fondamentale dei servizi di base {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Il servizio Experience Cloud Identity abilita il framework comune di identificazione dei servizi di base e delle soluzioni Experience Cloud, nonché degli attributi cliente e tipi di pubblico. Funziona assegnando un ID univoco e costante a un visitatore del sito. Quando l’organizzazione implementa il servizio ID, questo ID consente di identificare lo stesso visitatore del sito e i relativi dati in diverse soluzioni  Experience Cloud.

![](assets/ecid-new.png)

Inoltre, il servizio ID può sostituire i diversi ID specifici della soluzione (ad esempio, AID di Analytics). And, through the [Customer IDs and Authentication States](../reference/authenticated-state.md) functionality, the ID service lets you pass in your own customer IDs to the [!DNL Experience Cloud]. Ricorda, tuttavia, che il servizio ID funziona solo con le soluzioni per le quali hai già effettuato la sottoscrizione. Non fornirà l&#39;accesso ad altri prodotti se non siete iscritti.

Il servizio ID è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e [!DNL Experience Cloud] futuri di. Attualmente, il servizio ID supporta [Analytics](http://www.adobe.com/it/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/it/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/it/marketing-cloud/testing-targeting.html). È inoltre richiesto per partecipare ad [!DNL Adobe Experience Cloud] Device Co-op. Se non hai implementato il servizio ID, ti consigliamo di considerare fin d&#39;ora una strategia di migrazione. Per ulteriori informazioni sull’importanza e il ruolo del servizio ID, consulta l’articolo di blog [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/) (Perché considerare il servizio Experience Cloud Identity).

## Riepilogo delle funzioni {#section-96555473455c4bf8924c2d56ff4f3255}

In sintesi, il servizio ID:

* Crea una chiave o un ID comune che può essere utilizzata per collegare profili e identità.
* Identifica in modo univoco un dispositivo tra più soluzioni.
* Imposta un cookie di prima parte nel dominio del cliente per garantire il monitoraggio del dominio stesso. Consulta [Experience Cloud](../introduction/cookies.md).
* Riceve alias e mappature ID dai [!DNL Experience Cloud] clienti e dai partner.
* Gestisce la sincronizzazione ID all&#39;interno di [!DNL Experience Cloud].
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.
