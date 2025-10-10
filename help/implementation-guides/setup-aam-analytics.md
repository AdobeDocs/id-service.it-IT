---
description: Queste istruzioni sono per chi usa Analytics e Audience Manager, desidera usare Experience Cloud Identity Service e non usa i tag di Raccolta dati. Tuttavia, si consiglia vivamente di usare i tag per implementare il servizio ID. I tag agevolano il flusso di lavoro di implementazione e assicurano automaticamente il posizionamento e la sequenza del codice corretti.
keywords: Servizio ID
title: Implementare Experience Cloud Identity Service per Analytics e Audience Manager
exl-id: e31720a1-5c89-4084-88f6-443994dbb2f4
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 100%

---

# Implementare Experience Cloud Identity Service per Analytics e Audience Manager{#implement-the-experience-cloud-id-service-for-analytics-and-audience-manager}

Queste istruzioni sono per chi utilizza Analytics e Audience Manager, desidera utilizzare Experience Cloud Identity Service e usa i tag di [Raccolta dati](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it). Tuttavia, si consiglia vivamente di usare i tag per implementare il servizio ID. I tag agevolano il flusso di lavoro di implementazione e assicurano automaticamente il posizionamento e la sequenza del codice corretti.

>[!IMPORTANT]
>
>* [Prima di iniziare](../reference/requirements.md), leggi i requisiti.
>* Questa procedura richiede AppMeasurement. I clienti che usano s_code non possono completare questa procedura.
>* Configura e verifica questo codice in un ambiente di sviluppo prima di implementarlo in produzione.

## Passaggio 1: pianificazione dell&#39;inoltro lato server {#section-880797cc992d4755b29cada7b831f1fc}

Oltre ai passaggi qui descritti, i clienti che usano [!DNL Analytics] e [!DNL Audience Manager] devono effettuare la migrazione all’inoltro lato server. L’inoltro lato server consente di rimuovere il DIL (codice di raccolta dati di Audience Manager) e sostituirlo con il [modulo Gestione dell’audience](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/audience-management-module.html?lang=it). Per ulteriori informazioni, consulta la [documentazione dell’inoltro lato server](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/server-side-forwarding/ssf.html?lang=it).

La migrazione all’inoltro lato server richiede pianificazione e coordinamento. Questo processo comporta modifiche esterne al codice del sito e passaggi interni che Adobe deve effettuare per il provisioning del tuo account. Infatti, molte di queste procedure di migrazione devono avvenire in parallelo ed essere rilasciate insieme. Il percorso di implementazione deve seguire questa sequenza di eventi:

1. Pianifica con i tuoi contatti per [!DNL Analytics] e [!DNL Audience Manager] la migrazione dell&#39;inoltro lato server e il servizio ID. La selezione del server di tracciamento è una fase importante di questo piano.

1. Completa il modulo sulle [integrazioni e sul sito di provisioning](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) per iniziare.

1. Implementa il servizio ID e il [!DNL Audience Management Module] simultaneamente. Per funzionare correttamente, il [!DNL Audience Management Module] (inoltro lato server) e il servizio ID devono essere rilasciati per lo stesso set di pagine e allo stesso tempo.

## Passaggio 2: scarica il codice del servizio ID {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

Il servizio ID richiede la `VisitorAPI.js` libreria dei codici. Per scaricare la libreria dei codici:

1. Seleziona **[!UICONTROL Amministratore]** > **[!UICONTROL Gestione codici]**.

1. In Gestione codici, fai clic su **[!UICONTROL JavaScript (Nuovo)]** o su **[!UICONTROL JavaScript (Legacy)]**. Verranno scaricate le librerie dei codici compresse.

1. Decomprimi il file dei codici e apri il `VisitorAPI.js` file.

## Passaggio 3: aggiungi la funzione Visitor.getInstance al codice del servizio ID {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* Le versioni precedenti dell’API del servizio ID inserivano questa funzione in una posizione diversa e richiedevano una sintassi diversa. Se stai eseguendo la migrazione da una versione precedente alla [versione 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), tieni presente la nuova posizione e la sintassi qui documentate.
>* Il codice in maiuscolo è un segnaposto per i valori effettivi. Sostituisci questo testo con il tuo ID organizzazione, l’URL del server di tracciamento o un altro valore denominato.

**Parte 1: copia la funzione Visitor.getInstance di seguito**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**Parte 2: aggiungi il codice della funzione al file Visitor API.js**

