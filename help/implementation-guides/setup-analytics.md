---
description: Queste istruzioni sono per i clienti di Analytics che desiderano usare il servizio Experience Cloud ID e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
keywords: Servizio ID
seo-description: Queste istruzioni sono per i clienti di Analytics che desiderano usare il servizio Experience Cloud ID e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
seo-title: Implementazione del servizio Experience Cloud ID per Analytics
title: Implementazione del servizio Experience Cloud ID per Analytics
uuid: 7 fbd 6 fa 0-1713-4232-8680-500 ed 62709 d 5
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Implementazione del servizio Experience Cloud ID per Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Queste istruzioni sono per i clienti di Analytics che desiderano usare il servizio Experience Cloud ID e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l&#39;implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.

>[!IMPORTANT]
>
>* [Prima di iniziare, leggi i requisiti](../reference/requirements.md).
>* Configura e verifica questo codice in un ambiente di sviluppo prima di implementarlo in produzione.
>



Per implementare il servizio ID per Adobe Analytics, effettuate le seguenti operazioni:

1. [Scaricare il codice del servizio ID](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Aggiungi la funzione Visitor. getinstance al codice del servizio ID](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Aggiungi l&#39;ID organizzazione Experience Cloud a Visitor. getinstance](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Aggiungi i server di monitoraggio a Visitor. getinstance](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Aggiorna il file appmeasurement. js o s_ code. js](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [Aggiungere il codice API del visitatore alla pagina](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Facoltativo) Configura un periodo di tolleranza](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [Verificare e distribuire il codice del servizio ID](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Step 1: Download the ID Service code {#section-ead9403a6b7e45b887f9ac959ef89f7f}

The [!DNL ID Service] requires the `VisitorAPI.js` code library. Per scaricare la libreria dei codici:

1. Go to **[!UICONTROL Admin]** &gt; **[!UICONTROL Code Manager]**.
1. In [!DNL Code Manager], click either **[!UICONTROL JavaScript (New)]** or **[!UICONTROL JavaScript (Legacy)]**.

   Verranno scaricate le librerie dei codici compresse.

1. Decomprimi il file dei codici e apri il file `VisitorAPI.js`.

## Passaggio 2: Add the Visitor.getInstance function to the ID Service Code {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* Le versioni precedenti dell&#39;API del servizio ID inserivano questa funzione in una posizione diversa e richiedevano un&#39;altra sintassi. Se effettui la migrazione da una versione precedente alla [1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), prendi nota della nuova posizione e della sintassi indicate in questo documento.
>* Il codice riportato in MAIUSCOLO funge da segnaposto per valori effettivi. Sostituisci tale testo con il tuo ID organizzazione, l&#39;URL del server di tracciamento o altro valore con nome.
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

Posiziona la funzione `Visitor.getInstance` alla fine del file, dopo il blocco del codice. Il file modificato deve essere simile al seguente:

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

## Step 3: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

In the `Visitor.getInstance` function, replace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` with your [!DNL Experience Cloud] organization ID. Se non conosci il tuo ID organizzazione, puoi trovarlo nella pagina di amministrazione di [!DNL Experience Cloud]. Vedi anche [Amministrazione - Servizi principali](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). La funzione modificata deve essere simile a quella riportata di seguito.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Non* modificate il caso dei caratteri nell&#39;ID organizzazione. L&#39;ID distingue tra maiuscole e minuscole e deve essere utilizzato esattamente così come è stato fornito.

## Step 4: Add your tracking servers to Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

I server di monitoraggio sono utilizzati per la raccolta dati di [!DNL Analytics].

**Parte 1: trova gli URL del server di tracciamento**

Check your `s_code.js` or `AppMeasurement.js` files to find the tracking server URLs. Devi trovare gli URL specificati dalle seguenti variabili:

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
>When used, match the [!DNL Experience Cloud] server URLs to their corresponding tracking server URLs like this: &gt;
>* [!DNL Experience Cloud] URL server = URL del server di tracciamento
>* [!DNL Experience Cloud] URL server protetto = URL protetto del server di tracciamento
>



If you&#39;re not sure how to find your tracking server see the [FAQ](../faq-intro/faq.md) and [Correctly Populate the trackingServer and trackingServerSecure variables](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Step 5: Update your AppMeasurement.js or s_code.js file {#section-b53113aea1bd4de896e0e4e9a7edee19}

Add this function to your `AppMeasurement.js` or `s_code.js` file:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Place the code in the same section that contains configurations such as `linkInternalFilters`, `charSet`, `trackDownloads`, etc.

***(Facoltativo ma consigliato)*Crea un prop personalizzato**

Set a custom prop in `AppMeasurement.js` or `s_code.js` to measure coverage. Add this custom prop to the `doPlugins` function of your `AppMeasurement.js` or `s_code.js` files:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Step 6: Add Visitor API code to the page {#section-d46d6aa324c842f2931d901e38d6db1d}

Place the `VisitorAPI.js` file within the `<head>` tags on each page. Quando inserisci il file `VisitorAPI.js` nella pagina:

* Put it at the beginning of the `<head>` section to it appears before other solution tags.
* Deve essere eseguito prima di AppMeasurement e del codice di altre soluzioni [!DNL Experience Cloud].

Dopo il test e la verifica, trasferisci il codice in produzione.

## Step 7: (Optional) Configure a grace period {#section-7bbb2f72c26e4abeb8881e18366797a3}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). I periodi di tolleranza possono durare fino a 180 giorni. Se necessario, puoi rinnovare il periodo di tolleranza.

**Implementazione parziale**

Se solo alcune pagine utilizzano il servizio ID e tutte le pagine riferiscono alla stessa suite di rapporti [!DNL Analytics], devi configurare un periodo di tolleranza. Questa situazione è frequente, se si dispone di una suite di rapporti globale per tutti i domini.

Dopo aver distribuito il servizio ID su tutte le pagine Web che riferiscono alla stessa suite di rapporti, interrompi il periodo di tolleranza.

**Requisiti del cookie s_vi**

Se, dopo la migrazione al servizio ID, richiedi ai nuovi visitatori il cookie s_vi, devi configurare il periodo di tolleranza. Questa situazione è frequente, se l&#39;implementazione legge il cookie s_vi e lo memorizza in una variabile.

Quando l&#39;implementazione può acquisire il MID, invece di leggere il cookie s_vi, puoi interrompere il periodo di tolleranza.

See, [Cookies and the Experience Cloud ID Service](../introduction/cookies.md).

Se invii dati a un sistema interno da un feed di dati clickstream e per i processi sono utilizzate le colonne `visid_high` e `visid_low`, devi attivare un periodo di tolleranza.

Discontinue the grace period after your data ingestion process can use the `post_visid_high` and `post_visid_low` columns.

Vedi [Descrizione delle colonne nei dati di clickstream](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html).

**Inserimento dei dati di clickstream**

## Step 8: Test and deploy ID Service code {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

Potete eseguire il test e distribuirlo come segue.

**Test e verifica**

Per verificare l’implementazione del servizio ID, controlla i seguenti elementi:

* [Cookie AMCV](../introduction/cookies.md) nel dominio di hosting della pagina.
* Valore MID nella richiesta di immagine di [!DNL Analytics] con lo strumento [Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html).

See, [Test and Verify the Experience Cloud ID Service](../implementation-guides/test-verify.md).

**Implementare il codice**

Una volta superata la verifica, distribuisci il codice.

Se hai attivato un periodo di tolleranza al [passaggio 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Verifica che l&#39;ID di [!DNL Analytics] (AID) e il MID siano presenti nella richiesta di immagine.
* Ricorda di disattivare il periodo di tolleranza quando sono presenti i requisiti per l&#39;interruzione.
