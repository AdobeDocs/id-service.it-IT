---
title: Usare il servizio Opt-in per controllare le attività Experience Cloud in base al consenso degli utenti
description: L’oggetto Adobe Opt-in è un’estensione di Adobe Experience Platform Identity Service, utile per controllare se e quali soluzioni Experience Cloud possono creare dei cookie su pagine web o avviare dei beacon, in base al consenso dell’utente finale.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 36%

---

# Controllare le attività Experience Cloud in base al consenso degli utenti

L&#39;oggetto Adobe [!UICONTROL Opt-in] è un&#39;estensione di Adobe [!UICONTROL Experience Platform Identity Service], progettata per consentire il controllo di eventuali soluzioni Experience Cloud che possono creare cookie su pagine Web o avviare beacon, in base al consenso dell&#39;utente finale.

## Nozioni di base di [!UICONTROL Opt-In]

Un aspetto importante della normativa sulla privacy riguarda l’acquisizione e la trasmissione del consenso degli utenti in merito a come e da chi possono essere utilizzati i loro dati personali. La versione più recente di [!UICONTROL Identity Service] include funzionalità per l&#39;attivazione condizionale (ad esempio, pre e post-consenso) dei tag della soluzione Experience Cloud, in base al consenso fornito o negato dall&#39;utente finale. Tale processo è illustrato dall’immagine seguente:

![Diagramma del funzionamento di [!UICONTROL Opt-in]](assets/opt-in.png)

[!UICONTROL Opt-in] funziona come segue:

**Se [!UICONTROL Opt-in] è abilitato nel servizio Identity (tramite una variabile booleana), l&#39;attivazione di tag o l&#39;impostazione di cookie da parte delle librerie della soluzione Experience Cloud viene rinviata fino a quando non si riceve il consenso per tale soluzione.**

[!UICONTROL Opt-in] consente inoltre di decidere se i tag devono essere attivati prima del consenso dell&#39;utente. Le informazioni sul consenso (insieme al consenso fornito dall&#39;utente finale) vengono quindi memorizzate e utilizzate anche per gli hit successivi. L&#39;archiviazione del consenso è disponibile nelle opzioni [!UICONTROL Opt-in] oppure è possibile eseguire l&#39;integrazione con una CMP in modo che memorizzi le selezioni del consenso.

## Abilitazione e configurazione di [!UICONTROL Opt-In]

[!UICONTROL Opt-in] può essere facilmente configurato con i tag di Adobe Experience Platform (precedentemente Launch). come illustrato da questo breve video.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Se non utilizzi i tag di Experience Platform, puoi impostare la configurazione di [!UICONTROL Opt-in] nell&#39;inizializzazione dell&#39;oggetto globale Visitor, come descritto nella [documentazione](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=it).

## Implementazione di [!UICONTROL Opt-In] sulla pagina

La configurazione e l’impostazione back-end sono necessarie solo in preparazione alla fornitura di un’interfaccia che offra ai visitatori del sito le opzioni di consenso da selezionare. Puoi creare tale interfaccia utente internamente oppure puoi rivolgerti a un partner CMP (Consent Management Platform).

Quando si imposta un&#39;interfaccia utente per l&#39;utilizzo di [!UICONTROL Opt-in] per raccogliere il consenso, è necessario configurarla per chiamare le API che si agganciano a [!UICONTROL Opt-in] e lo informano per fornire il consenso ad alcune o a tutte le soluzioni Adobe Experience Cloud. Per informazioni dettagliate su queste API, consulta la [documentazione di riferimento di Opt-in](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=it). Ulteriori informazioni sul servizio Opt-in sono disponibili anche nelle pagine della documentazione circostanti.

## Demo di [!UICONTROL Opt-In]

Il video seguente offre una breve dimostrazione di [!UICONTROL Opt-in] che lavora sulla pagina e di come può determinare se le soluzioni Experience Cloud possano o meno impostare i cookie, avviare i beacon e così via.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**NOTA:** Al momento della stesura di questo articolo, [!UICONTROL Opt-in] non è ancora stato integrato nelle librerie di tutte le applicazioni Experience Cloud. Le librerie attualmente supportate per [!UICONTROL Opt-in] sono:

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]

