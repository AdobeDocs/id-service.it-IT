---
title: Identificazione di visitatori univoci
description: Documentazione di Adobe ECID (servizio ID)
translation-type: ht
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# Identificazione di visitatori univoci

Il metodo per identificare i visitatori univoci tra più contesti include una sequenza prioritaria per garantire di definirli con precisione. La tabella seguente mostra la sequenza prioritaria:


 
| Ordine utilizzato| Parametro query (metodo di raccolta)| valore colonna post_visid_type| Presente quando |
|--- |--- |--- |--- |
| 1 | |[vid (s.visitorID)](https://marketing.adobe.com/resources/help/it_IT/sc/implement/visid_custom.html) | 0 |s.visitorID è impostato.| 
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/it_IT/sc/implement/visid_analytics.html) | 
3 |Il visitatore aveva un cookie s_vi esistente prima dell’implementazione del servizio ID visitatore, oppure [un periodo di tolleranza](https://marketing.adobe.com/resources/help/it_IT/mcvid/mcvid_grace_period.html) configurato. |
| 3 | [mid (AMCV_ cookie impostato dal Servizio identità)](https://marketing.adobe.com/resources/help/it_IT/mcvid/) | 5 | Il browser del visitatore accetta i cookie (prime parti) e il Servizio identità è distribuito. |
| 4 | [fid (cookie di fallback su H.25.3 o versioni successive o AppMeasurement per JavaScript)](https://marketing.adobe.com/resources/help/it_IT/sc/implement/visid_fallback.html) | 4 |
 Il browser del visitatore accetta i cookie (prime parti). |
| 5 | [intestazione iscritto HTTP Mobile](https://marketing.adobe.com/resources/help/it_IT/sc/implement/visid_mobile.html) | 2 |
Il dispositivo è riconosciuto come dispositivo mobile. |
| 6 | [Indirizzo IP, Agente utente, Indirizzo gateway IP](https://marketing.adobe.com/resources/help/it_IT/sc/implement/visid_fallback.html) | 1 | Il browser del visitatore non accetta i cookie. |


Per informazioni sul modo in cui vengono segnalati i visitatori univoci, vedi [Visitatori univoci in Analytics](https://docs.adobe.com/content/help/it-IT/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.translate.html).
