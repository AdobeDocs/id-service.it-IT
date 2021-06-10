---
description: Se utilizzi un sito di accesso principale per l’identificazione dei clienti prima che visitino altri domini, un CNAME consente il monitoraggio tra più domini nei browser che non accettano i cookie di terze parti (ad esempio Safari).
keywords: ordine delle operazioni;servizio ID
title: Panoramica sull’implementazione di CNAME
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Panoramica sull’implementazione di CNAME {#cname-implementation-overview}

Le implementazioni di CNAME consentono di personalizzare il dominio di raccolta utilizzato da Adobe in modo che corrispondano al tuo dominio. Questo consente ad Adobe di impostare cookie di prime parti sul lato server anziché sul lato client utilizzando JavaScript. In passato, questi cookie di prime parti lato server non erano soggetti ai limiti imposti dalla policy ITP (Intelligent Tracking Prevention) di Apple. Tuttavia, a novembre 2020, [!DNL Apple] ha aggiornato i propri criteri in modo da applicare le stesse limitazioni anche ai cookie impostati tramite CNAME. Attualmente, sia i cookie impostati sul lato server tramite CNAME che quelli impostati sul lato client tramite JavaScript sono soggetti a una scadenza di sette giorni o 24 ore in ITP. Per ulteriori informazioni sulle policy ITP, consulta questo documento di [!DNL Apple] sulla [prevenzione del tracciamento](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Sebbene un’implementazione di CNAME non fornisca alcun vantaggio in termini di durata dei cookie, potrebbe offrire altri vantaggi, ad esempio riguardo gli ad blocker e i browser meno comuni che impediscono l’invio dei dati a domini classificati come tracciatori. In questi casi, l’utilizzo di un CNAME potrebbe agevolare la raccolta di dati relativi agli utenti che utilizzano tali strumenti.