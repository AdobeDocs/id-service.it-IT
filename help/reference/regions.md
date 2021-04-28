---
description: Il cookie AMCV contiene l'identificatore Experience Cloud ID (MID) e un ID di regione per i visitatori del sito. Questi ID sono archiviati come coppie chiave-valore. L'ID mid utente rappresenta l'Experience Cloud ID del visitatore. L'ID aamlh region rappresenta l'ID di regione del visitatore del sito. Puoi recuperare tali informazioni analizzando il cookie AMCV.
keywords: Servizio ID
seo-description: Il cookie AMCV contiene l'identificatore Experience Cloud ID (MID) e un ID di regione per i visitatori del sito. Questi ID sono archiviati come coppie chiave-valore. L'ID mid utente rappresenta l'Experience Cloud ID del visitatore. L'ID aamlh region rappresenta l'ID di regione del visitatore del sito. Puoi recuperare tali informazioni analizzando il cookie AMCV.
seo-title: Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID
title: Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---

# Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Il cookie AMCV contiene l&#39;identificatore Experience Cloud ID (MID) e un ID di regione per i visitatori del sito. Questi ID sono archiviati come coppie chiave-valore. L&#39;ID mid:user rappresenta l&#39;Experience Cloud ID del visitatore. L’ID aamlh:region rappresenta l’ID di regione dei visitatori del sito. Puoi recuperare tali informazioni analizzando il cookie AMCV.

Per ulteriori informazioni, consulta [Ottenere l’ID utente e di regione tramite il servizio Experience Cloud Identity](https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

Se sei un cliente di [!DNL Audience Manager], puoi ottenere l’ID di regione dalla risposta inviata dal server di raccolta dati (DCS, Data Collection Server). Consulta [Ottenere l’ID utente e di regione da una risposta DCS](https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

Puoi ottenere l&#39;ID di regione anche con un `GET` metodo fornito dal servizio ID. Consulta [Ottieni ID di regione (hint posizione)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
