---
description: Questa proprietà sovrascrive gli ID Experience Cloud e Analytics di un visitatore che naviga da dominio a un altro. Per sovrascrivere un ID, devi possedere e aver implementato il servizio ID su ciascun dominio. Questo codice non consente di sovrascrivere gli ID su domini che non controlli.
keywords: ID Service
seo-description: Questa proprietà sovrascrive gli ID Experience Cloud e Analytics di un visitatore che naviga da dominio a un altro. Per sovrascrivere un ID, devi possedere e aver implementato il servizio ID su ciascun dominio. Questo codice non consente di sovrascrivere gli ID su domini che non controlli.
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 32%

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Questa proprietà sovrascrive gli ID Experience Cloud e Analytics di un visitatore che naviga da dominio a un altro. Per sovrascrivere un ID, devi possedere e aver implementato il servizio ID su ciascun dominio. Questo codice non consente di sovrascrivere gli ID su domini che non controlli.

**Sintassi:**`Visitor.overwriteCrossDomainMCIDAndAID: true|false` (l&#39;impostazione predefinita è `false`)

**Esempio di codice**

Il codice JavaScript sarà simile al seguente esempio.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**Casi d&#39;uso**

Per tenere traccia dei visitatori del sito, il servizio ID scrive un identificatore [!DNL Experience Cloud] ID (MID) in un cookie del browser. Nella tabella seguente sono elencati e descritti i casi d’uso comuni in cui potrebbe essere utile sovrascrivere un identificatore MID esistente impostato dal servizio ID in un altro dominio.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso d'uso </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Identificare i visitatori su diverse pagine di destinazione del dominio</b> </p> </td> 
   <td colname="col2"> <p>Supponiamo che possiedi i domini A e B. In questo caso puoi impostare <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> quando: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">Ogni dominio ha una propria pagina di destinazione. </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">Un visitatore ha già un cookie (e un identificatore MID) impostato da una precedente visita al dominio B. </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">Vuoi identificare in modo coerente un visitatore che arriva al dominio B dal dominio A. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identificare i visitatori tra le pagine di destinazione e di conversione</b> </p> </td> 
   <td colname="col2"> <p>Supponiamo che possiedi i domini A e B. In questo caso puoi impostare <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> quando: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">Il dominio A è una pagina di destinazione. </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">Il dominio B è una pagina distinta di conversione, prenotazione o altra pagina finale del flusso di lavoro. </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">Un visitatore ha già un cookie (e un identificatore MID) impostato da una precedente visita al dominio B e sai che questi sono MID lato client meno rilevanti rispetto agli MID lato server. </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">Vuoi identificare in modo coerente un visitatore che arriva al dominio B dal dominio A. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identificare i visitatori dalle app mobili ai browser Web</b> </p> </td> 
   <td colname="col2"> <p>Questo caso di utilizzo è leggermente diverso. Si tratta di identificare gli utenti che si spostano da un’app mobile al sito Web. In questo caso, il visitatore ha già un identificatore MID impostato localmente da un’app mobile e un diverso identificatore MID impostato in un cookie del sito Web. Puoi impostare <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> per sovrascrivere l'identificatore MID impostato nel cookie del browser con l'identificatore MID impostato dall'app mobile. </p> </td> 
  </tr> 
 </tbody> 
</table>

