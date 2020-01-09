---
title: Identificazione di visitatori univoci
description: Documentazione per Adobe ECID (servizio ID)
translation-type: tm+mt
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# Identificazione di visitatori univoci

Il metodo per identificare i visitatori univoci tra più contesti include una sequenza con priorità per garantire la precisione in questa determinazione. La tabella seguente mostra la sequenza con priorità:


 
| Ordine utilizzato| Parametro query (metodo di raccolta)| valore colonna post_visid_type| Presente quando ||||| || 1 |[vid (s.visitorID)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_custom.html)| 0 |s.visitorID è impostato.|| 2 |[aid (cookie s_vi)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_analytics.html)| 3 |Il visitatore aveva un cookie s_vi esistente prima dell&#39;implementazione del servizio ID visitatore, oppure era configurato un periodo[di](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_grace_period.html)tolleranza ID visitatore. || 3 |[mid (cookie AMCV_ impostato da Identity Service)](https://marketing.adobe.com/resources/help/en_US/mcvid/)| 5 | Il browser del visitatore accetta i cookie (first-party) e il servizio identità è distribuito. || 4 |[fid (cookie di fallback su H.25.3 o versioni successive, o AppMeasurement per JavaScript)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 4 | Il browser del visitatore accetta i cookie (prime parti). || 5 | Intestazione[dell&#39;utente](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_mobile.html)HTTP Mobile Subscriber | 2 | Il dispositivo viene riconosciuto come dispositivo mobile. || 6 | Indirizzo[IP, Agente utente, Indirizzo](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)IP gateway | 1 | Il browser del visitatore non accetta i cookie. |


Per informazioni sul modo in cui vengono segnalati i visitatori univoci, vedi Visitatori [unici in Analytics](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
