---
description: Il cookie AMCV contiene l'identificatore Experience Cloud ID (MID) e un ID di regione per i visitatori del sito. Questi ID sono memorizzati come coppie chiave-valore. L'ID mid utente rappresenta l'Experience Cloud ID del visitatore. L'ID aamlh region rappresenta l'ID di regione del visitatore del sito. Puoi recuperare tali informazioni analizzando il cookie AMCV.
keywords: ID Service
seo-description: Il cookie AMCV contiene l'identificatore Experience Cloud ID (MID) e un ID di regione per i visitatori del sito. Questi ID sono memorizzati come coppie chiave-valore. L'ID mid utente rappresenta l'Experience Cloud ID del visitatore. L'ID aamlh region rappresenta l'ID di regione del visitatore del sito. Puoi recuperare tali informazioni analizzando il cookie AMCV.
seo-title: Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID
title: Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Il cookie AMCV contiene l&#39;identificatore Experience Cloud ID (MID) e un ID di regione per i visitatori del sito. Questi ID sono memorizzati come coppie chiave-valore. L&#39;ID mid:user rappresenta l&#39;Experience Cloud ID del visitatore. L’ID aamlh:region rappresenta l’ID di regione per i visitatori del sito. Puoi recuperare tali informazioni analizzando il cookie AMCV.

For more information, see [Get User IDs and Regions Through the Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

Se sei un [!DNL Audience Manager] cliente di, puoi ottenere l&#39;ID di regione dalla risposta inviata dal server di raccolta dati (DCS, Data Collection Server). See [Get User IDs and Regions from a DCS Response](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

Puoi ottenere l&#39;ID di regione anche con un `GET` metodo fornito dal servizio ID. Consulta [Ottieni ID di regione (hint posizione)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
