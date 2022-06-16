---
cloud: platform-cloud
audience: end-user
user-guide-title: Guida del servizio Experience Cloud Identity
breadcrumb-title: Guida al servizio Identity
user-guide-description: Il servizio ID fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni Experience Cloud. Può sostituire il codice di generazione ID per servizi come Analytics, Audience Manager, Target e altre soluzioni o funzionalità Experience Cloud.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 121fde9981e85da6cc56eec35fc931d6040356d7
workflow-type: ht
source-wordcount: '399'
ht-degree: 100%

---


# Guida del servizio Experience Cloud Identity {#using}

+ [Guida del servizio ID](home.md)
+ Panoramica {#intro}
   + [Panoramica](introduction/overview.md)
   + [Informazioni sul servizio ID](introduction/about-id-service.md)
   + [Cookie e il servizio ID](introduction/cookies.md)
   + [Richiesta e impostazione degli ID da parte del servizio ID](introduction/id-request.md)
   + [Sincronizzazione e percentuali di corrispondenza](introduction/match-rates.md)
+ Implementazione {#implementation}
   + [Metodi di implementazione](implementation-guides/implementation-methods.md)
   + [Guide all’implementazione](implementation-guides/implementation-guides.md)
   + [Implementazione con i tag di Experience Platform](implementation-guides/ecid-implement-with-launch.md)
   + [Implementazione per Analytics](implementation-guides/setup-analytics.md)
   + [Implementazione per Target](implementation-guides/setup-target.md)
   + [Implementazione per Analytics e Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implementazione per Analytics, Audience Manager e Target](implementation-guides/setup-aam-analytics-target.md)
   + [Uso del servizio ID con A4T e implementazione lato server di Target](implementation-guides/ecid-a4t-target.md)
   + [Integrazione diretta con il servizio ID](implementation-guides/direct-integration.md)
   + [Casi d’uso dell&#39;integrazione diretta](implementation-guides/direct-integration-examples.md)
   + [Test e verifica del servizio ID](implementation-guides/test-verify.md)
   + Servizio Opt-in {#opt-in-service}
      + [Panoramica del servizio Opt-in](implementation-guides/opt-in-service/optin-overview.md)
      + [Configurazione del servizio Opt-in](implementation-guides/opt-in-service/getting-started.md)
      + [Convalida del servizio Opt-in](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configurazione di Opt-in con Experience Platform Launch](implementation-guides/opt-in-service/launch.md)
      + [Configurare Opt-in con DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Controllare le attività Experience Cloud in base al consenso degli utenti](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Casi d&#39;uso di Opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Riferimenti di Opt-in](implementation-guides/opt-in-service/api.md)
      + [Utilizzo dei servizi Opt-in con il Framework IAB](implementation-guides/opt-in-service/iab.md)
+ API del servizio ID {#id-service-api}
   + [Panoramica delle API del servizio ID](library/library.md)
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
      + [isCoopSafe](library/function-vars/coopsafe.md)
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
   + Guida di riferimento di Analytics {#analytics-reference}
      + [Panoramica delle risorse di riferimento di Analytics](reference/analytics-reference/analytics-reference.md)
      + [Panoramica dell’implementazione di CNAME](reference/analytics-reference/cname.md)
      + [Impostazione degli ID di Analytics ed Experience Cloud](reference/analytics-reference/analytics-ids.md)
      + [Ordine delle operazioni per gli ID di Analytics](reference/analytics-reference/analytics-order-of-operations.md)
      + [Decisioni relative alla migrazione al servizio ID](reference/analytics-reference/migration-decisions.md)
      + [Scenari di migrazione al servizio ID](reference/analytics-reference/migration-scenarios.md)
      + [Analytics e richieste di identità](reference/analytics-reference/legacy-analytics.md)
      + [Implementazione lato server con JavaScript](reference/analytics-reference/server-side.md)
      + [Periodo di tolleranza per il servizio ID](reference/analytics-reference/grace-period.md)
   + [Modifiche all’etichettatura SameSite di Google Chrome](reference/chrome-samesite-labelling.md)
   + [Sicurezza dei contenuti e servizio ID](reference/csp.md)
   + [Supporto per COPPA nel servizio ID](reference/coppa.md)
   + [Supporto per CORS nel servizio ID](reference/cors.md)
   + [ID cliente e stati di autenticazione](reference/authenticated-state.md)
   + [Metodi della libreria ECID in ambito Safari ITP](reference/ecid-library-methods.md)
   + [Identificazione di visitatori univoci](reference/unique-vis-method.md)
   + [Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID](reference/regions.md)
   + [Requisiti del servizio ID](reference/requirements.md)
   + [Video Heartbeat e il servizio ID](reference/heartbeat.md)
   + [Data Workbench e il servizio ID](reference/dwb.md)
   + [Supporto di hashing SHA-256 per setCustomerIDs](reference/hashing-support.md)
+ Domande frequenti {#faqs}
   + [Panoramica sulle domande frequenti](faq-intro/faq-intro.md)
   + [Domande frequenti sul servizio ID](faq-intro/faq.md)
   + [Domande frequenti su Analytics e sul servizio ID](faq-intro/analytics-faq.md)
   + [Domande frequenti per altre soluzioni Experience Cloud](faq-intro/other-faq.md)
+ Note sulla versione del servizio ID {#release-notes}
   + [Note sulla versione 2020](release-notes/release-notes.md)
   + [Note sulla versione 2019](release-notes/notes-2019.md)
   + [Note sulla versione 2018](release-notes/notes-2018.md)
   + [Note sulla versione 2017](release-notes/notes-2017.md)
   + [Note sulla versione 2016](release-notes/notes-2016.md)
   + [Note sulla versione 2015](release-notes/notes-2015.md)
+ [Test per analisi nascosto dal sommario](analytics-test-file-hidetoc.md)
