---
description: nulle
keywords: ordine delle operazioni; Servizio ID
seo-description: nulle
seo-title: CNAME per raccolta dati e monitoraggio tra più domini
title: CNAME per raccolta dati e monitoraggio tra più domini
uuid: ba 42 c 822-b 677-4139-b 1 ed -4 d 98 d 3320 fd 0
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# CNAME per raccolta dati e monitoraggio tra più domini{#data-collection-cnames-and-cross-domain-tracking}

Se utilizzi un sito di accesso principale per l&#39;identificazione dei clienti prima che visitino altri domini, un CNAME consente il monitoraggio tra più domini nei browser che non accettano i cookie di terze parti (ad es. Safari).

Nei browser che accettano i cookie di terze parti, i cookie vengono configurati dai server di raccolta dati durante la richiesta dell&#39;ID visitatore. Questo cookie consente al servizio ID visitatore di restituire lo stesso ID visitatore Experience Cloud a tutti i domini configurati usando lo stesso ID organizzazione Experience Cloud.

Nei browser che rifiutano i cookie di terze parti, a ciascun dominio viene assegnato un nuovo ID visitatore Experience Cloud.

Il cookie demdex.net consente al servizio ID visitatore di offrire lo stesso livello di monitoraggio tra più domini del cookie s_vi di Analytics, che viene accettato in alcuni browser e utilizzato tra più domini, ma viene rifiutato da altri browser.

## CNAME per la raccolta dati {#section-48fd186d376a48079769d12c4bd9f317}

Quando il cookie di Analytics veniva impostato dal server di raccolta dati, molti clienti configuravano i record CNAME del server di raccolta dati durante l&#39;[implementazione dei cookie di prime parti](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/), in modo da evitare problemi con i browser che rifiutano i cookie di terze parti. Questo processo configura il dominio del server di raccolta dati in modo che corrisponda al dominio del sito Web, così il cookie dell&#39;ID visitatore viene impostato come cookie di prime parti.

Poiché il servizio ID visitatore imposta direttamente il cookie visitatore sul dominio del sito Web corrente usando JavaScript, questa configurazione non è più necessaria per impostare i cookie di prime parti.

I clienti con un&#39;unica proprietà Web (un solo dominio) possono effettuare la migrazione dai CNAME per la raccolta dati e utilizzare i propri nomi host di raccolta dati (`omtrdc.net` `2o7.net`o).

Usare un CNAME per la raccolta dati consente anche di monitorare i visitatori tra un dominio di destinazione principale e altri domini nei browser che non accettano i cookie di terze parti. I clienti che dispongono di più proprietà Web (più domini) possono trarre benefici dall&#39;utilizzo di un CNAME per la raccolta dati. La seguente sezione spiega in che modo funziona il monitoraggio dei visitatori tra più domini.

## Modalità di attivazione del monitoraggio tra più domini da parte dei CNAME {#section-78925af798e24917b9abed79de290ad9}

Poiché in Apple Safari e altri browser i cookie di prime parti possono essere usati in un contesto di terze parti, un CNAME consente di monitorare i clienti tra un dominio principale e altri domini che utilizzano lo stesso server di monitoraggio.

For example, you have a primary site at `mymainsite.com`. You configured the CNAME record to point to your secure data collection server: `smetrics.mymainsite.com`.

When a user visits `mymainsite.com`, the ID service cookie is set by the data collection server. This is allowed since the domain of the data collection server matches the domain of the website, and is what is known as using a cookie in a *first-party context*, or just a *first-party cookie*.

If you are also using this same data collection server on other sites (for example, `myothersiteA.com`, and `myothersiteB.com`), and a visitor later visits these sites, the cookie that was set during the visit to `mymainsite.com` is sent in the HTTPS request to the data collection server (remember that browsers send all cookies for a domain with all HTTPS requests to that domain, even if the domain doesn&#39;t match the domain of the current website). This is what is known as using a cookie in a *third-party context*, or just a *third-party cookie*, and it enables the same visitor ID to be used on these other domains. I browser gestiscono i cookie in contesti di terze parti in modo diverso rispetto ai cookie di prime parti.

*Nota: Safari blocca tutti i cookie nel contesto di terze parti, a prescindere da come sono impostati.*

Di conseguenza, il dominio di raccolta deve essere un dominio visitato regolarmente, in modo che i visitatori possano essere identificati in tutti i domini. If there is no *common* domain to use for the data collection domain, there is no cross-domain benefit to maintaining a CNAME for the data collection domain. Se il sito di accesso principale non viene visitato per primo, i visitatori vengono identificati in modo diverso negli altri siti rispetto al sito principale.

## Attivazione del supporto per i CNAME con il servizio Experience Cloud ID {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Data collection server CNAME support is enabled by setting the `visitor.marketingCloudServerSecure` variables.
