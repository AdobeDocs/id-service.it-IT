---
description: In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.
keywords: Servizio ID
seo-description: In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.
seo-title: Implementazione lato server con JavaScript
title: Implementazione lato server con JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Implementazione lato server con JavaScript {#server-side-implementation-mixed-with-javascript}

In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.

L’API del servizio ID fornisce i metodi, [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md) e [getAnalyticsVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md), per recuperare i valori ID che possono essere quindi trasferiti al server.

Controlla sia l&#39;ID visitatore di Experience Cloud, sia quello di Analytics e inviali (se presenti) per fare in modo che tutti i dati inviati vengano associati con il profilo visitatore di Analytics.

>[!IMPORTANT]
>
>AppMeasurement per Java al momento non supporta il servizio Experience Cloud ID.

## API di inserimento dati {#section-955ce7664a4646d38b3005cb2df40baf}

Include l&#39;ID visitatore di Analytics (se è impostato) nell&#39;elemento `<visitorID>`.

Include l&#39;ID visitatore di Experience Cloud nell&#39;elemento `<marketingCloudVisitorID>`.

Consulta [Tag XML supportati](https://marketing.adobe.com/developer/it_IT/documentation/data-insertion/r-supported-tags).

## AppMeasurement per Java {#section-d664b94934924d048300d9c2b6560085}

Al momento il servizio Experience Cloud ID non è supportato da AppMeasurement per Java.
