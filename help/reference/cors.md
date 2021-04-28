---
description: I browser usano Cross Origin Resource Sharing (CORS) per richiedere risorse da un dominio diverso da quello corrente. Il servizio Experience Cloud Identity supporta gli standard CORS per consentire tali richieste di risorse lato client tra origini diverse. Il servizio ID utilizza invece le richieste JSONP nei browser più datati che non supportano CORS.
keywords: Servizio ID
seo-description: I browser usano Cross Origin Resource Sharing (CORS) per richiedere risorse da un dominio diverso da quello corrente. Il servizio Experience Cloud Identity supporta gli standard CORS per consentire tali richieste di risorse lato client tra origini diverse. Il servizio ID utilizza invece le richieste JSONP nei browser più datati che non supportano CORS.
seo-title: Supporto per CORS nel servizio Experience Cloud Identity
title: Supporto per CORS nel servizio Experience Cloud Identity
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
exl-id: 0e8ffe85-8d1f-42a0-aae3-a2b3b28c7bce
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '674'
ht-degree: 100%

---

# Supporto per CORS nel servizio Experience Cloud Identity {#cors-support-in-the-experience-cloud-id-service}

I browser usano Cross Origin Resource Sharing (CORS) per richiedere risorse da un dominio diverso da quello corrente. Il servizio Experience Cloud Identity supporta gli standard CORS per consentire tali richieste di risorse lato client tra origini diverse. Il servizio ID utilizza invece le richieste JSONP nei browser più datati che non supportano CORS.

## Problemi relativi a criteri per la stessa origine e richieste del servizio ID {#section-6608cf46d27143eeaeabacaa6aa14e8e}

I criteri per la stessa origine sono controlli di sicurezza o restrizioni applicati dal browser Web. Quando viene applicato a questo livello, il browser stesso determina se una richiesta di risorse effettuata da una pagina all’altra sarà consentita o bloccata. Per determinare se una richiesta è della stessa origine, il browser confronta:

* URI (Uniform Resource Identifiers)
* Nomi host (ad esempio, http://www.my-webpage-example.com)
* Numeri di porta (ad esempio, porte 80 e 440 per le richieste HTTP e HTTPS)

Il browser consente una richiesta se entrambe le pagine condividono queste caratteristiche; in caso contrario, blocca le richieste di risorse.

## CORS risolve i problemi relativi a criteri per la stessa origine {#section-76c87ec3295d447bab220c84f138c235}

CORS offre un modo sicuro ed efficace per richiedere risorse tra domini diversi. La specifica CORS include un set di intestazioni HTTP utilizzate dai browser per inviare, ricevere e valutare richieste di risorse. La valutazione di una richiesta di risorse è detta *`preflight check`*. Questo controllo consente ai browser e ai server di determinare quali richieste sono consentite o bloccate. Il controllo preliminare è trasparente per l’app, l’API o lo script che richiede una risorsa. Due intestazioni importanti nel processo di richiesta delle risorse sono le seguenti:

* `Origin`: intestazione di richiesta che identifica l&#39;origine di una richiesta.
* `Access-Control-Allow-Origin`: intestazione di richiesta che indica se una risorsa può essere condivisa con il richiedente.

Vediamo come funzionano queste intestazioni. In questo esempio, supponiamo che una società di servizi finanziari abbia implementato il servizio [!DNL Experience Cloud] ID sul suo sito, www.finance-website.com. La tabella seguente definisce il modo in cui le intestazioni di richiesta e risposta CORS verificano l’accesso a una risorsa.

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Azione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Richiesta</b> </p> </td> 
   <td colname="col2"> <p>Al caricamento della pagina del sito della società di servizi finanziari, il browser invia una richiesta a <span class="codeph">dpm.demdex.net</span>. Si tratta di una chiamata al dominio dei server di raccolta dati (DCS) utilizzati dal servizio ID. Questa richiesta tra domini diversi include l’intestazione: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin: https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Risposta</b> </p> </td> 
   <td colname="col2"> <p>La risposta dal dominio DCS include queste intestazioni che consentono al sito della società di servizi finanziari di accedere alle risorse richieste: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

Vedi anche [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

## Altri benefici di CORS {#section-6f44f30694c44f95bf9854b8a2af8449}

La tabella seguente descrive alcuni dei vantaggi offerti da CORS ai clienti che utilizzano il servizio ID.

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Beneficio </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>Maggiore sicurezza</b> </p> </td> 
   <td colname="col2"> <p>CORS utilizza <a href="https://developer.mozilla.org/it-IT/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a> per richiedere e trasferire i dati. Questo metodo è più sicuro di una richiesta JSONP. In questo modo si evita di eseguire JavaScript arbitrari che potrebbero essere contenuti nella risposta del DCS. Il payload di risposta XMLHttpRequest di CORS viene analizzato dal JavaScript del servizio ID e non semplicemente eseguito in una funzione di callback. </p> <p> <p>Nota: per accettare i cookie, la proprietà <span class="codeph">withCredentials </span>dell'oggetto <span class="codeph">XMLHttpRequest</span> deve essere impostata su <span class="codeph">true</span>. Questa proprietà è supportata in Chrome, Firefox, Internet Explorer (v10+), Opera e Safari. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Miglioramenti delle prestazioni</b> </p> </td> 
   <td colname="col2"> <p>CORS consente di migliorare le prestazioni perché: </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">Il browser gestisce le richieste di risorse. Il processo di richiesta è trasparente per il servizio ID. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">A differenza delle richieste JSONP asincrone, il browser non toglie priorità e mette in coda le richieste CORS. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">Il servizio ID risponde in modo permissivo. Questo significa che quando un URL viene passato come <span class="codeph">Origin</span>, il servizio ID consente l'accesso alla pagina alle risorse richieste. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
