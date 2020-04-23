---
description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.
keywords: ID Service
seo-description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.
seo-title: Note sulla versione 2020
title: Note sulla versione 2020
translation-type: ht
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Note sulla versione di Experience Cloud - 2020 {#release-notes}

Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity (ECID).

## Versione 4.6

* È stato impostato il flag `loadSSL` per impostazione predefinita. Tutte le chiamate al servizio identità sono impostate su `https` per impostazione predefinita. I clienti possono impostarlo su false se desiderano chiamare i servizi identità su HTTP dalle proprie `non-ssl` pagine.
* È stata aggiornata la funzione utilizzata per rilevare la versione di `Internet-Explorer (IE)`, per risolvere un problema segnalato da `ESLint`.
È stato risolto un problema di prestazioni in `Internet-Explorer (IE) 11`, nel caso di `pre-approval` del consenso esplicito per l’ECID e successivo aggiornamento.

## Versione 4.5

* A partire dalla versione 4.5, ECID rifiuterà gli ID vuoti inviati al metodo `setCustomerIDs`.
* È stato risolto un problema che si verificava quando l’opzione di consenso era configurata come `doesOptInApply=false` e `isIabContext=true`.
