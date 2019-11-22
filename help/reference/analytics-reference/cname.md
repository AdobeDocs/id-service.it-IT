---
description: nulle
keywords: order of operations;ID Service
seo-description: nulle
seo-title: CNAME per raccolta dati e monitoraggio tra più domini
title: CNAME per raccolta dati e monitoraggio tra più domini
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 588c4b29ebd3cccea4f2ab032f69a4b6c6e97f2a

---


# Raccolta dati e identità{#data-collection-and-identity}

Nell'analisi sono disponibili tre modi per identificare i visitatori.

- Utilizzo del servizio ID [visitatore](https://docs.adobe.com/content/help/en/id-service/using/home.md)
- Utilizza l’ID visitatore Analytics [legacy](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-overview.md)
- Fornire la propria identità

## Utilizzo del Servizio ID visitatore{#using-the-visitor-id-service}

Il servizio ID visitatore è il metodo consigliato per identificare i visitatori. Si basa su due componenti

- ID 1st party - ID di prime parti che può essere utilizzato per misurare i visitatori del tuo sito Web. L’ID viene memorizzato nel primo ID di parametro, sia in un cookie lato client che in un cookie lato server (con un CNAME).
- ID di terze parti (facoltativo) - Un ID di terze parti separato memorizzato in demdex.net che può essere utilizzato per misurare i visitatori su più domini (ad esempio, example.com e example.net)

Analytics utilizzerà sempre l'ID di prime parti e se l'ID di terze parti è abilitato e presente, l'ID di prime parti in ogni sito sarà sempre lo stesso. Tuttavia, se l'ID di terze parti è disabilitato, dalle impostazioni o perché il browser blocca i cookie di terze parti, non è possibile collegare il traffico sui due siti.

## Domini Analytics legacy

Prima del lancio del servizio ID visitatore, molti anni fa, molti clienti utilizzavano i domini di analisi nativi per impostare i cookie ID. Questi includono `omtrdc.net`, `2o7.net` o un dominio CNAME. `omtrdc.net`, `2o7.net` e in alcuni casi un dominio CNAME d viene utilizzato per memorizzare cookie di terze parti. I cookie impostati in questo modo sono sempre stati limitati a un singolo cliente in modo che i clienti non potessero combinare i propri dati tra le aziende. Domini di terze parti CNAMED, a volte denominati amichevoli domini di terze parti, vengono utilizzati solo quando i clienti desiderano monitorare gli utenti tra siti che possiedono (ad esempio.com, example.co.jp). Questo metodo è obsoleto per consentire un servizio ID visitatore più affidabile e consapevole della privacy. I clienti devono passare al servizio ID visitatore con un CNAME per dominio non appena possibile.

## Immetti la tua identità

Se il cliente sceglie di ignorare completamente il sistema di identificazione di Adobe e implementare un proprio ID [visitatore](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)personalizzato. Ci sono alcune cose di cui essere consapevoli se si sceglie questo percorso.

- Sarà necessario implementare il rifiuto e adeguati controlli sulla privacy
- L'ID verrà applicato solo ad Analytics
- Sei responsabile della persistenza di tale ID

## CNAME di raccolta dati

Adobe consiglia ancora di utilizzare un CNAME insieme al servizio ID visitatore. Questo consente all’ID visitatore di prima parte di rimanere inalterato utilizzando i cookie HTTP, il che rende i cookie più duraturi.

## Rinunce

Adobe offre alle API la possibilità di condividere i segnali di rifiuto con i nostri sistemi in modo da consentire agli utenti di non partecipare al tracciamento. Forniamo istruzioni dettagliate sulla [rinuncia](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) e la [rinuncia](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md)

## Attivazione del supporto per i CNAME con il servizio Experience Cloud Identity {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Il supporto del CNAME del server di raccolta dati è [abilitato per la configurazione di un CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) e l'impostazione della `visitor.marketingCloudServerSecure` variabile in Experience Cloud Identity Service e `s.trackingServerSecure` in AppMeasurement.
