---
description: Panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud ID, inclusi Adobe Media Optimizer e il servizio ID.
keywords: Servizio ID
seo-description: Panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud ID, inclusi Adobe Media Optimizer e il servizio ID.
seo-title: Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza
title: Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza
uuid: 31 bd 655 f -2 b 9 e -4 f 8 d -9 a 1 f-e 81 a 6110 eda 8
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza{#understanding-id-synchronization-and-match-rates}

Panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud ID, inclusi Adobe Media Optimizer e il servizio ID.

## Sincronizzazione ID e percentuali di corrispondenza {#section-f652aae7234945e89d26dd833c5215fb}

La sincronizzazione degli ID effettua la corrispondenza tra gli ID assegnati dal servizio ID e quelli assegnati ai visitatori del sito dal nostro cliente. Ad esempio, supponiamo che il servizio ID abbia assegnato l&#39;ID visitatore 1234. Un&#39;altra piattaforma conosce invece lo stesso visitatore con l&#39;ID 4321. Nel processo di sincronizzazione, il servizio ID associa questi due ID. I risultati aggiungono nuovi punti di dati a ciò che il nostro cliente sa sui visitatori del suo sito. Inoltre, se il servizio ID non trova alcuna corrispondenza per un ID, ne crea uno nuovo che utilizzerà per successive operazioni di sincronizzazione.

Le percentuali di corrispondenza misurano e convalidano l&#39;efficacia del processo di sincronizzazione degli ID. Percentuali elevate suggeriscono che un particolare servizio sarà più efficace e permettono di accedere a un pubblico online più ampio rispetto a un servizio con percentuali più basse. Confrontando le percentuali di corrispondenza è possibile valutare diverse piattaforme integrate di tecnologie per la gestione di annunci.

![](assets/idsync2.png)

**Come ottenere percentuali di corrispondenza elevate**

Per generare percentuali di corrispondenza elevate, è importante configurare correttamente il servizio ID (consulta la [guida all&#39;implementazione standard](../mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). Una corretta implementazione permette di ottenere percentuali di corrispondenza elevate, poiché consente al servizio ID di impostare i cookie necessari per il suo funzionamento e per sincronizzare gli ID con i partner di dati abilitati. Tuttavia, fattori quali connessioni Internet lente, raccolta di dati da dispositivi mobili o rete wireless possono incidere sull&#39;efficacia di raccolta, sincronizzazione e corrispondenza degli ID da parte del servizio ID. Tali variabili lato client non possono essere controllate dal servizio ID e da [!DNL Adobe].

## Procedura di sincronizzazione ID descritta {#section-a541a85cbbc74f5682824b1a2ee2a657}

Il servizio ID sincronizza gli ID in tempo reale. Questo processo funziona nel browser e non attraverso il trasferimento di dati da server a server. La tabella seguente descrive i passaggi del processo di sincronizzazione degli ID.

**Passaggio 1: Carica pagina**

Quando un visitatore accede al sito e carica una pagina, la `Visitor.getInstance` funzione esegue una [chiamata CORS](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758) o JSON-P al servizio ID. Il servizio ID risponde con un cookie che include l&#39;identificatore [!DNL Experience Cloud] ID (MID) del visitatore. L&#39;identificatore MID è un ID univoco assegnato a ogni visitatore del sito. Vedi anche [Cookie e il servizio Experience Cloud ID](../mcvid-introduction/mcvid-cookies.md).

**Passaggio 2: caricamento dell&#39;iFrame**

Durante il caricamento della pagina, il servizio ID carica un iFrame denominato *`Destination Publishing iFrame`*. I [!DNL Destination Publishing iFrame] carichi vengono caricati in un dominio separato dalla pagina padre. Questo assicura buone prestazioni della pagina e migliora la sicurezza perché l&#39;iFrame:

* Viene caricato in modo asincrono rispetto alla pagina padre. Ciò significa che la pagina padre può essere caricata in modo indipendente dall &#39; [!DNL Destination Publishing iFrame]. Il caricamento dell&#39;iFrame e dei pixel di sincronizzazione ID dall&#39;interno dell&#39;iFrame non incide sulle prestazioni della pagina padre né sull&#39;esperienza dell&#39;utente.
* Viene caricato il più rapidamente possibile. Se questo risulta troppo veloce, puoi caricare l&#39;iFrame dopo l&#39;evento di caricamento della finestra (non consigliato). Per informazioni, consultate [idsyncattachiframeonwindowload](../mcvid-library/mcvid-function-vars/mcvid-idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) .
* Impedisce al codice presente nell&#39;iFrame di accedere alla pagina padre o di incidere su di essa.

Vedi anche [, in che modo il servizio Experience Cloud ID richiede e imposta gli ID…](../mcvid-introduction/mcvid-id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)

**Passaggio 3: attivazione delle sincronizzazioni ID**

La sincronizzazione ID consiste in un URL attivato nell&#39;iFrame di pubblicazione della destinazione. Come mostrato in questo esempio generico, un URL di sincronizzazione ID contiene l&#39;endpoint di sincronizzazione ID di un partner e un URL di reindirizzamento verso [!DNL Adobe] che include tale ID.

```
http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<
<varname>
  ADOBE_PARTNER_ID
</varname>>&dpuuid=<
<varname>
  PARTNER_UUID
</varname>>
```

Vedi anche [Sincronizzazione degli ID per trasferimenti di dati in entrata](https://marketing.adobe.com/resources/help/en_US/aam/c_id_sync_in.html).

**Passaggio 4: archiviazione degli ID**

Gli ID sincronizzati vengono archiviati nei [server di dati edge e core](https://marketing.adobe.com/resources/help/en_US/aam/c_compedge.html).

## I servizi di sincronizzazione gestiscono la sincronizzazione degli ID {#section-cd5784d7ad404a24aa28ad4816a0119a}

Il termine *`Sync Services`* fa riferimento [!DNL Experience Cloud] a tecnologie interne responsabili della sincronizzazione ID. Il servizio è abilitato per impostazione predefinita. Per disattivarlo, aggiungi una [variabile opzionale](../mcvid-library/mcvid-function-vars/mcvid-disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) alla funzione `Visitor.getInstance` del servizio ID. I servizi di sincronizzazione corrispondono [!DNL Experience Cloud] a ID diversi, ad esempio:

* ID [!DNL Experience Cloud] di cookie di terze parti con [!DNL Experience Cloud] ID di prime parti.

* ID [!DNL Experience Cloud] di cookie di prime parti con [!DNL Adobe Media Optimizer] ID (AMO).

* ID di cookie terze parti di [!DNL Experience Cloud] con ID di fornitori di dati terze parti e piattaforme di targeting. Questo comprende servizi e piattaforme come fornitori di dati, piattaforme lato domanda o fornitura, reti per annunci, scambi, ecc.
* ID [!DNL Experience Cloud] di cookie di prime parti con ID per partner diversi.

## Sincronizzazione ID con Adobe Media Optimizer {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Media Optimizer] è un&#39;eccezione al processo di sincronizzazione ID basato su iframe. Poiché [!DNL Media Optimizer] è un dominio affidabile, le sincronizzazioni ID hanno luogo dalla pagina padre anziché da [!DNL Destination Publishing iFrame]. Durante la sincronizzazione, le chiamate al servizio ID [!DNL Media Optimizer] sono utilizzate a `cm.eversttech.net`partire da un nome di dominio legacy utilizzato prima [!DNL Media Optimizer] della sua acquisizione da parte di Adobe. L&#39;invio di dati a [!DNL Media Optimizer] aiuta a migliore le percentuali di corrispondenza ed è automatico per i clienti del servizio ID che usano la versione 2.0 (o superiore). Vedi anche [Cookie di Media Optimizer](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_media_optimizer.html).

>[!MORE_ LIKE_ THIS]
>
>* [Informazioni sulle chiamate al dominio demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)

