---
title: Usare il servizio Opt-in per controllare le attività Experience Cloud in base al consenso degli utenti
description: L’oggetto Adobe Opt-in è un’estensione di Adobe Experience Platform Identity Service, utile per controllare se e quali soluzioni Experience Cloud possono creare dei cookie su pagine web o avviare dei beacon, in base al consenso dell’utente finale.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 100%

---

# Controllare le attività Experience Cloud in base al consenso degli utenti

L’oggetto Adobe [!UICONTROL Opt-in] è un’estensione di [!UICONTROL Adobe Experience Platform Identity Service], utile per controllare se e quali soluzioni Experience Cloud possono creare dei cookie su pagine web o avviare dei beacon, in base al consenso fornito dall’utente finale.

## Nozioni di base del servizio [!UICONTROL Opt-in]

Un aspetto importante della normativa sulla privacy riguarda l’acquisizione e la trasmissione del consenso degli utenti in merito a come e da chi possono essere utilizzati i loro dati personali. La versione più recente di [!UICONTROL Identity Service] include funzionalità per l&#39;attivazione condizionale (ad esempio, pre e post-consenso) dei tag della soluzione Experience Cloud, in base al consenso fornito o negato dall&#39;utente finale. Tale processo è illustrato dall’immagine seguente:

![Diagramma del funzionamento del servizio [!UICONTROL Opt-in]](assets/opt-in.png)

[!UICONTROL Opt-in] funziona come segue:

**Se [!UICONTROL Opt-in] è attivato in Identity Service (tramite una variabile booleana), l’attivazione di tag o l’impostazione di cookie da parte delle librerie della soluzione Experience Cloud viene rinviata fino a quando non si riceve il consenso per tale soluzione.**

[!UICONTROL Opt-in] permette inoltre di decidere se eventuali tag devono essere attivati prima del consenso dell’utente. Le informazioni sul consenso (insieme al consenso fornito dall’utente finale) vengono quindi memorizzate e utilizzate anche per gli hit successivi. L’archiviazione del consenso è disponibile nelle opzioni di [!UICONTROL Opt-in], oppure tramite l’integrazione con una soluzione CMP in cui possono essere archiviate le opzioni di consenso selezionate.

## Abilitazione e configurazione di [!UICONTROL Opt-in]

Il servizio [!UICONTROL Opt-in] può essere facilmente configurato con i tag di Adobe Experience Platform (precedentemente Launch), come illustrato da questo breve video.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Se non utilizzi i tag di Experience Platform, puoi impostare la configurazione di [!UICONTROL Opt-in] nell’inizializzazione dell’oggetto globale Visitor, come descritto nella [documentazione](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=it).

## Implementazione di [!UICONTROL Opt-in] sulla pagina

La configurazione e l’impostazione back-end sono necessarie solo in preparazione alla fornitura di un’interfaccia che offra ai visitatori del sito le opzioni di consenso da selezionare. Puoi creare tale interfaccia utente internamente oppure puoi rivolgerti a un partner CMP (Consent Management Platform).

Quando si imposta un’interfaccia utente affinché il servizio [!UICONTROL Opt-in] possa raccogliere le preferenze di consenso dell’utente, è necessario configurarla per chiamare delle API che si agganciano al servizio [!UICONTROL Opt-in] e lo informano se il consenso è applicabile solo ad alcune o a tutte le soluzioni Adobe Experience Cloud. Per informazioni dettagliate su queste API, consulta la [documentazione di riferimento di Opt-in](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=it). Ulteriori informazioni sul servizio Opt-in sono disponibili anche nelle pagine della documentazione circostanti.

## Demo di [!UICONTROL Opt-in]

Il seguente video offre una breve dimostrazione di come funziona il servizio [!UICONTROL Opt-in] sulla pagina e di come può determinare se le soluzioni di Experience Cloud possano o meno impostare i cookie, avviare i beacon e così via.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**NOTA:** al momento della stesura di questo articolo, [!UICONTROL Opt-in] non è ancora stato integrato nelle librerie di tutte le soluzioni Experience Cloud. Attualmente [!UICONTROL Opt-in] supporta le seguenti librerie:

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
