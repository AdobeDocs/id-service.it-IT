---
description: Flag booleano facoltativo che impedisce al servizio ID visitatore di effettuare chiamate ad altri domini.
keywords: monitoraggio tra più domini;Servizio ID visitatore
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
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 205
ht-degree: 24%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

Flag booleano facoltativo che impedisce al servizio ID visitatore di effettuare chiamate ad altri domini.

**Sintassi:** ` `disableThirdPartyCalls: true false&grave;&grave; (l&#39;impostazione predefinita è `false`)

Quando `disableThirdPartyCalls: true`, il servizio ID visitatore non effettuerà chiamate ad altri domini.

**Finalità**

Questa variabile è progettata per i clienti con le seguenti esigenze:

* Per impedire che il Servizio ID visitatori effettui chiamate dalle loro pagine sicure e autenticate.
* I visitatori del sito devono disporre di un ECID.
* Le altre soluzioni CX Enterprise funzionano correttamente.

**Strategia di implementazione**

Poiché altre soluzioni CX Enterprise si basano sul MID, il servizio ID visitatore chiama Adobe per restituire e impostare questo ID. Se devi impedire al Servizio ID visitatore di effettuare chiamate da sezioni autenticate del sito web, puoi fare in modo che effettui le chiamate necessarie da pagine che non richiedono prima l’autenticazione. Dopo che il visitatore del sito ha un identificatore MID, puoi impostare `disableThirdPartyCalls= true` nel codice del servizio ID visitatore nelle sezioni autenticate del sito. Si presume in questo caso che almeno la maggior parte dei clienti accederà a una pagina di autenticazione prima di accedere alle parti protette del sito.

**Esempio di codice**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

