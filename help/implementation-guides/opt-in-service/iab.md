---
description: Connetti la loro piattaforma di gestione del consenso (CMP) con il plug-in Audience Manager di Opt-in per IAB Transparency and Consent Framework (TCF).
seo-description: Connetti la loro piattaforma di gestione del consenso (CMP) con il plug-in Audience Manager per IAB Transparency and Consent Framework (TCF).
seo-title: (beta) Utilizzo dei servizi Opt-in con il Framework IAB
title: (beta) Utilizzo dei servizi Opt-in con il Framework IAB
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: cb75ac6a9d7a5a001fcb0a1d9d978d3845a4e829

---


# (beta) Utilizzo dei servizi Opt-in con il Framework IAB{#beta-using-opt-in-services-with-iab-framework}

Connetti la loro piattaforma di gestione del consenso (CMP) con il plug-in IAB del consenso per Audience Manager.

I clienti di Audience Manager che utilizzano [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) possono collegare la propria piattaforma di gestione dei contenuti (CMP) con il plug-in Audience Manager di Opt-in per IAB TCF. L'Opt-in è una funzione incorporata nella libreria JavaScript di (ECID) che può disabilitare le librerie della singola soluzione Adobe in base alle preferenze del visitatore impostate in una CMP. Quando il plug-in IAB viene implementato con la libreria ECID, le preferenze del visitatore della piattaforma CMP conforme all'IAB vengono mappate in automatico per l'Opt-in. Queste preferenze abiliteranno le librerie basate su Audience Manager (DIL e ECID) e le chiamate associate qalla ricezione del consenso.

## Implementare una piattaforma CMP che supporti IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Al fine di integrare Opt-in con il consenso IAB è necessario completare la procedura seguente:

1. Implementa una piattaforma CMP che supporti IAB e che sia [registrata come fornitore IAB](https://vendorlist.consensu.org/vendorlist.json) oppure sviluppa una piattaforma CMP interna che implementi le specifiche IAB e registrarla come CMP in IAB Europe.
1. Definisci/carica il `__cmp` prima di caricare Adobe JS.

Per altre informazioni, leggere i [documenti di Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Abilitare il plug-in IAB nella libreria JavaScript di ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in è disponibile solo in ECID 4.0+

Usa Experience Platform Launch per implementare sia Opt-in che il plug-in IAB per il tuo sito. Read the [documentation for the ECID Opt-in extension](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/) to learn how to set up the Experience Platform Launch extension.

Quando si abilita IAB per Opt-in in modo manuale, accertarsi che le seguenti opzioni siano impostate su true nell'oggetto Visitatore:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Quando le impostazioni sono state configurate in modo adeguato, le librerie ECID e DIL vengono abilitate/disabilitate in base ai criteri di consenso di CMP e del framework IAB.

>[!IMPORTANT]
>
>Al fine di distribuire i cookie e avviare oppure rispettare le sincronizzazioni degli ID in Audience Manager, è necessario dare il consenso per gli *scopi 1, 2 e 5 oltre al consenso del fornitore*. Altre informazioni sul plug-in IAB sono disponibili nella documentazione di Audience Manager [qui](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html).

Per altre informazioni su come convalidare sia Opt-in che il plug-in IAB, consulta il caso d’uso n. 4 nella guida alla convalida, disponibile [qui](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentazione correlata {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): per altre informazioni sugli standard IAB
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): per altre informazioni su Opt-in, un componente necessario per la gestione dei consensi nelle soluzioni della piattaforma
* Supporto di IAB Transparency and Consent Framework (TCF) [in Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)
* [Opzioni sulla privacy](https://www.adobe.com/privacy/opt-out.html#customeruse): un'altra opzione sulla privacy a tua disposizione è la capacità di negare il consenso alla raccolta dei dati usando gli strumenti di rifiuto globale. Il v sulla verifica di Opt-in e IAB.