Posiziona la `Visitor.getInstance` funzione alla fine del file, dopo il blocco del codice. Il file modificato deve essere simile al seguente:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Passaggio 4: aggiungi l’ID organizzazione Experience Cloud a Visitor.getInstance {#section-e2947313492546789b0c3b2fc3e897d8}

Nella `Visitor.getInstance` funzione sostituisci `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` con l&#39;ID organizzazione Experience Cloud. Se non conosci il tuo ID organizzazione, puoi trovarlo nella pagina di amministrazione di Experience Cloud. La funzione modificata deve essere simile a quella riportata di seguito.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Non* modificare le lettere maiuscole in minuscole e viceversa nell&#39;ID organizzazione. L&#39;ID distingue tra maiuscole e minuscole e deve essere utilizzato esattamente così come è stato fornito.

## Passaggio 5: aggiungi i server di monitoraggio a Visitor.getInstance {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics utilizza i server di tracciamento per la raccolta dei dati.

**Parte 1: trova gli URL del server di tracciamento**

Gli URL del server di monitoraggio si trovano nei file `s_code.js` e `AppMeasurement.js`. Devi trovare gli URL specificati dalle seguenti variabili:

* `s.trackingServer`
* `s.trackingServerSecure`

**Parte 2: imposta le variabili del server di tracciamento**

Per determinare quali variabili del server di tracciamento utilizzare:

1. Rispondi alle domande riportate nella matrice di decisione seguente. Utilizza le variabili corrispondenti alle risposte.
1. Sostituisci i segnaposto del server di tracciamento con gli URL del server di tracciamento.
1. Rimuovi dal codice le variabili non utilizzate del server di tracciamento e del server Experience Cloud.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Se utilizzato, fai corrispondere gli URL del server Experience Cloud con gli URL del server di tracciamento corrispondenti, come riportato di seguito:

* URL del server Experience Cloud = URL del server di tracciamento
* URL protetto del server Experience Cloud = URL protetto del server di tracciamento

Se non sei sicuro di come trovare il server di tracciamento, consulta le [Domande frequenti](../faq-intro/faq.md) e [Compilare correttamente le variabili trackingServer e trackingServerSecure](https://helpx.adobe.com/it/analytics/kb/determining-data-center.html#).

## Passaggio 6: aggiorna il file AppMeasurement.js {#section-5517e94a09bc44dfb492ebca14b43048}

Questo passaggio richiede [!UICONTROL AppMeasurement]. Se utilizzi ancora s_code, non potrai procedere.

Aggiungi la `Visitor.getInstance` funzione riportata di seguito al tuo `AppMeasurement.js` file. Inseriscilo nella stessa sezione che contiene configurazioni come `linkInternalFilters`, `charSet`, `trackDownloads`, ecc.:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>A questo punto, devi rimuovere il codice [!DNL Audience Manager] DIL e sostituirlo con il modulo Gestione del pubblico. Per istruzioni consulta [Implementare l’inoltro lato server](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/server-side-forwarding/ssf.html?lang=it).

***(Facoltativo ma consigliato)* Crea un prop personalizzato.**

Imposta un prop personalizzato in `AppMeasurement.js` per misurare la copertura. Aggiungi il prop personalizzato alla `doPlugins` funzione del `AppMeasurement.js` file:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Passaggio 7: aggiungi il codice API del visitatore alla pagina {#section-c2bd096a3e484872a72967b6468d3673}

Inserisci il `[!UICONTROL VisitorAPI.js]` file entro i tag `<head>` di ogni pagina. Quando inserisci il `VisitorAPI.js` file nella pagina:

* Inseriscilo all&#39;inizio della `<head>` sezione prima dei tag di altre soluzioni.
* Deve essere eseguito prima di AppMeasurement e del codice di altre [!DNL Experience Cloud] soluzioni.

## Passaggio 8: (facoltativo) configura un periodo di tolleranza {#section-aceacdb7d5794f25ac6ff46f82e148e1}

Se uno di questi casi d’uso è applicabile alla tua situazione, chiedi all’[Assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html) di impostare un [periodo di tolleranza](../reference/analytics-reference/grace-period.md) temporaneo. I periodi di tolleranza possono durare fino a 180 giorni. Se necessario, puoi rinnovare il periodo di tolleranza.

**Implementazione parziale**

Se alcune pagine utilizzano il servizio ID e altre no e tutte le pagine riferiscono alla stessa suite di rapporti di Analytics, devi impostare un periodo di tolleranza. Ciò è comune se disponi di una suite di rapporti globale per più domini.

Interrompi il periodo di tolleranza dopo che il servizio ID è stato distribuito su tutte le pagine Web che riferiscono alla stessa suite di rapporti.

**Requisiti del cookie s_vi**

Devi impostare un periodo di tolleranza se dopo la migrazione al servizio ID richiedi ai nuovi visitatori un cookie s_vi. Ciò è comune se l’implementazione legge il cookie s_vi e lo memorizza in una variabile.

Puoi interrompere il periodo di tolleranza dopo che l’implementazione sarà in grado di acquisire il MID invece di leggere il cookie s_vi.

Consulta anche [I cookie ed Experience Cloud Identity Service](../introduction/cookies.md).

**Integrazione dei dati di click-stream**

Se invii dati a un sistema interno da un feed di dati di click-stream e per i processi sono utilizzate le colonne `visid_high` e `visid_low`, devi attivare un periodo di tolleranza.

Quando il processo di acquisizione dei dati può utilizzare le colonne `post_visid_high` e `post_visid_low`, interrompi il periodo di tolleranza.

Vedi anche la [colonna di riferimento dei dati di click-stream](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html?lang=it).

## Passaggio 9: verifica e distribuisci il codice del servizio ID {#section-f857542bfc70496dbb9f318d6b3ae110}

Puoi eseguire il test e distribuirlo come segue.

**Test e verifica**

Per verificare l’implementazione del servizio ID, controlla i seguenti elementi:

* [Cookie AMCV](../introduction/cookies.md) nel dominio di hosting della pagina.
* Valore MID nella richiesta di immagine di Analytics con [Adobe debugger](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=it).
* Consulta anche [Testare e verificare Experience Cloud Identity Service](../implementation-guides/test-verify.md).

Per verificare l’inoltro lato server, vedi [Come verificare l’implementazione dell’inoltro lato server](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools//server-side-forwarding/ssf-verify.html?lang=it).

**Distribuzione**

Distribuisci il codice dopo aver superato il test.

Se hai abilitato un periodo di tolleranza:

* Verifica che l’ID di Analytics (AID) e il MID siano presenti nella richiesta di immagine.
* Ricorda di disattivare il periodo di tolleranza quando sono presenti i requisiti per l&#39;interruzione.
