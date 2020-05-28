---
description: Collega la loro piattaforma di gestione del consenso (CMP) con il plugin Audience Manager di Opt-in per IAB Transparency and Consent Framework (TCF).
seo-description: Collega la loro piattaforma di gestione del consenso (CMP) con il plug-in Audience Manager per IAB Transparency and Consent Framework (TCF).
seo-title: Utilizzo dei servizi Opt-in con il Framework IAB
title: Utilizzo dei servizi Opt-in con il Framework IAB
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: bb61c33491cb67795d58575c5dca5fa2ba4c372f
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 71%

---


# Utilizzo dei servizi Opt-in con il Framework IAB {#using-opt-in-services-with-iab-framework}

Collega la piattaforma di gestione del consenso (CMP) con il plugin Audience Manager di Opt-in per IAB TCF.

I clienti di Audience Manager che utilizzano [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) possono collegare la propria piattaforma di gestione dei contenuti (CMP) con il plugin Audience Manager di Opt-in per IAB TCF. L’Opt-in è una funzione incorporata nella libreria JavaScript di ECID che può disabilitare le librerie della singola soluzione Adobe in base alle preferenze del visitatore impostate in una CMP. Quando il plug-in Audience Manager per IAB TCF viene implementato con la libreria ECID, le preferenze dei visitatori dal CMP che supporta IAB TCF vengono mappate automaticamente al consenso. Queste preferenze abiliteranno le librerie basate su Audience Manager (DIL e ECID) e le chiamate associate qalla ricezione del consenso.

## Implementare una piattaforma CMP che supporti IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Per poter integrare il consenso con lo IAB TCF, è necessario completare quanto segue:

1. Implement a CMP that supports IAB and is [registered as an IAB vendor](https://vendorlist.consensu.org/vendorlist.json) or develop an in-house CMP that implements the IAB TCF spec, and register as a CMP with IAB TCF.
1. Definisci/carica il `__cmp` prima di caricare Adobe JS.

Per altre informazioni, leggere i [documenti di Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Abilita il plug-in Audience Manager per IAB TCF nella tua libreria ECID JavaScript {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in è disponibile solo in ECID 4.0+.

Usa Adobe Experience Platform Launch per implementare sia l’Opt-in sia il plug-in Audience Manager per IAB TCF per il tuo sito. Quando si abilita IAB per Opt-in in modo manuale, accertarsi che le seguenti opzioni siano impostate su true nell’oggetto Visitatore:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Una volta configurate correttamente le impostazioni, le librerie ECID e DIL verranno abilitate/disattivate in base ai criteri di consenso del CMP e del TCF IAB.

>[!IMPORTANT]
>
>Audience Manager needs consent for *Purpose 1 and Purpose 10, plus vendor consent* in order to deploy cookies and initiate or honor ID syncs. Ulteriori informazioni sul plug-in Audience Manager per IAB TCF sono disponibili nella documentazione di Audience Manager [qui](https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).

Per altre informazioni su come convalidare sia Opt-in sia il plug-in Audience Manager per IAB TCF, consulta il caso d’uso n. 4 nella guida alla convalida, disponibile [qui](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentazione correlata {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): per altre informazioni sugli standard IAB
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): per altre informazioni su Opt-in, un componente necessario per la gestione dei consensi nelle soluzioni della piattaforma
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)
* [Opzioni sulla privacy](https://www.adobe.com/it/privacy/opt-out.html#customeruse): un’altra opzione sulla privacy a tua disposizione è la capacità di negare il consenso alla raccolta dei dati usando gli strumenti di rifiuto globale. Il rifiuto globale ha la precedenza sulla verifica del consenso e del TCF IAB

