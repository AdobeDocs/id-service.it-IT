---
description: Panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud Identity, inclusi Adobe Media Optimizer e il servizio ID.
keywords: Servizio ID
title: Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza
exl-id: 9386824c-7d04-459b-9417-45b67f8a7b37
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '805'
ht-degree: 100%

---

# Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza {#understanding-id-synchronization-and-match-rates}

Panoramica dei processi di sincronizzazione ID e delle percentuali di corrispondenza nel servizio Experience Cloud Identity, inclusi Adobe Media Optimizer e il servizio ID.

## Sincronizzazione degli ID e percentuali di corrispondenza {#section-f652aae7234945e89d26dd833c5215fb}

La sincronizzazione ID associa gli ID assegnati dal servizio ID agli ID assegnati ai visitatori del sito dai nostri clienti. Ad esempio, supponiamo che il servizio ID abbia assegnato l’ID visitatore 1234. Un’altra piattaforma conosce questo visitatore come ID 4321. Il servizio ID associa questi ID durante il processo di sincronizzazione. I risultati aggiungono nuovi punti dati a ciò che i nostri clienti sanno sui visitatori del loro sito. Inoltre, se il servizio ID non è in grado di associare un ID ne crea uno nuovo e lo utilizza per la sincronizzazione futura.

Le percentuali di corrispondenza misurano e confermano l’efficacia del processo di sincronizzazione ID. Percentuali elevate di corrispondenza suggeriscono che un particolare servizio sarà più efficace e darà accesso a un pubblico online più ampio rispetto a un servizio con percentuali di corrispondenza più basse. Confrontare le percentuali di corrispondenza è un modo quantificabile per valutare diverse piattaforme ad tech integrate.

![](assets/idsync2.png)

**Come ottenere elevate percentuali di corrispondenza**

Per generare percentuali di corrispondenza elevate, è importante impostare correttamente il servizio ID (vedi la [guida all&#39;implementazione standard](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). Una corretta implementazione consente di ottenere percentuali di corrispondenza elevate, perché consente al servizio ID di impostare i cookie necessari per funzionare e sincronizzare gli ID con i partner dati abilitati. Tuttavia, fattori come connessioni Internet lente, raccolta di dati da dispositivi mobile o reti wireless possono influenzare l’efficacia con cui il servizio ID raccoglie, sincronizza e associa gli ID. Tali variabili lato client non possono essere controllate dal servizio ID e da [!DNL Adobe].

## Descrizione del processo di sincronizzazione degli ID {#section-a541a85cbbc74f5682824b1a2ee2a657}

Il servizio ID sincronizza gli ID in tempo reale. Questo processo funziona nel browser invece che tramite un trasferimento dati da server a server. Nella tabella seguente sono descritti i passaggi del processo di sincronizzazione ID.

**Passaggio 1: caricamento della pagina**

Quando un visitatore accede al sito e carica una pagina, la funzione `Visitor.getInstance` esegue una chiamata [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) o JSON-P al servizio ID. Il servizio ID risponde con un cookie che include l&#39;identificatore [!DNL Experience Cloud] ID (MID) del visitatore. L&#39;identificatore MID è un ID univoco assegnato a ogni visitatore del sito. Consulta anche [Cookie e il servizio Experience Cloud Identity](../introduction/cookies.md).

**Passaggio 2: caricamento dell&#39;iFrame**

Durante il caricamento della pagina, il servizio ID carica un iFrame denominato *`Destination Publishing iFrame`*. Il [!UICONTROL Destination Publishing iFrame] viene caricato in un dominio separato dalla pagina padre. Questo consente di garantire la prestazione della pagina e di migliorare la sicurezza perché l’iFrame:

* viene caricato in modo asincrono in relazione alla pagina padre. Questo significa che la pagina padre può essere caricata indipendentemente dal [!UICONTROL Destination Publishing iFrame]. Il caricamento dell’iFrame e dei pixel di sincronizzazione ID dall’interno dell’iFrame non influisce sulla pagina padre o sull’esperienza utente.
* Viene caricato il più rapidamente possibile. Se è troppo veloce, puoi caricare l’iFrame dopo l’evento di caricamento della finestra (non consigliato). Per informazioni, consulta [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4).
* Impedisce al codice presente nell&#39;iFrame di accedere alla pagina padre o di incidere su di essa.

Consulta anche: [Richiesta e impostazione degli ID da parte del servizio Experience Cloud Identity...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**Passaggio 3: attivazione della sincronizzazione ID**

La sincronizzazione ID è un URL attivato nel Destination Publishing iFrame. Come mostrato in questo esempio generico, un URL di sincronizzazione ID contiene l&#39;endpoint di sincronizzazione ID di un partner e un URL di reindirizzamento verso [!DNL Adobe] che include tale ID.

`http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<ADOBE_PARTNER_ID>&dpuuid=<PARTNER_UUID>`

Vedi anche [Sincronizzazione degli ID per trasferimenti di dati in entrata](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/sending-audience-data/batch-data-transfer-process/id-sync-http.html?lang=it).

**Passaggio 4: archiviazione degli ID**

Gli ID sincronizzati sono archiviati nei [server dati edge e core](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/system-components/components-edge.html?lang=it).

## I servizi di sincronizzazione gestiscono la sincronizzazione degli ID {#section-cd5784d7ad404a24aa28ad4816a0119a}

Il termine *`Sync Services`* fa riferimento alle tecnologie interne [!DNL Experience Cloud] responsabili della sincronizzazione ID. Il servizio è abilitato per impostazione predefinita. Per disattivarlo, aggiungi una [variabile opzionale](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) alla funzione `Visitor.getInstance` del servizio ID. I servizi di sincronizzazione effettuano la corrispondenza tra diversi ID di [!DNL Experience Cloud], ad esempio:

* ID di [!DNL Experience Cloud] cookie terze parti di con [!DNL Experience Cloud] ID di prime parti di.

* ID di [!DNL Experience Cloud] cookie prime parti di con ID di [!DNL Adobe Media Optimizer] (AMO).

* ID di cookie terze parti di [!DNL Experience Cloud] con ID di fornitori di dati terze parti e piattaforme di targeting. Questo comprende servizi e piattaforme come fornitori di dati, piattaforme lato domanda o fornitura, reti per annunci, scambi, ecc.
* ID di [!DNL Experience Cloud] cookie di prime parti di con ID di partner per diversi dispositivi.

## Sincronizzazione degli ID con Adobe Advertising Cloud {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Advertising Cloud] (prima chiamato [!DNL Adobe Media Optimizer]) è un’eccezione del processo di sincronizzazione ID basato sull’iFrame. Poiché [!DNL Advertising Cloud] è un dominio fidato, le sincronizzazioni ID hanno luogo dalla pagina padre invece che nel [!UICONTROL Destination Publishing iFrame]. Durante la sincronizzazione, il servizio ID chiama [!DNL Advertising Cloud] su `cm.eversttech.net`, che è un nome di dominio legacy usato da [!DNL Advertising Cloud] prima della sua acquisizione da parte di Adobe. L&#39;invio di dati a [!DNL Advertising Cloud] aiuta a migliore le percentuali di corrispondenza ed è automatico per i clienti del servizio ID che usano la versione 2.0 (o superiore). Vedi anche [Cookie di Advertising Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-advertising-cloud.html?lang=it).

>[!MORELIKETHIS]
>
>* [Informazioni sulle chiamate al dominio demdex](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=it)

