---
description: Questa API asincrona restituisce per impostazione predefinita identificatori per Analytics, il servizio ID, la rinuncia alla raccolta di dati, la geolocalizzazione, e contenuti di metadati BLOB. Inoltre, è possibile controllare gli ID che dovranno essere restituiti con l'enum opzionale visitor.FIELDS.
keywords: Servizio ID
seo-description: Questa API asincrona restituisce per impostazione predefinita identificatori per Analytics, il servizio ID, la rinuncia alla raccolta di dati, la geolocalizzazione, e contenuti di metadati BLOB. Inoltre, è possibile controllare gli ID che dovranno essere restituiti con l'enum opzionale visitor.FIELDS.
seo-title: getVisitorValues
title: getVisitorValues
uuid: 7 fb 831 b 3-cf 7 e -40 e 2-a 219-07 fec 28 ad 49 c
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# getVisitorValues{#getvisitorvalues}

Questa API asincrona restituisce per impostazione predefinita identificatori per Analytics, il servizio ID, la rinuncia alla raccolta di dati, la geolocalizzazione, e contenuti di metadati BLOB. Inoltre, è possibile controllare gli ID che dovranno essere restituiti con l&#39;enum opzionale visitor.FIELDS.

Sommario:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> Sintassi </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> Caso d'uso 1: richiesta di impostazione di dati predefiniti </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> Caso d'uso 2: richiesta di impostazione di dati personalizzati </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> Parametri di risposta definiti </a> </li> 
</ul>

## Sintassi {#section-5aebe3907b2b46e997f45a1d1ed35c09}

This function uses the following syntax (italics represents a placeholder for a variable): ` var *`values`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`ID type`*, visitor.FIELDS. *`ID type`*]);`

Nei parametri della funzione:

* ` *`callback`*` rappresenta il vostro codice di callback che riceve gli ID restituiti.
* *(Facoltativo)* ` visitor.FIELDS. *`Il tipo`*` ID è un enum che consente di specificare [quali valori](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5) ID devono essere restituiti.

Per maggiori informazioni, vedi i casi d&#39;uso seguenti e le definizioni.

## Caso d&#39;uso 1: richiesta di impostazione di dati predefiniti {#section-36a31683558742a5915db3a391e09f7b}

Questo codice restituisce il set di dati standard. La richiesta e la risposta saranno simili a quelle di questi esempi.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

Nella risposta di esempio predefinita, alcuni valori sono stati abbreviati per fini dimostrativi.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## Caso d&#39;uso 2: richiesta di impostazione di dati personalizzati {#section-467b2f4e513344c89b7332b05f6f59f3}

Questo codice utilizza un array facoltativo per restituire un set specifico di ID usando l&#39;enum `visitor.FIELDS` . In questo caso, vogliamo solo l&#39;Experience Cloud ID (MCID) e l&#39;Analytics ID (MCAID) del visitatore. La richiesta e la risposta saranno simili a quelle di questi esempi.

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

La risposta di esempio personalizzata restituisce solo quegli ID specificati nella richiesta.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## Parametri di risposta definiti {#section-4c4c300167694c6fbff1d6c612f372b5}

Nella seguente tabella sono elencati e definiti i parametri di risposta. Questi sono anche tutti i valori nell&#39;enum `visitor.FIELDS`. Nota, questo metodo restituisce una stringa vuota se non ci sono valori per una particolare variabile.

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Valore </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>Metadati <span class="keyword">Audience Manager</span> crittografati noti come BLOB. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>L'ID della regione di raccolta dati. Questo è un identificatore numerico della posizione geografica di un particolare datacenter del servizio ID. </p> <p>Consulta <a href="https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html" format="https" scope="external"> ID regioni DCS, posizioni e nomi host </a> e <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getlocationhint </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>L'ID <span class="keyword">Analytics</span> del visitatore. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>L'Experience Cloud ID del visitatore. </p> <p>Consulta  <a href="../../introduction/cookies.md" format="dita" scope="local"> Cookie e Servizio identità Experience Platform </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>Un flag che indica se un visitatore ha rinunciato alla raccolta dei dati. </p> <p>I valori includono: </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true'</span>: un visitatore ha rinunciato alla raccolta dei dati. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-false'</span>: un visitatore non ha rinunciato alla raccolta dei dati. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

