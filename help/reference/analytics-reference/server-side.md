---
description: In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.
keywords: ID Service
seo-description: In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.
seo-title: Implementazione lato server con JavaScript
title: Implementazione lato server con JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '211'
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

Consulta [Tag XML supportati](https://www.adobe.io).

## AppMeasurement per Java {#section-d664b94934924d048300d9c2b6560085}

Al momento il servizio Experience Cloud Identity non è supportato da AppMeasurement per Java.
