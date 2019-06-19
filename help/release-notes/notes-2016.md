---
description: Rilasci di funzioni, aggiornamenti o modifiche al servizio Identità Experience Platform per 2016.
keywords: Servizio ID
seo-description: Rilasci di funzioni, aggiornamenti o modifiche al servizio Identità Experience Platform per 2016.
seo-title: Note sulla versione 2016
title: Note sulla versione 2016
uuid: 7 a 5 a 314 a -3 ff 8-4561-9 c 64-6 c 10 d 2223887
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Note sulla versione 2016 {#release-notes}

Rilasci di funzioni, aggiornamenti o modifiche al servizio Identità Experience Platform per 2016.

Queste modifiche vengono anche riportate nelle [note sulla versione di Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/). Per gli annunci precedenti, vedi le [note sulle versioni precedenti](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html).[!DNL Experience Cloud]

## Versione 1.10 {#section-7d719b3213344a46858835042e0214ed}

Novembre 2016

>[!IMPORTANT]
>
>* La versione 1.10 richiede [!DNL AppMeasurement] 1.8.0.
>* Utilizzando la libreria del servizio identità Experience Platform 2.0.0 +, la sincronizzazione degli ID verrà avviata per Adobe Media Optimizer per impostazione predefinita. Consulta [Informazioni sulla sincronizzazione degli ID e delle percentuali di corrispondenza](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-match-rates.html).
>



**Correzioni e miglioramenti**

* Sono state aggiunte istruzioni su come implementare il servizio ID in un ambiente lato server.
* È stata aggiunta la funzione booleana `Visitor.overwriteCrossDomainMCIDAndAID`, che consente di sovrascrivere gli ID Experience Cloud e Analytics su altri domini di cui sei titolare. Consultate [Sovrascrivi ID visitatore](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* È stata aggiunta la marca temporale `TS = UTC`   come proprietà della funzione `visitor.appendVisitorIDsTo`. Il servizio ID utilizza la marca temporale per determinare se devono essere utilizzati gli ID nell&#39;URL di reindirizzamento in base a un intervallo di durata di 5 minuti. Consultare la sezione relativa alla [funzione di aggiunta dell’ID del visitatore](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)

* Aggiunta `Visitor.getLocationHint,` una nuova funzione che restituisce un ID di regione. Consulta [Ottieni ID di regione (hint posizione)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

* Sono state aggiunte le due funzioni `idSyncByURL` e `idSyncByDataSource`, che permettono di implementare manualmente una sincronizzazione ID nel Destination Publishing iFrame. Consulta [Sincronizzazione ID per URL o Origine dati](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* È stato corretto un bug che bloccava la chiamata di tracciamento AppMeasurement se `disableThirdPartyCalls:true`.
* È stato corretto un bug che impediva al servizio ID di passare l&#39;identificatore Experience Cloud ID (MID) tra domini differenti.

## Versione 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Ottobre 2016

**Correzioni e miglioramenti**

* Correzione di un bug per cui gli ID utente univoci di Audience Manager (AAMUUID) venivano trasferiti come Experience Cloud ID al servizio ID.
* Se il time-to-live (TTL) di un cookie AMCV è scaduto, il servizio ID restituirà comunque tali informazioni al server purché il cookie non contenga un Experience Cloud ID. Dopo questa chiamata, il servizio ID effettua una chiamata asincrona per aggiornare il cookie. Ciò consente di migliorare le prestazioni perché non è necessario che il servizio ID attenda una risposta dal server. Può utilizzare i valori del cookie AMCV esistenti e richiedere un aggiornamento.
* Il servizio ID sincronizza automaticamente gli Experience Cloud ID (MID) con Adobe Media Optimizer e altri domini interni di Adobe direttamente sulla pagina. La sincronizzazione automatica è abilitata per tutti gli account esistenti e nuovi. Ciò consente di migliorare le percentuali di corrispondenza di Media Optimizer. Applicabile a VisitorAPI.js versione 1.8 o versioni successive. Consultare anche [Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab). 

**Documentazione nuova e rivista**

**Nuovo:**[Ottieni ID e ID utente dal cookie AMCV](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Versione 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

Settembre 2016

**Correzioni e miglioramenti**

`disableThirdPartyCalls` aggiunto come flag booleano facoltativo che può essere configurato nella funzione `Visitor.getInstance`. Quando `disableThirdPartyCalls= true`, il servizio ID non effettua chiamate ad altri domini. Per impostazione predefinita, `disableThirdPartyCalls= false`. Vei [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Versione 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

Agosto 2016

**Correzioni e miglioramenti**

* Aggiunta di `idSyncAttachIframeOnWindowLoad` come flag opzionale booleano impostabile nella funzione `Visitor.getInstance`. Quando `idSyncAttachIframeOnWindowLoad= true`, il servizio ID carica l&#39;iFrame di sincronizzazione ID al caricamento della finestra. Per impostazione predefinita, il servizio ID carica l&#39;iFrame con la massima velocità possibile. Questo flag *sostituisce* `idSyncAttachIframeASAP`, che è diventato obsoleto. Vedere [Variabili della funzione Visitor. getinstance](../library/function-vars/function-vars.md).

* È stata aggiunta la possibilità di tenere traccia degli [!DNL Experience Cloud] ID attraverso domini diversi, app native e app ibride per transizioni Web. Consultare la sezione relativa alla [funzione di aggiunta dell&#39;ID helper del visitatore](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)

* Sono state aggiunte delle funzioni al codice visitorAPI.js che determinano se il servizio ID ha generato l&#39;ID [!DNL Experience Cloud] del visitatore lato client o lato server, oppure se la chiamata per l&#39;ID è scaduta per timeout. Consultate [Funzioni di tracciamento del timeout](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) e [Tracciamento della generazione degli ID visitatori lato client](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Documentazione nuova e rivista**

Rivisto: [Requisiti per il servizio identità della piattaforma Experience Platform](../reference/requirements.md)

**Problemi noti**

I clienti che utilizzano sulla stessa pagina il codice DIL di [!DNL Audience Manager] e il codice visitorapi.js devono impostare la variabile DIL `secureDataCollection= false`. Consulta [secureDataCollection](https://marketing.adobe.com/resources/help/en_US/aam/?f=dil-secure-data-collection.html).

## Versione 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

Luglio 2016

>[!IMPORTANT]
>
>Per la versione 1.6.0 del servizio [!DNL Experience Cloud] ID *è necessario* appmeasurement per javascript versione 1.6.2. Se effettui l&#39;aggiornamento al servizio ID versione 1.6.0, assicurati di usare la versione corretta del codice appmeasurement.

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funzione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Condivisione risorse tra le origini (CORS) </p> </td> 
   <td colname="col2"> <p>CORS consente ai browser di richiedere risorse da un dominio diverso da quello corrente. Il servizio Experience Platform Identity Service supporta gli standard CORS per abilitare le richieste di risorse lato client. Il servizio ID ripristina le richieste JSONP nei browser che non supportano CORS. </p> <p>Vedi: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> Supporto CORS nel servizio Identità Experience Platform </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Correzioni e miglioramenti**

* È stato aggiunto il parametro `d_fieldgroup` alle chiamate per la sincronizzazione ID verso `dpm.demdex.net`. Questo nuovo parametro è utilizzato per risolvere i problemi interni e per il debug.

* È stato aggiunto un attributo titolo all&#39;iFrame del servizio ID. Un titolo nell&#39;iFrame consente alle utilità per la lettura dello schermo di fornire informazioni sulla pagina agli utenti che necessitano di assistenza per interagire con i contenuti online. L’attributo titolo dell’iFrame è impostato su `Adobe ID Syncing iFrame`.
* È stato aggiunto `idSyncAttachIframeASAP: true` come flag opzionale impostabile nella funzione `Visitor.getInstance`. Quando è `true`, il servizio ID carica l&#39;iFrame di sincronizzazione ID il più rapidamente possibile. In questo modo è possibile aumentare le corrispondenze della sincronizzazione ID. Per impostazione predefinita, il servizio ID carica l&#39;iFrame durante il caricamento della finestra. Vedere [Variabili della funzione Visitor. getinstance](../library/function-vars/function-vars.md).

* È stato corretto un problema relativo a una funzione di callback che bloccava AppMeasurement in un ciclo infinito.
* Il valore predefinito `loadTimeout` è stato modificato da 500 a 30.000 millisecondi. Vedere [Variabili della funzione Visitor. getinstance](../library/function-vars/function-vars.md).

**Documentazione nuova e rivista**

**Novità**

* [Implementazione del servizio identità Experience Platform per Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [Implementazione del servizio Identità Experience Platform per Analytics, Audience Manager e Target](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Elementi revisionati**

* [Requisiti per il servizio identità della piattaforma Experience Platform](../reference/requirements.md)
* [Test e verifica del servizio identità Experience Platform](../implementation-guides/test-verify.md)

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
   <td colname="col2"> <p> iFrame è ora configurato in modo che <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin';</span> </p> <p>Consentendo solamente questi 2 token è possibile migliorare la sicurezza e fornire il servizio ID con la funzionalità di base necessaria alla sincronizzazione ID. </p> <p>L'attributo sandbox non è supportato da Internet Explorer versione 9 o precedenti. Per ulteriori informazioni, consultate la sezione Attributi in questa <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe" format="https" scope="external">documentazione iFrame</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Codifica di Experience Cloud ID (MID) </p> </td> 
   <td colname="col2"> <p>Il servizio ID codifica il valore MID restituito dal server o quando questo è configurato dalla funzione <span class="codeph">visitor.setMarketingCloudVisitorID()</span>. Per ulteriori informazioni sull'identificatore MID, vedi <a href="../introduction/cookies.md" format="dita" scope="local"> Cookie e Experience Cloud ID </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correzioni**

L&#39;API visitatore non forza più una chiamata di risincronizzazione supplementare con Audience Manager quando non è presente alcun ID visitatore Analytics precedente.

## Versione 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Maggio 2016

**Aggiornamenti alla documentazione**

* [Requisiti dell&#39;SDK per Android e iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Workbench dati e Servizio identità Experience Platform](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [Test e verifica del servizio identità Experience Platform](../implementation-guides/test-verify.md)

## 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

Aprile 2016

**Aggiornamenti alla documentazione**

[Implementazione del servizio identità Experience Platform per Target](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

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
   <td colname="col2"> <p>Il servizio <span class="keyword">Experience Cloud</span> ID supporta le richieste di disattivazione del visitatore. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Modifica alle tempistiche di sincronizzazione ID </p> </td> 
   <td colname="col2"> <p>Il servizio <span class="keyword">Experience Cloud ID</span> effettua ora le chiamate per la sincronizzazione ID su ogni chiamata ai server di raccolta dati. In precedenza, il servizio ID effettuava una sola richiesta sulla prima chiamata per ottenere un <span class="keyword">Experience Cloud</span> ID. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Aggiornamenti alla documentazione**

* [Implementazione del servizio Identità Experience Platform per Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd) : Nuova procedura che descrive la modalità [!DNL Analytics]con cui impostare il servizio ID.

* [Decisioni relative alla migrazione al servizio identità Experience Platform](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257) : Testo rivisto per chiarezza. L&#39;utilizzo di un solo dominio consente di effettuare la migrazione da un CNAME di raccolta dati, se non desideri gestirlo più. Se il CNAME funziona correttamente, non è necessario cambiarlo.

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
   <td colname="col2"> <p>Testo aggiornato. Gli ID cliente devono essere trasferiti solo come valori non codificati. L'utilizzo di ID codificati dà luogo a identificatori con doppia codifica. </p> </td> 
  </tr> 
 </tbody> 
</table>

