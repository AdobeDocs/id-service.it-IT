---
description: Queste istruzioni sono per i clienti Analytics che desiderano utilizzare il servizio identità Experience Platform e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
keywords: Servizio ID
seo-description: Queste istruzioni sono per i clienti Analytics che desiderano utilizzare il servizio identità Experience Platform e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
seo-title: Implementazione del servizio identità Experience Platform per Analytics
title: Implementazione del servizio identità Experience Platform per Analytics
uuid: 7 fbd 6 fa 0-1713-4232-8680-500 ed 62709 d 5
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Implementazione del servizio identità Experience Platform per Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Queste istruzioni sono per i clienti Analytics che desiderano utilizzare il servizio identità Experience Platform e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l&#39;implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.

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

## Passaggio 1: Scaricare il codice del servizio ID {#section-ead9403a6b7e45b887f9ac959ef89f7f}

La [!DNL ID Service] libreria richiede la libreria `VisitorAPI.js` dei codici. Per scaricare la libreria dei codici:

1. Vai a **[!UICONTROL Admin (Amministratore)]** &gt; **[!UICONTROL Code Manager]**(Gestione codici).
1. In [!DNL Code Manager], fai clic su **[!UICONTROL javascript (New)]** o **[!UICONTROL javascript (Legacy)]**.

   Verranno scaricate le librerie dei codici compresse.

1. Decomprimi il file dei codici e apri il file `VisitorAPI.js`.

## Passaggio 2: Aggiungi la funzione Visitor. getinstance al codice del servizio ID {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

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

## Passaggio 3: Aggiungi l&#39;ID organizzazione Experience Cloud a Visitor. getinstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

Nella `Visitor.getInstance` funzione, sostituisci `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` con l&#39;ID [!DNL Experience Cloud] organizzazione. Se non conosci il tuo ID organizzazione, puoi trovarlo nella pagina di amministrazione di [!DNL Experience Cloud]. Vedi anche [Amministrazione - Servizi principali](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). La funzione modificata deve essere simile a quella riportata di seguito.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Non* modificate il caso dei caratteri nell&#39;ID organizzazione. L&#39;ID distingue tra maiuscole e minuscole e deve essere utilizzato esattamente così come è stato fornito.

## Passaggio 4: Aggiungi i server di monitoraggio a Visitor. getinstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

I server di monitoraggio sono utilizzati per la raccolta dati di [!DNL Analytics].

**Parte 1: trova gli URL del server di tracciamento**

Controllate i file `s_code.js` o `AppMeasurement.js` i file per individuare gli URL del server di tracciamento. Devi trovare gli URL specificati dalle seguenti variabili:

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
>Se utilizzato, corrispondenza degli [!DNL Experience Cloud] URL del server con gli URL del server di tracciamento corrispondenti, come segue: &gt;
>* [!DNL Experience Cloud] URL server = URL del server di tracciamento
>* [!DNL Experience Cloud] URL server protetto = URL protetto del server di tracciamento
>



Se non sei sicuro di come trovare il server di tracciamento, consulta [le domande frequenti](../faq-intro/faq.md) e [Aggiunta corretta delle variabili trackingserver e trackingserversecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Passaggio 5: Aggiorna il file appmeasurement. js o s_ code. js {#section-b53113aea1bd4de896e0e4e9a7edee19}

Aggiungete questa funzione al `AppMeasurement.js` file o `s_code.js` al file:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Posiziona il codice nella stessa sezione che contiene configurazioni come `linkInternalFilters``charSet``trackDownloads`, ecc.

***(Facoltativo ma consigliato)*Crea un prop personalizzato**

Imposta un prop personalizzato in `AppMeasurement.js` o `s_code.js` misura la copertura. Aggiungere questo prop personalizzato alla `doPlugins` funzione dei file `AppMeasurement.js` o `s_code.js` dei file:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Passaggio 6: Aggiungere il codice API del visitatore alla pagina {#section-d46d6aa324c842f2931d901e38d6db1d}

Posizionare il `VisitorAPI.js` file all&#39;interno dei `<head>` tag su ogni pagina. Quando inserisci il file `VisitorAPI.js` nella pagina:

* Inseriscilo all&#39;inizio della `<head>` sezione, prima di altri tag delle soluzioni.
* Deve essere eseguito prima di AppMeasurement e del codice di altre soluzioni [!DNL Experience Cloud].

Dopo il test e la verifica, trasferisci il codice in produzione.

## Passaggio 7: (Facoltativo) Configura un periodo di tolleranza {#section-7bbb2f72c26e4abeb8881e18366797a3}

Se uno di questi casi d&#39;uso si applica alla tua situazione, chiedi [all&#39;Assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html) di impostare un periodo [di tolleranza temporaneo](../reference/analytics-reference/grace-period.md). I periodi di tolleranza possono durare fino a 180 giorni. Se necessario, puoi rinnovare il periodo di tolleranza.

**Implementazione parziale**

Se solo alcune pagine utilizzano il servizio ID e tutte le pagine riferiscono alla stessa suite di rapporti [!DNL Analytics], devi configurare un periodo di tolleranza. Questa situazione è frequente, se si dispone di una suite di rapporti globale per tutti i domini.

Dopo aver distribuito il servizio ID su tutte le pagine Web che riferiscono alla stessa suite di rapporti, interrompi il periodo di tolleranza.

**Requisiti del cookie s_vi**

Se, dopo la migrazione al servizio ID, richiedi ai nuovi visitatori il cookie s_vi, devi configurare il periodo di tolleranza. Questa situazione è frequente, se l&#39;implementazione legge il cookie s_vi e lo memorizza in una variabile.

Quando l&#39;implementazione può acquisire il MID, invece di leggere il cookie s_vi, puoi interrompere il periodo di tolleranza.

Vedi [Cookie e Servizio identità piattaforma Experience Platform](../introduction/cookies.md).

Se invii dati a un sistema interno da un feed di dati clickstream e per i processi sono utilizzate le colonne `visid_high` e `visid_low`, devi attivare un periodo di tolleranza.

Dopo il processo di assimilazione dei dati, interrompi il periodo `post_visid_high``post_visid_low` di tolleranza.

Vedi [Descrizione delle colonne nei dati di clickstream](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html).

**Inserimento dei dati di clickstream**

## Passaggio 8: Verificare e distribuire il codice del servizio ID {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

Potete eseguire il test e distribuirlo come segue.

**Test e verifica**

Per verificare l’implementazione del servizio ID, controlla i seguenti elementi:

* [Cookie AMCV](../introduction/cookies.md) nel dominio di hosting della pagina.
* Valore MID nella richiesta di immagine di [!DNL Analytics] con lo strumento [Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html).

Vedi [Test and Verify the Experience Platform Identity Service](../implementation-guides/test-verify.md).

**Implementare il codice**

Una volta superata la verifica, distribuisci il codice.

Se hai attivato un periodo di tolleranza al [passaggio 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Verifica che l&#39;ID di [!DNL Analytics] (AID) e il MID siano presenti nella richiesta di immagine.
* Ricorda di disattivare il periodo di tolleranza quando sono presenti i requisiti per l&#39;interruzione.