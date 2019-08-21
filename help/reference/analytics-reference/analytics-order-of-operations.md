---
description: Dopo l’implementazione del servizio ID visitatore, un visitatore può essere identificato in Analytics in 5 modi diversi.
keywords: Servizio ID
seo-description: Dopo l’implementazione del servizio ID visitatore, un visitatore può essere identificato in Analytics in 5 modi diversi.
seo-title: Ordine delle operazioni per gli ID di Analytics
title: Ordine delle operazioni per gli ID di Analytics
uuid: cb1d136e-093f-43b0-a7e1-96f1e61fdad0
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Ordine delle operazioni per gli ID di Analytics{#order-of-operations-for-analytics-ids}

Dopo l’implementazione del servizio ID visitatore, un visitatore può essere identificato in Analytics in 5 modi diversi.

In molte situazioni potrebbero essere presenti due o tre ID diversi in una chiamata, ma Analytics utilizza il primo ID presente nell&#39;elenco come ID ufficiale di [!DNL Experience Cloud]. Ad esempio, se imposti un ID visitatore personalizzato (incluso nel `vid` parametro di query), questo verrà usato prima degli altri ID visualizzati per lo stesso hit. Consulta [Impostazione degli ID di Analytics ed Experience Cloud](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) per maggiori informazioni.

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
   <td colname="col3"> <p>Il visitatore aveva un altro cookie s_vi prima dell'implementazione del servizio <span class="keyword">Experience Cloud</span> ID, oppure è stato configurato un.<a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">periodo di tolleranza</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3<sup>°</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>Il browser del visitatore accetta i cookie di prime parti. Questo è impostato dal cookie AMCV. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup>°</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (cookie di fallback in H.25.3 o successivo, o in AppMeasurement per JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Un browser non accetta cookie di terze parti e il server di tracciamento di Analytics è impostato come server di tracciamento terze parti. </p> <p> <p>Nota: <span class="codeph">fid</span> è un identificatore legacy e non viene utilizzato se hai implementato il servizio ID sul tuo sito. In questo caso, il <span class="codeph"> fid</span> non è necessario perché il <a href="../../introduction/cookies.md" format="dita" scope="local">cookie AMCV</a> di prime parti lo rende obsoleto. È stato mantenuto per supportare codice legacy e per motivi storici. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup>°</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> Indirizzo IP, agente utente, indirizzo IP gateway</a> </p> </td> 
   <td colname="col3"> <p>Il browser del visitatore non accetta i cookie. </p> </td> 
  </tr> 
 </tbody> 
</table>

