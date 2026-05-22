---
description: Queste istruzioni sono per chi utilizza Target, desidera usare Experience Cloud Identity Service e non usa i tag di Raccolta dati. Tuttavia, si consiglia vivamente di usare i tag per implementare il servizio ID. I tag agevolano il flusso di lavoro di implementazione e assicurano automaticamente il posizionamento e la sequenza del codice corretti.
keywords: Servizio ID
title: Implementare Experience Cloud Identity Service per Target
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
TQID: https://experienceleague.adobe.com/1994Y39yotvpJkcYazVnG0w-GupHiZZipnLWSTbgle8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 422
ht-degree: 100%

---

# Implementare Experience Cloud Identity Service per Target{#implement-the-experience-cloud-id-service-for-target}

Queste istruzioni sono per chi utilizza Target e desidera utilizzare Experience Cloud Identity Service e non usa i [tag di Raccolta dati](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it). Tuttavia, si consiglia vivamente di usare i tag per implementare il servizio ID. I tag agevolano il flusso di lavoro di implementazione e assicurano automaticamente il posizionamento e la sequenza del codice corretti.

>[!IMPORTANT]
>
>* [Prima di iniziare](../reference/requirements.md), leggi i requisiti.
>* Configura e verifica questo codice in un ambiente di sviluppo prima di implementarlo in produzione.

## Passaggio 1: ottieni il codice del servizio ID {#section-b32ba0548aa546a79dd38be59832a53e}

Il [!UICONTROL ID Service] richiede la `VisitorAPI.js` libreria dei codici. Per ottenere questo codice contatta l’[Assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html).

## Passaggio 2: aggiungi la funzione Visitor.getInstance al codice del servizio ID {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: copia la funzione Visitor.getInstance di seguito**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
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
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Passaggio 3: aggiungi l’ID organizzazione Experience Cloud a Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

Nella `Visitor.getInstance` funzione sostituisci `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` con l&#39;ID organizzazione [!DNL Experience Cloud]. Se non conosci il tuo ID organizzazione, puoi trovarlo nella pagina di amministrazione di [!DNL Experience Cloud]. Vedi anche [Amministrazione - Servizi di base](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=it). La funzione modificata deve essere simile a quella riportata di seguito.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Non* modificare le lettere maiuscole in minuscole e viceversa nell&#39;ID organizzazione. L&#39;ID distingue tra maiuscole e minuscole e deve essere utilizzato esattamente così come è stato fornito.

## Passaggio 4: aggiungi il codice API del visitatore alla pagina {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Distribuisci il file `VisitorAPI.js` sul tuo sito nei tag `<head>` prima del riferimento al file `mbox.js`. Il servizio [!DNL Experience Cloud] ID deve essere eseguito prima che venga generata la prima chiamata alla rete [!DNL Target]. Dopo il test e la verifica, trasferisci il codice in produzione.

## Passaggio 5: verifica e distribuisci il codice del servizio ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Puoi eseguire il test e distribuirlo come segue.

**Test e verifica**

Per verificare l’implementazione del servizio ID:

* Controlla il cookie AMCV nel dominio di hosting della pagina.
* Verifica che `mboxMCGVID` sia presente nella richiesta [!DNL Target] e che contenga l&#39;[!DNL Experience Cloud] ID (MID).

Per informazioni sul cookie AMCV e sull’identificatore MID, consulta [I cookie ed Experience Cloud Identity Service](../introduction/cookies.md).

**Distribuzione**

Distribuisci il codice dopo aver superato il test.

