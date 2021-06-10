---
description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.
keywords: Servizio ID
title: Note sulla versione 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 100%

---

# Note sulla versione di Experience Cloud - 2020 {#release-notes}

Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity (ECID).

## Versione 4.6

* È stato impostato il flag `loadSSL` per impostazione predefinita. Tutte le chiamate al servizio identità sono impostate su `https` per impostazione predefinita.  I clienti possono impostarlo su false se desiderano chiamare i servizi identità su HTTP dalle proprie `non-ssl` pagine.
* È stata aggiornata la funzione utilizzata per rilevare la versione di `Internet-Explorer (IE)`, per risolvere un problema segnalato da `ESLint`.
È stato risolto un problema di prestazioni in `Internet-Explorer (IE) 11`, nel caso di `pre-approval` del consenso esplicito per l’ECID e successivo aggiornamento.

## Versione 4.5

* A partire dalla versione 4.5, ECID rifiuterà gli ID vuoti inviati al metodo `setCustomerIDs`.
* È stato risolto un problema che si verificava quando l’opzione di consenso era configurata come `doesOptInApply=false` e `isIabContext=true`.

Consulta [Note sulla versione di Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=it) per le note sulle versioni mensili di tutti i prodotti.
