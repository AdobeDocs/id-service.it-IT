---
description: Chiama queste funzioni del servizio ID visitatore per determinare lo stato di timeout di una richiesta del servizio ID visitatore, di Analytics o di Audience Manager ID. Disponibile in VisitorAPI.js versione 1.7.0 o successiva.
keywords: Servizio ID visitatori
title: Metodi callTimeOut
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
TQID: https://experienceleague.adobe.com/DIis78iaPQ7qpawlKwWCwReXbh5Mt0K8J3w-5KYdhmg
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 129
ht-degree: 31%

---

# Metodi callTimeOut{#calltimeout-methods}

Chiama queste funzioni del servizio ID visitatore per determinare lo stato di timeout di una richiesta del servizio ID visitatore, di Analytics o di Audience Manager ID. Disponibile in `VisitorAPI.js` versione 1.7.0 o successiva.

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
   <td colname="col1"> <p>Servizio ID visitatori </p> </td> 
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
   <td colname="col2"> <p>Il servizio ID visitatore ha inviato una richiesta e la richiesta è scaduta. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>Il Servizio ID visitatore ha inviato una richiesta e ha ricevuto una risposta dal server. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>Il servizio ID visitatore non ha inviato una richiesta. </p> </td> 
  </tr> 
 </tbody> 
</table>

