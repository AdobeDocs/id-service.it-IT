---
description: Le funzioni idSyncByURL e idSyncByDataSource del servizio ID consentono di implementare manualmente una sincronizzazione ID nell’iFrame di pubblicazione della destinazione. Sono disponibili in VisitorAPI.js versione 1.10 o successiva.
keywords: Servizio ID
seo-description: Le funzioni idSyncByURL e idSyncByDataSource del servizio ID consentono di implementare manualmente una sincronizzazione ID nell’iFrame di pubblicazione della destinazione. Sono disponibili in VisitorAPI.js versione 1.10 o successiva.
seo-title: Sincronizzazione ID tramite URL o sorgente dati
title: Sincronizzazione ID tramite URL o sorgente dati
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
exl-id: a22e6b47-00ff-4b51-9958-ddeccc1e507e
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '275'
ht-degree: 100%

---

# Sincronizzazione ID tramite URL o sorgente dati {#id-synchronization-by-url-or-data-source}

Le funzioni idSyncByURL e idSyncByDataSource del servizio ID consentono di implementare manualmente una sincronizzazione ID nell’iFrame di pubblicazione della destinazione. Sono disponibili in VisitorAPI.js versione 1.10 o successiva.

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
   <td colname="col2"> <p>Tra partner dati diversi e <span class="keyword">Audience Manager</span> utilizzando un URL personalizzato per la sincronizzazione degli ID. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>Se conosci già gli identificatori DPID e DPUUID e vuoi inviarli ad <span class="keyword">Audience Manager</span> nel formato standard di URL per la sincronizzazione degli ID. </p> <p></p> </td> 
  </tr> 
 </tbody> 
</table>

**Proprietà**

Nella tabella seguente sono elencate e definite le proprietà di entrambe le funzioni.

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
   <td colname="col3"> <p>ID univoco del fornitore di dati per l’utente. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> Numero </td> 
   <td colname="col3"> <p> <i>(Facoltativo)</i> Imposta la data di scadenza del cookie. Deve essere un numero intero. Il valore predefinito è 20160 minuti (14 giorni). </p> </td> 
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

* `%TIMESTAMP%`: genera una marca temporale (in millisecondi). Utilizzato per svuotare la cache.
* `%DID%`: inserisce l’ID di Audience Manager per l’utente.
* `%HTTP_PROTO%`: imposta il protocollo di comunicazione (`http` o `https`).

## Codice di esempio e output {#section-0115615c37584a19a2ab11e917c4e7e9}

Entrambe le funzioni restituiscono `Successfully queued` in caso di esito positivo. In caso di esito negativo, restituiscono una stringa con un messaggio di errore.

### visitor.idSyncByURL

**Codice campione**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Output campione**

```
http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D
```

### visitor.idSyncByDataSource

**Codice campione**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dpuuid: '98765', // must be a string 
     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Output campione**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORELIKETHIS]
>
>* [DIL idSync](https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/dil-api/dil-instance-methods.html#idsync)

