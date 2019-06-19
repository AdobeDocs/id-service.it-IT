---
description: Questa proprietà sovrascrive gli ID Experience Cloud e Analytics di un visitatore che naviga da dominio a un altro. Per sovrascrivere un ID, devi possedere e aver implementato il servizio ID per ciascun dominio. Questo codice non ti permette di sovrascrivere gli ID per domini che non sono sotto il tuo controllo.
keywords: Servizio ID
seo-description: Questa proprietà sovrascrive gli ID Experience Cloud e Analytics di un visitatore che naviga da dominio a un altro. Per sovrascrivere un ID, devi possedere e aver implementato il servizio ID per ciascun dominio. Questo codice non ti permette di sovrascrivere gli ID per domini che non sono sotto il tuo controllo.
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8 e 48127 a-ac 62-4 ea 0-9756-2 a 27 b 20 ecbcf
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Questa proprietà sovrascrive gli ID Experience Cloud e Analytics di un visitatore che naviga da dominio a un altro. Per sovrascrivere un ID, devi possedere e aver implementato il servizio ID per ciascun dominio. Questo codice non ti permette di sovrascrivere gli ID per domini che non sono sotto il tuo controllo.

**Syntax:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (default is `false`)

**Esempio di codice**

Il codice JavaScript sarà simile a quello di questo esempio.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**Casi d&#39;uso**

Per tenere traccia dei visitatori del sito, il servizio ID scrive un identificatore [!DNL Experience Cloud] ID (MID) in un cookie del browser. Nella tabella seguente sono elencati e descritti alcuni casi d&#39;uso di situazioni in cui può essere utile sovrascrivere un identificatore MID esistente impostato dal servizio ID in un altro dominio.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso d'uso </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Identificare i visitatori su pagine di destinazione di altri domini</b> </p> </td> 
   <td colname="col2"> <p>Supponiamo che possiedi i domini A e B. In questo caso puoi impostare <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> quando: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">Ogni dominio ha una propria pagina di destinazione. </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">Un visitatore ha già un cookie (e un identificatore MID) impostato da una precedente visita al dominio B. </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">Vuoi identificare in modo coerente i visitatori che arrivano al dominio B dal dominio A. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identificare i visitatori di diverse pagine di destinazione e conversione</b> </p> </td> 
   <td colname="col2"> <p>Supponiamo che possiedi i domini A e B. In questo caso puoi impostare <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> quando: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">Il dominio A è una pagina di destinazione. </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">Il dominio B è una pagina distinta di conversione, di prenotazione o altro tipo di pagina finale di un flusso di lavoro. </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">Un visitatore ha già un cookie (e un identificatore MID) impostato da una precedente visita al dominio B e sai che questi sono identificatori MID lato client meno rilevanti rispetto agli identificatori MID lato server. </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">Vuoi identificare in modo coerente i visitatori che arrivano al dominio B dal dominio A. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identificare i visitatori da app mobili a browser Web</b> </p> </td> 
   <td colname="col2"> <p>Questo caso d'uso è leggermente diverso. Si tratta di identificare gli utenti che dopo aver usato un'app mobile accedono anche al sito Web. In questo caso, il visitatore ha già un identificatore MID impostato localmente da un'app mobile e un diverso identificatore MID impostato nel cookie del sito Web. Puoi impostare <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> per sovrascrivere l'identificatore MID impostato nel cookie del browser con l'identificatore MID impostato dall'app mobile. </p> </td> 
  </tr> 
 </tbody> 
</table>

