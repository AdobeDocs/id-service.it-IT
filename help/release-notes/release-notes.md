---
description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.
keywords: ID Service
seo-description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.
seo-title: Note sulla versione 2020
title: Note sulla versione 2020
translation-type: tm+mt
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Note sulla versione di Experience Cloud - 2020 {#release-notes}

Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity (ECID).

## Versione 4.6

* Il `loadSSL` flag è stato impostato per impostazione predefinita. Per impostazione predefinita, tutte le chiamate al servizio identità sono attivate `https` .  I clienti possono impostarlo su false se desiderano chiamare i servizi identità su http dalle proprie `non-ssl` pagine.
* Aggiornamento della funzione utilizzata per rilevare `Internet-Explorer (IE)` la versione, per risolvere un problema segnalato da `ESLint`.
È stato corretto un problema di prestazioni in `Internet-Explorer (IE) 11` caso di consenso esplicito per l’ECID `pre-approval` e successivo aggiornamento.

## Versione 4.5

* A partire dalla versione 4.5, ECID rifiuterà gli ID vuoti inviati al metodo `setCustomerIDs`. 
* È stato risolto un problema che si verificava quando l’opzione di consenso era configurata come `doesOptInApply=false` e `isIabContext=true`.
