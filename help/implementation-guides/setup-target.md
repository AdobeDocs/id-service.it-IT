---
description: Queste istruzioni sono per i clienti di Target che desiderano usare il servizio Experience Cloud ID e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
keywords: Servizio ID
seo-description: Queste istruzioni sono per i clienti di Target che desiderano usare il servizio Experience Cloud ID e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
seo-title: Implementazione del servizio Experience Cloud ID per Target
title: Implementazione del servizio Experience Cloud ID per Target
uuid: cb 3581 fa -4 c 4 b -43 aa-bb 8 e -8 db 85 a 6 a 1 ef 2
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Implementazione del servizio Experience Cloud ID per Target{#implement-the-experience-cloud-id-service-for-target}

Queste istruzioni sono per i clienti di Target che desiderano usare il servizio Experience Cloud ID e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l&#39;implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.

>[!IMPORTANT]
>
>* [Prima di iniziare, leggi i requisiti](../reference/requirements.md).
>* Configura e verifica questo codice in un ambiente di sviluppo prima di implementarlo in produzione.
>



## Step 1: Get the ID Service code {#section-b32ba0548aa546a79dd38be59832a53e}

The [!DNL ID Service] requires the `VisitorAPI.js` code library. Per ottenere questo codice, contatta l&#39;[assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html).

## Step 2: Add the Visitor.getInstance function to the ID Service code {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: copia la funzione Visitor.getInstance di seguito**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
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
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Step 3: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

In the `Visitor.getInstance` function, replace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` with your [!DNL Experience Cloud] organization ID. Se non conosci il tuo ID organizzazione, puoi trovarlo nella pagina di amministrazione di [!DNL Experience Cloud]. Vedi anche [Amministrazione - Servizi principali](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). La funzione modificata deve essere simile a quella riportata di seguito.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Non* modificate il caso dei caratteri nell&#39;ID organizzazione. L&#39;ID distingue tra maiuscole e minuscole e deve essere utilizzato esattamente così come è stato fornito.

## Step 4: Add Visitor API code to the page {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Deploy the `VisitorAPI.js` file to your site in the `<head>` tags before the reference to the `mbox.js` file. The [!DNL Experience Cloud] ID service must execute before the first [!DNL Target] network call is generated. Dopo il test e la verifica, trasferisci il codice in produzione.

## Step 5: Test and deploy ID Service code {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Potete eseguire il test e distribuirlo come segue.

**Test e verifica**

Per verificare l&#39;implementazione del servizio ID:

* Controlla il cookie AMCV nel dominio di hosting della pagina.
* Verify `mboxMCGVID` appears in your [!DNL Target] request and that it contains the [!DNL Experience Cloud] ID (MID).

See [Cookies and the Experience Cloud ID Service](../introduction/cookies.md) for information about the AMCV cookie and the MID.

**Distribuzione**

Una volta superata la verifica, distribuisci il codice.
