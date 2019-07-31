---
description: Rilasci di funzioni, aggiornamenti o modifiche al servizio Experience Cloud Identity.
keywords: Servizio ID
seo-description: Rilasci di funzioni, aggiornamenti o modifiche al servizio Experience Cloud Identity.
seo-title: Note sulla versione 2019
title: Note sulla versione 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 4532d09cc9b4d83fa62c13bd1adac7abdae222b1

---


# Note sulla versione 2019 {#release-notes}

Rilasci di funzioni, aggiornamenti o modifiche al servizio Experience Cloud Identity.

## Note sulla versione 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Versioni future, aggiornamenti o modifiche al servizio [!DNL Experience Cloud] ID.

## Versione 4.4 {#version-4point4}

**Nuova funzionalità**

[SHA 256 Hashing Support for setcustomerids](/help/reference/hashing-support.md). Il servizio Experience Cloud ID (ECID) supporta l'algoritmo di hash SHA -256 che consente di trasmettere ID cliente o indirizzi e-mail e di trasmettere gli ID con hash.

**Correzioni, miglioramenti, miglioramenti**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method. (CORE-29223)
* We fixed a bug related to `getVisitorValues` in `localVisitor`. (CORE-31287)
* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method. (CORE-29719)
* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites. (CORE-30623)

## Versione 4.3 {#version-4point3}

**Supporto per ITP 2.1**. Se un server di monitoraggio è impostato in un CNAME di prima parte, viene inserito un nuovo cookie (s_ ecid) con il valore ECID. La libreria ECID fa riferimento al valore per mantenere l'ID oltre i 7 giorni. See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**Correzione di bug per configurazione securecookie.**

## Versione 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servizio Opt-in**. L'opzione Consenso è un'estensione dell'Experience Cloud ID (ECID) che consente di controllare se (e quali) le librerie Experience Cloud possono creare cookie sulle pagine Web per i visitatori. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Versione 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descrizione |
|---|---|
| Il flag `disableIdSyncs` non funziona quando viene passata una stringa. | Corretto. Ora i valori impostati sul `disableidSyncs` parametro per la `getInstance` funzione vengono rispettati. |
| iFrames di terze parti non ottiene ECID | Corretto ECID su Safari Mobile ed ECID in diversi iFrames che non funzionavano. |

