---
description: Chiama questa funzione del servizio ID per determinare se il servizio ID ha generato un ID visitatore Experience Cloud (MID) lato client. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
keywords: Servizio ID
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 100%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Chiama questa funzione del servizio ID per determinare se il servizio ID ha generato un ID visitatore Experience Cloud (MID) lato client. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.

**Sintassi**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

Nella tabella seguente sono elencate e descritte le risposte restituite da questa funzione.

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Risposta </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> true</span> </p> </td> 
   <td colname="col2"> <p>Il servizio ID non ha potuto ricevere o non ha ricevuto un identificatore MID dal server <span class="keyword">Experience Cloud</span>. Ha creato un identificatore MID localmente, nel browser (lato client) </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>Il servizio ID ha ricevuto un identificatore MID dal server <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> nulle</span> </p> </td> 
   <td colname="col2"> <p>Il servizio ID non ha effettuato una chiamata al server <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>
