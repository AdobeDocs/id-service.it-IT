---
description: Queste istruzioni sono per i clienti di Analytics che desiderano usare il servizio Experience Cloud Identity e non usano Dynamic Tag Management (DTM). Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
keywords: Servizio ID
seo-description: Queste istruzioni sono per i clienti di Analytics che desiderano usare il servizio Experience Cloud Identity e non usano Dynamic Tag Management (DTM). Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
seo-title: Implementazione del servizio Experience Cloud Identity per Analytics
title: Implementazione del servizio Experience Cloud Identity per Analytics
uuid: 7fbd6fa0-1713-4232-8680-500ed62709d5
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Implementazione del servizio Experience Cloud Identity per Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Queste istruzioni sono per i clienti di Analytics che desiderano usare il servizio Experience Cloud Identity e non usano Dynamic Tag Management (DTM). Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.

>[!IMPORTANT]
>
>* [Prima di iniziare](../reference/requirements.md), leggi i requisiti.
>* Configura e verifica questo codice in un ambiente di sviluppo prima di implementarlo in produzione.
>



Per implementare il servizio ID per Adobe Analytics, effettua le seguenti operazioni:

1. [Scarica il codice del servizio ID](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Aggiungi la funzione Visitor.getInstance al codice del servizio ID](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Aggiungi l'ID organizzazione Experience Cloud a Visitor.getInstance](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Aggiungi i server di monitoraggio a Visitor.getInstance](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Aggiorna il file AppMeasurement.js o s_code.js](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [Aggiungi il codice API del visitatore alla pagina](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Facoltativo) Configura un periodo di tolleranza](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [Verifica e distribuisci il codice del servizio ID](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Passaggio 1: scarica il codice del servizio ID {#section-ead9403a6b7e45b887f9ac959ef89f7f}

Il [!UICONTROL servizio ID] richiede la libreria dei codici `VisitorAPI.js`. Per scaricare la libreria dei codici:

1. Seleziona **[!UICONTROL Amministratore]** &gt; **[!UICONTROL Gestione codici]**.
1. In [!UICONTROL Gestione codici], fai clic su **[!UICONTROL JavaScript (Nuovo)]** o su **[!UICONTROL JavaScript (Legacy)]**.

   Verranno scaricate le librerie dei codici compresse.

1. Decomprimi il file dei codici e apri il `VisitorAPI.js` file.

## Passaggio 2: Aggiungi la funzione Visitor.getInstance al codice del servizio ID {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* Le versioni precedenti dell'API del servizio ID inserivano questa funzione in una posizione diversa e richiedevano un'altra sintassi. Se effettui la migrazione da una versione precedente alla [1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), prendi nota della nuova posizione e della sintassi indicate in questo documento.
>* Il codice riportato in MAIUSCOLO funge da segnaposto per valori effettivi. Sostituisci tale testo con il tuo ID organizzazione, l'URL del server di tracciamento o altro valore con nome.
>



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

**Parte 2: aggiungi il codice della funzione nel file VisitorAPI.js**

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

## Passaggio 3: aggiungi l'ID organizzazione Experience Cloud a Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

Nella `Visitor.getInstance` funzione sostituisci `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` con l'ID organizzazione [!DNL Experience Cloud]. Se non conosci il tuo ID organizzazione, puoi trovarlo nella pagina di amministrazione di [!DNL Experience Cloud]. Vedi anche [Amministrazione - Servizi principali](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). La funzione modificata deve essere simile a quella riportata di seguito.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Non* modificare le lettere maiuscole in minuscole e viceversa nell'ID organizzazione. L'ID distingue tra maiuscole e minuscole e deve essere utilizzato esattamente così come è stato fornito.

## Passaggio 4: aggiungi i server di monitoraggio a Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

I server di monitoraggio sono utilizzati per la raccolta dati di [!DNL Analytics].

**Parte 1: trova gli URL del server di tracciamento**

Gli URL del server di monitoraggio si trovano nei file `s_code.js` e `AppMeasurement.js`. Devi trovare gli URL specificati dalle seguenti variabili:

* `s.trackingServer`
* `s.trackingServerSecure`

**Parte 2: imposta le variabili del server di tracciamento**

Per stabilire quali variabili usare per il server di monitoraggio:

1. Rispondi alle domande riportate nella griglia seguente. Usa le variabili che corrispondono alle tue risposte.
1. Sostituisci i segnaposto del server di monitoraggio con gli URL del server di monitoraggio.
1. Rimuovi dal codice le variabili del server di tracciamento e di [!DNL Experience Cloud] non utilizzate.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Se utilizzato, fai corrispondere gli [!DNL Experience Cloud] URL del server con gli URL del server di tracciamento corrispondenti, come riportato di seguito: &gt;
>* [!DNL Experience Cloud] URL del server = URL del server di tracciamento
>* [!DNL Experience Cloud] URL del server protetto = URL del server protetto di tracciamento
>



If you're not sure how to find your tracking server see the [FAQ](../faq-intro/faq.md) and [Correctly Populate the trackingServer and trackingServerSecure variables](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Passaggio 5: aggiorna il file AppMeasurement.js o s_code.js {#section-b53113aea1bd4de896e0e4e9a7edee19}

Aggiungi questa funzione al file `AppMeasurement.js` o `s_code.js`:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Posiziona il codice nella stessa sezione che contiene configurazioni come `linkInternalFilters`, `charSet`, `trackDownloads`, ecc.

***(Facoltativo ma consigliato)*Crea un prop personalizzato****

Imposta un prop personalizzato in `AppMeasurement.js` o in `s_code.js` per misurare la copertura. Aggiungi il prop personalizzato alla `doPlugins` funzione del file `AppMeasurement.js` o `s_code.js`:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Passaggio 6: aggiungi il codice API del visitatore alla pagina {#section-d46d6aa324c842f2931d901e38d6db1d}

Inserisci il `VisitorAPI.js` file entro i tag `<head>` di ogni pagina. Quando inserisci il `VisitorAPI.js` file nella pagina:

* Inseriscilo all'inizio della `<head>` sezione prima dei tag di altre soluzioni.
* Deve essere eseguito prima di AppMeasurement e del codice di altre [!DNL Experience Cloud] soluzioni.

Dopo il test e la verifica, trasferisci il codice in produzione.

## Passaggio 7: (facoltativo) configura un periodo di tolleranza {#section-7bbb2f72c26e4abeb8881e18366797a3}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). I periodi di tolleranza possono durare fino a 180 giorni. Se necessario, puoi rinnovare il periodo di tolleranza.

**Implementazione parziale**

Se solo alcune pagine utilizzano il servizio ID e tutte le pagine riferiscono alla stessa suite di [!DNL Analytics] rapporti, devi configurare un periodo di tolleranza. Questa situazione è frequente, se si dispone di una suite di rapporti globale per tutti i domini.

Dopo aver distribuito il servizio ID su tutte le pagine Web che riferiscono alla stessa suite di rapporti, interrompi il periodo di tolleranza.

**Requisiti del cookie s_vi**

Se, dopo la migrazione al servizio ID, richiedi ai nuovi visitatori il cookie s_vi, devi configurare il periodo di tolleranza. Questa situazione è frequente, se l'implementazione legge il cookie s_vi e lo memorizza in una variabile.

Quando l'implementazione può acquisire il MID, invece di leggere il cookie s_vi, puoi interrompere il periodo di tolleranza.

Consulta [Cookie e il servizio Experience Cloud Identity](../introduction/cookies.md).

Se invii dati a un sistema interno da un feed di dati clickstream e per i processi sono utilizzate le colonne `visid_high` e `visid_low`, devi attivare un periodo di tolleranza.

Quando il processo di inserimento dei dati può utilizzare le colonne `post_visid_high` e `post_visid_low`, interrompi il periodo di tolleranza.

Vedi [Descrizione delle colonne nei dati di clickstream](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html).

**Inserimento dei dati di clickstream**

## Passaggio 8: verifica e distribuisci il codice del servizio ID {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

Puoi eseguire il test e distribuirlo come segue.

**Test e verifica**

Per verificare l’implementazione del servizio ID, controlla i seguenti elementi:

* [Cookie AMCV](../introduction/cookies.md) nel dominio di hosting della pagina.
* Valore MID nella richiesta di immagine di [!DNL Analytics] con lo strumento [Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html).

Consulta [Test e verifica del servizio Experience Cloud Identity](../implementation-guides/test-verify.md).

**Distribuisci il codice**

Una volta superata la verifica, distribuisci il codice.

Se hai attivato un periodo di tolleranza al [passaggio 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Verifica che [!DNL Analytics] l'ID di (AID) e il MID siano presenti nella richiesta di immagine.
* Ricorda di disattivare il periodo di tolleranza quando sono presenti i requisiti per l'interruzione.
