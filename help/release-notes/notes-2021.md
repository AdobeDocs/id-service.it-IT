---
description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.
keywords: Servizio ID
title: Note sulla versione 2021
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 25%

---

# Note sulla versione del servizio Experience Cloud Identity - 2021

Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.

## Visitatore 5.3.0

I seguenti aggiornamenti sono stati inclusi nella versione di Visitor 5.3.0:

* È stato aggiornato l’algoritmo per generare ECID locale.
* Opt-in più recente con `Secure` e `SameSite` flag per cookie di privacy.
* Correzione della patch per un problema del browser Firefox quando una pagina viene caricata in un iFrame figlio.

## Visitatore 5.2.0

I seguenti aggiornamenti sono stati inclusi nella versione di Visitor 5.2.0:

* Questa versione introduce un evento `onRecieveEcid`, che viene chiamato quando un ECID viene ricevuto dal servizio Identity. Ad esempio:

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
