---
description: Queste istruzioni sono per chi utilizza Analytics e desidera usare il servizio Experience Cloud Identity e non usa i tag di Raccolta dati. Tuttavia, si consiglia vivamente di usare i tag per implementare il servizio ID. I tag agevolano il flusso di lavoro di implementazione e assicurano automaticamente il posizionamento e la sequenza del codice corretti.
keywords: Servizio ID
title: Implementazione del servizio Experience Cloud Identity per Analytics
exl-id: c0271e49-32e5-49ee-bb11-548751ccafad
source-git-commit: 792fb5d5192843f345577a99b6179fb6d95fedc0
workflow-type: ht
source-wordcount: '1007'
ht-degree: 100%

---

# Implementazione del servizio Experience Cloud Identity per Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Queste istruzioni sono per chi utilizza Analytics e desidera usare il servizio Experience Cloud Identity e non usa i [tag di Raccolta dati](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it). Tuttavia, si consiglia vivamente di usare i tag per implementare il servizio ID. I tag agevolano il flusso di lavoro di implementazione e assicurano automaticamente il posizionamento e la sequenza del codice corretti.

>[!IMPORTANT]
>
>* [Prima di iniziare](../reference/requirements.md), leggi i requisiti.
>* Configura e verifica questo codice in un ambiente di sviluppo prima di implementarlo in produzione.

Per implementare il servizio ID per Adobe Analytics, effettua le seguenti operazioni:

