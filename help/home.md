---
description: 'Il servizio Experience Cloud ID fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni Experience Cloud. '
keywords: Servizio ID
seo-description: Il servizio Adobe Experience Cloud ID fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni Experience Cloud. Può sostituire il codice di generazione ID di servizi come Analytics, Audience Manager, Target e altre soluzioni o funzionalità Experience Cloud.
seo-title: Servizio Experience Cloud ID
title: Servizio Experience Cloud ID
uuid: b 68194 b 5-e 549-4 f 6 f-bfaf -7744926 aeaac
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# Servizio Experience Cloud ID {#experience-cloud-id-service}

Il servizio Experience Cloud ID (servizio ID) fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni di Experience Cloud. Può sostituire il codice di generazione ID di servizi come Analytics, Audience Manager, Target e altre soluzioni o funzionalità Experience Cloud.

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Introduzione</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="mcvid-introduction/mcvid-overview.md" format="dita" scope="local"> Panoramica </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="mcvid-reference/mcvid-requirements.md" format="dita" scope="local"> Requisiti del servizio Experience Cloud ID </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Implementazione standard con DTM </a> </li> 
     </ul> </p> <p><b>Librerie JavaScript di Experience Cloud ID</b> </p> <p>JavaScript per il servizio Experience Cloud ID si trova all'indirizzo: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>Novità e funzioni</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Servizio di consenso</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="mcvid-faq-intro/ecid-faq-intro.md" format="dita" scope="local"> Domande frequenti </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="mcvid-library/mcvid-function-vars/mcvid-coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
    <draft-comment> 
     <p> <b>Annunci:</b> </p> 
     <p> <p>Importante: Il supporto del servizio ID per Internet Explorer 6, 7 e 8 è obsoleto e verrà interrotto in una versione futura. </p> </p> 
    </draft-comment> </td> 
   <td colname="col2"> <p> <b>Note sulla versione</b> </p> <p><b>La versione 4.0</b> del 12 febbraio 2019 include il servizio <a href="mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> di consenso</a> utilizzato per identificare se è possibile inserire un cookie sul dispositivo o sul browser di un utente quando visita il sito. </p> <p>La versione del 18 gennaio 2018 include l'aggiornamento a JavaScript 3.0.0 e gli aggiornamenti ai metodi API. Consulta  <a href="mcvid-library/mcvid-function-vars/mcvid-disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414" format="dita" scope="local"> Disableidsyncs</a> e <a href="mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md#reference-2dd2d60d12f34f0b98bbb5606b3734cc" format="dita" scope="local"> disablethirdpartycookies</a>. </p> 
    <draft-comment> 
     <p>La versione di ottobre 2017 non include modifiche o aggiornamenti del codice per il servizio ID. Il codice del servizio ID rimane immutato alla release v 2.5. </p> 
    </draft-comment> 
    <draft-comment> 
     <p> La versione di settembre 2017 incrementa il codice del servizio ID alla versione v 2.5. </p> 
    </draft-comment> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Per conoscere le nuove funzioni e le correzioni, vedi le <a href="https://marketing.adobe.com/resources/help/en_US/whatsnew/" format="https" scope="external">note sulla versione di Experience Cloud</a> più recenti. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Per gli annunci precedenti, vedi le <a href="https://marketing-stage.adobe.com/resources/help/en_US/whatsnew/c_legacy_releases.html" format="html" scope="external">note sulle versioni precedenti</a>. </li> 
     </ul> </p> <p> <b>Risorse di Experience Cloud</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> Centro per la privacy Adobe</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="http://www.adobe.com/marketing-cloud.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> Formazione e tutorial di Adobe</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://marketing.adobe.com/resources/help/en_US/home/index.html" scope="external" format="https"> Pagina principale documentazione del prodotto</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

