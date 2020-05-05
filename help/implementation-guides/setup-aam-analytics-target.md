---
description: Queste istruzioni sono per i clienti di Analytics, Audience Manager e Target che desiderano usare il servizio Experience Cloud Identity e non usano Dynamic Tag Management (DTM). Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Gestione dinamica dei tag semplifica il flusso di lavoro di implementazione e assicura automaticamente la corretta posizione del codice e la corretta sequenza.
keywords: ID Service
seo-description: Queste istruzioni sono per i clienti di Analytics, Audience Manager e Target che desiderano usare il servizio Experience Cloud Identity e non usano Dynamic Tag Management (DTM). Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Gestione dinamica dei tag semplifica il flusso di lavoro di implementazione e assicura automaticamente la corretta posizione del codice e la corretta sequenza.
seo-title: Implementazione del servizio Experience Cloud Identity per Analytics, Audience Manager e Target
title: Implementazione del servizio Experience Cloud Identity per Analytics, Audience Manager e Target
uuid: 9d446b77-ca62-4325-8bb0-ff43a52313c0
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Implementazione del servizio Experience Cloud Identity per Analytics, Audience Manager e Target{#implement-the-experience-cloud-id-service-for-analytics-audience-manager-and-target}

Queste istruzioni sono per i clienti di Analytics, Audience Manager e Target che desiderano usare il servizio Experience Cloud Identity e non usano Dynamic Tag Management (DTM). Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Gestione dinamica dei tag semplifica il flusso di lavoro di implementazione e assicura automaticamente la corretta posizione del codice e la corretta sequenza.

>[!IMPORTANT]
>
>Leggi i [requisiti](../reference/requirements.md) del servizio ID e prendi nota dei seguenti requisiti specifici per questa implementazione: >
>* I clienti che usano s_code non possono completare questa procedura. Aggiornamento al codice mbox v61 per completare questa procedura.
>* Configure and test this code in a development environment *before* you implement it in production.
>



## Passaggio 1: pianificazione dell&#39;inoltro lato server {#section-880797cc992d4755b29cada7b831f1fc}

Oltre ai passaggi qui descritti, i clienti che usano [!DNL Analytics] e [!DNL Audience Manager] devono effettuare la migrazione all&#39;inoltro lato server. Server-side forwarding lets you remove DIL (Audience Manager&#39;s data collection code) and replace it with the [Audience Management Module](https://docs.adobe.com/content/help/en/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/audience-management-module.html). See the [server-side forwarding documentation](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/server-side-forwarding/ssf.html) for more information.

La migrazione all&#39;inoltro lato server richiede pianificazione e coordinamento. Questo processo comporta modifiche esterne al codice del sito e passaggi interni che Adobe deve effettuare per il provisioning del tuo account. Infatti, molte di queste procedure di migrazione devono avvenire in parallelo e essere rilasciate insieme. Il percorso di implementazione deve seguire questa sequenza di eventi:

1. Pianifica con i tuoi contatti per [!DNL Analytics] e [!DNL Audience Manager] la migrazione dell&#39;inoltro lato server e il servizio ID. La selezione del server di tracciamento è una fase importante di questo piano.

1. Complete the form on the [integrations and provisioning site](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) to get started.

1. Implementa il servizio ID e il [!DNL Audience Management Module] simultaneamente. Per funzionare correttamente, il [!DNL Audience Management Module] (inoltro lato server) e il servizio ID devono essere rilasciati per lo stesso set di pagine e allo stesso tempo.

## Passaggio 2: scarica il codice del servizio ID {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

Il servizio ID richiede la `VisitorAPI.js` libreria dei codici. Per scaricare la libreria dei codici:

1. Seleziona **[!UICONTROL Amministratore > Gestione codici]**.
1. In Gestione codici, fai clic su **[!UICONTROL JavaScript (Nuovo)]** o su **[!UICONTROL JavaScript (Legacy)]**. Verranno scaricate le librerie dei codici compresse.

1. Decomprimi il file dei codici e apri il `VisitorAPI.js` file.

## Passaggio 3: aggiungi la funzione Visitor.getInstance al codice del servizio ID {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* Le versioni precedenti dell’API del servizio ID inserivano questa funzione in una posizione diversa e richiedevano una sintassi diversa. Se state eseguendo la migrazione da una versione precedente alla [versione 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), tenete presente la nuova posizione e la sintassi qui documentate.
>* Il codice in ALL CAPS è un segnaposto per i valori effettivi. Sostituisci questo testo con il tuo ID organizzazione, l’URL del server di tracciamento o altro valore denominato.
>



**Parte 1: Copia la funzione Visitor.getInstance di seguito**

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

**Parte 2: Aggiungi il codice della funzione al file Visitor API.js**

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

## Passaggio 4: aggiungi l&#39;ID organizzazione Experience Cloud a Visitor.getInstance {#section-e2947313492546789b0c3b2fc3e897d8}

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

**Parte 2: Impostazione delle variabili del server di tracciamento**

Per determinare quali variabili del server di tracciamento utilizzare:

1. Rispondi alle domande riportate nella matrice di decisione seguente. Utilizzate le variabili corrispondenti alle risposte.
1. Sostituisci i segnaposto del server di tracciamento con gli URL del server di tracciamento.
1. Rimuovi dal codice le variabili del server di tracciamento e del server Experience Cloud non utilizzate.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Se utilizzato, fai corrispondere gli URL del server Experience Cloud con gli URL del server di tracciamento corrispondenti, come riportato di seguito:

* URL del server Experience Cloud = URL del server di tracciamento
* URL del server protetto Experience Cloud = URL del server protetto di tracciamento

Se non sei sicuro di come trovare il server di tracciamento, consulta le [domande frequenti](../faq-intro/faq.md) e [Compilare correttamente le variabili trackingServer e trackingServerSecure](https://helpx.adobe.com/it/analytics/kb/determining-data-center.html#).

## Passaggio 6: aggiorna il file AppMeasurement.js {#section-5517e94a09bc44dfb492ebca14b43048}

This step requires [!UICONTROL AppMeasurement]. Se utilizzi ancora s_code, non potrai procedere.

Aggiungi la `Visitor.getInstance` funzione riportata di seguito al tuo `AppMeasurement.js` file. Inseriscilo nella stessa sezione che contiene configurazioni come `linkInternalFilters`, `charSet`, `trackDownloads`, ecc.:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>A questo punto, devi rimuovere il codice [!DNL Audience Manager] DIL e sostituirlo con il modulo Gestione dell&#39;audience. Per istruzioni, consultate [Implementazione dell&#39;inoltro](https://docs.adobe.com/content/help/it-IT/analytics/admin/admin-tools/server-side-forwarding/ssf.html) lato server.

***(Facoltativo ma consigliato)*Crea un prop personalizzato ****

Imposta un prop personalizzato in `AppMeasurement.js` per misurare la copertura. Aggiungi il prop personalizzato alla `doPlugins` funzione del `AppMeasurement.js` file:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Passaggio 7: aggiungi il codice API del visitatore alla pagina {#section-c2bd096a3e484872a72967b6468d3673}

Inserisci il ` [!UICONTROL VisitorAPI.js]` file entro i tag `<head>` di ogni pagina. Quando inserisci il `VisitorAPI.js` file nella pagina:

* Inseriscilo all&#39;inizio della `<head>` sezione prima dei tag di altre soluzioni.
* Deve essere eseguito prima di AppMeasurement e del codice di altre [!DNL Experience Cloud] soluzioni.

## Passaggio 8: (facoltativo) configura un periodo di tolleranza {#section-aceacdb7d5794f25ac6ff46f82e148e1}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/it/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). I periodi di tolleranza possono durare fino a 180 giorni. Se necessario, puoi rinnovare il periodo di tolleranza.

**Implementazione parziale**

Se hai delle pagine che utilizzano il servizio ID e alcune pagine che non lo fanno, hai bisogno di un periodo di tolleranza e tutte queste pagine fanno riferimento alla stessa suite di rapporti di Analytics. Ciò è comune se disponi di una suite di rapporti globale per più domini.

Interrompi il periodo di tolleranza dopo che il servizio ID è stato distribuito su tutte le pagine Web che riferiscono alla stessa suite di rapporti.

**Requisiti del cookie s_vi**

Se dopo la migrazione al servizio ID, richiedi ai nuovi visitatori un cookie s_vi, devi impostare un periodo di tolleranza. Ciò è comune se l’implementazione legge il cookie s_vi e lo memorizza in una variabile.

Dopo che l’implementazione sarà in grado di acquisire il MID invece di leggere il cookie s_vi, puoi interrompere il periodo di tolleranza.

Consulta anche [Cookie e il servizio Experience Cloud Identity](../introduction/cookies.md).

**Integrazione dei dati di clickstream**

Se invii dati a un sistema interno da un feed di dati clickstream e per i processi sono utilizzate le colonne `visid_high` e `visid_low`, devi attivare un periodo di tolleranza.

Quando il processo di inserimento dei dati può utilizzare le colonne `post_visid_high` e `post_visid_low`, interrompi il periodo di tolleranza.

Vedi anche Riferimento [colonna dati](https://docs.adobe.com/content/help/it-IT/analytics/export/analytics-data-feed/data-feed-overview.html)clickstream.

## Passaggio 9: test e verifica {#section-f857542bfc70496dbb9f318d6b3ae110}

Le soluzioni [!DNL Experience Cloud] di questa implementazione restituiscono gli ID sotto forma di coppie chiave-valore. Ogni soluzione usa chiavi diverse (ad esempio, [!DNL Analytics] SDID di e [!DNL Target] mboxMCSDID di) per lo stesso ID. Per verificare il corretto funzionamento dell&#39;implementazione, carica le pagine in un ambiente di sviluppo. Usa la console del browser o un software per monitorare le richieste HTTP e le risposte, e controlla gli ID elencati di seguito. Il servizio ID è stato implementato correttamente se le coppie chiave-valore elencate di seguito restituiscono gli stessi valori ID.

>[!TIP]
>
>You can use the [Adobe Debugger](https://docs.adobe.com/content/help/en/analytics/implementation/validate/debugger.html) or the [Charles HTTP proxy](https://www.charlesproxy.com/) to check for these solution-specific IDs. Puoi anche usare un altro strumento o debugger di tua preferenza.

**Tutte le soluzioni**

Controlla se:

* [Cookie AMCV](../introduction/cookies.md) nel dominio di hosting della pagina.
* [!DNL Experience Cloud] ID (MID) con [!DNL Adobe] Debugger o altro strumento di debug.

Per ulteriori verifiche utili per determinare se il servizio ID funziona correttamente, consulta [Test e verifica del servizio Experience Cloud Identity](../implementation-guides/test-verify.md).

**Analytics**

Verifica l’identificatore SDID nella richiesta JavaScript. Il valore SDID di Analytics deve corrispondere al valore mboxMCSDID di Target.

Se i test restituiscono un AID, questo può indicare:

* Sei un visitatore precedente ed è in corso la migrazione degli [!DNL Analytics] ID precedenti.
* Hai impostato un [periodo di tolleranza](../reference/analytics-reference/grace-period.md).

Quando ricevi un AID, controllane il valore rispetto al valore [!DNL Target] mboxMCAVID di. Questi valori sono identici se il servizio ID è stato implementato correttamente.

**Audience Manager**

Per verificare l&#39;inoltro lato server, vedere [Come verificare l&#39;implementazione](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/server-side-forwarding/ssf-verify.html)dell&#39;inoltro lato server.

**Target**

Controlla se:

* mboxMCGVID
* mboxMCSDID (il valore mboxMCSDID deve corrispondere al valore SDID di Analytics).

Se i test restituiscono un mboxMCAVID, questo può indicare uno dei seguenti elementi:

* Sei un visitatore precedente ed è in corso la migrazione degli [!DNL Analytics] ID precedenti.
* Hai impostato un periodo di tolleranza.

Quando ricevi un mboxMCAVID, controllane il valore rispetto al valore [!DNL Analytics] AID di. Questi valori sono identici se il servizio ID è stato implementato correttamente.

**Implementazione**

## Passaggio 10: distribuisci {#section-4188fa95e7dc455a986b48a6c517c1c9}

Distribuisci il codice dopo aver superato il test.

Se hai attivato un periodo di tolleranza:

* Verifica che l’ID Analytics (AID) e il MID siano nella richiesta di immagine.
* Remember to disable the grace period once you meet the [criteria for discontinuation](../implementation-guides/setup-aam-analytics-target.md#section-aceacdb7d5794f25ac6ff46f82e148e1).

