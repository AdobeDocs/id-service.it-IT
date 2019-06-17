---
description: Panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l'assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.
keywords: Servizio ID
seo-description: Panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l'assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.
seo-title: Richiesta e impostazione degli ID da parte del servizio Experience Cloud ID
title: Richiesta e impostazione degli ID da parte del servizio Experience Cloud ID
uuid: ff 7 f 5 b 7 e-e 959-4391-b 75 c-b 7 a 36286 e 0 ea
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Richiesta e impostazione degli ID da parte del servizio Experience Cloud ID{#how-the-experience-cloud-id-service-requests-and-sets-ids}

Panoramica del processo di richiesta degli ID e di risposta. Questi esempi descrivono l&#39;assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti Experience Cloud con i propri ID organizzazione.

>[!NOTE]
>
>Se non sai in che modo il servizio Experience Cloud ID crea l&#39;ID visitatore, consulta [Experience Cloud](../mcvid-introduction/mcvid-cookies.md).

**Suggerimento:** consulta anche il [ video sul monitoraggio interdominio del servizio ID](https://helpx.adobe.com/marketing-cloud-core/kb/MCID/CrossDomain.html).

## Richiesta di un Experience Cloud ID {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

Nei seguenti esempi viene spiegato in che modo il servizio ID richiede e riceve l&#39;ID visitatore di Experience Cloud. Questi esempi utilizzano due società fittizie, la società Azienda alimentare e la Società Azienda sportiva, per dimostrare i flussi di dati per richieste e risposte ID. Per ciascuna società è presente un ID organizzazione Experience Cloud univoco e ciascuna di esse ha implementato il codice del servizio ID su tutti i propri siti. Questi casi d&#39;uso descrivono i flussi di dati per un&#39;implementazione generica del servizio ID, senza ID Analytics legacy o browser che bloccano i cookie di terze parti.

![](assets/sample_sites.png)

**Prima richiesta**

In questo esempio, un nuovo visitatore accede al sito pizzeria gestito dalla società Azienda alimentare. La società Azienda alimentare ha implementato il codice del servizio ID sul sito Web pizzeria. Quando il sito pizzeria viene caricato, il codice del servizio ID verifica il cookie AMCV nel dominio pizza.

* Se il cookie AMCV è impostato, il visitatore del sito dispone di un Experience Cloud ID. In questo caso, il cookie monitora il visitatore e condivide i dati con altre soluzioni Experience Cloud.
* Se il cookie AMCV non è impostato, il codice del servizio ID effettua una chiamata a un [server di raccolta dati](https://marketing.adobe.com/resources/help/en_US/aam/?f=c_compcollect.html) (DCS) locale su `dpm.demdex.net/id` (vedi anche [Informazioni sulle chiamate al dominio demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)). La chiamata include l&#39;ID organizzazione della società Azienda alimentare. L&#39;ID organizzazione viene impostato nella funzione `Visitor.getInstance` del codice del servizio ID.

![](assets/request1.png)

**Prima risposta**

All&#39;interno della risposta, il DCS restituisce l&#39;[!DNL Experience Cloud] ID (MID) e il cookie demdex. Il codice del servizio ID scrive il valore MID nel cookie AMCV. Ad esempio, il DCS restituisce il MID 1234. Il viene memorizzato nel cookie AMCV come `mid|1234`mid|  e viene impostato nel dominio pizzeria di prime parti. Anche il cookie demdex contiene un ID univoco (ad esempio 5678). Questo cookie viene impostato nel dominio demdex.net di terze parti, diverso dal dominio pizzeria.

![](assets/response1.png)

Come spiegato nel prossimo esempio, l&#39;ID demdex e l&#39;ID organizzazione consentono al servizio ID di creare e restituire il MID corretto quando i visitatori si spostano in un altro sito appartenente alla società Azienda alimentare.

## Richiesta e risposta tra siti {#section-15ea880453af467abd2874b8b4ed6ee9}

In questo esempio, il visitatore della società Azienda alimentare passa dal sito pizzeria al sito taqueria. La società Azienda alimentare ha implementato il codice del servizio ID sul sito Web taqueria. Il visitatore non è mai stato nel sito Web taqueria.

Di conseguenza, sul sito taqueria non è presente il cookie AMCV. Pertanto, il servizio ID non può utilizzare il cookie AMCV impostato sul sito pizzeria, perché è specifico per il dominio pizzeria. Il servizio ID deve quindi chiamare il DCS per verificare e richiedere un ID visitatore. In tal caso, la chiamata al DCS comprende l&#39;ID organizzazione della società Azienda alimentare *e* l&#39;ID demdex. L&#39;ID demdex viene prelevato dal sito pizzeria e memorizzato come cookie di terze parti nel dominio demdex.net.

![](assets/request2.png)

Quando il DCS riceve l&#39;ID organizzazione e l&#39;ID demdex, crea e restituisce il MID corretto per il visitatore del sito. Poiché il viene derivato matematicamente dall&#39;ID organizzazione e dall&#39;ID demdex, il cookie AMCV contiene il valore MID, `mid = 1234`mid = .

![](assets/response2.png)

## Richieste ID da altri siti {#section-ba9a929e50d64b0aba080630fd83b6f1}

In questo esempio, il visitatore abbandona i siti dell&#39;azienda Azienda alimentare e accede al sito campo da calcio di proprietà della società Azienda sportiva. Quando il visitatore accede al sito campo da calcio, la verifica e la richiesta di ID vengono effettuate nello stesso modo descritto negli esempi precedenti. Tuttavia, poiché la società Azienda sportiva dispone di un proprio ID organizzazione, il servizio ID restituisce un MID diverso. Il nuovo MID è univoco per i domini controllati dalla società Azienda sportiva e consente alla società di monitorare e condividere i dati del visitatore tra le soluzioni [!DNL Experience Cloud]. L&#39;ID demdex del visitatore rimane invariato, perché è contenuto in un cookie di terze parti e viene mantenuto nei diversi domini.

![](assets/req_resp.png)

