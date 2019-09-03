---
description: In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.
keywords: Servizio ID
seo-description: In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.
seo-title: Implementazione lato server con JavaScript
title: Implementazione lato server con JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Implementazione lato server con JavaScript {#server-side-implementation-mixed-with-javascript}

In alcune implementazioni, gli ID visitatore vengono trasferiti da JavaScript a un server, pertanto gli eventi aggiuntivi di Analytics (ad esempio gli acquisti) possono essere inviati dal server.

L’API del servizio ID fornisce i metodi, [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) e [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md), per recuperare i valori ID che possono essere quindi trasferiti al server.

Controlla sia l'ID visitatore di Experience Cloud, sia quello di Analytics e inviali (se presenti) per fare in modo che tutti i dati inviati vengano associati con il profilo visitatore di Analytics.

>[!IMPORTANT]
>
>AppMeasurement per Java al momento non supporta il servizio Experience Cloud Identity.

## API di inserimento dati {#section-955ce7664a4646d38b3005cb2df40baf}

Include l'ID visitatore di Analytics (se è impostato) nell'elemento `<visitorID>`.

Include l'ID visitatore di Experience Cloud nell'elemento `<marketingCloudVisitorID>`.

Consulta [Tag XML supportati](https://marketing.adobe.com/developer/it_IT/documentation/data-insertion/r-supported-tags).

## AppMeasurement per Java {#section-d664b94934924d048300d9c2b6560085}

Al momento il servizio Experience Cloud Identity non è supportato da AppMeasurement per Java.
