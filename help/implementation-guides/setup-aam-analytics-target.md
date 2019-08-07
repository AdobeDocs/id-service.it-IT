---
description: Queste istruzioni sono per i clienti di Analytics, Audience Manager e Target che desiderano utilizzare il servizio identità Experience Cloud e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
keywords: Servizio ID
seo-description: Queste istruzioni sono per i clienti di Analytics, Audience Manager e Target che desiderano utilizzare il servizio identità Experience Cloud e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
seo-title: Implementazione del servizio identità Experience Cloud per Analytics, Audience Manager e Target
title: Implementazione del servizio identità Experience Cloud per Analytics, Audience Manager e Target
uuid: 9d446b77-ca62-4325-8bb0-ff43a52313c0
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Implement the Experience Cloud Identity Service for Analytics, Audience Manager, and Target {#implement-the-experience-cloud-id-service-for-analytics-audience-manager-and-target}

Queste istruzioni sono per i clienti di Analytics, Audience Manager e Target che desiderano utilizzare il servizio identità Experience Cloud e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.

>[!IMPORTANT]
>
>Leggi i [requisiti](../reference/requirements.md) del servizio ID e prendi nota dei seguenti requisiti specifici per questa implementazione: &gt;
>* I clienti che usano s_code non possono completare questa procedura. Per completare la procedura, aggiorna il codice mbox alla versione 61.
>* Configura e verifica questo codice in un ambiente di sviluppo *prima* di implementarlo in produzione.
>



## Passaggio 1: pianificazione dell'inoltro lato server {#section-880797cc992d4755b29cada7b831f1fc}

Oltre ai passaggi qui descritti, i clienti che usano [!DNL Analytics] e [!DNL Audience Manager] devono effettuare la migrazione all'inoltro lato server. L'inoltro lato server consente di rimuovere DIL (codice di raccolta dati di Audience Manager) e sostituirlo con il [modulo Gestione dell'audience](https://marketing.adobe.com/resources/help/en_US/aam/c_profiles_audiences.html). Per ulteriori informazioni, consulta la [documentazione sull'inoltro lato server](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html).

La migrazione all'inoltro lato server richiede un'attenta pianificazione e coordinazione. Il processo comporta modifiche esterne da apportare al codice del sito e passaggi interni che Adobe deve effettuare per il provisioning del tuo account. In effetti, molte di queste procedure di migrazione devono avvenire in parallelo ed essere rilasciate insieme. Il percorso di implementazione dovrà seguire questa sequenza di eventi:

1. Pianifica con i tuoi contatti per [!DNL Analytics] e [!DNL Audience Manager] la migrazione dell'inoltro lato server e il servizio ID. La selezione del server di tracciamento è una fase importante di questo piano.

1. Per iniziare, completa il modulo disponibile sul [sito di integrazioni e provisioning](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES).

1. Implementa il servizio ID e il [!DNL Audience Management Module] simultaneamente. Per funzionare correttamente, il [!DNL Audience Management Module] (inoltro lato server) e il servizio ID devono essere rilasciati per lo stesso set di pagine e allo stesso tempo.

## Passaggio 2: scarica il codice del servizio ID {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

Il servizio ID richiede la `VisitorAPI.js` libreria dei codici. Per scaricare la libreria dei codici:

1. Seleziona **[!UICONTROL Amministratore &gt; Gestione codici]**.
1. In Gestione codici, fai clic su **[!UICONTROL JavaScript (Nuovo)]** o su **[!UICONTROL JavaScript (Legacy)]**. Verranno scaricate le librerie dei codici compresse.

1. Decomprimi il file dei codici e apri il `VisitorAPI.js` file.

## Passaggio 3: aggiungi la funzione Visitor.getInstance al codice del servizio ID {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* Le versioni precedenti dell'API del servizio ID inserivano questa funzione in una posizione diversa e richiedevano un'altra sintassi. Se effettui la migrazione da una versione precedente alla [1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), prendi nota della nuova posizione e della sintassi indicate in questo documento.
>* Il codice riportato in MAIUSCOLO funge da segnaposto per valori effettivi. Sostituisci tale testo con il tuo ID organizzazione, l'URL del server di tracciamento o altro valore con nome.
>



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

**Parte 2: aggiungi il codice della funzione nel file VisitorAPI.js**

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

## Passaggio 4: aggiungi l'ID organizzazione Experience Cloud a Visitor.getInstance {#section-e2947313492546789b0c3b2fc3e897d8}

Nella `Visitor.getInstance` funzione sostituisci `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` con l'ID organizzazione Experience Cloud. Se non conosci il tuo ID organizzazione, puoi trovarlo nella pagina di amministrazione di Experience Cloud. La funzione modificata deve essere simile a quella riportata di seguito.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Non* modificare le lettere maiuscole in minuscole e viceversa nell'ID organizzazione. L'ID distingue tra maiuscole e minuscole e deve essere utilizzato esattamente così come è stato fornito.

## Passaggio 5: aggiungi i server di monitoraggio a Visitor.getInstance {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics usa i server di tracciamento per la raccolta dei dati.

**Parte 1: trova gli URL del server di tracciamento**

Gli URL del server di monitoraggio si trovano nei file `s_code.js` e `AppMeasurement.js`. Devi trovare gli URL specificati dalle seguenti variabili:

* `s.trackingServer`
* `s.trackingServerSecure`

**Parte 2: imposta le variabili del server di tracciamento**

Per stabilire quali variabili usare per il server di monitoraggio:

1. Rispondi alle domande riportate nella griglia seguente. Usa le variabili che corrispondono alle tue risposte.
1. Sostituisci i segnaposto del server di monitoraggio con gli URL del server di monitoraggio.
1. Rimuovi dal codice le variabili del server di tracciamento e di Experience Cloud non utilizzate.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Se utilizzato, fai corrispondere gli URL del server Experience Cloud con gli URL del server di tracciamento corrispondenti, come riportato di seguito:

* URL del server Experience Cloud = URL del server di tracciamento
* URL del server protetto Experience Cloud = URL del server protetto di tracciamento

Se non sei sicuro di come trovare il server di tracciamento, consulta [Domande frequenti](../faq-intro/faq.md) e [Aggiunta corretta delle variabili trackingServer e trackingServerSecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Passaggio 6: aggiorna il file AppMeasurement.js {#section-5517e94a09bc44dfb492ebca14b43048}

Questo passaggio richiede [!UICONTROL AppMeasurement]. Se utilizzi ancora s_code, non potrai procedere.

Aggiungi la `Visitor.getInstance` funzione riportata di seguito al tuo `AppMeasurement.js` file. Inseriscilo nella stessa sezione che contiene configurazioni come `linkInternalFilters`, `charSet`, `trackDownloads`, ecc.:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>A questo punto, devi rimuovere il codice [!DNL Audience Manager] DIL e sostituirlo con il modulo Gestione dell'audience. Vedi [Implementazione dell'inoltro lato server](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html).

***(Facoltativo ma consigliato)*Crea un prop personalizzato****

Imposta un prop personalizzato in `AppMeasurement.js` per misurare la copertura. Aggiungi il prop personalizzato alla `doPlugins` funzione del `AppMeasurement.js` file:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Passaggio 7: aggiungi il codice API del visitatore alla pagina {#section-c2bd096a3e484872a72967b6468d3673}

Inserisci il ` [!UICONTROL VisitorAPI.js]` file entro i tag `<head>` di ogni pagina. Quando inserisci il `VisitorAPI.js` file nella pagina:

* Inseriscilo all'inizio della `<head>` sezione prima dei tag di altre soluzioni.
* Deve essere eseguito prima di AppMeasurement e del codice di altre [!DNL Experience Cloud] soluzioni.

## Passaggio 8: (facoltativo) configura un periodo di tolleranza {#section-aceacdb7d5794f25ac6ff46f82e148e1}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). I periodi di tolleranza possono durare fino a 180 giorni. Se necessario, puoi rinnovare il periodo di tolleranza.

**Implementazione parziale**

Se solo alcune pagine utilizzano il servizio ID e tutte le pagine riferiscono alla stessa suite di rapporti Analytics, devi configurare un periodo di tolleranza. Questa situazione è frequente, se si dispone di una suite di rapporti globale per tutti i domini.

Dopo aver distribuito il servizio ID su tutte le pagine Web che riferiscono alla stessa suite di rapporti, interrompi il periodo di tolleranza.

**Requisiti del cookie s_vi**

Se, dopo la migrazione al servizio ID, richiedi ai nuovi visitatori il cookie s_vi, devi configurare il periodo di tolleranza. Questa situazione è frequente, se l'implementazione legge il cookie s_vi e lo memorizza in una variabile.

Quando l'implementazione può acquisire il MID, invece di leggere il cookie s_vi, puoi interrompere il periodo di tolleranza.

See also, [Cookies and the Experience Cloud Identity Service](../introduction/cookies.md).

**Integrazione dei dati di clickstream**

Se invii dati a un sistema interno da un feed di dati clickstream e per i processi sono utilizzate le colonne `visid_high` e `visid_low`, devi attivare un periodo di tolleranza.

Quando il processo di inserimento dei dati può utilizzare le colonne `post_visid_high` e `post_visid_low`, interrompi il periodo di tolleranza.

Vedi [Descrizione delle colonne nei dati di clickstream](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html).

## Passaggio 9: test e verifica {#section-f857542bfc70496dbb9f318d6b3ae110}

Le soluzioni [!DNL Experience Cloud] di questa implementazione restituiscono gli ID sotto forma di coppie chiave-valore. Ogni soluzione usa chiavi diverse (ad esempio, [!DNL Analytics] SDID di e [!DNL Target] mboxMCSDID di) per lo stesso ID. Per verificare il corretto funzionamento dell'implementazione, carica le pagine in un ambiente di sviluppo. Usa la console del browser o un software per monitorare le richieste HTTP e le risposte, e controlla gli ID elencati di seguito. Il servizio ID è stato implementato correttamente se le coppie chiave-valore elencate di seguito restituiscono gli stessi valori ID.

>[!TIP]
>
>You can use the [Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=debugger.html) or the [Charles HTTP proxy](https://www.charlesproxy.com/) to check for these solution-specific IDs. Puoi anche usare un altro strumento o debugger di tua preferenza.

**Tutte le soluzioni**

Elementi da verificare:

* [Cookie AMCV](../introduction/cookies.md) nel dominio di hosting della pagina.
* [!DNL Experience Cloud] ID (MID) con [!DNL Adobe] Debugger o altro strumento di debug.

For additional checks that help you determine if the ID service is working properly, see [Test and Verify the Experience Cloud Identity Service](../implementation-guides/test-verify.md).

**Analytics**

Verifica l'identificatore SDID nella richiesta JavaScript. Il valore SDID di Analytics deve corrispondere al valore mboxMCSDID di Target.

Se le verifiche restituiscono un AID, questo può dipendere dalle seguenti possibili situazioni:

* Sei un visitatore precedente ed è in corso la migrazione degli [!DNL Analytics] ID precedenti.
* Hai impostato un [periodo di tolleranza](../reference/analytics-reference/grace-period.md).

Quando ricevi un AID, controllane il valore rispetto al valore [!DNL Target] mboxMCAVID di. Se il servizio ID è stato implementato correttamente, questi due valori saranno identici.

**Audience Manager**

Per verificare l'inoltro lato server, vedi:

* [Come determinare se il tuo account è pronto per ricevere dati inoltrati](https://marketing.adobe.com/resources/help/en_US/aam/ssf-success.html)
* [Come determinare se il tuo account non è pronto per ricevere dati inoltrati](https://marketing.adobe.com/resources/help/en_US/aam/ssf-fail.html)

**Target**

Elementi da verificare:

* mboxMCGVID
* mboxMCSDID (il valore mboxMCSDID deve corrispondere al valore SDID di Analytics.)

Se il test restituisce un valore mboxMCAVID, questo può dipendere dalle seguenti possibili situazioni:

* Sei un visitatore precedente ed è in corso la migrazione degli [!DNL Analytics] ID precedenti.
* Hai impostato un periodo di tolleranza.

Quando ricevi un mboxMCAVID, controllane il valore rispetto al valore [!DNL Analytics] AID di. Se il servizio ID è stato implementato correttamente, questi due valori saranno identici.

**Distribuzione**

## Passaggio 10: distribuisci {#section-4188fa95e7dc455a986b48a6c517c1c9}

Una volta superata la verifica, distribuisci il codice.

Se hai attivato un periodo di tolleranza:

* Verifica che l'ID di Analytics (AID) e il MID siano presenti nella richiesta di immagine.
* Ricorda di disattivare il periodo di tolleranza quando sono presenti i [requisiti per l'interruzione](../implementation-guides/setup-aam-analytics-target.md#section-aceacdb7d5794f25ac6ff46f82e148e1).

