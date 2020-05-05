---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: CNAME per raccolta dati e monitoraggio tra più domini
title: CNAME per raccolta dati e monitoraggio tra più domini
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 9fe63cf3983a2ed6642837b02a3c3441ef745d70

---


# CNAME per raccolta dati e monitoraggio tra più domini {#data-collection-cnames-and-cross-domain-tracking}

Se hai un sito di accesso principale in cui i clienti possono essere identificati prima che visitino altri domini, allora un CNAME può abilitare il tracciamento tra domini nei browser che non accettano i cookie di terze parti (come Safari).

Nei browser che accettano i cookie di terze parti, un cookie viene impostato dai server di raccolta dati durante la richiesta di un ID visitatore. Questo cookie consente al servizio ID visitatore di restituire lo stesso ID visitatore Experience Cloud a tutti i domini configurati usando lo stesso ID organizzazione Experience Cloud.

Nei browser che rifiutano i cookie di terze parti, a ciascun dominio viene assegnato un nuovo ID visitatore Experience Cloud.

Il cookie demdex.net consente al servizio ID visitatore di offrire lo stesso livello di monitoraggio tra più domini del cookie s_vi di Analytics, che viene accettato in alcuni browser e utilizzato tra più domini, ma viene rifiutato da altri browser.

## CNAME per la raccolta dati {#section-48fd186d376a48079769d12c4bd9f317}

When the Analytics cookie was set by the data collection server, many customers have configured data collection server CNAME records as part of a [first-party cookie implementation](https://docs.adobe.com/content/help/it-IT/core-services/interface/ec-cookies/cookies-first-party.html) to avoid issues with browsers that reject third-party cookies. Questo processo configura il dominio del server di raccolta dati in modo che corrisponda al dominio del sito Web, in modo che il cookie dell’ID visitatore sia impostato come cookie di prime parti.

Poiché il servizio ID visitatore imposta il cookie visitatore direttamente sul dominio del sito Web corrente utilizzando JavaScript, questa configurazione non è più necessaria per impostare i cookie di prime parti.

I clienti con un&#39;unica proprietà Web (un solo dominio) possono effettuare la migrazione dai CNAME per la raccolta dati e utilizzare i propri nomi host di raccolta dati (`omtrdc.net` o `2o7.net`).

Tuttavia, esiste un ulteriore vantaggio nell’utilizzo di un CNAME per la raccolta dati che consente di monitorare i visitatori tra un dominio di destinazione principale e altri domini nei browser che non accettano i cookie di terze parti. I clienti che dispongono di più proprietà Web (più domini) potrebbero trarre vantaggio dalla gestione di un CNAME di raccolta dati. La sezione seguente spiega come funziona il tracciamento dei visitatori tra domini.

## Monitoraggio tra domini {#section-78925af798e24917b9abed79de290ad9}

Il servizio ID visitatore utilizza demdex.net come dominio per il monitoraggio dei visitatori tra domini diversi (ma all’interno della stessa società proprietaria) se la privacy dell’utente e le impostazioni del browser lo consentono.

Un CNAME non offre ulteriori vantaggi tra domini diversi. Ad esempio, il tuo sito principale è `mymainsite.com`. Hai configurato il record CNAME in modo che punti al server di raccolta dati protetto: `smetrics.mymainsite.com`.

Se un utente accede a `mymainsite.com`, il cookie del servizio ID viene impostato dal server di raccolta dati. Ciò è possibile perché il dominio del server di raccolta dei dati corrisponde a quello del sito Web: in tal caso si parla di utilizzo di un cookie nel *contesto di prime parti*, o più semplicemente di *cookie di prime parti*.

Se utilizzi questo stesso server di raccolta dati su altri siti (ad esempio, `myothersiteB.com` e `myothersiteA.com`), e un visitatore accede in seguito a tali siti il cookie impostato durante l&#39;accesso a `mymainsite.com` viene inviato nella richiesta HTTPS al server di raccolta dati (i browser inviano tutti i cookie di un dominio con tutte le richieste HTTPS a tale dominio, anche se il dominio non corrisponde a quello del sito Web corrente). Questo è ciò che viene definito utilizzo di un cookie in un contesto *di* terze parti, o semplicemente di un cookie *di* terze parti, anche se si utilizza un CNAME. Adobe consiglia un CNAME per ciascun dominio univoco.

*Nota: Safari blocca tutti i cookie nel contesto di terze parti, a prescindere da come sono impostati.*

## Attivazione del supporto per i CNAME con il servizio Experience Cloud Identity {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Il supporto per i CNAME del server di raccolta dati può essere attivato impostando le variabili `visitor.marketingCloudServerSecure`.
