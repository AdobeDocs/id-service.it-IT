---
audience: end-user
user-guide-title: Guida del servizio ID visitatore di Adobe
breadcrumb-title: Guida al servizio ID visitatore
user-guide-description: Il servizio ID visitatore di Adobe fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni di CX Enterprise. Consente di sostituire il codice di generazione ID legacy per le soluzioni e i servizi aziendali CX.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 7621dc8925235bd3cf159a404741bd02fc9b6a77
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 45%

---


# Guida del servizio ID visitatore di Adobe {#using}

+ [Guida del servizio ID visitatori](home.md)
+ Panoramica {#intro}
   + [Panoramica](introduction/overview.md)
   + [Informazioni sul servizio ID visitatori](introduction/about-id-service.md)
   + [Cookie e il servizio ID visitatore](introduction/cookies.md)
   + [Richiesta e impostazione degli ID da parte del servizio ID visitatori](introduction/id-request.md)
   + [Sincronizzazione e tassi di corrispondenza](introduction/match-rates.md)
+ Implementazione {#implementation}
   + [Metodi di implementazione](implementation-guides/implementation-methods.md)
   + [Guide all’implementazione](implementation-guides/implementation-guides.md)
   + [Implementare con i tag](implementation-guides/ecid-implement-with-launch.md)
   + [Implementazione per Analytics](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/overview){target=_blank}
   + [Implementazione per Target](implementation-guides/setup-target.md)
   + [Implementazione per Analytics e Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implementazione per Analytics, Audience Manager e Target](implementation-guides/setup-aam-analytics-target.md)
   + [Uso del servizio ID visitatori con A4T e l&#39;implementazione lato server di Target](implementation-guides/ecid-a4t-target.md)
   + [Integrazione diretta con il servizio ID visitatore](implementation-guides/direct-integration.md)
   + [Casi d’uso dell&#39;integrazione diretta](implementation-guides/direct-integration-examples.md)
   + [Test e verifica del servizio ID visitatori](implementation-guides/test-verify.md)
   + Servizio Opt-in {#opt-in-service}
      + [Panoramica del servizio Opt-in](implementation-guides/opt-in-service/optin-overview.md)
      + [Configurazione del servizio Opt-in](implementation-guides/opt-in-service/getting-started.md)
      + [Convalida del servizio Opt-in](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configurazione di Opt-in con i tag](implementation-guides/opt-in-service/launch.md)
      + [Controllare le attività aziendali di CX in base al consenso degli utenti](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Casi d&#39;uso di Opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Riferimenti di Opt-in](implementation-guides/opt-in-service/api.md)
      + [Utilizzo dei servizi Opt-in con il Framework IAB](implementation-guides/opt-in-service/iab.md)
+ API del servizio ID visitatore {#id-service-api}
   + [Panoramica API del servizio ID visitatori](library/library.md)
   + Configurazione {#configurations}
      + [Panoramica sulle configurazioni](library/function-vars/function-vars.md)
      + [audienceManagerServer e audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [Configurazioni Secure e SameSite](library/function-vars/secure-samesite-config.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain e whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + Metodi {#methods}
      + [Metodi](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (Monitoraggio interdominio)](library/get-set/appendvisitorid.md)
      + [Metodi callTimeOut](library/get-set/timeout-functions.md)
      + [Sincronizzazione ID tramite URL o sorgente dati](library/get-set/idsync.md)
      + [getInstance](library/get-set/getinstance.md)
      + [getAnalyticsVisitorID](library/get-set/getanalyticsvisitorid.md)
      + [getCustomerIDs](library/get-set/getcustomerids.md)
      + [setCustomerIDs](library/get-set/setcustomerids.md)
      + [getMarketingCloudVisitorID](library/get-set/getmcvid.md)
      + [getLocationHint](library/get-set/getlocationhint.md)
      + [getVisitorValues](library/get-set/getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](library/get-set/client-side-id.md)
      + [resetState](library/get-set/resetstate.md)
+ Riferimenti {#reference}
   + [Panoramica dei riferimenti](reference/reference.md)
   + [Modifiche all’etichettatura SameSite di Google Chrome](reference/chrome-samesite-labelling.md)
   + [Informativa sulla sicurezza dei contenuti e servizio ID visitatore](reference/csp.md)
   + [Supporto per COPPA nel servizio ID visitatori](reference/coppa.md)
   + [Supporto per CORS nel servizio ID visitatori](reference/cors.md)
   + [ID cliente e stati di autenticazione](reference/authenticated-state.md)
   + [Metodi della libreria ECID in ambito Safari ITP](reference/ecid-library-methods.md)
   + [Identificazione di visitatori univoci](reference/unique-vis-method.md)
   + [Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID visitatore](reference/regions.md)
   + [Requisiti del servizio ID visitatori](reference/requirements.md)
   + [Video Heartbeat e il servizio ID visitatori](reference/heartbeat.md)
   + [Supporto di hashing SHA-256 per setCustomerIDs](reference/hashing-support.md)
+ Domande frequenti {#faqs}
   + [Panoramica sulle domande frequenti](faq-intro/faq-intro.md)
   + [Domande frequenti sul servizio ID visitatore](faq-intro/faq.md)
   + [Domande frequenti per altre soluzioni aziendali CX](faq-intro/other-faq.md)
+ Note sulla versione del servizio ID visitatore {#release-notes}
   + [Note sulla versione 2022](release-notes/notes-2022.md)
   + [Note sulla versione 2021](release-notes/notes-2021.md)
   + [Note sulla versione 2020](release-notes/notes-2020.md)
   + [Note sulla versione 2019](release-notes/notes-2019.md)
   + [Note sulla versione 2018](release-notes/notes-2018.md)
   + [Note sulla versione 2017](release-notes/notes-2017.md)
   + [Note sulla versione 2016](release-notes/notes-2016.md)
   + [Note sulla versione 2015](release-notes/notes-2015.md)
