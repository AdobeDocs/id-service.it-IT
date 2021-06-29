---
description: Flag booleano opzionale che impedisce al servizio ID di effettuare chiamate ad altri domini.
keywords: monitoraggio interdominio; servizio ID
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '200'
ht-degree: 100%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

Flag booleano opzionale che impedisce al servizio ID di effettuare chiamate ad altri domini.

**Sintassi:** ` `disableThirdPartyCalls: true false`` (l&#39;impostazione predefinita è `false`)

Quando `disableThirdPartyCalls: true`, il servizio ID non effettua chiamate ad altri domini.

**Finalità**

Questa variabile è progettata per i clienti con le seguenti esigenze:

* Impedire che il servizio ID effettui chiamate dalle loro pagine sicure e autenticate.
* Assegnare ai visitatori del sito un Experience Cloud ID (MID).
* Far funzionare correttamente le altre soluzioni Experience Cloud.

**Strategia di implementazione**

Poiché altre soluzioni Experience Cloud usano l&#39;identificatore MID, il servizio ID chiama Adobe per restituire e impostare questo ID. Per evitare che il servizio ID effettui tali chiamate da sezioni autenticate del sito, puoi fare sì che le chiamate necessarie vengano effettuate da pagine che non richiedono la preventiva autenticazione. Una volta che un visitatore ha un suo identificatore MID, puoi impostare `disableThirdPartyCalls= true` nel codice del servizio ID sulle sezioni autenticate del sito. Si presume in questo caso che almeno la maggior parte dei clienti accederà a una pagina di autenticazione prima di accedere alle parti protette del sito.

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```
