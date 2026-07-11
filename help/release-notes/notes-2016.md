---
description: Versioni future, aggiornamenti o modifiche al servizio ID visitatori per il 2016.
keywords: Servizio ID visitatori
title: Note sulla versione 2016
feature-set: Experience Cloud Services
feature: TK421
exl-id: f96b9869-6282-4090-b392-797608e25a51
TQID: https://experienceleague.adobe.com/u91aLAt-ycKk1U1A1yhAVUAonGhV6fHWNRVTZB0QAXI
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11id: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 1114
ht-degree: 47%

---

# Note sulla versione 2016 {#release-notes}

Versioni future, aggiornamenti o modifiche al servizio ID visitatori per il 2016.

Queste modifiche vengono riportate anche nelle [note sulla versione di CX Enterprise](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=it).

## Versione 1.10 {#section-7d719b3213344a46858835042e0214ed}

Novembre 2016

>[!IMPORTANT]
>
>* La versione 1.10 richiede [!UICONTROL AppMeasurement] 1.8.0.
>* Se si utilizza la libreria 2.0.0+ del servizio ID visitatore, la sincronizzazione degli ID verrà avviata per Adobe Media Optimizer per impostazione predefinita. Consulta [Informazioni sulla sincronizzazione degli ID e sui tassi di corrispondenza](/help/introduction/match-rates.md).

**Correzioni e miglioramenti**

