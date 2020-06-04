---
title: Identificazione di visitatori univoci
description: Documentazione di Adobe ECID (servizio ID)
translation-type: tm+mt
source-git-commit: d39cb79bac3a0a277e6390a8127c1f1b68579fa6
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 66%

---


# Identificazione di visitatori univoci

Il metodo per identificare i visitatori univoci tra più contesti include una sequenza prioritaria per garantire di definirli con precisione. La tabella seguente mostra la sequenza prioritaria:

| Ordine utilizzato | Parametro query (metodo di raccolta) | post_visid_type, valore della colonna | Presente quando |
|---|---|---|---|
|  1  | vid [(s.visitorID)](https://docs.adobe.com/content/help/it-IT/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` è impostato. |
|  2  | aid  [(s_vi cookie)](https://docs.adobe.com/content/help/it-IT/analytics/technotes/visitor-identification.html)  | 3  | Il visitatore aveva un cookie s_vi esistente prima che tu implementassi il servizio ID visitatore oppure hai configurato un [periodo di tolleranza](https://docs.adobe.com/content/help/it-IT/id-service/using/reference/analytics-reference/grace-period.html) per il servizio ID visitatore.  |
|  3  | mid[(cookie AMCV_ impostato da Identity Service)](https://docs.adobe.com/content/help/it-IT/id-service/using/home.html)  |  5  |  Il browser del visitatore accetta i cookie (di prime parti) e il servizioidentità viene distribuito.  |
|  4  | fid [(fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript)](https://docs.adobe.com/content/help/it-IT/analytics/technotes/visitor-identification.html)  |  4  |  Il browser del visitatore accetta i cookie (first-party).  |
|  5  |  [Intestazione del sottoscrittore HTTP Mobile](https://docs.adobe.com/content/help/it-IT/analytics/technotes/visitor-identification.html)  |  2  |  Il dispositivo è riconosciuto come dispositivo mobile.  |
|  6  |  [IP Address, User Agent, Gateway IP Address](https://docs.adobe.com/content/help/it-IT/analytics/technotes/visitor-identification.html)  |  1  |  Il browser del visitatore non accetta i cookie. |

Per informazioni sul modo in cui vengono segnalati i visitatori univoci, vedi [Visitatori univoci in Analytics](https://docs.adobe.com/content/help/it-IT/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
