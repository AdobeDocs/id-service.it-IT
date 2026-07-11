---
description: Leggi questa sezione per essere certo di usare le soluzioni, i servizi e le versioni di codice corrette per il servizio ID visitatore.
keywords: Servizio ID visitatori
title: Requisiti del servizio ID visitatore di Adobe
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
TQID: https://experienceleague.adobe.com/yOoLEIKihVSpDLeZsplTZzg-toOENKlBzsQt2G2YcKk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 39%

---

# Requisiti del servizio ID visitatore di Adobe {#requirements-for-the-experience-cloud-id-service}

Leggi questa sezione per essere certo di usare le soluzioni, i servizi e le versioni di codice corrette per il Servizio ID visitatore.

## Requisiti per il successo e il supporto dell&#39;implementazione {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Un&#39;implementazione di successo e supportata deve rispettare (o superare) i requisiti di codice e aderire alle istruzioni fornite nella guida di Adobe. Un’implementazione non supportata darà risultati imprevisti e impedirà all’Assistenza clienti e ai nostri team tecnici di prestare assistenza per la risoluzione dei problemi con il Servizio ID visitatori.

### Implementazioni standard

Consulta [tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=it) in Raccolta dati Adobe Experience Platform per la tua implementazione standard.

### Implementazioni non standard

Per le implementazioni non standard o manuali, devi impostare il Servizio ID visitatore come descritto dalle procedure di questa guida. Come per le linee guida di implementazione standard di cui sopra, un posizionamento e un caricamento improprio del codice creeranno un’implementazione non supportata.

## Requisiti aziendali di CX: ID organizzazione IMS {#section-a02f537129a64ffbb690d5738d360c26}

Per utilizzare il servizio ID visitatore, la società deve essere abilitata per CX Enterprise e disporre di un ID organizzazione IMS. Se non sei sicuro di quale sia lo stato CX Enterprise della tua azienda e vuoi trovare il tuo ID organizzazione IMS, consulta il seguente elenco.

>[!IMPORTANT]
>
>L’ID organizzazione IMS distingue tra maiuscole e minuscole e deve essere utilizzato esattamente come è stato fornito.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stato aziendale CX </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Abilitato</b> </p> </td> 
   <td colname="col2"> <p>Se la società è abilitata per CX Enterprise ma non disponi del tuo ID organizzazione IMS, vedi <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=it" format="https" scope="external"> ID organizzazione</a> (scorri verso il basso fino alla sezione <i>Trova il tuo ID organizzazione</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Non sono sicuro</b> </p> </td> 
   <td colname="col2"> <p> Se non conosci lo stato CX Enterprise della tua società, chiedi a chi gestisce il tuo account Adobe se i membri della società possono effettuare l'accesso a <a href="https://experiencecloud.adobe.com" format="https" scope="external"> marketing.adobe.com</a> utilizzando un Adobe ID. Se puoi, allora sei abilitato e un amministratore può visualizzare il tuo ID organizzazione IMS. Per trovare l'ID organizzazione IMS, vedere la sezione "Pagina di amministrazione" in <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=it" format="https" scope="external"> CX Enterprise Administration</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Non abilitato</b> </p> </td> 
   <td colname="col2"> <p> Se la società non è abilitata per CX Enterprise, vedere <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=it" format="https" scope="external"> Servizi di base - Abilitazione delle soluzioni</a> per iniziare. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisiti di Analytics: raccolta dati regionali (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Tutti i server di tracciamento sono stati convertiti in RDC, pertanto non è necessario modificare il server di tracciamento di Analytics. [Ulteriori informazioni...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=it)

## Librerie dei codici e versioni richieste {#section-ad7542a4317d430fa79fc6b095beb84d}

Nelle sezioni seguenti sono elencate le versioni minime dei codici necessarie per utilizzare il servizio ID visitatore.

>[!TIP]
>
>Invece dei requisiti minimi, consigliamo di usare le ultime versioni del codice.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Soluzione aziendale CX </th> 
   <th colname="col3" class="entry"> Libreria dei codici </th> 
   <th colname="col4" class="entry"> Requisiti di versione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Servizio ID visitatore</b> </p> </td> 
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
   <td colname="col4"> <p>H.27 </p> <p> <p>Nota: <span class="keyword"> Analytics</span> s_code versione H.27 non è più supportato con il rilascio del servizio ID visitatori versione 1.6.0. Aggiorna il codice all’ultima versione di AppMeasurement. </p> </p> </td> 
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
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Vedi <a href="https://experienceleague.adobe.com/it/docs/target-dev/developer/client-side/at-js-implementation/at-js/overview" format="https" scope="external">Codice mbox</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Vedi <a href="https://experienceleague.adobe.com/it/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works" format="https" scope="external">Implementazione at.js</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisiti dell&#39;SDK per Android e iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

Come minimo, il Servizio ID visitatore richiede le versioni di SDK elencate di seguito.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>Invece dei requisiti minimi, consigliamo di usare le ultime versioni del codice.

Il codice SDK deve essere abilitato per il servizio ID visitatori. Abilita e scarica il codice SDK più recente per ciascuna app dal tuo account [Adobe Mobile Services](https://mobilemarketing.adobe.com/). Vedi anche:

* [Configurare le opzioni del servizio ID visitatore dell’SDK](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=it)
* [Metodi SDK per Android](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=it)
* [Metodi SKD di iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=it)

>[!MORELIKETHIS]
>
>* [Libreria dei codici](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
