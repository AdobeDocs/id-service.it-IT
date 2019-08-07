---
description: Queste configurazioni consentono a diverse istanze del codice del servizio ID implementate in un iFrame e sulla pagina padre di comunicare tra di loro. Risolvono problemi rilevati per 2 casi d'uso specifici in cui si può controllare o meno la pagina padre o il dominio e si carica il codice del servizio ID nell'iFrame di un dominio controllato. Sono disponibili in VisitorAPI.js versione del codice 2.2 o successiva.
keywords: Servizio ID
seo-description: Queste configurazioni consentono a diverse istanze del codice del servizio ID implementate in un iFrame e sulla pagina padre di comunicare tra di loro. Risolvono problemi rilevati per 2 casi d'uso specifici in cui si può controllare o meno la pagina padre o il dominio e si carica il codice del servizio ID nell'iFrame di un dominio controllato. Sono disponibili in VisitorAPI.js versione del codice 2.2 o successiva.
seo-title: whitelistParentDomain e whitelistIframeDomains
title: whitelistParentDomain e whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-0c4f4ab1efb6
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# whitelistParentDomain e whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

Queste configurazioni consentono a diverse istanze del codice del servizio ID implementate in un iFrame e sulla pagina padre di comunicare tra di loro. Risolvono problemi rilevati per 2 casi d'uso specifici in cui si può controllare o meno la pagina padre o il dominio e si carica il codice del servizio ID nell'iFrame di un dominio controllato. Sono disponibili in VisitorAPI.js versione del codice 2.2 o successiva.

Sommario:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local"> Sintassi </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> Esempio di codice </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> Casi d'uso </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> Sicurezza della configurazione </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> Metodi API del visitatore supportati </a> </li> 
</ul>

## Sintassi {#section-f645198bbaba4fba8961acb6e88d1470}

Entrambi gli elementi di configurazione sono richiesti quando si questo codice.

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Sintassi di configurazione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: " <span class="varname"> Nome di dominio della pagina padre </span>" </span> </p> </td> 
   <td colname="col2"> <p>Accetta un nome di dominio singolo trasmesso come stringa. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [ <span class="varname"> "dominio iFrame","dominio iFrame","dominio iFrame" </span>] </span> </p> </td> 
   <td colname="col2"> <p>Accetta uno o più nomi di dominio iFrame trasmessi come array. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Esempio di codice {#section-09d0049fe88a473baa69d404c50bf8ae}

Una volta configurato il tuo codice del [!UICONTROL servizio ID] potrebbe assomigliare a questo esempio.

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## Casi d'uso {#section-fc2eeb93546b406fae3b102dbcd11de7}

Queste configurazioni aiutano a risolvere il problema dell'impostazione di un cookie del servizio ID e dell'assegnazione di un ID visitatore quando i browser bloccano i cookie di terza parte e se si applica una delle condizioni seguenti:

* Controlli o non controlli la pagina/dominio padre.
* Il codice del servizio ID non è installato sulla pagina padre, ma è implementato in un iFrame.

>[!TIP]
>
>You may also want to implement these configurations when you're serving video in an iFrame with [Video Heartbeat](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/). Video Heartbeat richiede un ID del servizio ID (il codice MID) per funzionare in modo appropriato.

**Caso d'uso 1: il browser blocca i cookie di terza parte e il servizio ID è implementato su iFrame e sulla pagina padre**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento del caso d'uso </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condizioni</b> </p> </td> 
   <td colname="col2"> <p>Questo caso d'uso include le condizioni seguenti: </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">La società A implementa il servizio ID sulla sua pagina iniziale. </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">La società A implementa il servizio ID in iFrame sulla sua pagina iniziale. </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">La società A è proprietaria della pagina padre e di iFrame e ha implementato il servizio ID in entrambi i posti. </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">Un cliente carica la pagina padre in un browser che blocca i cookie di terza parte. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Risultati</b> </p> </td> 
   <td colname="col2"> <p>Considerate queste condizioni, il servizio ID: </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">Funziona correttamente nella pagina padre. Richiede e imposta il cookie AMCV e assegna un ID univoco al visitatore del sito. </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">Non funziona nell'iFrame. Questo perché il browser vede l'iFrame come un dominio di terza parte e impedisce al servizio ID di impostare il cookie AMCV. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Soluzione</b> </p> </td> 
   <td colname="col2"> <p>Modifica la funzione <span class="codeph">Visitor.getInstance</span> del servizio ID nell'iFrame con queste configurazioni della whitelist. Specifica i domini padre e figlio nel codice. Queste configurazioni permettono al codice del servizio ID nell'iFrame di controllare il codice del servizio ID sulla pagina padre per un ID visitatore. </p> <p>Se il codice del servizio ID nell'iFrame non riceve una pagina padre di risposta, queste configurazioni generano un ID del visitatore locale. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Caso d'uso 2: richiesta di un ID da un iFrame integrato in una pagina padre che non controlli o che non usa il servizio ID**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento del caso d'uso </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condizioni</b> </p> </td> 
   <td colname="col2"> <p>Questo caso d'uso include le condizioni seguenti: </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">La società A non usa il servizio ID. </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">La società A carica un iFrame sulla pagina. Questo iFrame è di proprietà della società B e si carica in un dominio separato rispetto alla società A. </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">Il browser blocca i cookie di terza parte. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Risultati</b> </p> </td> 
   <td colname="col2"> <p>Considerate queste condizioni, il servizio ID: </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">Non funziona nell'iFrame. Questo perché il browser vede l'iFrame come un dominio di terza parte e impedisce al servizio ID di impostare il cookie AMCV. </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">Non è possibile ottenere un ID visitatore dalla pagina padre perché la società A non usa questo servizio. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Soluzione</b> </p> </td> 
   <td colname="col2"> <p>Modifica la funzione <span class="codeph">Visitor.getInstance</span> del servizio ID nell'iFrame con queste configurazioni della whitelist. Specifica i domini padre e figlio nel codice. Queste configurazioni permettono al codice del servizio ID nell'iFrame di controllare il codice del servizio ID sulla pagina padre per un ID visitatore. </p> <p>Se il codice del servizio ID nell'iFrame non riceve una pagina padre di risposta, queste configurazioni generano un ID del visitatore locale. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Sicurezza della configurazione {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

Puoi implementare queste configurazioni con sicurezza perché:

* Il servizio ID implementato sul dominio padre e sul dominio iFrame deve usare lo stesso ID organizzazione. Queste configurazioni della whitelist non funzioneranno quando gli ID organizzazione sul dominio padre o sull'iFrame sono diversi.
* Queste configurazioni comunicano solo con il dominio e l'iFrame specificati nel codice.
* La comunicazione tra l'iFrame e la pagina padre segue un formato specifico. Il processo di condivisione non riuscirà correttamente se il servizio ID sulla pagina padre non riceve una richiesta nel formato atteso.

## Metodi API del visitatore supportati {#section-30c6a9f4dcdc4265a1149260b97cc057}

Il servizio ID supporta un set limitato di metodi API pubblici quando si implementano queste configurazioni della whitelist. I metodi supportati variano a seconda degli scenari di casi d'uso descritti sopra.

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso d'uso </th> 
   <th colname="col2" class="entry"> Metodi supportati </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Caso 1</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Caso 2</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

