---
description: Se utilizzi un sito di accesso principale per l’identificazione dei clienti prima che visitino altri domini, un CNAME consente il monitoraggio tra più domini nei browser che non accettano i cookie di terze parti (ad esempio Safari).
keywords: ordine delle operazioni;servizio ID
title: Panoramica sull’implementazione di CNAME
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: 61f9f1888430ff0fdbb90a8cf6561bf23d204a45
workflow-type: ht
source-wordcount: '266'
ht-degree: 100%

---

# Panoramica sull’implementazione di CNAME {#cname-implementation-overview}

Le implementazioni di CNAME consentono di personalizzare il dominio di raccolta utilizzato da Adobe in modo che corrispondano al tuo dominio. Questi domini sono anche denominati domini di raccolta di prime parti. Queste implementazioni consentono ad Adobe di impostare cookie di prime parti sul lato server anziché sul lato client utilizzando JavaScript. In passato, questi cookie di prime parti lato server non erano soggetti ai limiti imposti dalla policy ITP (Intelligent Tracking Prevention) di Apple. Tuttavia, a novembre 2020, [!DNL Apple] ha aggiornato i propri criteri in modo da applicare le stesse limitazioni anche ai cookie impostati tramite CNAME. Attualmente, sia i cookie impostati sul lato server tramite CNAME che quelli impostati sul lato client tramite JavaScript sono soggetti a una scadenza di sette giorni o 24 ore in ITP. Per ulteriori informazioni sulle policy ITP, consulta questo documento di [!DNL Apple] sulla [prevenzione del tracciamento](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Nonostante un’implementazione CNAME non offra vantaggi in termini di durata dei cookie, potrebbero esserci altri vantaggi. Questi vantaggi includono ad blocker e browser meno comuni che impediscono l’invio dei dati ai domini classificati come tracciatori. In questi casi, l’utilizzo di un CNAME potrebbe agevolare la raccolta di dati relativi agli utenti che utilizzano tali strumenti.

Inoltre, le implementazioni CNAME consentono di specificare **[!UICONTROL Scegli il tipo di RDC personalizzato]**, il quale controlla dove gli hit degli utenti vengono inizialmente instradati. La maggior parte dei clienti non utilizza tipi RDC personalizzati.
