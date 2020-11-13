---
title: Utilizzo del consenso per il controllo delle attività  Experience Cloud in base al consenso degli utenti
description: L'oggetto di consenso  Adobe è un'estensione di Adobe Experience Platform Identity Service, progettata per aiutarti a controllare se e quali soluzioni Experience Cloud possono creare cookie su pagine Web o avviare beacon, in base al consenso dell'utente finale.
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# Controllo  attività del Experience Cloud in base al consenso degli utenti

 Adobe [!UICONTROL Opt-in] Object è un&#39;estensione del  Adobe [!UICONTROL Experience Platform Servizio]identità di , progettato per aiutarti a controllare se e quali soluzioni di Experience Cloud possono creare cookie su pagine Web o avviare beacon, in base al consenso dell&#39;utente finale.

## Le basi del [!UICONTROL consenso]

Un aspetto importante della normativa sulla privacy è l&#39;acquisizione e la trasmissione del consenso degli utenti su come i loro dati personali possono essere utilizzati e da chi. L&#39;ultima versione di [!UICONTROL Identity Service] include funzionalità che si trovano tra l&#39;utente (l&#39;interfaccia utente) e le soluzioni del Adobe  e forniscono attivazione condizionale (ad esempio, pre e post-consenso) dei tag delle soluzioni Adobe Experience Cloud in base al consenso o meno fornito dall&#39;utente finale. Questo viene mostrato nella seguente immagine:

![Diagramma del funzionamento del [!UICONTROL consenso]](assets/opt-in.png)

[!UICONTROL Il consenso] è fondamentalmente il portiere... o è il keymaster? Decidete.

Si riduce a questo:

**Se il [!UICONTROL consenso] è attivato nel servizio identità (tramite una variabile booleana), ritarda l&#39;attivazione di tag o l&#39;impostazione di cookie da parte delle librerie della soluzione del Experience Cloud  fino a quando non viene fornito il consenso per tale soluzione.**

[!UICONTROL Il consenso] consente inoltre di decidere se i tag vengono attivati *prima* del consenso dell&#39;utente, e quindi le informazioni sul consenso (insieme al consenso fornito dall&#39;utente finale) vengono memorizzate, in modo che possano essere utilizzate anche per gli hit successivi. L&#39;archiviazione del consenso è disponibile nelle opzioni di [!UICONTROL consenso] , oppure è possibile integrarsi con un CMP e fare in modo che memorizzi le selezioni del consenso.

## Abilitazione e configurazione del [!UICONTROL consenso]

[!UICONTROL Il consenso] è inoltre facilmente configurabile con  Adobe Experience Platform Launch. Guardate il seguente breve video per vedere come.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Se non utilizzi l’Experience Platform Launch, puoi impostare la configurazione del [!UICONTROL consenso]nell’inizializzazione dell’oggetto Visitor globale, come mostrato nella [documentazione](https://marketing.adobe.com/resources/help/en_US/mcvid/getting-started.html).

## Implementazione del [!UICONTROL consenso] sulla pagina

Tutta questa configurazione e la roba di back-end è solo in preparazione per fornire un&#39;interfaccia per i visitatori del sito da presentare con opzioni di consenso. L’interfaccia utente può essere creata dall’utente stesso oppure potete utilizzare un partner CMP (Consent Management Platform) per creare l’interfaccia utente.

Quando si configura un&#39;interfaccia utente per l&#39;utilizzo del [!UICONTROL consenso] per la raccolta, è necessario che sia configurata per chiamare le API che verranno collegate al [!UICONTROL consenso] e informarlo per dare il consenso ad alcune o a tutte le soluzioni Adobe Experience Cloud. Informazioni dettagliate su queste API sono disponibili nella documentazione [di riferimento per il](https://marketing.adobe.com/resources/help/en_US/mcvid/api.html)consenso. Ulteriori informazioni sul consenso sono disponibili anche nelle pagine della documentazione circostante.

## [!UICONTROL Demo di consenso]

Nel video seguente, vedete una breve dimostrazione del [!UICONTROL consenso] sulla pagina e come può influenzare se le soluzioni di Experience Cloud  possono impostare o meno i cookie, avviare beacon e così via.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**NOTA:** È importante notare che al momento della stesura di questo articolo, il [!UICONTROL consenso] non è stato integrato nelle librerie per tutte le soluzioni del Experience Cloud . Le librerie attualmente supportate per il [!UICONTROL consenso] sono:

* Servizio identità
* Analytics
* Audience Manager
* [!DNL Target]
