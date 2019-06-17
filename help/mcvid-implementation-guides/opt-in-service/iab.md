---
description: Collegate la piattaforma di gestione del consenso (CMP) con il plug-plugin IAB di consenso.
seo-description: Collegate la piattaforma di gestione del consenso (CMP) con il plug-plugin IAB di consenso.
seo-title: (beta) Utilizzo dei servizi di consenso con IAB Framework
title: (beta) Utilizzo dei servizi di consenso con IAB Framework
uuid: 8 df 39 d 9 c-c 016-490 e-b 4 db-d 02 e 4044 b 480
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# (beta) Utilizzo dei servizi di consenso con IAB Framework{#beta-using-opt-in-services-with-iab-framework}

Collegate la piattaforma di gestione del consenso (CMP) con il plug-plugin IAB di consenso.

I clienti Audience Manager che usano [IAB Transparency e Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) possono collegare la piattaforma di gestione del consenso (CMP) con il plug-plugin IAB di consenso. La funzione di consenso è una funzione incorporata nella libreria javd javascript in grado di disattivare le singole librerie delle soluzioni Adobe in base alle preferenze dei visitatori impostate in una CMP. Quando il plug-plugin IAB viene implementato con la libreria ECID, le preferenze dei visitatori dalla CMP conforme con IAB vengono mappate automaticamente all&#39;opzione Consenso. Queste preferenze abiliteranno le librerie basate su Audience Manager (DIL e ECID) e le chiamate associate quando viene ricevuto il consenso.

## Implementare una piattaforma CMP che supporti IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Al fine di integrare Opt-in con il consenso IAB è necessario completare la procedura seguente:

1. Implementare una piattaforma CMP che supporti IAB e che sia [registrata come fornitore IAB](https://vendorlist.consensu.org/vendorlist.json) oppure sviluppare una piattaforma CMP interna che implementi le specifiche IAB e registrarla come CMP in IAB Europe.
1. Definire/caricare il `__cmp` caricamento di Adobe JS.

Per altre informazioni, leggere i [documenti di Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Abilitare il plug-in IAB nella libreria JavaScript di ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>La funzione di consenso è disponibile solo in ECID 4.0 +

Usare Adobe Launch per implementare sia Opt-in che il plug-in IAB per il sito. Leggere la [documentazione per l&#39;estensione Opt-in ECID](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/) per informazioni su come configurare l&#39;estensione Launch.

Quando si abilita IAB per Opt-in in modo manuale, accertarsi che le seguenti opzioni siano impostate su true nell&#39;oggetto Visitatore:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Quando le impostazioni sono state configurate in modo adeguato, le librerie ECID e DIL vengono abilitate/disabilitate in base ai criteri di consenso di CMP e del framework IAB.

>[!IMPORTANT]
>
>Al fine di distribuire i cookie e avviare oppure rispettare le sincronizzazioni degli ID in Audience Manager, è necessario dare il consenso per gli *scopi 1, 2 e 5 oltre al consenso del fornitore*. Per ulteriori informazioni sul plug-plugin IAB nella documentazione di Audience Manager**, [consultate**](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html).

Per altre informazioni su come convalidare sia Opt-in che il plug-in IAB, controllare il caso d&#39;uso n. 4 nella guida alla convalida [**qui** ](../../mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentazione correlata {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): per altre informazioni sugli standard IAB
* [Adobe Opt-in](../../mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): per altre informazioni su Opt-in, un componente necessario per la gestione dei consensi nelle soluzioni della piattaforma
* Supporto di IAB Transparency and Consent Framework (TCF) [in Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)
* [Opzioni sulla privacy](https://www.adobe.com/privacy/opt-out.html#customeruse): un&#39;altra opzione sulla privacy a tua disposizione è la capacità di negare il consenso alla raccolta dei dati usando gli strumenti di rifiuto globale. Il v sulla verifica di Opt-in e IAB.

