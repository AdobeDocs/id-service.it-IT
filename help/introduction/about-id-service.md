---
description: Il ruolo del servizio Identità Experience Platform in Adobe Experience Cloud.
keywords: Servizio ID
seo-description: Il ruolo del servizio Identità Experience Platform in Adobe Experience Cloud.
seo-title: Il servizio ID
title: Panoramica
uuid: c 52 d 6155-00 a 0-4 fc 5-9 d 8 e -5 ce 00 b 8 d 01 e 6
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Il servizio ID{#aboutidservice}

Il ruolo del servizio Identità Experience Platform in Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Servizio identità Experience Platform: Elemento fondamentale dei servizi di base {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Experience Platform Identity Service abilita il framework comune di identificazione dei servizi di base, delle soluzioni e degli attributi del cliente di Experience Cloud nel servizio di base Persone. Funziona tramite l&#39;assegnazione di un ID univoco persistente a un visitatore del sito. Quando l&#39;organizzazione implementa il servizio ID, tale ID consente di identificare lo stesso visitatore del sito e i relativi dati in diverse soluzioni Experience Cloud.

![](assets/ecid.png)

Inoltre, il servizio ID può sostituire i diversi ID specifici di ogni soluzione (ad esempio, AID di Analytics). E tramite la funzionalità [ID cliente e stati di autenticazione](../reference/authenticated-state.md), il servizio ID ti permette di trasmettere gli ID dei tuoi clienti a [!DNL Experience Cloud]. Ricorda però che il servizio ID può essere utilizzato solo con le soluzioni per le quali hai effettuato la sottoscrizione. Se non hai sottoscritto altri prodotti, questo servizio non consente di utilizzarli.

Il servizio ID è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e futuri di [!DNL Experience Cloud]. Attualmente, il servizio ID supporta [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). È inoltre richiesto per partecipare ad [!DNL Adobe Experience Cloud] Device Co-op. Se non hai implementato il servizio ID, ti consigliamo di considerare fin d&#39;ora una strategia di migrazione. Per ulteriori informazioni sull&#39;importanza e il ruolo del servizio ID, vedi [Why the Experience Platform Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Riepilogo delle funzioni {#section-96555473455c4bf8924c2d56ff4f3255}

Riepilogando, il servizio ID:

* Crea una chiave o un ID comune che possono essere usati per collegare profili ed identità.
* Identifica in maniera univoca un dispositivo all&#39;interno di varie soluzioni.
* Imposta un cookie di prima parte nel dominio del cliente per garantire il monitoraggio del dominio stesso. Consulta  [Experience Cloud](../introduction/cookies.md).
* Riceve alias e mappature ID dai clienti e dai partner [!DNL Experience Cloud].
* Gestisce la sincronizzazione ID all&#39;interno della [!DNL Experience Cloud].
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.
