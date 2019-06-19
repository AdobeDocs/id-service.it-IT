---
description: Queste istruzioni sono per i clienti di Target che desiderano utilizzare il servizio Identità Experience Platform e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
keywords: Servizio ID
seo-description: Queste istruzioni sono per i clienti di Target che desiderano utilizzare il servizio Identità Experience Platform e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l'implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.
seo-title: Implementazione del servizio identità Experience Platform per Target
title: Implementazione del servizio identità Experience Platform per Target
uuid: cb 3581 fa -4 c 4 b -43 aa-bb 8 e -8 db 85 a 6 a 1 ef 2
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Implementazione del servizio identità Experience Platform per Target{#implement-the-experience-cloud-id-service-for-target}

Queste istruzioni sono per i clienti di Target che desiderano utilizzare il servizio Identità Experience Platform e non usano Gestione dinamica dei tag. Tuttavia, si consiglia vivamente di usare Dynamic Tag Management per implementare il servizio ID. Dynamic Tag Management semplifica l&#39;implementazione e verifica automaticamente che il codice sia inserito correttamente e nella giusta sequenza.

>[!IMPORTANT]
>
>* [Prima di iniziare, leggi i requisiti](../reference/requirements.md).
>* Configura e verifica questo codice in un ambiente di sviluppo prima di implementarlo in produzione.
>



## Passaggio 1: Ottenere il codice del servizio ID {#section-b32ba0548aa546a79dd38be59832a53e}

La [!DNL ID Service] libreria richiede la libreria `VisitorAPI.js` dei codici. Per ottenere questo codice, contatta l&#39;[assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html).

## Passaggio 2: Aggiungi la funzione Visitor. getinstance al codice del servizio ID {#section-287ef2958e9f43858fe9d630ae519e22}

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

## Passaggio 3: Aggiungi l&#39;ID organizzazione Experience Cloud a Visitor. getinstance {#section-522b1877be9243c39b222859b821f0ce}

Nella `Visitor.getInstance` funzione, sostituisci `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` con l&#39;ID [!DNL Experience Cloud] organizzazione. Se non conosci il tuo ID organizzazione, puoi trovarlo nella pagina di amministrazione di [!DNL Experience Cloud]. Vedi anche [Amministrazione - Servizi principali](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). La funzione modificata deve essere simile a quella riportata di seguito.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Non* modificate il caso dei caratteri nell&#39;ID organizzazione. L&#39;ID distingue tra maiuscole e minuscole e deve essere utilizzato esattamente così come è stato fornito.

## Passaggio 4: Aggiungere il codice API del visitatore alla pagina {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Distribuite il `VisitorAPI.js` file sul sito nei `<head>` tag prima del riferimento al `mbox.js` file. Il [!DNL Experience Cloud] servizio ID deve essere eseguito prima della generazione della prima [!DNL Target] chiamata di rete. Dopo il test e la verifica, trasferisci il codice in produzione.

## Passaggio 5: Verificare e distribuire il codice del servizio ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Potete eseguire il test e distribuirlo come segue.

**Test e verifica**

Per verificare l&#39;implementazione del servizio ID:

* Controlla il cookie AMCV nel dominio di hosting della pagina.
* Verifica `mboxMCGVID` che sia presente nella [!DNL Target] richiesta e che contenga l&#39; [!DNL Experience Cloud] ID (MID).

Per informazioni sul cookie AMCV e sul MID, vedi [Cookie e Servizio](../introduction/cookies.md) identità piattaforma Experience Platform.

**Distribuzione**

Una volta superata la verifica, distribuisci il codice.
