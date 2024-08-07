---
description: Leggi questa sezione per essere certo di usare le soluzioni, i servizi e le versioni di codice corrette per Experience Cloud Identity Service.
keywords: Servizio ID
title: Requisiti di Experience Cloud Identity Service
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
source-git-commit: 00ebcaa16ec6b432b480d96fbf79b6a745515b1b
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 100%

---

# Requisiti di Experience Cloud Identity Service {#requirements-for-the-experience-cloud-id-service}

Leggi questa sezione per essere certo di usare le soluzioni, i servizi e le versioni di codice corrette per Experience Cloud Identity Service.

## Requisiti per il successo e il supporto dell&#39;implementazione {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Un&#39;implementazione di successo e supportata deve rispettare (o superare) i requisiti di codice e aderire alle istruzioni fornite nell&#39;[!DNL Adobe] Aiuto di. Un’implementazione non supportata darà risultati imprevisti e impedirà all’assistenza clienti e ai nostri team tecnici di prestare aiuto per la risoluzione dei problemi con il servizio ID.

### Implementazioni standard

Vedi [Tag di Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it) per la tua implementazione standard.

### Implementazioni non standard

Per implementazioni non standard o manuali, devi impostare il servizio ID come descritto dalle procedure di questa guida. Come per le linee guida di DTM presentate sopra, una posizione e un caricamento impropri del codice risulteranno in un’implementazione non supportata.

## Requisiti di Experience Cloud: ID organizzazione {#section-a02f537129a64ffbb690d5738d360c26}

Per utilizzare il servizio ID, la società deve essere abilitata per [!DNL Experience Cloud] e deve disporre di un ID organizzazione. Se non sei sicuro di quale sia lo stato [!DNL Experience Cloud] della tua società e vuoi trovare il tuo ID organizzazione, consulta il seguente elenco.

>[!IMPORTANT]
>
>L&#39;ID organizzazione è sensibile all&#39;uso di maiuscole e minuscole e deve essere utilizzato esattamente come è stato fornito.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stato di Experience Cloud </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Abilitato</b> </p> </td> 
   <td colname="col2"> <p>Se l'azienda è abilitata per <span class="keyword">Experience Cloud</span> ma non possiedi l'ID organizzazione, controlla gli <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=it" format="https" scope="external">ID organizzazione</a> (scorri la sezione <i>Ricerca dell'ID organizzazione</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Non sono sicuro</b> </p> </td> 
   <td colname="col2"> <p> Se non conosci lo stato <span class="keyword">Experience Cloud</span> della tua società, chiedi a chi gestisce il tuo account Adobe se i membri della società possono effettuare l'accesso a <a href="https://experiencecloud.adobe.com" format="https" scope="external">marketing.adobe.com</a> utilizzando un Adobe ID. Se possono farlo, la società è abilitata e l'amministratore può vedere l'ID organizzazione. L'ID organizzazione è indicato nella sezione “Pagina di amministrazione” della pagina di <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=it" format="https" scope="external">amministrazione di Experience Cloud</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Non abilitato</b> </p> </td> 
   <td colname="col2"> <p> Se la società non è abilitata per Experience Cloud, vedi <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=it" format="https" scope="external">Servizi di base - Come abilitare le soluzioni</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisiti di Analytics: raccolta dati regionali (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Tutti i server di tracciamento sono stati convertiti in RDC, pertanto non è necessario modificare il server di tracciamento di Analytics. [Ulteriori informazioni...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=it)

## Librerie dei codici e versioni richieste {#section-ad7542a4317d430fa79fc6b095beb84d}

Nelle seguenti sezioni sono elencate le versioni minime dei codici richieste per usare il servizio [!DNL Experience Cloud] ID.

>[!TIP]
>
>Invece dei requisiti minimi, consigliamo di usare le ultime versioni del codice.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Soluzione Experience Cloud </th> 
   <th colname="col3" class="entry"> Libreria dei codici </th> 
   <th colname="col4" class="entry"> Requisiti di versione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Servizio </span>Experience Cloud ID</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 o successiva </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>Vedi <a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=it" format="https" scope="external">AppMeasurement per JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>1.6.4 o successiva </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Nota:<span class="keyword"> la versione H.27 di Analytics</span> s_code non è più supportata a partire dal rilascio del servizio ID versione 1.6.0. Aggiorna il codice all'ultima versione di AppMeasurement. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Video Heartbeat </p> <p>Guarda il <a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=it" format="https" scope="external">video su Heartbeat 2.x per JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> Vedi <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=it" format="https" scope="external">Libreria di integrazione dei dati</a> (DIL). </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Vedi <a href="https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/overview.html?lang=it" format="https" scope="external">Codice mbox</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Vedi <a href="https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works.html?lang=it" format="https" scope="external">Implementazione at.js</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisiti dell&#39;SDK per Android e iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

Come minimo, il servizio ID richiede le versioni SDK elencate di seguito.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>Invece dei requisiti minimi, consigliamo di usare le ultime versioni del codice.

Il codice SDK deve essere abilitato per il servizio ID. Abilita e scarica il codice SDK più recente per ciascuna app dal tuo account [Adobe Mobile Services](https://mobilemarketing.adobe.com/). Vedi anche:

* [Configurare le opzioni del servizio ID visitatore dell’SDK](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=it)
* [Metodi SDK per Android](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=it)
* [Metodi SDK per iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=it)

>[!MORELIKETHIS]
>
>* [Libreria dei codici](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
