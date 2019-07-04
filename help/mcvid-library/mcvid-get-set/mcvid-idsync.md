---
description: Le funzioni idSyncByURL e idSyncByDataSource del servizio ID permettono di implementare manualmente una sincronizzazione ID nell'iFrame di pubblicazione della destinazione. Sono disponibili in VisitorAPI.js versione 1.10 o successiva.
keywords: Servizio ID
seo-description: Le funzioni idSyncByURL e idSyncByDataSource del servizio ID permettono di implementare manualmente una sincronizzazione ID nell'iFrame di pubblicazione della destinazione. Sono disponibili in VisitorAPI.js versione 1.10 o successiva.
seo-title: Sincronizzazione ID tramite URL o sorgente dati
title: Sincronizzazione ID tramite URL o sorgente dati
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Sincronizzazione ID tramite URL o sorgente dati{#id-synchronization-by-url-or-data-source}

Le funzioni idSyncByURL e idSyncByDataSource del servizio ID permettono di implementare manualmente una sincronizzazione ID nell&#39;iFrame di pubblicazione della destinazione. Sono disponibili in VisitorAPI.js versione 1.10 o successiva.

Sommario:

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-idsync.md#section-90ac61617482463aaf4c57009b830332" format="dita" scope="local"> Sintassi, proprietà e macro </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-idsync.md#section-0115615c37584a19a2ab11e917c4e7e9" format="dita" scope="local"> Codice di esempio e output </a> </li> 
</ul>

## Sintassi, proprietà e macro {#section-90ac61617482463aaf4c57009b830332}

**Sintassi**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Codice </th> 
   <th colname="col2" class="entry"> Sincronizza gli ID utente </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>Tra partner dati diversi e <span class="keyword">Audience Manager</span> utilizzando un URL personalizzato per la sincronizzazione degli ID. </p> <p> 
     <draft-comment>
       Tra partner di dati diversi e Audience Manager. Ad esempio, il partner x lo utilizzerà per sincronizzare un ID utente con il partner y e inviarlo ad Audience Manager. 
     </draft-comment> </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>Se conosci già gli identificatori DPID e DPUUID e vuoi inviarli ad <span class="keyword">Audience Manager</span> nel formato standard di URL per la sincronizzazione degli ID. </p> <p> 
     <draft-comment>
       Quando conosci già l'ID utente e vuoi inviarlo ad Audience Manager. 
     </draft-comment> </p> </td> 
  </tr> 
 </tbody> 
</table>

**Proprietà**

Nella seguente tabella sono elencate e definite le proprietà di entrambe le funzioni.

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nome </th> 
   <th colname="col2" class="entry"> Tipo </th> 
   <th colname="col3" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> Stringa </td> 
   <td colname="col3"> <p>ID del fornitore dei dati assegnato da Audience Manager. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> Stringa </td> 
   <td colname="col3"> <p>ID univoco del fornitore di dati per l'utente. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> Numero </td> 
   <td colname="col3"> <p> <i>(Facoltativo)</i> Imposta la data di scadenza del cookie. Deve essere un numero intero. Impostazione predefinita: 20160 minuti (14 giorni). </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> Stringa </td> 
   <td colname="col3"> <p>URL di destinazione. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Macro**

Entrambe le funzioni accettano le seguenti macro:

* ** `%TIMESTAMP%`: **genera una marca temporale (in millisecondi). Utilizzato per svuotare la cache.
* ** `%DID%`: **inserisce l&#39;ID di Audience Manager per l&#39;utente.
* ** `%HTTP_PROTO%`: **Imposta il protocollo di comunicazione (`http` o `https`).

## Codice di esempio e output {#section-0115615c37584a19a2ab11e917c4e7e9}

Entrambe le funzioni restituiscono `Successfully queued` in caso di esito positivo. In caso di esito negativo, restituiscono la stringa di un messaggio di errore.

**visitor.idSyncByURL**

<table id="table_56AD8291DF9445C69CC2BF50435E1626"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Codice di esempio </th> 
   <th colname="col2" class="entry"> Output di esempio </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Crea istanza visitatore 
      var visitor = Visitor.getInstance("MARKETING-CLOUD-ORG-ID-HERE",{});

    //&amp;nbsp;Fires&amp;nbsp;url&amp;nbsp;with&amp;nbsp;macros&amp;nbsp;replaced
    visitor.idSyncByURL({
    &amp;nbsp;dpid:&amp;nbsp;&#39;24&#39;,&amp;nbsp;//&amp;nbsp;must&amp;nbsp;be&amp;nbsp;a&amp;nbsp;string
    &amp;nbsp;url:&amp;nbsp;&#39;//su.addthis.com/red/usync?pid=16&amp;amp;puid=%DID%&amp;amp;url=%HTTP_PROTO%%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D&#39;,
    &amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp;
    }); &lt;/code&gt; &lt;/p&gt; &lt;/td&gt;
<td colname="col2"> <p> <span class="codeph"> http://su.addthis.com/red/usync?pid=16&amp;puid=28777806459181003670799219185178493848&amp;url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

**visitor.idSyncByDataSource**

<table id="table_90D61A7E715D47238AAFF2808B33C2F0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Codice di esempio </th> 
   <th colname="col2" class="entry"> Output di esempio </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Crea istanza visitatore 
      var visitor = Visitor.getInstance("MARKETING-CLOUD-ORG-ID-HERE",{});

    //&amp;nbsp;Fires&amp;nbsp;&#39;http:/https:&#39;&amp;nbsp;+&amp;nbsp;&#39;//dpm.demdex.net/ibs:dpid=&amp;lt;dpid&amp;gt;&amp;amp;dpuuid=&amp;lt;dpuuid&amp;gt;&#39;
    visitor.idSyncByDataSource({
    &amp;nbsp;dpid:&amp;nbsp;&#39;24&#39;,&amp;nbsp;//&amp;nbsp;must&amp;nbsp;be&amp;nbsp;a&amp;nbsp;string
    &amp;nbsp;dpuuid:&amp;nbsp;&#39;98765&#39;,&amp;nbsp;//&amp;nbsp;must&amp;nbsp;be&amp;nbsp;a&amp;nbsp;string
    &amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp;
    }); &lt;/code&gt; &lt;/p&gt; &lt;/td&gt;
<td colname="col2"> <p> <span class="codeph"> http://dpm.demdex.net/ibs:dpid=24&amp;dpuuid=98765 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_LIKE_THIS]
>
>* [DIL idSync](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html)

