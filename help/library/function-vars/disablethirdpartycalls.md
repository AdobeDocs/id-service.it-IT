---
description: Flag booleano opzionale che impedisce al servizio ID di effettuare chiamate ad altri domini.
keywords: monitoraggio interdominio; servizio ID
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
TQID: https://experienceleague.adobe.com/mv00QfToxSqeITADmY1LbihbtJNHf1zzQef9uKDu-dc
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 200
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

