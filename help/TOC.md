---
cloud: platform-cloud
product: Servizio ID
audience: utente finale
user-guide-title: Aiuto del servizio Experience Cloud ID
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: 4fbfefddcf36855f32f2a4047e19ef0b22fc508c

---


# Experience Cloud ID Service Help {#using}

+ [Guida al servizio ID](home.md)
+ Panoramica {#intro}
   + [Panoramica](introduction/overview.md)
   + [Informazioni sul servizio ID](introduction/about-id-service.md)
   + [Cookie e il servizio ID](introduction/cookies.md)
   + [Richiesta e impostazione degli ID da parte del servizio ID](introduction/id-request.md)
   + [Informazioni sulla sincronizzazione degli e sulle percentuali di corrispondenza](introduction/match-rates.md)
+ Guide all&#39;implementazione {#implementation-guides}
   + [Guide all&#39;implementazione](implementation-guides/implementation-guides.md)
   + [Metodi di implementazione](implementation-guides/implementation-methods.md)
   + [Implementazione con Experience Platform Launch](implementation-guides/ecid-implement-with-launch.md)
   + [Implementazione con DTM](implementation-guides/standard.md)
   + [Implementazione per Analytics](implementation-guides/setup-analytics.md)
   + [Implementazione per Target](implementation-guides/setup-target.md)
   + [Implementazione per Analytics e Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implementazione per Analytics, Audience Manager e Target](implementation-guides/setup-aam-analytics-target.md)
   + [Uso del servizio ID con A4T e l&#39;implementazione lato server di Target](implementation-guides/ecid-a4t-target.md)
   + [Integrazione diretta con il servizio ID](implementation-guides/direct-integration.md)
   + [Casi d&#39;uso dell&#39;integrazione diretta](implementation-guides/direct-integration-examples.md)
   + [Verificare e verificare il servizio ID](implementation-guides/test-verify.md)
   + Documentazione Opt-in {#opt-in-service}
      + [Panoramica del servizio Opt-in](implementation-guides/opt-in-service/optin-overview.md)
      + [Configurazione del servizio Opt-in](implementation-guides/opt-in-service/getting-started.md)
      + [Convalida del servizio Opt-in](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configurazione di Opt-in con Experience Platform Launch](implementation-guides/opt-in-service/launch.md)
      + [Configurare Opt-in con DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Casi d&#39;uso di Opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Riferimenti di Opt-in](implementation-guides/opt-in-service/api.md)
      + [(beta) Utilizzo dei servizi Opt-in con il framework IAB](implementation-guides/opt-in-service/iab.md)
+ API del servizio ID {#id-service-api}
   + [Panoramica API servizio ID](library/library.md)
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
   + [Panoramica di riferimento](reference/reference.md)
   + Guida di riferimento di Analytics {#analytics-reference}
      + [Panoramica sulla guida di riferimento di Analytics](reference/analytics-reference/analytics-reference.md)
      + [Impostazione degli ID di Analytics ed Experience Cloud](reference/analytics-reference/analytics-ids.md)
      + [Ordine delle operazioni per gli ID di Analytics](reference/analytics-reference/analytics-order-of-operations.md)
      + [Decisioni relative alla migrazione al servizio ID](reference/analytics-reference/migration-decisions.md)
      + [Scenari di migrazione al servizio ID](reference/analytics-reference/migration-scenarios.md)
      + [Analytics e richieste di identità](reference/analytics-reference/legacy-analytics.md)
      + [CNAME per raccolta dati e monitoraggio tra più domini](reference/analytics-reference/cname.md)
      + [Implementazione lato server con JavaScript](reference/analytics-reference/server-side.md)
      + [Periodo di tolleranza per il servizio ID](reference/analytics-reference/grace-period.md)
   + [Informativa sulla sicurezza dei contenuti e servizio ID](reference/csp.md)
   + [Supporto per COPPA nel servizio ID](reference/coppa.md)
   + [Supporto CORS nel servizio ID](reference/cors.md)
   + [ID cliente e stati di autenticazione](reference/authenticated-state.md)
   + [Metodi della libreria ECID in un world Safari ITP](reference/ecid-library-methods.md)
   + [Ottenere gli ID di utente e regione dal cookie AMCV o dal servizio ID](reference/regions.md)
   + [Requisiti del servizio ID](reference/requirements.md)
   + [Video Heartbeat e il servizio ID](reference/heartbeat.md)
   + [Workbench dati e servizio ID](reference/dwb.md)
+ Domande frequenti {#faqs}
   + [Panoramica sulle domande frequenti](faq-intro/faq-intro.md)
   + [Domande frequenti sul servizio ID](faq-intro/faq.md)
   + [Domande frequenti su Analytics e sul servizio ID](faq-intro/analytics-faq.md)
   + [Domande frequenti per altre soluzioni Experience Cloud](faq-intro/other-faq.md)
+ Note sulla versione del servizio ID {#release-notes}
   + [Note sulla versione 2019](release-notes/release-notes.md)
   + [Note sulla versione 2018](release-notes/notes-2018.md)
   + [Note sulla versione 2017](release-notes/notes-2017.md)
   + [Note sulla versione 2016](release-notes/notes-2016.md)
   + [Note sulla versione 2015](release-notes/notes-2015.md)
