---
description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'uso delle soluzioni Experience Cloud con il servizio ID.
keywords: Servizio ID
seo-description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'uso delle soluzioni Experience Cloud con il servizio ID.
seo-title: Domande frequenti per altre soluzioni Experience Cloud
title: Domande frequenti per altre soluzioni Experience Cloud
uuid: 7d848663-6cbb-4d80-ab06-7b6d2dc20e2b
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Domande frequenti per altre soluzioni Experience Cloud{#faqs-for-other-experience-cloud-solutions}

Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all&#39;uso delle soluzioni Experience Cloud con il servizio ID.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Posso usare Dynamic Tag Management per distribuire il servizio ID?**

Sì, questa è l&#39;opzione di distribuzione preferita e consigliata.

Consulta  [Implementazione standard con DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics e Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**La cronologia delle visite di un utente verrà esportata[!DNL Adobe Analytics]in[!DNL Audience Manager]seguito all&#39;implementazione del servizio Identità Experience Platform?**

In questo caso sono disponibili due opzioni:

* Se un utente ha un&#39;attività di visita dopo aver implementato il servizio ID, il visitatore e la cronologia vengono inclusi nell&#39;esportazione dei dati in [!DNL Audience Manager].
* Se un utente non ha un&#39;attività di visita dopo aver implementato il servizio ID, il visitatore e la cronologia non vengono inclusi nell&#39;esportazione dei dati in Audience Manager. Poiché la nuova attività non è presente, non è possibile associare l&#39;ID di Analytics a quello di Experience Cloud.

