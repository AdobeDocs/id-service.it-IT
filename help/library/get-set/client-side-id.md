---
description: Chiama questa funzione del servizio ID per determinare se il servizio ID ha generato un ID visitatore Experience Cloud (MID) lato client. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
keywords: Servizio ID
seo-description: Chiama questa funzione del servizio ID per determinare se il servizio ID ha generato un ID visitatore Experience Cloud (MID) lato client. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1 c 39 ac 60-1 d 2 b -4 ed 4-a 2 ea -30 d 680 e 61 e 10
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Chiama questa funzione del servizio ID per determinare se il servizio ID ha generato un ID visitatore Experience Cloud (MID) lato client. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.

**Sintassi**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

La tabella seguente elenca e descrive le risposte restituite da questa funzione.

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

