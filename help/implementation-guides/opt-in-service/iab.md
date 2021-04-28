---
description: Collega la loro piattaforma di gestione del consenso (CMP) con il plugin Audience Manager di Opt-in per IAB Transparency and Consent Framework (TCF).
seo-description: Collega la loro piattaforma di gestione del consenso (CMP) con il plug-in Audience Manager per IAB Transparency and Consent Framework (TCF).
seo-title: Utilizzo dei servizi Opt-in con il Framework IAB
title: Utilizzo dei servizi Opt-in con il Framework IAB
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '493'
ht-degree: 100%

---

# Utilizzo dei servizi Opt-in con il Framework IAB {#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>Il seguente documento si applica solo a IAB 2.0. Per lavorare con questa versione gli utenti devono utilizzare Visitor.js 5.0.

Collega la piattaforma di gestione del consenso (CMP) con il plug-in di Opt-in IAB Transparency and Consent Framework (TCF).

I clienti di Adobe Audience Manager che utilizzano [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) possono collegare la loro CMP con il plug-in di Opt-in IAB TCF. L’Opt-in è una funzione incorporata nella libreria JavaScript di ECID che può disabilitare le librerie della singola soluzione Adobe in base alle preferenze del visitatore impostate in una CMP. Quando il plug-in di Opt-in IAB TCF è implementato con la libreria di ECID, le preferenze dei visitatori dalla CMP che supporta IAB TCF sono automaticamente mappate a Opt-in. Queste preferenze abiliteranno le librerie basate su Audience Manager (DIL e ECID) e le chiamate associate qalla ricezione del consenso.

## Implementare una piattaforma CMP che supporti IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Per eseguire l’integrazione di Opt-in con IAB TCF è necessario svolgere le seguenti azioni:

1. Implementa una CMP che supporti IAB e sia [registrata come fornitore IAB](https://vendorlist.consensu.org/vendorlist.json) o sviluppa una CMP interna che implementi la specifica IAB TCF e registrala come CMP con IAB TCF.
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
>Audience Manager richiede il consenso per *Scopo 1, Scopo 10 e il consenso del fornitore* per distribuire i cookie e avviare o rispettare le sincronizzazioni degli ID. Trovi maggiori informazioni sul plug-in di Opt-in IAB TCF nella documentazione di Audience Manager [qui](https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).

Per maggiori informazioni su come convalidare il plug-in di Opt-in IAB TCF, fai riferimento al caso d’uso n° 4 nella guida alla convalida [qui](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentazione correlata {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): per altre informazioni sugli standard IAB
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): per altre informazioni su Opt-in, un componente necessario per la gestione dei consensi nelle soluzioni della piattaforma
* Supporto IAB Transparency and Consent Framework (TCF) [in Audience Manager](https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)
* [Opzioni sulla privacy](https://www.adobe.com/it/privacy/opt-out.html#customeruse): un’altra opzione sulla privacy a tua disposizione è la capacità di negare il consenso alla raccolta dei dati usando gli strumenti di rifiuto globale. Il rifiuto globale ha la precedenza sull’Opt-in e sulla verifica IAB TCF
