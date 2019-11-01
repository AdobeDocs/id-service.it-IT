---
description: Panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud Identity, inclusi Adobe Media Optimizer e il servizio ID.
keywords: Servizio ID
seo-description: Panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud Identity, inclusi Adobe Media Optimizer e il servizio ID.
seo-title: Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza
title: Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza
uuid: 31bd655f-2b9e-4f8d-9a1f-e81a6110eda8
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza{#understanding-id-synchronization-and-match-rates}

Panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud Identity, inclusi Adobe Media Optimizer e il servizio ID.

## Sincronizzazione degli ID e percentuali di corrispondenza {#section-f652aae7234945e89d26dd833c5215fb}

La sincronizzazione degli ID effettua la corrispondenza tra gli ID assegnati dal servizio ID e quelli assegnati ai visitatori del sito dal nostro cliente. Ad esempio, supponiamo che il servizio ID abbia assegnato l'ID visitatore 1234. Un'altra piattaforma conosce invece lo stesso visitatore con l'ID 4321. Nel processo di sincronizzazione, il servizio ID associa questi due ID. I risultati aggiungono nuovi punti di dati a ciò che il nostro cliente sa sui visitatori del suo sito. Inoltre, se il servizio ID non trova alcuna corrispondenza per un ID, ne crea uno nuovo che utilizzerà per successive operazioni di sincronizzazione.

Le percentuali di corrispondenza misurano e convalidano l'efficacia del processo di sincronizzazione degli ID. Percentuali elevate suggeriscono che un particolare servizio sarà più efficace e permettono di accedere a un pubblico online più ampio rispetto a un servizio con percentuali più basse. Confrontando le percentuali di corrispondenza è possibile valutare diverse piattaforme integrate di tecnologie per la gestione di annunci.

![](assets/idsync2.png)

**Come ottenere elevate percentuali di corrispondenza**

Per generare percentuali di corrispondenza elevate, è importante impostare correttamente il servizio ID (vedi la [guida all'implementazione standard](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). Una corretta implementazione permette di ottenere percentuali di corrispondenza elevate, poiché consente al servizio ID di impostare i cookie necessari per il suo funzionamento e per sincronizzare gli ID con i partner di dati abilitati. Tuttavia, fattori quali connessioni Internet lente, raccolta di dati da dispositivi mobili o rete wireless possono incidere sull'efficacia di raccolta, sincronizzazione e corrispondenza degli ID da parte del servizio ID. Tali variabili lato client non possono essere controllate dal servizio ID e da [!DNL Adobe].

## Descrizione del processo di sincronizzazione degli ID {#section-a541a85cbbc74f5682824b1a2ee2a657}

Il servizio ID sincronizza gli ID in tempo reale. Questo processo funziona nel browser e non attraverso il trasferimento di dati da server a server. La tabella seguente descrive i passaggi del processo di sincronizzazione degli ID.

**Passaggio 1: caricamento della pagina**

Quando un visitatore accede al sito e carica una pagina, la funzione `Visitor.getInstance` esegue una chiamata [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) o JSON-P al servizio ID. Il servizio ID risponde con un cookie che include l'identificatore [!DNL Experience Cloud] ID (MID) del visitatore. L'identificatore MID è un ID univoco assegnato a ogni visitatore del sito. Consulta anche [Cookie e il servizio Experience Cloud Identity](../introduction/cookies.md).

**Passaggio 2: caricamento dell'iFrame**

Durante il caricamento della pagina, il servizio ID carica un iFrame denominato *`Destination Publishing iFrame`*. L'[!UICONTROL iFrame di pubblicazione della destinazione] viene caricato in un dominio diverso dalla pagina padre. Questo assicura buone prestazioni della pagina e migliora la sicurezza perché l'iFrame:

* Viene caricato in modo asincrono rispetto alla pagina padre. Questo significa che la pagina padre può essere caricata in modo indipendente dall'[!UICONTROL iFrame di pubblicazione della destinazione]. Il caricamento dell'iFrame e dei pixel di sincronizzazione ID dall'interno dell'iFrame non incide sulle prestazioni della pagina padre né sull'esperienza dell'utente.
* Viene caricato il più rapidamente possibile. Se questo risulta troppo veloce, puoi caricare l'iFrame dopo l'evento di caricamento della finestra (non consigliato). Per informazioni, consulta [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4).
* Impedisce al codice presente nell'iFrame di accedere alla pagina padre o di incidere su di essa.

Consulta anche: [Richiesta e impostazione degli ID da parte del servizio Experience Cloud Identity...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**Passaggio 3: attivazione delle sincronizzazioni ID**

La sincronizzazione ID consiste in un URL attivato nell'iFrame di pubblicazione della destinazione. Come mostrato in questo esempio generico, un URL di sincronizzazione ID contiene l'endpoint di sincronizzazione ID di un partner e un URL di reindirizzamento verso [!DNL Adobe] che include tale ID.

`http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<ADOBE_PARTNER_ID>&dpuuid=<PARTNER_UUID>`

Vedi anche [Sincronizzazione degli ID per trasferimenti di dati in entrata](https://marketing.adobe.com/resources/help/en_US/aam/c_id_sync_in.html).

**Passaggio 4: archiviazione degli ID**

Gli ID sincronizzati vengono archiviati nei [server di dati edge e core](https://marketing.adobe.com/resources/help/en_US/aam/c_compedge.html).

## I servizi di sincronizzazione gestiscono la sincronizzazione degli ID {#section-cd5784d7ad404a24aa28ad4816a0119a}

Il termine *`Sync Services`* fa riferimento alle tecnologie interne [!DNL Experience Cloud]responsabili della sincronizzazione ID. Il servizio è abilitato per impostazione predefinita. Per disattivarlo, aggiungi una [variabile opzionale](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) alla funzione `Visitor.getInstance` del servizio ID. I servizi di sincronizzazione effettuano la corrispondenza tra diversi ID di [!DNL Experience Cloud], ad esempio:

* ID di [!DNL Experience Cloud] cookie terze parti di con [!DNL Experience Cloud] ID di prime parti di.

* ID di [!DNL Experience Cloud] cookie prime parti di con ID di [!DNL Adobe Media Optimizer] (AMO).

* ID di cookie terze parti di [!DNL Experience Cloud] con ID di fornitori di dati terze parti e piattaforme di targeting. Questo comprende servizi e piattaforme come fornitori di dati, piattaforme lato domanda o fornitura, reti per annunci, scambi, ecc.
* ID di [!DNL Experience Cloud] cookie di prime parti di con ID di partner per diversi dispositivi.

## Sincronizzazione degli ID con Adobe Media Optimizer {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Media Optimizer] è un'eccezione del processo di sincronizzazione ID basato su iFrame. Poiché [!DNL Media Optimizer] è un dominio fidato, le sincronizzazioni ID hanno luogo dalla pagina padre invece che nel [!UICONTROL Destination Publishing iFrame]. Durante la sincronizzazione, il servizio ID chiama [!DNL Media Optimizer] su `cm.eversttech.net`, che è un nome di dominio legacy usato da [!DNL Media Optimizer] prima della sua acquisizione da parte di Adobe. L'invio di dati a [!DNL Media Optimizer] aiuta a migliore le percentuali di corrispondenza ed è automatico per i clienti del servizio ID che usano la versione 2.0 (o superiore). Vedi anche [Cookie di Media Optimizer](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_media_optimizer.html).

>[!MORELIKETHIS]
>
>* [Informazioni sulle chiamate al dominio demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)

