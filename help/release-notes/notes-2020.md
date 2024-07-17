---
description: Versioni future, aggiornamenti o modifiche a Experience Cloud Identity Service.
keywords: Servizio ID
title: Note sulla versione 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 99%

---

# Note sulla versione 2020 di Experience Cloud {#release-notes}

Versioni future, aggiornamenti o modifiche a Experience Cloud Identity Service.

## Versione 5.1.1

* Correzione della patch per l’impostazione del cookie AMCV con `SameSite=None` quando VisitorJS viene caricato in un iFrame.

## Versione 5.1.0

* Aggiunta della configurazione `sameSiteCookie` per specificare l’attributo `SameSite` del cookie AMCV. La configurazione supporta i seguenti valori per l’attributo `SameSite`:
   * `Strict`
   * `Lax`
   * `None`

Per ulteriori informazioni su questi valori di attributo, visita [web.dev](https://web.dev/samesite-cookies-explained/) e [Aggiornamenti SameSite per i progetti Chromium](https://www.chromium.org/updates/same-site/).

## Versione 5.0.1

* Correzione della patch per includere il flag `d_cf` quando una nuova stringa di consenso IAB viene inviata agli Edge di raccolta dati di Adobe.

## Versione 5.0.0

* Versione 5.0.0 di Visitor con supporto per `IAB 2.0`.

## Versione 4.6

* È stato impostato il flag `loadSSL` per impostazione predefinita. Tutte le chiamate a Identity Service sono impostate su `https` per impostazione predefinita. I clienti possono impostarlo su falso se desiderano chiamare i servizi Identity Service su HTTP dalle proprie pagine `non-ssl`.
* È stata aggiornata la funzione utilizzata per rilevare la versione di `Internet-Explorer (IE)`, per risolvere un problema segnalato da `ESLint`.
È stato risolto un problema di prestazioni in `Internet-Explorer (IE) 11`, nel caso di `pre-approval` del consenso esplicito per l’ECID e successivo aggiornamento.

## Versione 4.5

* A partire dalla versione 4.5, ECID rifiuterà gli ID vuoti inviati al metodo `setCustomerIDs`.
* È stato risolto un problema che si verificava quando l’opzione di consenso era configurata come `doesOptInApply=false` e `isIabContext=true`.

Consulta [Note sulla versione di Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=it) per le note sulle versioni mensili di tutti i prodotti.
