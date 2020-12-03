---
description: Questa API asincrona restituisce per impostazione predefinita identificatori per Analytics, il servizio ID, la rinuncia alla raccolta di dati, la geolocalizzazione, e contenuti di metadati BLOB. Inoltre, è possibile controllare gli ID che dovranno essere restituiti con l'enum opzionale visitor.FIELDS.
keywords: ID Service
seo-description: Questa API asincrona restituisce per impostazione predefinita identificatori per Analytics, il servizio ID, la rinuncia alla raccolta di dati, la geolocalizzazione, e contenuti di metadati BLOB. Inoltre, è possibile controllare gli ID che dovranno essere restituiti con l'enum opzionale visitor.FIELDS.
seo-title: getVisitorValues
title: getVisitorValues
uuid: 7fb831b3-cf7e-40e2-a219-07fec28ad49c
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 100%

---


# getVisitorValues {#getvisitorvalues}

Questa API asincrona restituisce per impostazione predefinita identificatori per Analytics, il servizio ID, la rinuncia alla raccolta di dati, la geolocalizzazione, e contenuti di metadati BLOB. Inoltre, è possibile controllare gli ID che dovranno essere restituiti con l&#39;enum opzionale visitor.FIELDS.

Sommario:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> Sintassi </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> Caso d'uso 1: richiesta di impostazione di dati predefiniti </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> Caso d'uso 2: richiesta di impostazione di dati personalizzati </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> Parametri di risposta definiti </a> </li> 
</ul>

## Sintassi {#section-5aebe3907b2b46e997f45a1d1ed35c09}

Questa funzione utilizza la seguente sintassi (il corsivo rappresenta un segnaposto per una variabile): ` var *`valori`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`tipo ID`*, visitor.FIELDS. *`tipo ID`*]);`

Nei parametri della funzione:

* ` *`callback`*` rappresenta il codice di callback che riceve l&#39;ID restituito.
* *(Facoltativo)* ` visitor.FIELDS. *`Tipo ID`*` è un enum che ti permette di specificare quali [valori ID](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5) vuoi che siano restituiti da questa funzione.

Per maggiori informazioni, vedi i casi d&#39;uso seguenti e le definizioni.

## Caso d&#39;uso 1: richiesta di impostazione di dati predefiniti {#section-36a31683558742a5915db3a391e09f7b}

Questo codice restituisce il set di dati standard. La richiesta e la risposta potrebbero essere simili ai seguenti esempi.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

Nella risposta di esempio predefinita alcuni valori sono stati abbreviati a scopo dimostrativo.

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

Questo codice utilizza un array facoltativo per restituire un set specifico di ID usando `visitor.FIELDS` l&#39;enum. In questo caso vogliamo solo l’Experience Cloud ID (MCID) e l’ID Analytics (MCAID) del visitatore. La richiesta e la risposta potrebbero essere simili ai seguenti esempi.

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

La risposta di esempio personalizzata restituisce solo gli ID specificati nella richiesta.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## Parametri di risposta definiti {#section-4c4c300167694c6fbff1d6c612f372b5}

Nella seguente tabella sono elencati e definiti i parametri di risposta. Questi sono anche tutti i valori `visitor.FIELDS` nell&#39;enum. Nota che questo metodo restituisce una stringa vuota se non sono presenti valori per una particolare variabile.

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
   <td colname="col2"> <p>L'ID della regione di raccolta dati. Questo è un identificatore numerico per la posizione geografica di un particolare datacenter del servizio ID. </p> <p>Consulta <a href="https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html" format="https" scope="external">ID regioni DCS, posizioni e nomi host</a> e <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getLocationHint </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>L'ID <span class="keyword">Analytics</span> del visitatore. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>L’Experience Cloud ID del visitatore. </p> <p>Consulta <a href="../../introduction/cookies.md" format="dita" scope="local"> I cookie e il servizio Experience Cloud Identity </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>Flag che indica se un visitatore ha rinunciato alla raccolta dati. </p> <p>I valori includono: </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true'</span>: un visitatore ha rinunciato alla raccolta dei dati. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-false'</span>: un visitatore non ha rinunciato alla raccolta dei dati. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

