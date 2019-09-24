---
description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.
keywords: Servizio ID
seo-description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.
seo-title: Note sulla versione 2019
title: Note sulla versione 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 4532d09cc9b4d83fa62c13bd1adac7abdae222b1

---


# Note sulla versione 2019 {#release-notes}

Versioni future, aggiornamenti o modifiche al servizio Experience Cloud Identity.

## Note sulla versione 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Versioni future, aggiornamenti o modifiche al servizio [!DNL Experience Cloud] ID.

## Versione 4.4 {#version-4point4}

**Nuova funzionalità**

[Supporto di hashing SHA-256 per setCustomerIDs](/help/reference/hashing-support.md). Il servizio Experience Cloud ID (ECID) supporta l’algoritmo di hashing SHA-256 che consente di ricevere gli ID o indirizzi e-mail dei clienti e di inoltrare gli ID con hashing.

**Correzioni e miglioramenti**

* È stato effettuato un aggiornamento della configurazione per `cookieDomain`. La libreria ECID ora filtra la stringa vuota `cookieDomain` in `initConfig` e utilizza il dominio del cookie di livello principale, restituito dal metodo getDomain. (CORE-29223)
* È stato corretto un bug correlato a `getVisitorValues` in `localVisitor`. (CORE-31287)
* È stato corretto un bug a causa del quale si verificava un’incoerenza per il valore MCOPTOUT nel browser Safari, restituito dal metodo `getVisitorValue`. (CORE-29719)
* Abbiamo aggiornato la libreria Opt-in aggiungendo `optIn.off` per annullare l’iscrizione agli eventi.
* È stato corretto un bug correlato alla funzione setTimeout, che in alcuni siti dei clienti causava la violazione della CSP (Content Security Policy) da parte di `setTimeout`. (CORE-30623)

## Versione 4.3 {#version-4point3}

**Supporto per ITP 2.1**. Se un server di tracciamento è impostato in un CNAME di prima parte, viene inserito un nuovo cookie (s_ecid) con il valore ECID. La libreria ECID fa riferimento a tale valore in modo che l’ID venga mantenuto oltre il limite di 7 giorni. Consulta [Metodi della libreria ECID in ambito Safari ITP](/help/reference/ecid-library-methods.md).

**Correzione di bug nella configurazione di secureCookie.**

## Versione 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servizio Opt-in**. Opt-in è un'estensione di Experience Cloud ID (ECID) che consente di controllare se (e quali) librerie di Experience Cloud possono creare dei cookie sulle pagine Web per i visitatori. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Versione 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descrizione |
|---|---|
| Il flag`disableIdSyncs` non funziona quando viene passata una stringa. | Corretto. Ora i valori impostati sul `disableidSyncs` parametro per la `getInstance` funzione vengono rispettati. |
| iFrames di terze parti non ottiene ECID | Corretto ECID su Safari Mobile ed ECID in diversi iFrames che non funzionavano. |

