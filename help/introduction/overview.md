---
description: Il ruolo del servizio ID visitatori in Adobe CX Enterprise.
title: Panoramica del servizio ID visitatore di Adobe
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
TQID: https://experienceleague.adobe.com/fkT81V3iLEz2irg-3SDoyx733RNhqa2zWV1FgiXoYO4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 497
ht-degree: 18%

---

# Panoramica del servizio ID visitatore di Adobe

Il servizio ID visitatore di Adobe abilita il framework comune di identificazione per i servizi applicativi CX Enterprise. Puoi usare il servizio ID visitatori per impostare [ECID](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=it).

L&#39;ECID è uno spazio dei nomi di identità condiviso e utilizzato nelle applicazioni Adobe Experience Platform e CX Enterprise per monitorare il comportamento dei visitatori e garantire che ogni dispositivo abbia un identificatore univoco che possa persistere in più sessioni.

>[!TIP]
>
>Il servizio ID visitatori, il servizio Experience Platform Identity e l&#39;ECID sono tre entità **diverse**.

Il Servizio ID visitatore può sostituire diversi ID specifici dell&#39;applicazione e utilizzare la funzionalità [ID cliente e stati di autenticazione](/help/reference/authenticated-state.md) per consentire la trasmissione degli ID dei clienti a CX Enterprise.

>[!NOTE]
>
>Il servizio ID visitatore funziona solo con i servizi applicativi CX Enterprise ai quali sei abbonato e non fornisce l&#39;accesso ad altri servizi applicativi se non sei abbonato.

Il servizio ID visitatori supporta le seguenti applicazioni:

* [Adobe Analytics](https://business.adobe.com/it/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/it/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/it/products/target/adobe-target.html)

Il Servizio ID visitatore è un componente integrale di un gran numero di funzioni, miglioramenti e servizi correnti e futuri di CX Enterprise. Attualmente, il servizio ID visitatori supporta [Analytics](http://www.adobe.com/it/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/it/marketing-cloud/data-management-platform.html) e [Target](http://www.adobe.com/it/marketing-cloud/testing-targeting.html). Se non hai implementato il servizio ID visitatore, ti consigliamo di considerare fin da ora una strategia di migrazione.

## Riepilogo delle funzioni

In sintesi, il Servizio ID visitatore aiuta a:

* Identificare in modo univoco un visitatore su un dispositivo in più applicazioni.
* Imposta un cookie di prima parte nel dominio del cliente affinché sia possibile eseguire il tracciamento sullo stesso dominio. Per ulteriori informazioni, consulta il documento su [cookie e sul servizio ID visitatore](./cookies.md).
* Riceve alias e mappature ID dai clienti e dai partner aziendali CX.
* Gestisce la sincronizzazione ID in CX Enterprise.
* Supporta la sincronizzazione ID con terze parti diverse all&#39;interno dell&#39;ecosistema di tecnologie per la gestione di annunci.

## Requisiti del servizio ID visitatore

La tua soluzione e altre librerie di codice di Adobe devono soddisfare [alcuni requisiti](/help/reference/requirements.md) prima di poter utilizzare il servizio ID visitatori.

* [Cookie e il servizio ID visitatore](cookies.md): il servizio ID visitatore utilizza l&#39;ID organizzazione IMS, il cookie AMCV di CX Enterprise e un cookie demdex per creare e memorizzare identificatori univoci e costanti per i visitatori del sito. Questi cookie consentono al servizio ID visitatore di tenere traccia dei visitatori nei diversi domini e di condividere i dati tra le diverse soluzioni aziendali CX.
* [Richiesta e impostazione degli ID da parte del servizio ID visitatori](id-request.md): panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l&#39;assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti CX Enterprise con i propri ID organizzazione IMS.
* [Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza](match-rates.md): panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio ID visitatore, inclusi Adobe Media Optimizer e il servizio ID visitatore.

