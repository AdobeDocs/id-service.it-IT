---
description: Il ruolo del servizio Experience Cloud Identity in Adobe Experience Cloud.
keywords: Servizio ID
title: Panoramica
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '339'
ht-degree: 100%

---

# Informazioni sul servizio ID{#aboutidservice}

Il ruolo del servizio Experience Cloud Identity in Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Servizio Experience Cloud Identity: elemento fondamentale dei servizi di base {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Il servizio Experience Cloud Identity abilita il framework comune di identificazione dei servizi di base e delle soluzioni Experience Cloud, nonché degli attributi cliente e tipi di pubblico. Funziona tramite l’assegnazione di un ID univoco e persistente a un visitatore del sito. Quando l’organizzazione implementa il servizio ID, questo ID consente di identificare lo stesso visitatore del sito e i relativi dati in diverse soluzioni Experience Cloud.

![](assets/ecid-new.png)

Inoltre, il servizio ID può sostituire i diversi ID delle singole soluzioni (ad esempio, AID di Analytics). E, tramite la funzionalità [ID cliente e stati di autenticazione](../reference/authenticated-state.md), il servizio ID permette di trasmettere gli ID dei tuoi clienti a [!DNL Experience Cloud]. Tuttavia, il servizio ID funziona solo con le soluzioni alle quali sei abbonato. Se non ti sei registrato per altri prodotti, non sarà possibile accedere ad altri prodotti.

Il servizio ID è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e [!DNL Experience Cloud] futuri di. Attualmente, il servizio ID supporta [Analytics](http://www.adobe.com/it/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/it/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/it/marketing-cloud/testing-targeting.html). È inoltre richiesto per partecipare ad [!DNL Adobe Experience Cloud] Device Co-op. Se non hai implementato il servizio ID, ti consigliamo di considerare fin d&#39;ora una strategia di migrazione. Per ulteriori informazioni sull’importanza e il ruolo del servizio ID, consulta l’articolo di blog [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/) (Perché considerare il servizio Experience Cloud Identity).

## Riepilogo delle funzioni {#section-96555473455c4bf8924c2d56ff4f3255}

In sintesi, il servizio ID svolge le seguenti funzioni:

* Crea una chiave o un ID comune che può essere utilizzato per collegare profili e identità.
* Identifica in modo univoco un dispositivo tra più soluzioni.
* Imposta un cookie di prima parte nel dominio del cliente per garantire il monitoraggio del dominio stesso. Consulta [Experience Cloud](../introduction/cookies.md).
* Riceve alias e mappature ID dai [!DNL Experience Cloud] clienti e dai partner.
* Gestisce la sincronizzazione ID all&#39;interno di [!DNL Experience Cloud].
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.
