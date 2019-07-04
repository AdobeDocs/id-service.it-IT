---
description: Il ruolo del servizio Experience Cloud ID in Adobe Experience Cloud.
keywords: Servizio ID
seo-description: Il ruolo del servizio Experience Cloud ID in Adobe Experience Cloud.
seo-title: Informazioni sul servizio ID
title: Panoramica
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Informazioni sul servizio ID{#aboutidservice}

Il ruolo del servizio Experience Cloud ID in Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Servizio Experience Cloud ID: elemento fondamentale di servizi core {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Il servizio Experience Cloud ID abilita il framework comune di identificazione dei servizi di base e delle soluzioni di Experience Cloud, e gli attributi cliente e pubblico nel servizio di base Persone. Funziona tramite l&#39;assegnazione di un ID univoco persistente a un visitatore del sito. Quando l&#39;organizzazione implementa il servizio ID, tale ID consente di identificare lo stesso visitatore del sito e i relativi dati in diverse soluzioni Experience Cloud.

![](assets/ecid.png)

Inoltre, il servizio ID può sostituire i diversi ID specifici di ogni soluzione (ad esempio, AID di Analytics). E tramite la funzionalità [ID cliente e stati di autenticazione](../mcvid-reference/mcvid-authenticated-state.md), il servizio ID ti permette di trasmettere gli ID dei tuoi clienti a [!DNL Experience Cloud]. Ricorda però che il servizio ID può essere utilizzato solo con le soluzioni per le quali hai effettuato la sottoscrizione. Se non hai sottoscritto altri prodotti, questo servizio non consente di utilizzarli.

Il servizio ID è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e [!DNL Experience Cloud] futuri di. Attualmente, il servizio ID supporta [Analytics](https://www.adobe.com/it/analytics/web-analytics.html), [Audience Manager](https://www.adobe.com/it/analytics/audience-manager.html) e [Target](https://www.adobe.com/it/marketing/target.html). È inoltre richiesto per partecipare ad [!DNL Adobe Experience Cloud] Device Co-op. Se non hai implementato il servizio ID, ti consigliamo di considerare fin d&#39;ora una strategia di migrazione. Per ulteriori informazioni sull&#39;importanza e il ruolo del servizio ID, vedi l&#39;articolo di blog [Why the Experience Cloud ID Service Should be on Your Radar (Perché il servizio Experience Cloud ID dovrebbe diventare il tuo radar).](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)

## Riepilogo delle funzioni {#section-96555473455c4bf8924c2d56ff4f3255}

Riepilogando, il servizio ID:

* Crea una chiave o un ID comune che possono essere usati per collegare profili ed identità.
* Identifica in maniera univoca un dispositivo all&#39;interno di varie soluzioni.
* Imposta un cookie di prima parte nel dominio del cliente per garantire il monitoraggio del dominio stesso. Consulta [Experience Cloud](../mcvid-introduction/mcvid-cookies.md).
* Riceve alias e mappature ID dai [!DNL Experience Cloud] clienti e dai partner
* Gestisce la sincronizzazione ID all&#39;interno di [!DNL Experience Cloud].
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.
