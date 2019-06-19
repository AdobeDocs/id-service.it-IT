---
description: In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.
keywords: Servizio ID
seo-description: In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.
seo-title: Implementazione lato server con JavaScript
title: Implementazione lato server con JavaScript
uuid: 256 ea 0 e 7-1 eb 4-4 c 92-9 a 7 e-f 61 cb 1 ed 13 c 7
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Implementazione lato server con JavaScript {#server-side-implementation-mixed-with-javascript}

In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.

L’API del servizio ID fornisce i metodi, [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) e [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md), per recuperare i valori ID che possono essere quindi trasferiti al server.

Controlla sia l&#39;ID visitatore di Experience Cloud, sia quello di Analytics e inviali (se presenti) per fare in modo che tutti i dati inviati vengano associati con il profilo visitatore di Analytics.

>[!IMPORTANT]
>
>Appmeasurement per Java al momento non supporta il servizio identità Experience Platform.

## API di inserimento dati {#section-955ce7664a4646d38b3005cb2df40baf}

Includi l&#39;ID visitatore di Analytics (se impostato) nell&#39; `<visitorID>` elemento.

Include l&#39;ID visitatore Experience Cloud nell&#39; `<marketingCloudVisitorID>` elemento.

Vedi [Tag XML supportati](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags).

## AppMeasurement per Java {#section-d664b94934924d048300d9c2b6560085}

Il servizio Identità Experience Platform non è attualmente supportato da appmeasurement per Java.
