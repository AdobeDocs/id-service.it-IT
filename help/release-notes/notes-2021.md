---
description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.
keywords: Servizio ID
title: Note sulla versione 2021
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
source-git-commit: 52956b38c59f60507aaf236b152ce41fc1229d14
workflow-type: ht
source-wordcount: '103'
ht-degree: 100%

---

# Note sulla versione 2021 del servizio Experience Cloud Identity

Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.

## Visitor 5.3.0

I seguenti aggiornamenti sono stati inclusi nella versione di Visitor 5.3.0:

* È stato aggiornato l’algoritmo per generare l’ECID locale.
* Servizio Opt-in più recente con i flag `Secure` e `SameSite` per cookie di privacy.
* Correzione della patch per un problema del browser Firefox quando una pagina viene caricata in un iFrame secondario.

## Visitor 5.2.0

I seguenti aggiornamenti sono stati inclusi nella versione di Visitor 5.2.0:

* Questa versione introduce un evento `onReceiveEcid`, che viene chiamato quando un ECID viene ricevuto dal servizio Identity. Ad esempio:

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```
