---
description: Questi esempi coprono 2 casi d'uso comuni relativi a un'integrazione diretta e all'Experience Cloud ID (MID). L'identificatore MID è un ID univoco e costante per i visitatori del tuo sito.
keywords: ID Service
seo-description: Questi esempi coprono 2 casi d'uso comuni relativi a un'integrazione diretta e all'Experience Cloud ID (MID). L'identificatore MID è un ID univoco e costante per i visitatori del tuo sito.
seo-title: Casi d'uso dell'integrazione diretta
title: Casi d'uso dell'integrazione diretta
uuid: 6de1eb8b-4783-4545-8a64-ab6b9ef93432
translation-type: tm+mt
source-git-commit: 6342ea02c74e6d1c96f987c5f2620246602ce6c5

---


# Casi d&#39;uso dell&#39;integrazione diretta {#direct-integration-use-cases}

Questi esempi coprono 2 casi d’uso comuni relativi a un’integrazione diretta e all’Experience Cloud ID (ECID o MID). Questo ID è univoco e costante per i visitatori del sito.

>[!TIP]
>
>* Leggi e comprendi la [sintassi del codice e le variabili](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9) prima di immergerti nei casi d&#39;uso.
>* Per ulteriori informazioni sull’identificatore MID, consulta [Cookie e il servizio Experience Cloud Identity](../introduction/cookies.md).
>



## Caso d’uso 1: ho un identificatore Experience Cloud ID (MID) ma voglio trasmettere i miei ID visitatori e impostare uno stato di autenticazione {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento del caso d'uso </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condizioni</b> </p> </td> 
   <td colname="col2"> <p>I presupposti di questo caso d'uso sono: </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">Avere un MID per il visitatore del sito. Chiamiamolo ID 1234. </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">Conoscere questo visitatore per il suo ID univoco. Chiamiamolo ID 9876. </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">Volere collegare il MID (1234) all'ID univoco (9876). </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>(Facoltativo)</i> Voler impostare uno stato di autenticazione su questo visitatore. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Azioni</b> </p> </td> 
   <td colname="col2"> <p>Considerate queste condizioni, effettua una chiamata al servizio ID che includa: </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">Il MID (1234). </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">L'ID del fornitore dei dati. Questo è un ID univoco assegnato alla tua azienda. Chiamiamolo ID 4444. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">L'ID del visitatore (9876). </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>(Facoltativo)</i> Un ID di stato per definite lo stato di autenticazione per quel visitatore. </li> 
    </ul> <p>Nel caso in cui tu disponga degli altri parametri elencati in <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local">guida all'integrazione diretta</a> (es.,<span class="codeph"> d_blob</span> o <span class="codeph">dcs_region</span>, ecc.) puoi benissimo trasmettere anche quelli. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Soluzione ed esempio di codice</b> </p> </td> 
   <td colname="col2"> <p>Formula la tua chiamata al servizio ID seguendo questo esempio: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>Nota che la chiamata di esempio contiene: </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID: <span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">MID unito all'ID univoco per il visitatore: <span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">ID dello stato di autenticazione: <span class="codeph">...d_cid=4444%019876%011</span> (nota: corrisponde all'ultima cifra). </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Caso d&#39;uso 2: non ho un MID e ho bisogno di generarlo {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento del caso d'uso </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condizioni</b> </p> </td> 
   <td colname="col2"> <p>I presupposti di questo caso d'uso sono: </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">Non avere un MID per il visitatore del sito. </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">Aver bisogno di richiedere un MID per il servizio ID. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">Conoscere l'<a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local">ID organizzazione</a>. Chiamiamolo 5555. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Azioni</b> </p> </td> 
   <td colname="col2"> <p>Considerate queste condizioni, effettua una chiamata al servizio ID che includa il tuo ID organizzazione. </p> <p>Nel caso in cui tu disponga degli altri parametri elencati in <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local">guida all'integrazione diretta</a> (es.,<span class="codeph"> d_blob</span> o <span class="codeph">dcs_region</span>, ecc.) puoi benissimo trasmettere anche quelli. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Soluzione ed esempio di codice</b> </p> </td> 
   <td colname="col2"> <p>Formula la tua chiamata al servizio ID seguendo questo esempio: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>Nota come questa chiamata d'esempio contiene il tuo ID organizzazione, <span class="codeph">d_orgid=5555</span>. Ti verrà restituito un ID <span class="keyword">Experience Cloud</span> per il visitatore. </p> </td> 
  </tr> 
 </tbody> 
</table>

