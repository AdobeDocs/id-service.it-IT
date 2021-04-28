---
description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'uso delle soluzioni Experience Cloud con il servizio ID.
keywords: Servizio ID
seo-description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'uso delle soluzioni Experience Cloud con il servizio ID.
seo-title: Domande frequenti per altre soluzioni Experience Cloud
title: Domande frequenti per altre soluzioni Experience Cloud
uuid: 7d848663-6cbb-4d80-ab06-7b6d2dc20e2b
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '211'
ht-degree: 100%

---

# Domande frequenti per altre soluzioni Experience Cloud {#faqs-for-other-experience-cloud-solutions}

Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all&#39;uso delle soluzioni Experience Cloud con il servizio ID.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Posso usare Dynamic Tag Management per implementare il servizio ID visitatore?**

Sì, questa è l’opzione di implementazione preferita e consigliata.

Consulta [Implementazione standard con DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics e Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**La cronologia delle visite di un utente verrà esportata da [!DNL Adobe Analytics] a [!DNL Audience Manager] in seguito all’implementazione del servizio Experience Cloud Identity?**

In questo caso sono disponibili due opzioni:

* Se un utente ha un&#39;attività di visita dopo aver implementato il servizio ID, il visitatore e la cronologia vengono inclusi nell&#39;esportazione dei dati in [!DNL Audience Manager].
* Se un utente non ha un&#39;attività di visita dopo aver implementato il servizio ID, il visitatore e la cronologia non vengono inclusi nell&#39;esportazione dei dati in Audience Manager. Poiché la nuova attività non è presente, non è possibile associare l’ID di Analytics all’ID di Experience Cloud.
