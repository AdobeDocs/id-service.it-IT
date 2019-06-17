---
description: Dopo l'implementazione del servizio ID visitatore, un visitatore può essere identificato in Analytics in 5 modi diversi.
keywords: Servizio ID
seo-description: Dopo l’implementazione del servizio ID visitatore, un visitatore può essere identificato in Analytics in 5 modi diversi.
seo-title: Ordine delle operazioni per gli ID di Analytics
title: Ordine delle operazioni per gli ID di Analytics
uuid: cb 1 d 136 e -093 f -43 b 0-a 7 e 1-96 f 1 e 61 fdad 0
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Ordine delle operazioni per gli ID di Analytics{#order-of-operations-for-analytics-ids}

Dopo l&#39;implementazione del servizio ID visitatore, un visitatore può essere identificato in Analytics in 5 modi diversi.

In molte situazioni potrebbero essere presenti due o tre ID diversi in una chiamata, ma Analytics utilizza il primo ID presente nell&#39;elenco come ID ufficiale di [!DNL Experience Cloud]. Ad esempio, se imposti un ID visitatore personalizzato (incluso nel parametro di query `vid`), questo verrà usato prima degli altri ID visualizzati per lo stesso hit. Per ulteriori informazioni, consultate [Impostazione degli ID](../../mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) di Analytics e Experience Cloud.

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ordine </th> 
   <th colname="col2" class="entry"> Parametro query (metodo di raccolta) </th> 
   <th colname="col3" class="entry"> Presente se </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>1<sup>°</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p><span class="codeph">s.visitorID</span> è impostato. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2<sup>°</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>Il visitatore aveva un cookie s_ vi esistente prima dell'implementazione del <span class="keyword"> servizio Experience Cloud</span> ID oppure è stato configurato un <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md" format="dita" scope="local"> periodo</a> di tolleranza. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup>°</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../mcvid-introduction/mcvid-cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>Il browser del visitatore accetta i cookie di prime parti. Questo è impostato dal cookie AMCV. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup>°</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (cookie di fallback in H.25.3 o successivo, o in AppMeasurement per JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Un browser non accetta cookie di terze parti e il server di tracciamento di Analytics è impostato come server di tracciamento terze parti. </p> <p> <p>Nota: <span class="codeph">fid</span> è un identificatore legacy e non viene utilizzato se hai implementato il servizio ID sul tuo sito. In questo caso <span class="codeph"> , fid</span> non è necessario perché il cookie <a href="../../mcvid-introduction/mcvid-cookies.md" format="dita" scope="local"> AMCV di prime parti lo</a> rende obsoleto. È stato mantenuto per supportare codice legacy e per motivi storici. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup>°</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> Indirizzo IP, agente utente, indirizzo IP gateway</a> </p> </td> 
   <td colname="col3"> <p>Il browser del visitatore non accetta i cookie. </p> </td> 
  </tr> 
 </tbody> 
</table>

