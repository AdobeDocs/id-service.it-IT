---
description: Flag booleano opzionale che impedisce al servizio ID di effettuare chiamate ad altri domini.
keywords: cross domain tracking;ID Service
seo-description: Flag booleano opzionale che impedisce al servizio ID di effettuare chiamate ad altri domini.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 68%

---


# disableThirdPartyCalls{#disablethirdpartycalls}

Flag booleano opzionale che impedisce al servizio ID di effettuare chiamate ad altri domini.

**Sintassi:** ` `disableThirdPartyCalls: true|false`` (l&#39;impostazione predefinita è `false`)

Quando `disableThirdPartyCalls: true`, il servizio ID non effettua chiamate ad altri domini.

**Finalità**

Questa variabile è progettata per i clienti che hanno bisogno di:

* Per impedire che il servizio ID effettui chiamate dalle loro pagine sicure e autenticate.
* Assegnare ai visitatori del sito un ID Experience Cloud  (MID).
* Le altre soluzioni  Experience Cloud per funzionare correttamente.

**Strategia di implementazione**

Poiché altre soluzioni Experience Cloud usano l&#39;identificatore MID, il servizio ID chiama Adobe per restituire e impostare questo ID. Per evitare che il servizio ID effettui tali chiamate da sezioni autenticate del sito, puoi fare sì che le chiamate necessarie vengano effettuate da pagine che non richiedono la preventiva autenticazione. Una volta che un visitatore ha un suo identificatore MID, puoi impostare `disableThirdPartyCalls= true` nel codice del servizio ID sulle sezioni autenticate del sito. Il presupposto è che la maggior parte, se non tutti, dei clienti accederà a una pagina di autenticazione prima di accedere alle parti protette del sito.

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

