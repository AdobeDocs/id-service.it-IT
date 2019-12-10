---
description: Collega la loro piattaforma di gestione del consenso (CMP) con il plugin Audience Manager di Opt-in per IAB Transparency and Consent Framework (TCF).
seo-description: Collega la loro piattaforma di gestione del consenso (CMP) con il plug-in Audience Manager per IAB Transparency and Consent Framework (TCF).
seo-title: (beta) Utilizzo dei servizi Opt-in con il Framework IAB
title: (beta) Utilizzo dei servizi Opt-in con il Framework IAB
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: ab85467ad0f9f661c472eb373809c699c4b9130f

---


# (beta) Utilizzo dei servizi Opt-in con il Framework IAB {#beta-using-opt-in-services-with-iab-framework}

Collegate la piattaforma di gestione del consenso (CMP) al plug-in Audience Manager di Opt-in per IAB TCF.

I clienti di Audience Manager che utilizzano [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) possono collegare la propria piattaforma di gestione dei contenuti (CMP) con il plugin Audience Manager di Opt-in per IAB TCF. L’Opt-in è una funzione incorporata nella libreria JavaScript di ECID che può disabilitare le librerie della singola soluzione Adobe in base alle preferenze del visitatore impostate in una CMP. Quando il plug-in Audience Manager per IAB TCF viene implementato con la libreria ECID, le preferenze del visitatore della piattaforma CMP conforme all’IAB vengono mappate in automatico per l’Opt-in. Queste preferenze abiliteranno le librerie basate su Audience Manager (DIL e ECID) e le chiamate associate qalla ricezione del consenso.

## Implementare una piattaforma CMP che supporti IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Al fine di integrare Opt-in con il consenso IAB è necessario completare la procedura seguente:

1. Implementa una piattaforma CMP che supporti IAB e che sia [registrata come fornitore IAB](https://vendorlist.consensu.org/vendorlist.json) oppure sviluppa una piattaforma CMP interna che implementi le specifiche IAB e registrarla come CMP in IAB Europe.
1. Definisci/carica il `__cmp` prima di caricare Adobe JS.

Per altre informazioni, leggere i [documenti di Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Enable the Audience Manager plug-in for IAB TCF within your ECID Javascript Library {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in è disponibile solo in ECID 4.0+

Usa Adobe Experience Platform Launch per implementare sia l’Opt-in sia il plug-in Audience Manager per IAB TCF per il tuo sito. Quando si abilita IAB per Opt-in in modo manuale, accertarsi che le seguenti opzioni siano impostate su true nell'oggetto Visitatore:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Quando le impostazioni sono state configurate in modo adeguato, le librerie ECID e DIL vengono abilitate/disabilitate in base ai criteri di consenso di CMP e del framework IAB.

>[!IMPORTANT]
>
>Al fine di distribuire i cookie e avviare oppure rispettare le sincronizzazioni degli ID in Audience Manager, è necessario dare il consenso per gli *scopi 1, 2 e 5 oltre al consenso del fornitore*. Ulteriori informazioni sul plug-in Audience Manager per IAB TCF nella documentazione di Audience Manager [sono disponibili qui](https://docs.adobe.com/help/en/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html).

For more information on how to validate both Opt-in and the Audience Manager plug-in for IAB TCF, check use case #4 in the validation guide [here](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentazione correlata {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): per altre informazioni sugli standard IAB
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): per altre informazioni su Opt-in, un componente necessario per la gestione dei consensi nelle soluzioni della piattaforma
* Supporto di IAB Transparency and Consent Framework (TCF) [in Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)
* [Opzioni sulla privacy](https://www.adobe.com/privacy/opt-out.html#customeruse): un'altra opzione sulla privacy a tua disposizione è la capacità di negare il consenso alla raccolta dei dati usando gli strumenti di rifiuto globale. Il Global Opt-Out ha precedenza rispetto alla verifica di Opt-in e IAB.

