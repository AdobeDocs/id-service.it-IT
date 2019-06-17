---
description: nulle
keywords: ordine delle operazioni; Servizio ID
seo-description: nulle
seo-title: CNAME per raccolta dati e monitoraggio tra più domini
title: CNAME per raccolta dati e monitoraggio tra più domini
uuid: ba 42 c 822-b 677-4139-b 1 ed -4 d 98 d 3320 fd 0
translation-type: tm+mt
source-git-commit: 337e7eef2cce8c0bc827ec04833ad0d14ee9c89a

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

Ad esempio, è presente `mymainsite.com`un sito principale. Hai configurato il record CNAME in modo che punti al server di raccolta dati protetto: `smetrics.mymainsite.com`.

Quando un utente visita `mymainsite.com`, il cookie del servizio ID viene impostato dal server di raccolta dati. Questo è consentito perché il dominio del server di raccolta dati corrisponde al dominio del sito Web ed è il cosiddetto utilizzo di un cookie in un contesto *di prime parti*, o semplicemente di *cookie first-party*.

Se utilizzi anche lo stesso server di raccolta dati su altri siti (ad esempio, `myothersiteA.com`e `myothersiteB.com`) e un visitatore visita successivamente questi siti, il cookie impostato durante l&#39;accesso a `mymainsite.com` viene inviato nella richiesta HTTPS al server di raccolta dati (ricorda che i browser inviano tutti i cookie per un dominio con tutte le richieste HTTPS a quel dominio, anche se il dominio non corrisponde al dominio del sito Web corrente). Si parla di utilizzo di un cookie in un contesto *di terze parti*, o semplicemente di cookie *di terze parti*, e consente l&#39;utilizzo dello stesso ID visitatore negli altri domini. I browser gestiscono i cookie in contesti di terze parti in modo diverso rispetto ai cookie di prime parti.

*Nota: Safari blocca tutti i cookie nel contesto di terze parti, a prescindere da come sono impostati.*

Di conseguenza, il dominio di raccolta deve essere un dominio visitato regolarmente, in modo che i visitatori possano essere identificati in tutti i domini. Se non esiste un dominio *comune* da utilizzare per il dominio di raccolta dati, non esiste alcun vantaggio a livello multidominio che consenta di mantenere un CNAME per il dominio di raccolta dati. Se il sito di accesso principale non viene visitato per primo, i visitatori vengono identificati in modo diverso negli altri siti rispetto al sito principale.

## Attivazione del supporto per i CNAME con il servizio Experience Cloud ID {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Il supporto per CNAME del server di raccolta dati è abilitato impostando le `visitor.marketingCloudServerSecure` variabili.
