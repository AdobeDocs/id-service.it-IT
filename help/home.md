---
description: 'Il servizio Experience Cloud Identity fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni di Experience Cloud. '
keywords: Servizio ID
title: Servizio Experience Cloud Identity
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Servizio Adobe Experience Cloud Identity {#experience-cloud-id-service}

Il servizio Adobe Experience Cloud Identity (servizio ID) fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni di Experience Cloud. Può sostituire il codice di generazione ID di servizi come Analytics, Audience Manager, Target e altre soluzioni o funzionalità Experience Cloud.

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Introduzione</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local"> Panoramica </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Requisiti del servizio Experience Cloud Identity </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Implementazione standard con DTM </a> </li> 
     </ul> </p> <p><b>Librerie JavaScript di Experience Cloud ID</b> </p> <p>JavaScript per il servizio Experience Cloud Identity si trova all’indirizzo: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>Novità e funzioni</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Servizio Opt-in</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> Domande frequenti </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>Note sulla versione</b> </p> <p>La <b>versione 4.4</b> del 17 luglio 2019 include il supporto dell’<a href="reference/hashing-support.md" format="dita" scope="local">algoritmo di hashing SHA-256</a> che consente di ricevere gli ID o indirizzi e-mail dei clienti e di inoltrarli con hashing.</p><p>La <b>versione 4.0</b> del 12 febbraio 2019 include il <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">servizio Opt-in</a> utilizzato per identificare se è possibile inserire un cookie sul dispositivo o nel browser di un utente quando visita il sito. </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Per conoscere le nuove funzioni e le correzioni, vedi le <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=en" format="https" scope="external">note sulla versione di Experience Cloud</a> più recenti. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Per le versioni precedenti consulta la sezione <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=en" format="html" scope="external">note sulla versione precedente</a>. </li> 
     </ul> </p> <p> <b>Risorse di Experience Cloud</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/it/privacy.html" format="http" scope="external"> Centro per la privacy Adobe</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://experienceleague.adobe.com/docs/home.html?lang=en" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/it/learning.html?promoid=KAUDK" scope="external" format="http"> Formazione e tutorial di Adobe</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/it/support/experience-cloud.html" scope="external" format="https"> Pagina principale documentazione del prodotto</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
