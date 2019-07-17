---
description: Queste istruzioni sono per i clienti di Target che desiderano utilizzare il servizio identità Experience Cloud e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
keywords: Servizio ID
seo-description: Queste istruzioni sono per i clienti di Target che desiderano utilizzare il servizio identità Experience Cloud e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
seo-title: Implementazione del servizio identità Experience Cloud per Target
title: Implementazione del servizio identità Experience Cloud per Target
uuid: cb3581fa-4c4b-43aa-bb8e-8db85a6a1ef2
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Implement the Experience Cloud Identity Service for Target{#implement-the-experience-cloud-id-service-for-target}

Queste istruzioni sono per i clienti di Target che desiderano utilizzare il servizio identità Experience Cloud e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.

>[!IMPORTANT]
>
>* [Prima di iniziare, leggi i requisiti](../reference/requirements.md).
>* Configura e verifica questo codice in un ambiente di sviluppo prima di implementarlo in produzione.
>



## Passaggio 1: ottieni il codice del servizio ID {#section-b32ba0548aa546a79dd38be59832a53e}

Il [!DNL ID Service] richiede la `VisitorAPI.js` libreria dei codici. Per ottenere questo codice, contatta l'[assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html).

## Passaggio 2: aggiungi la funzione Visitor.getInstance al codice del servizio ID {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: copia la funzione Visitor.getInstance di seguito**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
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
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Passaggio 3: aggiungi l'ID organizzazione Experience Cloud a Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

Nella `Visitor.getInstance` funzione sostituisci `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` con l'ID organizzazione [!DNL Experience Cloud]. Se non conosci il tuo ID organizzazione, puoi trovarlo nella pagina di [!DNL Experience Cloud]amministrazione di. Vedi anche [Amministrazione - Servizi principali](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). La funzione modificata deve essere simile a quella riportata di seguito.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Non* modificare le lettere maiuscole in minuscole e viceversa nell'ID organizzazione. L'ID distingue tra maiuscole e minuscole e deve essere utilizzato esattamente così come è stato fornito.

## Passaggio 4: aggiungi il codice API del visitatore alla pagina {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Distribuisci il file `VisitorAPI.js` sul tuo sito nei tag `<head>` prima del riferimento al file `mbox.js`. Il servizio [!DNL Experience Cloud] ID deve essere eseguito prima che venga generata la prima chiamata alla rete [!DNL Target]. Dopo il test e la verifica, trasferisci il codice in produzione.

## Passaggio 5: verifica e distribuisci il codice del servizio ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Puoi eseguire il test e distribuirlo come segue.

**Test e verifica**

Per verificare l'implementazione del servizio ID:

* Controlla il cookie AMCV nel dominio di hosting della pagina.
* Verifica che `mboxMCGVID` sia presente nella richiesta [!DNL Target] e che contenga l'[!DNL Experience Cloud] ID (MID).

See [Cookies and the Experience Cloud Identity Service](../introduction/cookies.md) for information about the AMCV cookie and the MID.

**Distribuzione**

Una volta superata la verifica, distribuisci il codice.
