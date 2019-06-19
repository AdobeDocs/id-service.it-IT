---
cloud: experience-cloud
product: Servizio ID
audience: end-user
user-guide-title: Aiuto del servizio ID
user-guide-url: /content/help/en/id-service/using/mcvid-home.html
translation-type: tm+mt
source-git-commit: 4dc668afd37cd1d6f9104adb1b102f1dd4c5746e

---


# Aiuto del servizio ID {#using}

+ [Servizio Experience Cloud ID](mcvid-home.md)
+ Panoramica {#mcvid-introduction}
   + [Panoramica](mcvid-introduction/mcvid-overview.md)
   + [Il servizio ID](mcvid-introduction/mcvid-about-id-service.md)
   + [Cookie e il servizio Experience Cloud ID](mcvid-introduction/mcvid-cookies.md)
   + [Richiesta e impostazione degli ID da parte del servizio Experience Cloud ID](mcvid-introduction/mcvid-id-request.md)
   + [Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza](mcvid-introduction/mcvid-match-rates.md)
+ Guide all&#39;implementazione {#implementation-guides}
   + [Guide all&#39;implementazione](mcvid-implementation-guides/mcvid-implementation-guides.md)
   + [Metodi di implementazione](mcvid-implementation-guides/mcvid-implementation-methods.md)
   + [Implementare con Launch](mcvid-implementation-guides/ecid-implement-with-launch.md)
   + [Implementazione con Gestione tag dinamica](mcvid-implementation-guides/mcvid-standard.md)
   + [Implementazione del servizio Experience Cloud ID per Analytics](mcvid-implementation-guides/mcvid-setup-analytics.md)
   + [Implementazione del servizio Experience Cloud ID per Target](mcvid-implementation-guides/mcvid-setup-target.md)
   + [Implementazione del servizio Experience Cloud ID per Analytics e Audience Manager](mcvid-implementation-guides/mcvid-setup-aam-analytics.md)
   + [Implementazione del servizio Experience Cloud ID per Analytics, Audience Manager e Target](mcvid-implementation-guides/mcvid-setup-aam-analytics-target.md)
   + [Uso del servizio Experience Cloud ID con A4T e l&#39;implementazione lato server di Target](mcvid-implementation-guides/ecid-a4t-target.md)
   + [Integrazione diretta con il servizio Experience Cloud ID](mcvid-implementation-guides/mcvid-direct-integration.md)
   + [Casi d&#39;uso dell&#39;integrazione diretta](mcvid-implementation-guides/mcvid-direct-integration-examples.md)
   + [Verificare e verificare il servizio Experience Cloud ID](mcvid-implementation-guides/mcvid-test-verify.md)
   + Documentazione di consenso {#opt-in-service}
      + [Panoramica del servizio di consenso](mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md)
      + [Configurazione del servizio di consenso](mcvid-implementation-guides/opt-in-service/getting-started.md)
      + [Convalida del servizio di consenso](mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configurare Opt-in con Launch](mcvid-implementation-guides/opt-in-service/launch.md)
      + [Configurare Opt-in con DTM](mcvid-implementation-guides/opt-in-service/optin-dtm.md)
      + [Casi d&#39;uso di Opt-in](mcvid-implementation-guides/opt-in-service/use-cases.md)
      + [Riferimenti di Opt-in](mcvid-implementation-guides/opt-in-service/api.md)
      + [(beta) Utilizzo dei servizi di consenso con IAB Framework](mcvid-implementation-guides/opt-in-service/iab.md)
+ API del servizio ID {#id-service-api}
   + [Panoramica API servizio ID](mcvid-library/mcvid-library.md)
   + Configurazione {#configurations}
      + [Panoramica sulle configurazioni](mcvid-library/mcvid-function-vars/mcvid-function-vars.md)
      + [audienceManagerServer e audienceManagerServerSecure](mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md)
      + [cookieDomain](mcvid-library/mcvid-function-vars/mcvid-cookiedomain.md)
      + [cookieLifetime](mcvid-library/mcvid-function-vars/mcvid-cookielifetime.md)
      + [disableIdSyncs](mcvid-library/mcvid-function-vars/mcvid-disableidsync.md)
      + [disableThirdPartyCalls](mcvid-library/mcvid-function-vars/mcvid-disablethirdpartycalls.md)
      + [disableThirdPartyCookies](mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](mcvid-library/mcvid-function-vars/mcvid-idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md)
      + [idSyncSSLUseAkamai](mcvid-library/mcvid-function-vars/mcvid-idsyncssluseakamai.md)
      + [isCoopSafe](mcvid-library/mcvid-function-vars/mcvid-coopsafe.md)
      + [loadTimeout](mcvid-library/mcvid-function-vars/mcvid-loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)
      + [resetBeforeVersion](mcvid-library/mcvid-function-vars/mcvid-resetbeforeversion.md)
      + [sdidParamExpiry](mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md)
      + [secureCookie](mcvid-library/mcvid-function-vars/mcvid-securecookie.md)
      + [useCORSOnly](mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md)
      + [whitelistParentDomain e whitelistIframeDomains](mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md)
   + Metodi {#methods}
      + [Metodi](mcvid-library/mcvid-get-set/mcvid-get-set.md)
      + [appendSupplementalDataIDTo](mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (Monitoraggio interdominio)](mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md)
      + [Metodi callTimeOut](mcvid-library/mcvid-get-set/mcvid-timeout-functions.md)
      + [Sincronizzazione ID tramite URL o sorgente dati](mcvid-library/mcvid-get-set/mcvid-idsync.md)
      + [getInstance](mcvid-library/mcvid-get-set/mcvid-getinstance.md)
      + [getAnalyticsVisitorID](mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)
      + [getCustomerIDs](mcvid-library/mcvid-get-set/mcvid-getcustomerids.md)
      + [setCustomerIDs](mcvid-library/mcvid-get-set/mcvid-setcustomerids.md)
      + [getMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-getmcvid.md)
      + [getLocationHint](mcvid-library/mcvid-get-set/mcvid-getlocationhint.md)
      + [getVisitorValues](mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-client-side-id.md)
      + [resetState](mcvid-library/mcvid-get-set/mcvid-resetstate.md)
+ Riferimenti {#reference}
   + [Panoramica di riferimento](mcvid-reference/mcvid-reference.md)
   + Guida di riferimento di Analytics {#analytics-reference}
      + [Panoramica di riferimento di Analytics](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-reference.md)
      + [Impostazione degli ID di Analytics ed Experience Cloud](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md)
      + [Ordine delle operazioni per gli ID di Analytics](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md)
      + [Decisioni relative alla migrazione al servizio Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md)
      + [Scenari di migrazione al servizio Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-migration-scenarios.md)
      + [Richieste Analytics ed Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-legacy-analytics.md)
      + [CNAME per raccolta dati e monitoraggio tra più domini](mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)
      + [Implementazione lato server con JavaScript](mcvid-reference/mcvid-analytics-reference/mcvid-server-side.md)
      + [Periodo di tolleranza per il servizio ID](mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)   
   + [Informativa sulla sicurezza dei contenuti e servizio Experience Cloud ID](mcvid-reference/mcvid-csp.md)
   + [Supporto per COPPA nel servizio Experience Cloud ID](mcvid-reference/mcvid-coppa.md)
   + [Supporto per CORS nel servizio Experience Cloud ID](mcvid-reference/mcvid-cors.md)
   + [ID cliente e stati di autenticazione](mcvid-reference/mcvid-authenticated-state.md)
   + [Metodi della libreria ECID in un world Safari ITP](mcvid-reference/ecid-library-methods.md)
   + [Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID](mcvid-reference/mcvid-regions.md)
   + [Requisiti del servizio Experience Cloud ID](mcvid-reference/mcvid-requirements.md)
   + [Video Heartbeat e il servizio Experience Cloud ID](mcvid-reference/mcvid-heartbeat.md)
   + [Data Workbench e il servizio Experience Cloud ID](mcvid-reference/mcvid-dwb.md)
+ Domande frequenti {#faqs}
   + [Panoramica frequente](mcvid-faq-intro/mcvid-faq-intro.md)
   + [Domande frequenti sul servizio ID](mcvid-faq-intro/mcvid-faq.md)
   + [Domande frequenti su Analytics e sul servizio ID](mcvid-faq-intro/mcvid-analytics-faq.md)
   + [Domande frequenti per altre soluzioni Experience Cloud](mcvid-faq-intro/mcvid-other-faq.md)
+ Note sulla versione del servizio ID {#release-notes}
   + [Note sulla versione 2019](mcvid-release-notes/mcvid-release-notes.md)
   + [Note sulla versione 2018](mcvid-release-notes/mcvid-notes-2018.md)
   + [Note sulla versione 2017](mcvid-release-notes/mcvid-notes-2017.md)
   + [Note sulla versione 2016](mcvid-release-notes/mcvid-notes-2016.md)
   + [Note sulla versione 2015](mcvid-release-notes/mcvid-notes-2015.md)
