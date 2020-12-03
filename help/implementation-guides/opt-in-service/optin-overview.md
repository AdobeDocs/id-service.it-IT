---
description: Il servizio Opt-in consente di configurare i protocolli per il visitatore per identificare se è possibile impostare un cookie sul dispositivo o sul browser dell'utente che visita il tuo sito.
seo-description: Il servizio Opt-in consente di configurare i protocolli per il visitatore per identificare se è possibile impostare un cookie sul dispositivo o sul browser dell'utente che visita il tuo sito.
seo-title: Servizio Opt-in
title: Servizio Opt-in
uuid: aebd72ad-4118-471b-9755-d08a72caa0fd
translation-type: tm+mt
source-git-commit: 4fbfefddcf36855f32f2a4047e19ef0b22fc508c
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 81%

---


# Servizio Opt-in{#opt-in-service}

Il servizio Opt-in consente di configurare i protocolli per il visitatore per identificare se è possibile impostare un cookie sul dispositivo o sul browser dell&#39;utente che visita il tuo sito.

Il servizio Opt-in è un&#39;estensione del servizio Experience Cloud ID (ECID) progettato per consentire il controllo di eventuali soluzioni Experience Cloud che possono creare cookie sulle pagine Web per i visitatori prima che l&#39;utente dia il consenso. Il servizio Opt-in consente di impostare protocolli da integrare con la Piattaforma di gestione dei consensi (CMP) e i sistemi esistenti come parte di un progetto più grande.

Usando il servizio Opt-in è possibile specificare se un visitatore può dare il consenso a tutte le soluzioni Adobe in una sola volta oppure deve darlo per ogni soluzione seguendo la sequenza di autorizzazioni per ognuna di esse. Una volta che il cliente ha completato e registrato il processo di approvazione, è possibile recuperare le approvazioni del visitatore CMP da tutte le soluzioni Adobe.

The Opt-in service is implemented and configured easily using [Adobe Experience Platform Launch](https://docs.adobe.com/content/help/it-IT/launch/using/overview.html) with the [Opt-in extension](../../implementation-guides/opt-in-service/launch.md). Può essere implementato e configurato anche usando [DTM](../../implementation-guides/opt-in-service/optin-dtm.md).

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

* Indicate se i requisiti per la raccolta del consenso si applicano in generale a un utente.
* Specificare le soluzioni consentite per generare i cookie.
* Applica preferenze predefinite per qualsiasi soluzione la cui categoria non sia esplicitamente consenziente o rifiutata dall&#39;utente.
* Attiva la risposta personalizzata in base alle modifiche apportate alle impostazioni del consenso dell&#39;utente, consentendo di mantenere o aggiornare le impostazioni dell&#39;utente.

Con il servizio Opt-in è possibile configurare il proprio sito per consentire il caricamento di alcuni cookie con il consenso concesso prima che l&#39;utente effettui la sua scelta. È possibile impostare i servizi Opt-in per i nuovi clienti per consentire il caricamento dei cookie dopo il consenso dell&#39;utente o dopo aver reso disponibile una scelta. È inoltre possibile memorizzare e recuperare il consenso di consenso dalla piattaforma di gestione del consenso esistente o semplicemente memorizzare le autorizzazioni di consenso in un cookie.

![](assets/Opt-in-approval.png)

Le soluzioni Adobe possono quindi verificare che il tag sia stato approvato, sottoscrivere delle modifiche e quindi recuperare tutti i clienti Opt-in. Il servizio Opt-in ti consente di ottenere autorizzazioni direttamente attraverso le librerie JavaScript della soluzione o tramite ECID se implementato.
