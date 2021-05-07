---
description: Se utilizzi un sito di accesso principale per l’identificazione dei clienti prima che visitino altri domini, un CNAME consente il monitoraggio tra più domini nei browser che non accettano i cookie di terze parti (ad esempio Safari).
keywords: ordine delle operazioni;servizio ID
seo-description: Se utilizzi un sito di accesso principale per l’identificazione dei clienti prima che visitino altri domini, un CNAME consente il monitoraggio tra più domini nei browser che non accettano i cookie di terze parti (ad esempio Safari).
seo-title: Panoramica sull’implementazione CNAME
title: Panoramica sull’implementazione CNAME
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: ebeca9e285af71872c05d58ba252ca65bde24f3d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 28%

---


# Panoramica sull&#39;implementazione CNAME{#cname-implementation-overview}

Le implementazioni CNAME ti consentono di personalizzare il dominio di raccolta utilizzato da Adobe in modo che corrispondano al tuo dominio. Questo consente ad Adobe di impostare cookie di prime parti sul lato server anziché sul lato client utilizzando JavaScript. In passato, questi cookie di prime parti lato server non erano soggetti a limiti imposti dalla politica ITP (Intelligent Tracking Prevention) di Apple. Tuttavia, a novembre 2020, [!DNL Apple] ha aggiornato i propri criteri in modo che tali limitazioni siano state applicate anche ai cookie impostati tramite CNAME. Attualmente, entrambi i cookie impostati sul lato server tramite CNAME e quelli impostati sul lato client tramite Javascript sono limitati a una scadenza di sette giorni o 24 ore in ITP. Per ulteriori informazioni sui criteri ITP, consulta questo [!DNL Apple] documento [sulla prevenzione del tracciamento](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Sebbene un’implementazione CNAME non fornisca alcun vantaggio in termini di durata dei cookie, potrebbero esserci altri vantaggi, come ad blocker e browser meno comuni che impediscono l’invio dei dati ai domini classificati come tracciatori. In questi casi, l’utilizzo di un CNAME potrebbe impedire l’interruzione della raccolta dati da parte degli utenti che utilizzano questi strumenti.