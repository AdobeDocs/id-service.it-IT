---
description: Il servizio Consenso consente di impostare i protocolli per il visitatore per determinare se è possibile impostare un cookie sul dispositivo o sul browser dell'utente quando accede al sito.
seo-description: Il servizio Consenso consente di impostare i protocolli per il visitatore per determinare se è possibile impostare un cookie sul dispositivo o sul browser dell'utente quando accede al sito.
seo-title: Servizio di consenso
title: Servizio di consenso
uuid: aebd 72 ad -4118-471 b -9755-d 08 a 72 caa 0 fd
translation-type: tm+mt
source-git-commit: 7d0df419c4af7f8a58ffa56b1176bf638bc0045b

---


# Servizio di consenso{#opt-in-service}

Il servizio Consenso consente di impostare i protocolli per il visitatore per determinare se è possibile impostare un cookie sul dispositivo o sul browser dell&#39;utente quando accede al sito.

Il servizio di consenso è un&#39;estensione dell&#39;Experience Cloud ID (ECID), progettato per consentire di controllare se e quali soluzioni Experience Cloud possono creare cookie sulle pagine Web per i visitatori prima del consenso dell&#39;utente. Il servizio di consenso consente inoltre di impostare protocolli per l&#39;integrazione con la piattaforma CMP (Permission Management Platform) e i sistemi esistenti come parte della progettazione più grande.

Utilizzando il servizio di consenso, puoi specificare se un visitatore può optare per le soluzioni Adobe alla volta oppure presentare soluzioni in sequenza per le autorizzazioni. Una volta che il cliente ha completato e registrato il processo di approvazione, è possibile recuperare le approvazioni del visitatore CMP da tutte le soluzioni Adobe.

Il servizio di consenso è implementato e configurato facilmente utilizzando [Adobe Launch](https://docs.adobelaunch.com/) con l&#39;estensione [Opt-in](../../implementation-guides/opt-in-service/launch.md). Può anche essere implementato e configurato utilizzando [DTM](../../implementation-guides/opt-in-service/optin-dtm.md).

Per iniziare, consultate [Configurazione del servizio](../../implementation-guides/opt-in-service/getting-started.md) di consenso.

>[!NOTE]
>
>Il servizio Consenso consente di configurare un sistema per approvare o rifiutare solo i cookie Adobe. Non fornisce supporto per raccogliere le preferenze del consenso dell&#39;utente e non è un archivio per le preferenze.

>[!IMPORTANT]
>
>I contenuti di questo documento non sono consigli legali e non sono destinati alla sostituzione legale. Consulta l&#39;ufficio legale della tua azienda per ricevere un consiglio sul consenso e le pratiche da seguire quando si configura l&#39;implementazione di Opt-in.

## Opt-in nelle soluzioni Experience Cloud {#section-053e6224505542cf961896f0ca869e52}

Il servizio di consenso è uno strumento che consente di rifiutare il flusso di lavoro in base alle proprie esigenze, consentendo di creare un flusso di lavoro per reagire (tag attivatore) prima e dopo l&#39;autorizzazione dell&#39;utente o del controller del consenso.

Il servizio Opt-in consente di impostare pratiche di gestione del consenso per le soluzioni Adobe a:

* Indicare se i requisiti di raccolta del consenso si applicano in generale per un utente.
* Specificare quali soluzioni possono generare cookie.
* Applicare le preferenze predefinite per tutte le soluzioni la cui categoria non ha ricevuto un consenso o un rifiuto esplicito dall&#39;utente.
* Attivare una risposta personalizzata in base alle modifiche apportate alle impostazioni del consenso dell&#39;utente, consentendoti di mantenere o aggiornare le impostazioni dell&#39;utente.

Utilizzando i servizi di consenso, potete configurare il sito in modo che alcuni cookie vengano caricati con il preconsenso prima della scelta dell&#39;utente. Potete impostare i servizi di consenso per i nuovi clienti per consentire il caricamento dei cookie dopo che l&#39;utente ha acconsentito o dopo che è stata resa disponibile una scelta. È anche possibile archiviare o recuperare il consenso opt-in dalla Piattaforma di gestione dei consensi esistente o semplicemente archiviare le autorizzazioni opt-in in un cookie.

![](assets/Opt-in-approval.png)

Le soluzioni Adobe possono quindi verificare che il tag sia stato approvato, sottoscrivere delle modifiche e quindi recuperare tutti i clienti Opt-in. Il servizio di consenso consente di ottenere le autorizzazioni direttamente tramite le librerie javascript della soluzione o tramite ECID se implementato.
