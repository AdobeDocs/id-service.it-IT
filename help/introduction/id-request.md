---
description: Panoramica del processo di richiesta ID e risposta. Questi esempi descrivono l'assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti CX Enterprise con i propri ID organizzazione IMS.
keywords: Servizio ID visitatori
title: Richiesta e impostazione degli ID da parte del servizio ID visitatore di Adobe
exl-id: 1bbee560-d72a-47cf-b3fe-d6bbcacb9eff
TQID: https://experienceleague.adobe.com/B6fpw9A-yjGD58XgzLd1UQmAhxr-rGYcSbfPODdbZz4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 777
ht-degree: 35%

---

# Richiesta e impostazione degli ID da parte del servizio ID visitatore di Adobe{#how-the-experience-cloud-id-service-requests-and-sets-ids}

Panoramica del processo di richiesta ID e risposta. Questi esempi descrivono l&#39;assegnazione degli ID per siti individuali, per siti diversi e per siti gestiti da diversi clienti CX Enterprise con i propri ID organizzazione IMS.

>[!NOTE]
>
>Se non sai in che modo il Servizio ID visitatore crea l&#39;ID visitatore, consulta la sezione [Cookie e il Servizio ID visitatore](../introduction/cookies.md).

## Richiesta di un ECID {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

Gli esempi seguenti mostrano come il Servizio ID visitatore richiede e riceve l’ECID. Negli esempi vengono utilizzate due società fittizie, l&#39;Azienda alimentare e l&#39;Azienda sportiva, per illustrare il flusso dei dati per le richieste e le risposte relative agli ID. Ogni azienda ha un ID organizzazione IMS univoco e ha implementato il codice del servizio ID visitatore su tutti i suoi siti. Questi casi d’uso rappresentano flussi di dati per un’implementazione generica del Servizio ID visitatore senza Analytics, ID legacy o browser che bloccano i cookie di terze parti.

![](assets/sample_sites.png)

**Prima richiesta**

In questo esempio, un nuovo visitatore accede al sito pizzeria gestito dalla società Azienda alimentare. La società Azienda alimentare ha il codice del servizio ID visitatore sul sito Web pizzeria. Quando il sito pizzeria viene caricato, il codice del servizio ID visitatore controlla la presenza del cookie AMCV nel dominio pizzeria.

* Se il cookie AMCV è impostato, il visitatore del sito dispone di un ECID. In questo caso, il cookie tiene traccia del visitatore e condivide i dati con altre soluzioni CX Enterprise.
* Se il cookie AMCV non è impostato, il codice del servizio ID visitatore chiama un [server di raccolta dati](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=it) (DCS) regionale in `dpm.demdex.net/id` (vedi anche [Informazioni sulle chiamate al dominio demdex](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=it). La chiamata include l’ID organizzazione IMS per la società Azienda alimentare. L&#39;ID organizzazione IMS è impostato nella funzione `Visitor.getInstance` del codice del servizio ID visitatore.

![](assets/request1.png)

**Prima risposta**

Nella risposta, il DCS restituisce l’ECID e il cookie demdex. Il codice del servizio ID visitatore scrive il valore MID nel cookie AMCV. Ad esempio, supponiamo che il DCS restituisca un valore MID pari a 1234. Il viene memorizzato nel cookie AMCV come `mid|1234`mid| e viene impostato nel dominio pizzeria di prime parti. Il cookie demdex contiene a sua volta un ID univoco (chiamiamolo 5678). Questo cookie è impostato nel dominio demdex.net di terze parti, separato dal dominio pizzeria.

![](assets/response1.png)

Come vedrai nel prossimo esempio, l’ID demdex e l’ID organizzazione IMS consentono al servizio ID visitatore di creare e restituire il MID corretto quando il visitatore si sposta su un altro sito appartenente alla società Azienda alimentare.

## Richieste e risposte intersito {#section-15ea880453af467abd2874b8b4ed6ee9}

In questo esempio, il visitatore della società Azienda alimentare accede al sito taqueria dal sito pizzeria. La società Azienda alimentare ha il codice del servizio ID visitatore sul sito Web taqueria. Il visitatore non è mai stato sul sito Web taqueria.

Date queste condizioni, sul sito taqueria non ci sono cookie AMCV. Inoltre, il servizio ID visitatore non può utilizzare il cookie AMCV impostato sul sito pizzeria perché è specifico per il dominio pizzeria. Di conseguenza, il Servizio ID visitatore deve chiamare il DCS per verificare e richiedere un ID visitatore. In questo caso, la chiamata al DCS include l&#39;ID organizzazione IMS *e* della società Azienda alimentare l&#39;ID demdex. Ricorda che l’ID demdex viene prelevato dal sito pizzeria e memorizzato come cookie di terze parti nel dominio demdex.net.

![](assets/request2.png)

Dopo che il DCS riceve l’ID organizzazione IMS e l’ID demdex, crea e restituisce il MID corretto per il visitatore del sito. Poiché il viene derivato matematicamente dall&#39;ID organizzazione IMS e dall&#39;ID demdex, il cookie AMCV contiene il valore MID, `mid = 1234`.

![](assets/response2.png)

## Richieste di ID da altri siti {#section-ba9a929e50d64b0aba080630fd83b6f1}

In questo esempio, il visitatore abbandona i siti della società Azienda alimentare e accede al sito di calcio di proprietà della società Azienda sportiva. Quando il visitatore accede al sito di calcio, il processo di verifica e richiesta degli ID funziona nel modo descritto negli esempi precedenti. Tuttavia, poiché la società Azienda sportiva ha il proprio ID organizzazione IMS, il servizio ID visitatore restituisce un MID diverso. Il nuovo MID è univoco per i domini controllati dalla società Azienda sportiva e consente alla società di monitorare e condividere i dati dei visitatori tra le soluzioni CX Enterprise. L&#39;ID demdex del visitatore rimane invariato, perché è contenuto in un cookie di terze parti e viene mantenuto nei diversi domini.

![](assets/req_resp.png)
