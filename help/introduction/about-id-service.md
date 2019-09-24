---
description: Il ruolo del servizio Experience Platform Identity in Adobe Experience Cloud.
keywords: Servizio ID
seo-description: Il ruolo del servizio Experience Platform Identity in Adobe Experience Cloud.
seo-title: Informazioni sul servizio ID
title: Panoramica
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Informazioni sul servizio ID{#aboutidservice}

Il ruolo del servizio Experience Cloud Identity in Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Servizio Experience Cloud Identity: elemento fondamentale dei servizi di base {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Il servizio Experience Cloud Identity abilita il framework comune di identificazione dei servizi di base e delle soluzioni Experience Cloud, nonché degli attributi cliente e tipi di pubblico. Funziona tramite l'assegnazione di un ID univoco persistente a un visitatore del sito. Quando l'organizzazione implementa il servizio ID, tale ID consente di identificare lo stesso visitatore del sito e i relativi dati in diverse soluzioni Experience Cloud.

![](assets/ecid.png)

Inoltre, il servizio ID può sostituire i diversi ID specifici di ogni soluzione (ad esempio, AID di Analytics). E tramite la funzionalità [ID cliente e stati di autenticazione](../reference/authenticated-state.md), il servizio ID ti permette di trasmettere gli ID dei tuoi clienti a [!DNL Experience Cloud]. Ricorda però che il servizio ID può essere utilizzato solo con le soluzioni per le quali hai effettuato la sottoscrizione. Se non hai sottoscritto altri prodotti, questo servizio non consente di utilizzarli.

Il servizio ID è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e [!DNL Experience Cloud] futuri di. Attualmente, il servizio ID supporta [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). È inoltre richiesto per partecipare ad [!DNL Adobe Experience Cloud] Device Co-op. Se non hai implementato il servizio ID, ti consigliamo di considerare fin d'ora una strategia di migrazione. Per ulteriori informazioni sull’importanza e il ruolo del servizio ID, consulta l’articolo di blog [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/) (/ (Perché considerare il servizio Experience Cloud Identity).

## Riepilogo delle funzioni {#section-96555473455c4bf8924c2d56ff4f3255}

Riepilogando, il servizio ID:

* Crea una chiave o un ID comune che possono essere usati per collegare profili ed identità.
* Identifica in maniera univoca un dispositivo all'interno di varie soluzioni.
* Imposta un cookie di prima parte nel dominio del cliente per garantire il monitoraggio del dominio stesso. Consulta [Experience Cloud](../introduction/cookies.md).
* Riceve alias e mappature ID dai [!DNL Experience Cloud] clienti e dai partner.
* Gestisce la sincronizzazione ID all'interno di [!DNL Experience Cloud].
* Supporta la sincronizzazione ID con terze parti diverse all'interno dell'ecosistema di tecnologie per la gestione di annunci.
