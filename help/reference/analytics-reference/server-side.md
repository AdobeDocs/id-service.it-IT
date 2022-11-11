---
description: In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.
keywords: Servizio ID
title: Implementazione lato server con JavaScript
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# Implementazione lato server con JavaScript {#server-side-implementation-mixed-with-javascript}

In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.

L’API del servizio ID fornisce i metodi [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) e [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) per recuperare i valori ID che possono poi essere passati al server.

Controlla sia l&#39;ID visitatore di Experience Cloud, sia quello di Analytics e inviali (se presenti) per fare in modo che tutti i dati inviati vengano associati con il profilo visitatore di Analytics.

>[!IMPORTANT]
>
>AppMeasurement per Java al momento non supporta il servizio Experience Cloud Identity.

## API di inserimento dati {#section-955ce7664a4646d38b3005cb2df40baf}

Include l&#39;ID visitatore di Analytics (se è impostato) nell&#39;elemento `<visitorID>`.

Include l&#39;ID visitatore di Experience Cloud nell&#39;elemento `<marketingCloudVisitorID>`.

Consulta [Tag XML supportati](https://developer.adobe.com/).

## AppMeasurement per Java {#section-d664b94934924d048300d9c2b6560085}

Al momento il servizio Experience Cloud Identity non è supportato da AppMeasurement per Java.
