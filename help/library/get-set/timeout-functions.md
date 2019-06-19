---
description: Chiama queste funzioni del servizio ID per determinare lo stato di timeout per una richiesta Experience Platform Identity Service, Analytics o Audience Manager ID. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
keywords: Servizio ID
seo-description: Chiama queste funzioni del servizio ID per determinare lo stato di timeout per una richiesta Experience Platform Identity Service, Analytics o Audience Manager ID. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
seo-title: callTimeOut Methods
title: callTimeOut Methods
uuid: e 5047498-11 db -4945-b 356-c 92 b 7 d 447573
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Metodi callTimeOut{#calltimeout-methods}

Chiama queste funzioni del servizio ID per determinare lo stato di timeout per una richiesta Experience Platform Identity Service, Analytics o Audience Manager ID. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.

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
   <td colname="col1"> <p>Servizio identità piattaforma Experience </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. mcidcalltimedout ()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. analyticsidcalltimedout ()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. aamidcalltimedout ()</span> </p> </td> 
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

