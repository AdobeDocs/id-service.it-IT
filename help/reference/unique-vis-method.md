---
title: Identificazione di visitatori univoci
description: Documentazione di Adobe ECID (servizio ID)
translation-type: tm+mt
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 100%

---


# Identificazione di visitatori univoci

Il metodo per identificare i visitatori univoci tra più contesti include una sequenza prioritaria per garantire di definirli con precisione. La tabella seguente mostra la sequenza prioritaria:

| Ordine utilizzato | Parametro query (metodo di raccolta) | Valore della colonna post_visid_type | Presente quando |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/it-IT/analytics/components/metrics/unique-visitors.translate.html)  | 0  | `s.visitorID` è impostato. |
|  2  | aid [s_vi cookie](https://docs.adobe.com/content/help/it-IT/analytics/components/metrics/unique-visitors.translate.html)  | 3  | Il visitatore aveva un cookie s_vi esistente prima che tu implementassi il servizio ID visitatore, oppure hai configurato un [periodo di tolleranza](https://docs.adobe.com/content/help/it-IT/id-service/using/reference/analytics-reference/grace-period.html) per il servizio ID visitatore.  |
|  3  | mid [cookie AMCV_ impostato da Identity Service](https://docs.adobe.com/content/help/it-IT/id-service/using/home.html)  |  5  |  Il browser del visitatore accetta i cookie (di prima parte) e [!UICONTROL Identity Service] viene distribuito.  |
|  4  | fid [cookie di fallback su H.25.3 o versioni successive, o AppMeasurement per JavaScript](https://docs.adobe.com/content/help/it-IT/analytics/components/metrics/unique-visitors.translate.html)  |  4  |  Il browser del visitatore accetta i cookie (di prima parte).  |
|  5  |  [Intestazione del sottoscrittore mobile HTTP](https://docs.adobe.com/content/help/it-IT/analytics/components/metrics/unique-visitors.translate.html)  |  2  |  Il dispositivo è riconosciuto come dispositivo mobile.  |
|  6  |  [Indirizzo IP, agente utente, indirizzo IP gateway](https://docs.adobe.com/content/help/it-IT/analytics/components/metrics/unique-visitors.translate.html)  |  1  |  Il browser del visitatore non accetta i cookie. |

Per informazioni sul modo in cui vengono segnalati i visitatori univoci, vedi [Visitatori univoci in Analytics](https://docs.adobe.com/content/help/it-IT/analytics/components/metrics/unique-visitors.translate.html).
