---
description: Panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l'assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.
keywords: Servizio ID
seo-description: Panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l'assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.
seo-title: Richiesta e impostazione degli ID da parte del servizio Experience Cloud Identity
title: Richiesta e impostazione degli ID da parte del servizio Experience Cloud Identity
uuid: ff7f5b7e-e959-4391-b75c-b7a36286e0ea
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Richiesta e impostazione degli ID da parte del servizio Experience Cloud Identity{#how-the-experience-cloud-id-service-requests-and-sets-ids}

Panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l'assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.

>[!NOTE]
>
>Se non sai in che modo il servizio Experience Cloud Identity crea l’ID visitatore, consulta la sezione [Experience Cloud](../introduction/cookies.md).

**Suggerimento:** guarda anche il [video del servizio ID sul monitoraggio tra più domini](https://helpx.adobe.com/it/marketing-cloud-core/kb/MCID/CrossDomain.html).

## Richiesta di un Experience Cloud ID {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

Nei seguenti esempi viene spiegato in che modo il servizio ID richiede e riceve l'ID visitatore di Experience Cloud. Negli esempi vengono utilizzate due società fittizie, l'Azienda alimentare e l'Azienda sportiva, per illustrare il flusso dei dati per le richieste e le risposte relative agli ID. Per ciascuna società è presente un ID organizzazione Experience Cloud univoco e ciascuna di esse ha implementato il codice del servizio ID su tutti i propri siti. Questi casi d'uso descrivono i flussi di dati per un'implementazione generica del servizio ID, senza ID Analytics legacy o browser che bloccano i cookie di terze parti.

![](assets/sample_sites.png)

**Prima richiesta**

In questo esempio, un nuovo visitatore accede al sito pizzeria gestito dalla società Azienda alimentare. La società Azienda alimentare ha implementato il codice del servizio ID sul sito Web pizzeria. Quando il sito pizzeria viene caricato, il codice del servizio ID verifica il cookie AMCV nel dominio pizza.

* Se il cookie AMCV è impostato, il visitatore del sito dispone di un Experience Cloud ID. In questo caso, il cookie monitora il visitatore e condivide i dati con altre soluzioni Experience Cloud.
* Se il cookie AMCV non è impostato, il codice del servizio ID chiama un [server di raccolta dati regionale](https://marketing.adobe.com/resources/help/en_US/aam/?f=c_compcollect.html) (DCS) in `dpm.demdex.net/id` (vedi anche, [Informazioni sulle chiamate a Demdex Domain](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)). La chiamata include l'ID organizzazione della società Azienda alimentare. L'ID organizzazione viene impostato nella funzione `Visitor.getInstance` del codice del servizio ID.

![](assets/request1.png)

**Prima risposta**

All'interno della risposta, il DCS restituisce l'[!DNL Experience Cloud] ID (MID) e il cookie demdex. Il codice del servizio ID scrive il valore MID nel cookie AMCV. Ad esempio, il DCS restituisce il MID 1234. Il viene memorizzato nel cookie AMCV come `mid|1234`mid| e viene impostato nel dominio pizzeria di prime parti. Anche il cookie demdex contiene un ID univoco (ad esempio 5678). Questo cookie viene impostato nel dominio demdex.net di terze parti, diverso dal dominio pizzeria.

![](assets/response1.png)

Come spiegato nel prossimo esempio, l'ID demdex e l'ID organizzazione consentono al servizio ID di creare e restituire il MID corretto quando i visitatori si spostano in un altro sito appartenente alla società Azienda alimentare.

## Richieste e risposte intersito {#section-15ea880453af467abd2874b8b4ed6ee9}

In questo esempio, il visitatore della società Azienda alimentare passa dal sito pizzeria al sito taqueria. La società Azienda alimentare ha implementato il codice del servizio ID sul sito Web taqueria. Il visitatore non è mai stato nel sito Web taqueria.

Di conseguenza, sul sito taqueria non è presente il cookie AMCV. Pertanto, il servizio ID non può utilizzare il cookie AMCV impostato sul sito pizzeria, perché è specifico per il dominio pizzeria. Il servizio ID deve quindi chiamare il DCS per verificare e richiedere un ID visitatore. In tal caso, la chiamata al DCS comprende l'ID organizzazione della società Azienda alimentare *e* l'ID demdex. L'ID demdex viene prelevato dal sito pizzeria e memorizzato come cookie di terze parti nel dominio demdex.net.

![](assets/request2.png)

Quando il DCS riceve l'ID organizzazione e l'ID demdex, crea e restituisce il MID corretto per il visitatore del sito. Poiché il viene derivato matematicamente dall'ID organizzazione e dall'ID demdex, il cookie AMCV contiene il valore MID, `mid = 1234`mid = .

![](assets/response2.png)

## Richieste di ID da altri siti {#section-ba9a929e50d64b0aba080630fd83b6f1}

In questo esempio, il visitatore abbandona i siti dell'azienda Azienda alimentare e accede al sito campo da calcio di proprietà della società Azienda sportiva. Quando il visitatore accede al sito campo da calcio, la verifica e la richiesta di ID vengono effettuate nello stesso modo descritto negli esempi precedenti. Tuttavia, poiché la società Azienda sportiva dispone di un proprio ID organizzazione, il servizio ID restituisce un MID diverso. Il nuovo MID è univoco per i domini controllati dalla società Azienda sportiva e consente alla società di monitorare e condividere i dati del visitatore tra le soluzioni [!DNL Experience Cloud]. L'ID demdex del visitatore rimane invariato, perché è contenuto in un cookie di terze parti e viene mantenuto nei diversi domini.

![](assets/req_resp.png)