* Sono state aggiunte istruzioni su come implementare il servizio ID visitatore in un ambiente lato server.
* Aggiunta di `Visitor.overwriteCrossDomainMCIDAndAID`, una funzione booleana che consente di sovrascrivere gli ID ECID e Analytics su altri domini di cui sei titolare. Consulta [Sovrascrivi ID visitatore](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* È stata aggiunta la marca temporale `TS = UTC` come proprietà della funzione `visitor.appendVisitorIDsTo`. Il servizio ID visitatore utilizza la marca temporale per determinare se deve utilizzare gli ID nell&#39;URL di reindirizzamento in base a un intervallo di durata di 5 minuti. Consultare la sezione relativa alla [funzione di aggiunta dell’ID del visitatore](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)

* È stata aggiunta la nuova funzione `Visitor.getLocationHint,`, che restituisce un ID regionale. Consulta [Ottieni ID di regione (hint posizione)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

* Sono state aggiunte le due funzioni `idSyncByURL` e `idSyncByDataSource`, che permettono di implementare manualmente una sincronizzazione ID nel Destination Publishing iFrame. Consulta [Sincronizzazione ID tramite URL o sorgente dati](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* È stato corretto un bug che bloccava la chiamata di tracciamento AppMeasurement se `disableThirdPartyCalls:true`.
* È stato corretto un bug che impediva al Servizio ID visitatore di passare l’ECID tra domini diversi.

## Versione 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Ottobre 2016

**Correzioni e miglioramenti**

* È stato corretto un bug per cui gli ID utente univoci di Audience Manager (AAMUUID) venivano trasferiti come ECID al servizio ID visitatore.
* Se il time-to-live (TTL) di un cookie AMCV è scaduto, il servizio ID visitatore restituirà comunque tali informazioni al server purché il cookie non contenga un ECID. Dopo questa chiamata, il Servizio ID visitatore effettua una chiamata asincrona per aggiornare il cookie. Questo consente di migliorare le prestazioni perché il Servizio ID visitatore non deve attendere una risposta del server. Può utilizzare i valori del cookie AMCV esistenti e richiedere un aggiornamento.
* Il Servizio ID visitatore sincronizza automaticamente gli ECID (MID) con Adobe Media Optimizer e altri domini interni di Adobe direttamente sulla pagina. La sincronizzazione automatica è abilitata per tutti gli account esistenti e nuovi. Questo consente di migliorare i tassi di corrispondenza per Media Optimizer. Applicabile a `VisitorAPI.js` versione 1.8 o successiva. Consulta anche [Informazioni sulla sincronizzazione degli ID e sui tassi di corrispondenza](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Documentazione nuova e rivista**

**Nuovo:** [Ottieni ID regione e ID utente dal cookie AMCV](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Versione 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

Settembre 2016

**Correzioni e miglioramenti**

`disableThirdPartyCalls` aggiunto come flag booleano facoltativo che può essere configurato nella funzione `Visitor.getInstance`. Quando `disableThirdPartyCalls= true`, il servizio ID visitatore non effettuerà chiamate ad altri domini. Per impostazione predefinita, `disableThirdPartyCalls= false`. Vei [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Versione 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

Agosto 2016

**Correzioni e miglioramenti**

* Aggiunta di `idSyncAttachIframeOnWindowLoad` come flag opzionale booleano impostabile nella funzione `Visitor.getInstance`. Quando `idSyncAttachIframeOnWindowLoad= true`, il servizio ID visitatore carica l&#39;iFrame di sincronizzazione ID al caricamento della finestra. Per impostazione predefinita, il Servizio ID visitatore carica l’iFrame il più rapidamente possibile. Questo flag *sostituisce* `idSyncAttachIframeASAP`, che è diventato obsoleto. Consulta [Variabili della funzione Visitor.getInstance](../library/function-vars/function-vars.md).

* È stata aggiunta la possibilità di tenere traccia degli ECID tra domini diversi, app native e app ibride per transizioni Web. Consultare la sezione relativa alla [funzione di aggiunta dell&#39;ID helper del visitatore](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)

* Sono state aggiunte delle funzioni al codice `VisitorAPI.js` che determinano se il servizio ID visitatore ha generato l&#39;identificatore ECID lato client o lato server del visitatore oppure se la chiamata per l&#39;ID è scaduta per timeout. Consultate [Funzioni di tracciamento del timeout](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) e [Tracciamento della generazione degli ID visitatori lato client](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Documentazione nuova e rivista**

Rivisto: [Requisiti del servizio ID visitatori](../reference/requirements.md)

**Problemi noti**

I clienti che utilizzano sulla stessa pagina il codice DIL di Audience Manager e il codice `VisitorAPI.js` devono impostare la variabile DIL `secureDataCollection= false`. Consulta [secureDataCollection](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=it).

## Versione 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

Luglio 2016

>[!IMPORTANT]
>
>La versione 1.6.0 del servizio ID visitatore *richiede* AppMeasurement per JavaScript versione 1.6.2. Se effettui l’aggiornamento alla versione 1.6.0 del servizio ID visitatore, assicurati di utilizzare la versione corretta del codice AppMeasurement.

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funzione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Condivisione delle risorse multiorigine (CORS) </p> </td> 
   <td colname="col2"> <p>CORS consente ai browser di richiedere risorse da un dominio diverso da quello corrente. Il servizio ID visitatori supporta gli standard CORS per consentire le richieste di risorse tra le origini lato client. Il servizio ID visitatori ripristina le richieste JSONP sui browser che non supportano CORS. </p> <p>Consulta: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> Supporto per CORS <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> nel servizio ID visitatori </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Correzioni e miglioramenti**

* È stato aggiunto il parametro `d_fieldgroup` alle chiamate per la sincronizzazione ID verso `dpm.demdex.net`. Questo nuovo parametro viene utilizzato per la risoluzione interna dei problemi e per il debug.

* È stato aggiunto un attributo titolo all’iFrame del servizio ID visitatore. Un titolo nell&#39;iFrame consente alle utilità per la lettura dello schermo di fornire informazioni sulla pagina agli utenti che necessitano di assistenza per interagire con i contenuti online. L’attributo titolo dell’iFrame è impostato su `Adobe ID Syncing iFrame`.
* È stato aggiunto `idSyncAttachIframeASAP: true` come flag opzionale impostabile nella funzione `Visitor.getInstance`. Quando `true`, il servizio ID visitatore carica l&#39;iFrame di sincronizzazione ID il più rapidamente possibile. Questa funzione è stata progettata per migliorare i tassi di corrispondenza della sincronizzazione ID. Per impostazione predefinita, il Servizio ID visitatore carica l’iFrame al caricamento della finestra. Consulta [Variabili della funzione Visitor.getInstance](../library/function-vars/function-vars.md).

* È stato corretto un problema relativo a una funzione di callback che bloccava AppMeasurement in un ciclo infinito.
* Il valore predefinito `loadTimeout` è stato modificato da 500 a 30.000 millisecondi. Consulta [Variabili della funzione Visitor.getInstance](../library/function-vars/function-vars.md).

**Documentazione nuova e rivista**

**Novità**

* [Implementazione del servizio ID visitatori per Analytics, Audience Manager e Target](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Articoli rivisti:**

* [Requisiti del servizio ID visitatori](../reference/requirements.md)
* [Test e verifica del servizio ID visitatori](../implementation-guides/test-verify.md)

## Versione 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

Giugno 2016

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funzione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Modifiche all'attributo <span class="codeph">iframe.sandbox</span> </p> </td> 
   <td colname="col2"> <p>iFrame è ora configurato in modo che <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin';</span> </p> <p>Consentendo solo questi 2 token è possibile migliorare la sicurezza e fornire al Servizio ID visitatore le funzionalità di base necessarie per la sincronizzazione ID. </p> <p>L'attributo sandbox non è supportato da Internet Explorer versione 9 o precedenti. Per ulteriori informazioni, consultate la sezione Attributi in questa <a href="https://developer.mozilla.org/it-IT/docs/Web/HTML/Element/iframe" format="https" scope="external">documentazione iFrame</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Codifica dell’ECID </p> </td> 
   <td colname="col2"> <p>Il servizio ID visitatore codifica il valore MID restituito dal server o quando è impostato dalla funzione <span class="codeph"> visitor.setMarketingCloudVisitorID() </span>. Per ulteriori informazioni sull'identificatore MID, vedere Cookie <a href="../introduction/cookies.md" format="dita" scope="local"> e l'identificatore ECID </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Problemi risolti**

L’API del visitatore non forza più una chiamata di risincronizzazione aggiuntiva con Audience Manager quando manca l’ID visitatore di Analytics legacy.

## Versione 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Maggio 2016

**Aggiornamenti alla documentazione**

* [Requisiti dell&#39;SDK per Android e iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Test e verifica del servizio ID visitatori](../implementation-guides/test-verify.md)

## Versione 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

Aprile 2016

**Aggiornamenti alla documentazione**

[Implementazione del servizio ID visitatori per Target](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## Versione 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

Marzo 2016

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funzione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Supporto per la disattivazione </p> </td> 
   <td colname="col2"> <p>Il Servizio ID visitatore supporta le richieste di rinuncia del visitatore. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Modifica alle tempistiche di sincronizzazione ID </p> </td> 
   <td colname="col2"> <p>Il Servizio ID visitatore effettua ora le chiamate per la sincronizzazione ID su ogni chiamata ai server di raccolta dati. In precedenza, il Servizio ID visitatore effettuava una sola richiesta sulla prima chiamata per ottenere un ECID. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versione 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Gennaio 2016

**Aggiornamenti alla documentazione**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Argomento </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../reference/authenticated-state.md" format="dita" scope="local"> ID cliente e stati di autenticazione </a> </p> </td> 
   <td colname="col2"> <p>Testo rivisto. Gli ID cliente devono essere trasferiti solo come valori non codificati. Gli ID di codifica creeranno identificatori con doppia codifica. </p> </td> 
  </tr> 
 </tbody> 
</table>


