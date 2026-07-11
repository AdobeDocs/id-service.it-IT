---
description: Il cookie AMCV contiene l'ECID e un ID di regione per i visitatori del sito. Questi ID sono archiviati come coppie chiave-valore. L'ID mid utente rappresenta l'ECID del visitatore. L'ID aamlh region rappresenta l'ID di regione del visitatore del sito. Puoi recuperare tali informazioni analizzando il cookie AMCV.
keywords: Servizio ID visitatori
title: Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID visitatore
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
TQID: https://experienceleague.adobe.com/OBzPrrLffDFgRisA27XIIl33x-4aWmj0krXF3prLPUk
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 235
ht-degree: 42%

---

# Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID visitatore {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Il cookie AMCV contiene l&#39;ECID e un ID di regione per i visitatori del sito. Questi ID sono archiviati come coppie chiave-valore. L&#39;ID mid:user contiene l&#39;ECID del visitatore. L&#39;ID aamlh:region rappresenta l&#39;ID di regione per i visitatori del sito. Puoi recuperare tali informazioni analizzando il cookie AMCV.

Per ulteriori informazioni, consulta [Ottenere ID utente e regione tramite il servizio ID visitatore](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=it).

Se sei un cliente di Audience Manager, puoi ottenere l’ID di regione dalla risposta inviata dal server di raccolta dati (DCS, Data Collection Server). Consulta [Ottenere l’ID utente e di regione da una risposta DCS](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=it).

È inoltre possibile ottenere l&#39;ID di regione con un metodo `GET` fornito dal servizio ID visitatore. Consulta [Ottieni ID di regione (hint posizione)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