1. [Scarica il codice del servizio ID](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Aggiungi la funzione Visitor.getInstance al codice del servizio ID](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Aggiungi l&#39;ID organizzazione Experience Cloud a Visitor.getInstance](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Aggiungi i server di monitoraggio a Visitor.getInstance](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Aggiorna il file AppMeasurement.js o s_code.js](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [Aggiungi il codice API del visitatore alla pagina](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Facoltativo) Configura un periodo di tolleranza](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [Verifica e distribuisci il codice del servizio ID](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Passaggio 1: scarica il codice del servizio ID {#section-ead9403a6b7e45b887f9ac959ef89f7f}

Il [!UICONTROL servizio ID] richiede la libreria dei codici `VisitorAPI.js`. Per scaricare la libreria dei codici:

1. Seleziona **[!UICONTROL Amministratore]** > **[!UICONTROL Gestione codici]**.
1. In [!UICONTROL Gestione codici], fai clic su **[!UICONTROL JavaScript (Nuovo)]** o su **[!UICONTROL JavaScript (Legacy)]**.

   Verranno scaricate le librerie dei codici compresse.

1. Decomprimi il file dei codici e apri il `VisitorAPI.js` file.

## Passaggio 2: Aggiungi la funzione Visitor.getInstance al codice del servizio ID {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* Le versioni precedenti dell’API del servizio ID inserivano questa funzione in una posizione diversa e richiedevano una sintassi diversa. Se stai eseguendo la migrazione da una versione precedente alla [versione 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), tieni presente la nuova posizione e la sintassi qui documentate.
>* Il codice in maiuscolo è un segnaposto per i valori effettivi. Sostituisci questo testo con il tuo ID organizzazione, l’URL del server di tracciamento o un altro valore denominato.

**Parte 1: copia la funzione Visitor.getInstance di seguito**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**Parte 2: aggiungi il codice della funzione al file VisitorAPI.js**

Posiziona la `Visitor.getInstance` funzione alla fine del file, dopo il blocco del codice. Il file modificato deve essere simile al seguente:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library

var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Passaggio 3: aggiungi l’ID organizzazione Experience Cloud a Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

Nella `Visitor.getInstance` funzione sostituisci `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` con l&#39;ID organizzazione [!DNL Experience Cloud]. Se non conosci il tuo ID organizzazione, puoi trovarlo nella pagina di amministrazione di [!DNL Experience Cloud]. Vedi anche [Amministrazione - Servizi di base](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=it). La funzione modificata deve essere simile a quella riportata di seguito.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Non* modificare le lettere maiuscole in minuscole e viceversa nell&#39;ID organizzazione. L&#39;ID distingue tra maiuscole e minuscole e deve essere utilizzato esattamente così come è stato fornito.

## Passaggio 4: aggiungi i server di monitoraggio a Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

I server di monitoraggio sono utilizzati per la raccolta dati di [!DNL Analytics].

**Parte 1: trova gli URL del server di tracciamento**

Gli URL del server di monitoraggio si trovano nei file `s_code.js` e `AppMeasurement.js`. Devi trovare gli URL specificati dalle seguenti variabili:

* `s.trackingServer`
* `s.trackingServerSecure`

**Parte 2: imposta le variabili del server di tracciamento**

Per determinare quali variabili del server di tracciamento utilizzare:

1. Rispondi alle domande riportate nella matrice di decisione seguente. Utilizza le variabili corrispondenti alle risposte.
1. Sostituisci i segnaposto del server di tracciamento con gli URL del server di tracciamento.
1. Rimuovi dal codice le variabili del server di tracciamento e di [!DNL Experience Cloud] non utilizzate.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Se utilizzati, gli URL del server [!DNL Experience Cloud] devono corrispondere a quelli del relativo server di tracciamento, come riportato di seguito:
>
>* URL del server [!DNL Experience Cloud] = URL del server di tracciamento
>* URL sicuro del server [!DNL Experience Cloud] = URL sicuro del server di tracciamento

Se non sei sicuro di come trovare il server di tracciamento, consulta le [Domande frequenti](../faq-intro/faq.md) e [Compilare correttamente le variabili trackingServer e trackingServerSecure](https://helpx.adobe.com/it/analytics/kb/determining-data-center.html#).

## Passaggio 5: aggiorna il file AppMeasurement.js o s_code.js {#section-b53113aea1bd4de896e0e4e9a7edee19}

Aggiungi questa funzione al file `AppMeasurement.js` o `s_code.js`:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Posiziona il codice nella stessa sezione che contiene configurazioni come `linkInternalFilters`, `charSet`, `trackDownloads`, ecc.

***(Facoltativo ma consigliato)* Crea un prop personalizzato.**

Imposta un prop personalizzato in `AppMeasurement.js` o in `s_code.js` per misurare la copertura. Aggiungi il prop personalizzato alla `doPlugins` funzione del file `AppMeasurement.js` o `s_code.js`:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Passaggio 6: aggiungi il codice API del visitatore alla pagina {#section-d46d6aa324c842f2931d901e38d6db1d}

Inserisci il `VisitorAPI.js` file entro i tag `<head>` di ogni pagina. Quando inserisci il `VisitorAPI.js` file nella pagina:

* Inseriscilo all&#39;inizio della `<head>` sezione prima dei tag di altre soluzioni.
* Deve essere eseguito prima di AppMeasurement e del codice di altre [!DNL Experience Cloud] soluzioni.

Dopo il test e la verifica, trasferisci il codice in produzione.

## Passaggio 7: (facoltativo) configura un periodo di tolleranza {#section-7bbb2f72c26e4abeb8881e18366797a3}

Se uno di questi casi d’uso è applicabile alla tua situazione, chiedi all’[Assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html) di impostare un [periodo di tolleranza](../reference/analytics-reference/grace-period.md) temporaneo. I periodi di tolleranza possono durare fino a 180 giorni. Se necessario, puoi rinnovare il periodo di tolleranza.

**Implementazione parziale**

Se solo alcune pagine utilizzano il servizio ID e tutte le pagine riferiscono alla stessa suite di [!DNL Analytics] rapporti, devi configurare un periodo di tolleranza. Ciò è comune se disponi di una suite di rapporti globale per più domini.

Interrompi il periodo di tolleranza dopo che il servizio ID è stato distribuito su tutte le pagine Web che riferiscono alla stessa suite di rapporti.

**Requisiti del cookie s_vi**

Devi impostare un periodo di tolleranza se dopo la migrazione al servizio ID richiedi ai nuovi visitatori un cookie s_vi. Ciò è comune se l’implementazione legge il cookie s_vi e lo memorizza in una variabile.

Puoi interrompere il periodo di tolleranza dopo che l’implementazione sarà in grado di acquisire il MID invece di leggere il cookie s_vi.

Consulta [Cookie e il servizio Experience Cloud Identity](../introduction/cookies.md).

Se invii dati a un sistema interno da un feed di dati click-stream e per i processi sono utilizzate le colonne `visid_high` e `visid_low`, devi attivare un periodo di tolleranza.

Quando il processo di inserimento dei dati può utilizzare le colonne `post_visid_high` e `post_visid_low`, interrompi il periodo di tolleranza.

Vedi la [colonna di riferimento dei dati di click-stream](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html?lang=it).

**Inserimento dei dati di click-stream**

## Passaggio 8: verifica e distribuisci il codice del servizio ID {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

Puoi eseguire il test e distribuirlo come segue.

**Test e verifica**

Per verificare l’implementazione del servizio ID, controlla i seguenti elementi:

* [Cookie AMCV](../introduction/cookies.md) nel dominio di hosting della pagina.
* Valore MID nella richiesta di immagine [!DNL Analytics] con lo [strumento Adobe Debugger](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=it).

Consulta [Test e verifica del servizio Experience Cloud Identity](../implementation-guides/test-verify.md).

**Distribuisci il codice**

Distribuisci il codice dopo aver superato il test.

Se hai attivato un periodo di tolleranza nel [passaggio 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Verifica che [!DNL Analytics] l&#39;ID di (AID) e il MID siano presenti nella richiesta di immagine.
* Ricorda di disattivare il periodo di tolleranza quando sono presenti i requisiti per l&#39;interruzione.
