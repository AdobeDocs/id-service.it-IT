---
description: Il servizio Opt-in consente di configurare i protocolli per il visitatore per identificare se è possibile impostare un cookie sul dispositivo o sul browser dell'utente che visita il tuo sito.
title: Servizio Opt-in
exl-id: 351da861-4faa-409b-b0ff-f4d2ce66700b
source-git-commit: 070390ec0534c9066d717fe52ff572f34c110137
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 96%

---

# Servizio Opt-in{#opt-in-service}

Il servizio Opt-in consente di configurare i protocolli per il visitatore per identificare se è possibile impostare un cookie sul dispositivo o sul browser dell&#39;utente che visita il tuo sito.

Il servizio Opt-in è un&#39;estensione del servizio Experience Cloud ID (ECID) progettato per consentire il controllo di eventuali soluzioni Experience Cloud che possono creare cookie sulle pagine Web per i visitatori prima che l&#39;utente dia il consenso. Il servizio Opt-in consente di impostare protocolli da integrare con la Piattaforma di gestione dei consensi (CMP) e i sistemi esistenti come parte di un progetto più grande.

Usando il servizio Opt-in è possibile specificare se un visitatore può dare il consenso a tutte le soluzioni Adobe in una sola volta oppure deve darlo per ogni soluzione seguendo la sequenza di autorizzazioni per ognuna di esse. Una volta che il cliente ha completato e registrato il processo di approvazione, è possibile recuperare le approvazioni del visitatore CMP da tutte le soluzioni Adobe.

Il servizio Opt-in viene implementato e configurato facilmente utilizzando [Tag in Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it) con [Estensione Opt-in](../../implementation-guides/opt-in-service/launch.md). Può essere implementato e configurato anche usando [DTM](../../implementation-guides/opt-in-service/optin-dtm.md).

Per iniziare, consulta [Configurazione del servizio Opt-in](../../implementation-guides/opt-in-service/getting-started.md).

>[!NOTE]
>
>Il servizio Opt-in consente di configurare un sistema per approvare o negare il download dei soli cookie di Adobe. Non fornisce supporto per raccogliere le preferenze del consenso dell&#39;utente e non è un archivio per le preferenze.

>[!IMPORTANT]
>
>Il contenuto di questo documento non rappresenta e non intende sostituirsi a una consulenza legale. Consulta l&#39;ufficio legale della tua azienda per ricevere un consiglio sul consenso e le pratiche da seguire quando si configura l&#39;implementazione di Opt-in.

## Opt-in nelle soluzioni Experience Cloud {#section-053e6224505542cf961896f0ca869e52}

Il servizio Opt-in è uno strumento per creare un flusso di lavoro di scelta del consenso in base alle tue esigenze, che ti consente di progettare un flusso di lavoro che attivi dei tag prima e dopo che l&#39;utente o il controller conceda il consenso.

Il servizio Opt-in ti consente di configurare le pratiche di gestione dei consensi per le soluzioni Adobe per:

* Indica se i requisiti di raccolta del consenso si applicano in generale per un utente.
* Specifica quali soluzioni possono generare i cookie.
* Applica le preferenze predefinite per tutte le soluzioni la cui categoria non è esplicitamente autorizzata o rifiutata dall’utente.
* Attiva la risposta personalizzata in base alle modifiche alle impostazioni di consenso di un utente, permettendoti di mantenere o aggiornare le impostazioni dell’utente.

Con il servizio Opt-in è possibile configurare il proprio sito per consentire il caricamento di alcuni cookie con il consenso concesso prima che l&#39;utente effettui la sua scelta. È possibile impostare i servizi Opt-in per i nuovi clienti per consentire il caricamento dei cookie dopo il consenso dell&#39;utente o dopo aver reso disponibile una scelta. Puoi anche archiviare e recuperare il consenso opt-in dalla tua attuale piattaforma per la gestione dei consensi o semplicemente archiviare le autorizzazioni opt-in in un cookie.

![](assets/Opt-in-approval.png)

Le soluzioni Adobe possono quindi verificare che il tag sia stato approvato, sottoscrivere delle modifiche e quindi recuperare tutti i clienti Opt-in. Il servizio Opt-in ti consente di ottenere autorizzazioni direttamente attraverso le librerie JavaScript della soluzione o tramite ECID se implementato.
