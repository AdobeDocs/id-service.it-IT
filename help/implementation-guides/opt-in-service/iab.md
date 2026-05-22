---
description: Collega la loro piattaforma di gestione del consenso (CMP) con relativo il plug-in di Audience Manager per i servizi Opt-in con la specifica IAB TCF (Trasparency and Consent Framework).
title: Utilizzo dei servizi Opt-in con il Framework IAB
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
TQID: https://experienceleague.adobe.com/70QH1BoRSSbiw7cMfRjrHmiSxQLbuiHcWAG5b-xVOLw
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
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 518
ht-degree: 96%

---

# Utilizzo dei servizi Opt-in con il Framework IAB{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>Il seguente documento si applica solo a IAB 2.0. Per lavorare con IAB 2.0, gli utenti devono utilizzare Visitor.js versione 5.0.

Collega la piattaforma di gestione del consenso (CMP) con il plug-in di Opt-in IAB Transparency and Consent Framework (TCF).

I clienti di Adobe Audience Manager che utilizzano [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) possono collegare la loro CMP con il plug-in di Opt-in IAB TCF. L’Opt-in è una funzione incorporata nella libreria JavaScript di ECID che può disabilitare le librerie della singola soluzione Adobe in base alle preferenze del visitatore impostate in una CMP. Quando il plug-in di Opt-in IAB TCF è implementato con la libreria di ECID, le preferenze dei visitatori dalla CMP che supporta IAB TCF sono automaticamente mappate a Opt-in. Queste preferenze abiliteranno le librerie basate su Audience Manager (DIL e ECID) e le chiamate associate alla ricezione del consenso.

## Implementare una piattaforma CMP che supporti IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Per eseguire l’integrazione di Opt-in con IAB TCF è necessario svolgere le seguenti azioni:

1. Implementa una CMP che supporti IAB e sia registrata come fornitore IAB o sviluppa una CMP interna che implementi la specifica IAB TCF e registrala come CMP con IAB TCF.
1. Definisci/carica il `__tcfapi` prima di caricare Adobe JS.

Per altre informazioni, leggere i [documenti di Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md).

## Abilitare il plug-in di Opt-in IAB TCF all’interno della libreria JavaScript di ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in è disponibile solo in ECID 4.0+.

Utilizza Adobe Experience Platform Launch per implementare il plug-in di Opt-in IAB TCF sul tuo sito. Quando si abilita IAB per Opt-in in modo manuale, accertarsi che le seguenti opzioni siano impostate su true nell’oggetto Visitatore:

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

Una volta configurate correttamente le impostazioni, le librerie ECID e DIL verranno abilitate/disabilitate in base ai criteri di consenso della CMP e di TCF IAB.

>[!IMPORTANT]
>
>Audience Manager richiede il consenso per *Scopo 1, Scopo 10 e il consenso del fornitore* per distribuire i cookie e avviare o rispettare le sincronizzazioni degli ID. Trovi maggiori informazioni sul plug-in di Opt-in IAB TCF nella documentazione di Audience Manager [qui](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=it).

Per maggiori informazioni su come convalidare il plug-in di Opt-in IAB TCF, fai riferimento al caso d’uso n° 4 nella guida alla convalida [qui](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentazione correlata {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): per altre informazioni sugli standard IAB
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): per altre informazioni su Opt-in, un componente necessario per la gestione dei consensi nelle soluzioni della piattaforma
* Supporto IAB Transparency and Consent Framework (TCF) [in Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=it)
* [Opzioni sulla privacy](https://www.adobe.com/it/privacy/opt-out.html#customeruse): un’altra opzione sulla privacy a tua disposizione è la capacità di negare il consenso alla raccolta dei dati usando gli strumenti di rifiuto globale. Il rifiuto globale ha la precedenza sull’Opt-in e sulla verifica IAB TCF

