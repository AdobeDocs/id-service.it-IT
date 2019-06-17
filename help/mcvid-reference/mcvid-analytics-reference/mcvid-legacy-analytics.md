---
description: Panoramica del funzionamento del servizio Experience Cloud ID con gli ID Analytics legacy.
keywords: Servizio ID
seo-description: Panoramica del funzionamento del servizio Experience Cloud ID con gli ID Analytics legacy.
seo-title: Richieste Analytics ed Experience Cloud ID
title: Richieste Analytics ed Experience Cloud ID
uuid: 28 beed 16-7 ef 9-4824-8 e 82-853930756 eca
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Richieste Analytics ed Experience Cloud ID{#analytics-and-experience-cloud-id-requests}

Panoramica del funzionamento del servizio Experience Cloud ID con gli ID Analytics legacy.

## Riepilogo {#section-64d8523ff7634cb987d0c6480f587dd3}

Il servizio Experience Cloud ID era stato integrato in Adobe Analytics. Ora rimane una parte integrale di Analytics, ma esegue altre funzioni importanti per altre soluzioni e funzionalità di [!DNL Experience Cloud]. A causa di questo legacy legacy, la verifica o la scrittura di un ID Analytics funziona in modo leggermente diverso rispetto al processo generico descritto in [Come il servizio Experience Cloud ID richiede e imposta gli ID…](../../mcvid-introduction/mcvid-id-request.md#concept-2caacebb1d244402816760e9b8bcef6a) Per ulteriori informazioni sull&#39;ordine delle operazioni per la verifica degli ID, consultate [Impostazione degli ID di Analytics e Experience Cloud](../../mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## Il cookie AMCV non è impostato nel browser {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

Se il cookie [!DNL Experience Cloud] (AMCV) non è presente, una chiamata del servizio ID a [!DNL Adobe] genera una risposta che varia a seconda della presenza o dell&#39;assenza di un ID Analytics legacy. L&#39;ID [!DNL Analytics] legacy è memorizzato nel cookie [s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html). La tabella seguente descrive il modo in cui gli ID vengono scritti nel cookie AMCV in base allo stato del cookie s_vi.

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stato del cookie s_vi </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> Cookie s_vi non impostato</b> </p> </td> 
   <td colname="col2"> <p>Il servizio ID assegna ai visitatori un <span class="keyword">Experience Cloud ID</span> (MID). Il MID identifica i visitatori in <span class="keyword">Analytics</span> e in altre soluzioni <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Cookie s_vi impostato</b> </p> </td> 
   <td colname="col2"> <p>Quando un visitatore con cookie s_vi accede a un sito con il servizio Experience Cloud ID, il servizio: </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">Scrive l'ID di <span class="keyword">Analytics</span> memorizzato nel cookie s_vi all'interno del cookie AMCV. Viene scritto come ID di <span class="keyword">Analytics</span> (AID). Questa azione <i>non</i> ha effetti sui conteggi dei visitatori. <span class="keyword"> Analytics</span> continua a identificare gli utenti in base ai loro ID legacy. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">Scrive il MID nel cookie AMCV. Il MID identifica gli utenti nelle diverse soluzioni. </li> 
    </ul> <p> <p>Nota: Con un <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md" format="dita" scope="local"> periodo di tolleranza</a>, la risposta del datacenter include sempre un ID legacy memorizzato nel cookie s_ vi. Durante il periodo di tolleranza, l'ID legacy viene scritto nel cookie AMCV come valore AID. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Per gli utenti identificati dal cookie s_ fid non viene migrato il valore FID precedente al cookie AMCV. Se gli utenti dispongono del cookie s_fid, vengono migrati come se il cookie s_vi non fosse presente (vedi sopra) e vengono quindi visualizzati come nuovi visitatori nel sito. Per ulteriori informazioni, vedi [Cookie di Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

## Il cookie AMCV è impostato nel browser {#section-01c088fc565c4b24ba1722c7cc240310}

Se il cookie AMCV è presente,  utilizza il MID come identificatore [!DNL Analytics], se nel cookie non è presenta un ID [!DNL Analytics]Analytics legacy.