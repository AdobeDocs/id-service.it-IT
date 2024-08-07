---
description: Panoramica del funzionamento di Experience Cloud Identity Service con gli ID legacy di Analytics.
keywords: Servizio ID
title: Richieste Analytics ed Experience Cloud ID
exl-id: 8c682159-e23a-4641-9ffd-e0028dc2f305
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 95%

---

# Richieste Analytics ed Experience Cloud ID{#analytics-and-experience-cloud-id-requests}

Panoramica del funzionamento di Experience Cloud Identity Service con gli ID legacy di Analytics.

## Riepilogo {#section-64d8523ff7634cb987d0c6480f587dd3}

Experience Cloud Identity Service era stato integrato in Adobe Analytics. Ora rimane una parte integrale di Analytics, ma esegue altre funzioni importanti per altre soluzioni e funzionalità di [!DNL Experience Cloud]. A causa di questa integrazione storica, la verifica o la scrittura di un ID di Analytics funziona in modo leggermente diverso rispetto al processo generico descritto in [Richiesta e impostazione degli ID da parte di Experience Cloud Identity Service...](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a) Per ulteriori informazioni sull&#39;ordine delle operazioni per la verifica degli ID, consulta [Impostazione degli ID di Analytics ed Experience Cloud](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## Il cookie AMCV non è impostato nel browser {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

Se il cookie [!DNL Experience Cloud] (AMCV) non è presente, una chiamata del servizio ID a [!DNL Adobe] genera una risposta che varia a seconda della presenza o dell’assenza di un ID Analytics legacy. L’ID legacy di [!DNL Analytics] è memorizzato nel [cookie s_vi](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=it). La tabella seguente descrive il modo in cui gli ID vengono scritti nel cookie AMCV in base allo stato del cookie s_vi.

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stato del cookie s_vi </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Il cookie s_vi non è impostato</b> </p> </td> 
   <td colname="col2"> <p>Il servizio ID assegna ai visitatori un <span class="keyword">Experience Cloud ID</span> (MID). Il MID identifica i visitatori in <span class="keyword">Analytics</span> e in altre soluzioni <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Cookie s_vi impostato</b> </p> </td> 
   <td colname="col2"> <p>Quando un visitatore con cookie s_vi accede a un sito in cui è stato implementato Experience Cloud Identity Service, il servizio: </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">Scrive l'ID di <span class="keyword">Analytics</span> memorizzato nel cookie s_vi all'interno del cookie AMCV. Viene scritto come ID di <span class="keyword">Analytics</span> (AID). Questa azione <i>non</i> ha effetti sui conteggi dei visitatori. <span class="keyword"> Analytics</span> continua a identificare gli utenti in base ai loro ID legacy. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">Scrive il MID al cookie AMCV. Il MID identifica gli utenti tra diverse soluzioni. </li> 
    </ul> <p> <p>Con un <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">periodo di tolleranza</a>, la risposta del datacenter include sempre un ID legacy memorizzato nel cookie s_vi. Durante il periodo di tolleranza, l'ID legacy viene scritto nel cookie AMCV come valore AID. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Il valore FID degli utenti identificati dal cookie s_fid non viene migrato nel cookie AMCV. Se gli utenti dispongono del cookie s_fid, vengono migrati come se il cookie s_vi non fosse presente (vedi sopra) e vengono quindi visualizzati come nuovi visitatori nel sito. Per ulteriori informazioni, consulta [Cookie di Analytics](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=it).

## Il cookie AMCV è impostato nel browser {#section-01c088fc565c4b24ba1722c7cc240310}

Se il cookie AMCV è presente, utilizza il MID come identificatore [!DNL Analytics], se nel cookie non è presenta un ID [!DNL Analytics] Analytics legacy.
