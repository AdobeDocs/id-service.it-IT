---
title: Identificazione di visitatori univoci
description: Documentazione di Adobe ECID (servizio ID)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
source-git-commit: c65816530ae2269b216f60b9b0450077e5aaac2f
workflow-type: ht
source-wordcount: '253'
ht-degree: 100%

---

# Identificazione di visitatori univoci

Il metodo per identificare i visitatori univoci tra più contesti include una sequenza prioritaria per garantire di definirli con precisione. La tabella seguente mostra la sequenza prioritaria:

| Ordine utilizzato | Parametro query (metodo di raccolta) | Valore della colonna post_visid_type | Presente quando |
|---|---|---|---|
|  1  | vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=it)  | 0  | `s.visitorID` è impostato. |
|  2  | aid [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=it#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | Il visitatore aveva un cookie s_vi esistente prima che tu implementassi il servizio ID visitatore, oppure hai configurato un [periodo di tolleranza](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=it) per il servizio ID visitatore.  |
|  3  | mid [cookie AMCV_ impostato da Identity Service](../introduction/cookies.md)  |  5  |  Il browser del visitatore accetta i cookie (di prima parte) e [!DNL Identity Service] viene distribuito.  |
|  4  | fid [cookie di fallback su H.25.3 o versioni successive, o AppMeasurement per JavaScript](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=it#section-65e33f9bfc264959ac1513e2f4b10ac7)  |  4  |  Il browser del visitatore accetta i cookie (di prima parte).  |
|  5  |  [Intestazione del sottoscrittore mobile HTTP](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=it)  |  2  |  Il dispositivo è riconosciuto come dispositivo mobile.  |
|  6  |  [Indirizzo IP, agente utente, indirizzo IP gateway](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=it)  |  1  |  Il browser del visitatore non accetta i cookie. |

{style=&quot;table-layout:auto&quot;}

Per informazioni sul modo in cui vengono segnalati i visitatori univoci, vedi [Visitatori univoci in Analytics](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=it).
