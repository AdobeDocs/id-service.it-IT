---
description: Chiama queste funzioni del servizio ID per determinare lo stato di timeout di una richiesta dell’ID del servizio Experience Cloud Identity, di Analytics o di Audience Manager. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
keywords: Servizio ID
title: Metodi callTimeOut
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '125'
ht-degree: 100%

---

# Metodi callTimeOut {#calltimeout-methods}

Chiama queste funzioni del servizio ID per determinare lo stato di timeout di una richiesta dell’ID del servizio Experience Cloud Identity, di Analytics o di Audience Manager. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.

## Funzioni di timeout {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Soluzione o servizio </th> 
   <th colname="col2" class="entry"> Sintassi della funzione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Servizio Experience Cloud Identity </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AAMIDCallTimedOut()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Risposte della funzione {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Risposta </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>Il servizio ID ha inviato una richiesta e non è stata ricevuta una risposta prima della scadenza per timeout. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>Il servizio ID ha inviato una richiesta e ha ricevuto una risposta dal server. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>Il servizio ID non ha inviato alcuna richiesta. </p> </td> 
  </tr> 
 </tbody> 
</table>
