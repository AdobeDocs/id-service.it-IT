---
title: Usa il servizio Opt-in per controllare le attività Experience Cloud in base al consenso degli utenti
description: L’oggetto Opt-in di Adobe è un’estensione del servizio Adobe Experience Platform Identity, utile per controllare se e quali soluzioni di Experience Cloud possono creare cookie su pagine web o avviare beacon, in base al consenso dell’utente finale.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 47%

---

# Controllare le attività Experience Cloud in base al consenso degli utenti

L&#39;Adobe [!UICONTROL Opt-in] L’oggetto è un’estensione dell’Adobe [!UICONTROL Servizio Experience Platform Identity], progettato per aiutarti a controllare se e quali soluzioni di Experience Cloud possono creare cookie su pagine web o avviare beacon, in base al consenso dell’utente finale.

## Nozioni di base del servizio [!UICONTROL Opt-in]

Un aspetto importante della normativa sulla privacy riguarda l’acquisizione e la trasmissione del consenso degli utenti in merito a come e da chi possono essere utilizzati i loro dati personali. La versione più recente del [!UICONTROL Servizio identità] include funzionalità che forniscono l&#39;attivazione condizionale (ad esempio, pre e post-consenso) dei tag della soluzione di Experience Cloud, in base al fatto che venga dato o meno il consenso dell&#39;utente finale. Questo processo viene mostrato nell&#39;immagine seguente:

![ Diagramma del funzionamento del servizio [!UICONTROL  Opt-in] ](assets/opt-in.png)

[!UICONTROL Opt-in] funziona come segue:

**Se il servizio [!UICONTROL Opt-in] è attivato nel servizio Identity (tramite una variabile booleana), l’attivazione di tag o l’impostazione di cookie da parte delle librerie della soluzione Experience Cloud viene rinviata fino a quando non si riceve il consenso per tale soluzione.**

[!UICONTROL Opt-in] ti consente anche di decidere se i tag vengono attivati prima del consenso dell’utente, e quindi queste informazioni di consenso (insieme al consenso fornito dall’utente finale) vengono memorizzate in modo che possano essere utilizzate negli hit successivi. L’archiviazione del consenso è disponibile nelle opzioni di [!UICONTROL Opt-in], oppure tramite l’integrazione con una soluzione CMP in cui possono essere archiviate le opzioni di consenso selezionate.

## Abilitazione e configurazione di [!UICONTROL Opt-in]

[!UICONTROL Opt-in] è facilmente configurabile con i tag Adobe Experience Platform (precedentemente Launch). come illustrato da questo breve video.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Se non si utilizzano tag di Experience Platform, è possibile impostare [!UICONTROL Opt-in]configurazione nell’inizializzazione dell’oggetto Visitor globale, come mostrato nella [documentazione](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## Implementazione di [!UICONTROL Opt-in] sulla pagina

La configurazione e l’impostazione back-end sono necessarie solo in preparazione alla fornitura di un’interfaccia che offra ai visitatori del sito le opzioni di consenso da selezionare. Puoi creare tale interfaccia utente internamente oppure puoi rivolgerti a un partner CMP (Consent Management Platform).

Quando si imposta un’interfaccia utente affinché il servizio [!UICONTROL Opt-in] possa raccogliere le preferenze di consenso dell’utente, è necessario configurarla per chiamare delle API che si agganciano al servizio [!UICONTROL Opt-in] e lo informano se il consenso è applicabile solo ad alcune o a tutte le soluzioni Adobe Experience Cloud. Per informazioni dettagliate su queste API, consulta la [documentazione di riferimento di Opt-in](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en). Ulteriori informazioni sul servizio Opt-in sono disponibili anche nelle pagine della documentazione circostanti.

## Demo di [!UICONTROL Opt-in]

Nel video seguente, vedi una breve demo di [!UICONTROL Opt-in] lavorare sulla pagina e come può influenzare se le soluzioni Experience Cloud possono impostare i cookie, avviare i beacon e così via.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**NOTA:** È importante notare che al momento della stesura del presente articolo, [!UICONTROL Opt-in] non è stato incorporato nelle librerie per tutte le applicazioni Experience Cloud. Attualmente [!UICONTROL Opt-in] supporta le seguenti librerie:

* Servizio Identity
* Analytics
* Audience Manager
* [!DNL Target]
