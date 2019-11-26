---
description: nulle
keywords: order of operations;ID Service
seo-description: nulle
seo-title: CNAME per raccolta dati e monitoraggio tra più domini
title: CNAME per raccolta dati e monitoraggio tra più domini
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 989b5f537848a7506a96e2eac17409f8b0307217

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

Analytics utilizzerà l'ID 1st party a meno che non siano abilitati gli ID di terze parti, dove i browser lo consentono. L'ID di terze parti è preceduto dal nome del cliente, in modo che quest'ultimo non possa combinare dati con un altro cliente in Analytics.

## Domini Analytics legacy

Prima dell’avvio del servizio ID visitatore Adobe, molti clienti utilizzavano i domini di analisi nativi per impostare i cookie ID. Questi includono `omtrdc.net`, `2o7.net` o un dominio CNAME. `omtrdc.net`, `2o7.net`, in alcuni casi un dominio CNAME è stato utilizzato per memorizzare cookie di terze parti. I cookie impostati in questo modo sono stati limitati a un singolo cliente in modo che i clienti non potessero combinare i propri dati con i dati di altri clienti. Domini CNAMED di terze parti, a volte chiamati amichevoli domini di terze parti sono stati utilizzati quando i clienti desiderano monitorare gli utenti tra siti che possiedono (ad esempio.com, example.co.jp). Questo metodo o l’utilizzo di CNAME per supportare domini di terze parti descrittivi è obsoleto per consentire il servizio ID visitatore più affidabile e consapevole della privacy. I clienti devono passare al servizio ID visitatore con un CNAME per dominio non appena possibile.

## Immetti la tua identità

Se il cliente sceglie di ignorare completamente il sistema di identificazione di Adobe e implementare un proprio ID [visitatore](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)personalizzato. Ci sono alcune cose di cui essere consapevoli se si sceglie questo percorso.

- Sarà necessario implementare il rifiuto e adeguati controlli sulla privacy
- L'ID verrà applicato solo ad Analytics
- Sei responsabile della persistenza di tale ID

## CNAME di raccolta dati

Adobe consiglia ancora di utilizzare un CNAME insieme al servizio ID visitatore. Questo consente all’ID visitatore di prima parte di rimanere inalterato utilizzando i cookie HTTP, il che rende i cookie più duraturi.

## OPTOUT

Adobe fornisce ai clienti le API per condividere i segnali di rifiuto con i nostri sistemi, in modo che i clienti possano a loro volta consentire agli utenti di non partecipare al tracciamento. Forniamo istruzioni dettagliate su come il cliente può implementare i controlli appropriati per supportare la scelta degli utenti; l'API [di](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) rifiuto o le opzioni per [impedire l'attivazione](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md) dei cookie fino a quando non viene ottenuto il consenso

## Attivazione del supporto per i CNAME con il servizio Experience Cloud Identity {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Il supporto del CNAME del server di raccolta dati è [abilitato per la configurazione di un CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) e l'impostazione della `visitor.marketingCloudServerSecure` variabile in Experience Cloud Identity Service e `s.trackingServerSecure` in AppMeasurement.
