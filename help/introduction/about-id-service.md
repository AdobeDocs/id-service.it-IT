---
description: Il ruolo del servizio ID visitatori in Adobe CX Enterprise.
keywords: Servizio ID visitatori
title: Panoramica
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
TQID: https://experienceleague.adobe.com/YUy7gs28-5lGzLmfE-MJ4nRtQc7I05Q4nRCBO4gOdMI
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 29%

---

# Informazioni sul servizio ID visitatori{#aboutidservice}

Il ruolo del servizio ID visitatori in Adobe CX Enterprise.

<!--
mcvid-functionality.xml
-->

## Servizio ID visitatore: elemento fondamentale dei servizi core {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Il servizio ID visitatore abilita il framework comune di identificazione dei servizi principali e delle soluzioni CX Enterprise, nonché degli attributi cliente e tipi di pubblico. Funziona tramite l’assegnazione di un ID univoco e persistente a un visitatore del sito. Quando l&#39;organizzazione implementa il Servizio ID visitatore, questo ID consente di identificare lo stesso visitatore del sito e i relativi dati in diverse soluzioni CX Enterprise.

![](assets/ecid-new.png)

Inoltre, il Servizio ID visitatore può sostituire i diversi ID specifici della soluzione (ad esempio, AID di Analytics). Inoltre, tramite la funzionalità [ID cliente e stati di autenticazione](../reference/authenticated-state.md), il servizio ID visitatore consente di trasmettere gli ID dei propri clienti a CX Enterprise. Tuttavia, il Servizio ID visitatore funziona solo con le soluzioni alle quali sei abbonato. Se non ti sei registrato per altri prodotti, non sarà possibile accedere ad altri prodotti.

Il Servizio ID visitatore è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e futuri di CX Enterprise. Attualmente, il servizio ID visitatori supporta [Analytics](http://www.adobe.com/it/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/it/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/it/marketing-cloud/testing-targeting.html). È inoltre richiesto per partecipare ad Adobe Device Co-op. Se non hai implementato il servizio ID visitatore, ti consigliamo di considerare fin da ora una strategia di migrazione.

## Riepilogo delle funzioni {#section-96555473455c4bf8924c2d56ff4f3255}

In sintesi, il servizio ID visitatore:

* Crea una chiave o un ID comune che può essere utilizzato per collegare profili e identità.
* Identifica in modo univoco un dispositivo tra più soluzioni.
* Imposta un cookie di prima parte nel dominio del cliente affinché sia possibile eseguire il tracciamento sullo stesso dominio. Consulta [Cookie e il servizio ID visitatori](../introduction/cookies.md).
* Riceve alias e mappature ID dai clienti e dai partner aziendali CX.
* Gestisce la sincronizzazione ID in CX Enterprise.
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.

