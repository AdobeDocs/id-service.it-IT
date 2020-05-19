---
title: Identificazione di visitatori univoci
description: Documentazione di Adobe ECID (servizio ID)
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '223'
ht-degree: 100%

---


# Identificazione di visitatori univoci

Il metodo per identificare i visitatori univoci tra più contesti include una sequenza prioritaria per garantire di definirli con precisione. La tabella seguente mostra la sequenza prioritaria:
 
| Ordine utilizzato | Parametro query (metodo di raccolta) | valore colonna post_visid_type | Presente quando |
|--- |--- |--- |--- |
| 1 | [vid (s.visitorID)](https://docs.adobe.com/content/help/it-IT/analytics/technotes/visitor-identification.html) | 0 |s.visitorID è impostato.|
| 2 | [aid (s_vi cookie)](https://docs.adobe.com/content/help/it-IT/analytics/technotes/visitor-identification.html) | 3 |Il visitatore aveva un cookie s_vi esistente prima che tu implementassi il servizio ID visitatore oppure hai configurato un [periodo di tolleranza](https://docs.adobe.com/content/help/it-IT/id-service/using/reference/analytics-reference/grace-period.html) per il servizio ID visitatore. |
| 3 | [mid (AMCV_ cookie impostato dal Servizio identità)](https://docs.adobe.com/content/help/it-IT/id-service/using/home.html) | 5 | Il browser del visitatore accetta i cookie (prime parti) e il Servizio identità è distribuito. |
| 4 | [fid (cookie di fallback su H.25.3 o versioni successive o AppMeasurement per JavaScript)](https://docs.adobe.com/content/help/it-IT/analytics/technotes/visitor-identification.html) | 4 | Il browser del visitatore accetta i cookie (prime parti). |
| 5 | [intestazione iscritto HTTP Mobile](https://docs.adobe.com/content/help/it-IT/analytics/technotes/visitor-identification.html) | 2 | Il dispositivo è riconosciuto come dispositivo mobile. |
| 6 | [Indirizzo IP, Agente utente, Indirizzo gateway IP](https://docs.adobe.com/content/help/it-IT/analytics/technotes/visitor-identification.html) | 1 | Il browser del visitatore non accetta i cookie. |

Per informazioni sul modo in cui vengono segnalati i visitatori univoci, vedi [Visitatori univoci in Analytics](https://docs.adobe.com/content/help/it-IT/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
