---
description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud ID.
keywords: Servizio ID
seo-description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud ID.
seo-title: Note sulla versione 2019
title: Note sulla versione 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Note sulla versione 2019 {#release-notes}

Versioni future, aggiornamenti o modifiche al servizio Experience Cloud ID.

## Note sulla versione 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Versioni future, aggiornamenti o modifiche al servizio [!DNL Experience Cloud] ID.

## Versione 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servizio Opt-in**. Opt-in è un&#39;estensione di [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/it_IT/mcvid/) che consente di controllare se (e quali) librerie di Experience Cloud possono creare dei cookie sulle pagine Web per i visitatori. Usando [Launch](https://docs.adobelaunch.com/), è possibile semplificare la raccolta dei consensi dei visitatori per la soluzione Experience Cloud consentendo ad Analytics, Target, Audience Manager e a tutte le altre soluzioni Experience Cloud di partecipare al sistema di gestione dei consensi.

## Versione 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descrizione |
|---|---|
| Il flag `disableIdSyncs` non funziona quando viene passata una stringa. | Corretto. Ora i valori impostati sul `disableidSyncs` parametro per la `getInstance` funzione vengono rispettati. |
| iFrames di terze parti non ottiene ECID | Corretto ECID su Safari Mobile ed ECID in diversi iFrames che non funzionavano. |

