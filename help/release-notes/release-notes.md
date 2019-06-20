---
description: Rilasci di funzioni, aggiornamenti o modifiche al servizio Experience Cloud ID.
keywords: Servizio ID
seo-description: Rilasci di funzioni, aggiornamenti o modifiche al servizio Experience Cloud ID.
seo-title: Note sulla versione 2019
title: Note sulla versione 2019
uuid: a 5 a 59410-7 f 85-48 f 9-a 30 a-fef 1 c 2 e 2 b 558
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Note sulla versione 2019 {#release-notes}

Rilasci di funzioni, aggiornamenti o modifiche al servizio Experience Cloud ID.

## Note sulla versione 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Versioni future, aggiornamenti o modifiche al servizio [!DNL Experience Cloud] ID.

## Versione 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servizio Opt-in**. L&#39;opzione Consenso è un&#39;estensione dell&#39;Experience Cloud ID (ECID) che consente di controllare se (e quali) le librerie Experience Cloud possono creare cookie sulle pagine Web per i visitatori. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Versione 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descrizione |
|---|---|
| Il flag `disableIdSyncs` non funziona quando viene passata una stringa. | Problema risolto. Values set on `disableidSyncs` parameter for `getInstance` function are now being honored. |
| iFrames di terze parti non ottiene ECID | Corretto ECID su Safari Mobile ed ECID in diversi iFrames che non funzionavano. |

