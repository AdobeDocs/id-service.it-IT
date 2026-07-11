---
description: Il servizio ID visitatore di Adobe abilita il framework comune di identificazione delle applicazioni e dei servizi aziendali CX. Funziona tramite l’assegnazione a un visitatore del sito di un ID univoco e costante noto come ECID.
keywords: Servizio ID visitatore; ECID
title: Servizio ID visitatore di Adobe
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
TQID: https://experienceleague.adobe.com/xzEgzuN2NnyOnhCPocQikOXHFRU6zmLWLGdrJL4C3GM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 433
ht-degree: 26%

---

# Servizio ID visitatore di Adobe {#experience-cloud-id-service}

>[!BEGINSHADEBOX]

Il servizio ID visitatori è **not** il [servizio Experience Platform Identity](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=it). Il servizio ID visitatori è la libreria JavaScript `VisitorAPI.js` descritta in questa guida che imposta l&#39;ECID per Adobe Analytics, Audience Manager e Target. Se stai cercando il servizio Adobe Experience Platform che risolve le identità tra dispositivi e sistemi in un profilo cliente unificato, consulta invece la [panoramica del servizio Experience Platform Identity](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=it).

>[!ENDSHADEBOX]

Il servizio ID visitatore di Adobe abilita il framework comune di identificazione delle applicazioni e dei servizi aziendali CX. Funziona tramite l’assegnazione a un visitatore del sito di un ID univoco e costante noto come ECID.

## Informazioni sulle principali entità di identità

Per capire meglio in che modo Adobe aiuta a identificare in modo univoco i visitatori e a risolvere le informazioni sull’identità, leggi la suddivisione seguente:

* **Servizio ID visitatore**: il servizio ID visitatore **è responsabile dell&#39;impostazione dell&#39;ECID**. Per ulteriori informazioni, consulta la [Panoramica del servizio ID visitatori](./introduction/overview.md).
* **ECID**: ECID è uno spazio dei nomi di identità condiviso e utilizzato nelle applicazioni Adobe Experience Platform e Adobe CX Enterprise per identificare persone e dispositivi. Per ulteriori informazioni sull’identificatore ECID, consulta la sezione [Panoramica di ECID](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/ecid).
* **Experience Platform Identity Service**: Experience Platform Identity Service fornisce una panoramica completa dei clienti e del loro comportamento, collegando le identità attraverso i diversi dispositivi e sistemi. Per ulteriori informazioni, consulta [Panoramica di Experience Platform Identity Service](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=it).

## Introduzione

* [Panoramica del servizio ID visitatore](introduction/overview.md): scopri cosa fa il servizio ID visitatore e come si inserisce in CX Enterprise.
* [Requisiti del servizio ID visitatori](reference/requirements.md): prima di implementare il servizio ID visitatori, verifica che le soluzioni e le librerie di codice soddisfino i prerequisiti.
* [Metodi di implementazione](implementation-guides/implementation-methods.md): confrontare l&#39;implementazione standard utilizzando [tag](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it) con metodi di integrazione diretta non standard.

## Esplora la documentazione

**Implementazione**

* [Guide all’implementazione](implementation-guides/implementation-guides.md)
* [Integrazione diretta con il servizio ID visitatore](implementation-guides/direct-integration.md)
* [Panoramica del servizio Opt-in](implementation-guides/opt-in-service/optin-overview.md)
* [Test e verifica del servizio ID visitatori](implementation-guides/test-verify.md)

**Riferimento API**

* [Panoramica API del servizio ID visitatore](library/library.md)
* [getVisitorValues](library/get-set/getvisitorvalues.md)
* [idSyncContainerID](library/function-vars/idsyncontainerid.md)

**Domande frequenti**

* [Domande frequenti sul servizio ID visitatore](faq-intro/faq.md)
* [Domande frequenti per altre soluzioni CX Enterprise](faq-intro/other-faq.md)

## Risorse aggiuntive

* [Versioni della libreria JavaScript ECID](https://github.com/Adobe-Marketing-Cloud/id-service/releases) su GitHub
* [Note sulla versione del servizio ID visitatore](release-notes/notes-2022.md)
* [Centro per la privacy Adobe](http://www.adobe.com/it/privacy.html)
* [Documentazione di Adobe CX Enterprise](https://experienceleague.adobe.com/docs/home.html?lang=it)

