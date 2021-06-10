---
description: Questa implementazione permette ai clienti di usare il servizio ID su dispositivi che non possono accettare o lavorare con il nostro codice JavaScript o SDK. Tra questi dispositivi sono incluse consolle di gioco, smart TV o altri apparecchi dotati di Internet. Fai riferimento a questa sezione per sintassi, esempi di codice e definizioni.
keywords: Servizio ID
title: Integrazione diretta con il servizio Experience Cloud Identity
exl-id: 29565b74-5fe7-41f7-b278-6a90559faab9
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 96%

---

# Integrazione diretta con il servizio Experience Cloud Identity {#direct-integration-with-the-experience-cloud-id-service}

Questa implementazione permette ai clienti di usare il servizio ID su dispositivi che non possono accettare o lavorare con il nostro codice JavaScript o SDK. Tra questi dispositivi sono incluse consolle di gioco, smart TV o altri apparecchi dotati di Internet. Fai riferimento a questa sezione per sintassi, esempi di codice e definizioni.

## Sintassi {#section-a4754afec5ad40b6be00d6f1011d68bb}

I dispositivi che non possono usare le librerie di codici VisitorAPI.js o SDK possono effettuare chiamate dirette ai server di raccolta dati (DCS) usati dal servizio ID. A tal fine, effettuerai una chiamata `dpm.demdex.net` formulando la tua richiesta come mostrato di seguito. Il *corsivo* indica un segnaposto variabile.

![](assets/directSyntax.png)

In questo esempio di sintassi, il `d_` prefisso identifica le coppie chiave-valore nella chiamata come variabile a livello di sistema. Puoi trasmettere una serie di `d_` parametri al servizio ID, ma fai particolare attenzione alle coppie chiave-valore mostrate nel codice seguente. Per ulteriori informazioni su altre variabili, consulta [Attributi supportati per le chiamate API DCS](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-keys.html).

Il servizio ID supporta le chiamate HTTP e HTTPS. Utilizza HTTPS per trasmettere dati da una pagina protetta.

## Richiesta di esempio {#section-26302b8851704888b6f8e6b2071bcdb0}

L&#39;aspetto della tua richiesta potrebbe essere simile all&#39;esempio mostrato di seguito. Le variabili lunghe sono state abbreviate.

![](assets/directExample.png)

## Risposta di esempio {#section-89bc103b3e9e4a8b98e74c32897b1200}

Il servizio ID restituisce i dati in un oggetto JSON come mostrato di seguito. La tua risposta potrebbe essere diversa.

```js
{
     "d_mid":"12345",
     "dcs_region":"6",
     "id_sync_ttl":"604800",
     "d_blob":"wxyz5432"
}
```

## Parametri di richiesta e risposta definiti {#section-4a9912b545364dc4acad4f1ea5ec641d}

**Parametri di richiesta**

<table id="table_C8FFA89AB74E4E31A6926CDE5CD54217"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Parametro </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dpm.demdex.net</span> </p> </td> 
   <td colname="col2"> <p>Un dominio legacy controllato da <span class="keyword">Adobe</span>. Vedi <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Informazioni sulle chiamate al dominio demdex</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_mid</span> </p> </td> 
   <td colname="col2"> <p>L'ID visitatore Experience Cloud. Consulta <a href="../introduction/cookies.md" format="dita" scope="local"> Cookie e il servizio Experience Cloud Identity</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_orgid</span> </p> </td> 
   <td colname="col2"> <p>L'ID organizzazione Experience Cloud. Per maggiori informazioni su come trovare questo ID vedere, <a href="../reference/requirements.md" format="dita" scope="local"> Requisiti del servizio Experience Cloud Identity</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cid</span> </p> </td> 
   <td colname="col2"> <p>Un parametro facoltativo che trasmette l'ID del fornitore dati (DPID), l'ID utente univoco (DPUUID) e un <a href="../reference/authenticated-state.md" format="dita" scope="local">ID dello stato di autenticazione</a> al servizio ID. Come mostrato nell'esempio di codice, separata il DPID e il DPUUID con il carattere di controllo non stampabile, <span class="codeph">%01</span>. </p> <p> <b>DPID e DPUUID</b> </p> <p>Nel parametro <span class="codeph">d_cid</span>, assegna ogni combinazione di DPID e DPUUID allo stesso parametro <span class="codeph">d_cid</span>. Ciò ti consente di restituire set di ID multipli in un'unica richiesta. Inoltre, separa il DPID, il DPUUID e il flag di autenticazione opzionale con il carattere di controllo non stampabile, <span class="codeph">%01</span>. Negli esempi seguenti, gli ID del fornitore e dell'utente sono in <b>grassetto</b>. </p> 
    <ul id="ul_2E19D837296B40E9ACD096495CF711C5"> 
     <li id="li_5B94B057654440B99B989BA60E4ED053">Sintassi: <span class="codeph">...d_cid=DPID%01DPUUID%01authentication state...</span> </li> 
     <li id="li_B07833EF51D54F088574B7B7F9FB841A">Esempio: <span class="codeph">...d_cid=123%01456%011...</span> </li> 
    </ul> <p> <b>Stato di autenticazione</b> </p> <p>Questo è un ID opzionale nel parametro <span class="codeph">d_cid</span>. Espresso sotto forma di numero intero, identifica gli utenti a seconda del loro stato di autenticazione come mostrato di seguito: </p> 
    <ul id="ul_E2B36922B11C4AA2A9016B6E2DC9EDAA"> 
     <li id="li_31C018E3F9514B938C73EF40C436715F"> <span class="codeph"> 0</span> (sconosciuto) </li> 
     <li id="li_1F125C3879324C2F8EF4613C0ECB5F02"> <span class="codeph"> 1</span> (autenticato) </li> 
     <li id="li_EF6792D0115D407485079D5D7480D965"> <span class="codeph"> 2</span> (disconnesso) </li> 
    </ul> <p>Per specificare uno stato di autenticazione, imposta questo flag dopo la variabile ID utente (UUID). Separa il UUID e il flag di autenticazione con il carattere di controllo non stampabile, <span class="codeph">%01</span>. Negli esempi seguenti, gli ID di autenticazione sono in <b>grassetto</b>. </p> <p>Sintassi: <span class="codeph">...d_cid=DPID%01DPUUID%01authentication state</span> </p> <p>Esempi: </p> 
    <ul id="ul_4C1054CE860A4D9C8DD85C2A8020C47F"> 
     <li id="li_AD4000BF3E0146C0BD37B1EC513EC314">Sconosciuto: <span class="codeph">...d_cid=123%01456%010...</span> </li> 
     <li id="li_B037D424AADA4D41BF29381A9602AE61">Autenticato: <span class="codeph">...d_cid=123%01456%011...</span> </li> 
     <li id="li_0410FCB9E60D4DD08E7898D814E1C3C9">Disconnesso: <span class="codeph">...d_cid=123%01456%012...</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dcs_region</span> </p> </td> 
   <td colname="col2"> <p>Il servizio ID è un sistema distribuito geograficamente e bilanciato in base al carico. L'ID identifica la regione del centro dati che gestisce la chiamata. Consulta <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html" format="https" scope="external">ID regioni DCS, posizioni e nomi host</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cb</span> </p> </td> 
   <td colname="col2"> <p> <i>(Facoltativo)</i> Un parametro di callback che ti permette di eseguire una funzione JavaScript nel corpo della richiesta. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_blob</span> </p> </td> 
   <td colname="col2"> <p>Un pezzo crittografato di metadati JavaScript. I vincoli di dimensione limitano il blob a un massimo di 512 byte. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_ver</span> </p> </td> 
   <td colname="col2"> <p>Obbligatorio. Questo imposta il numero della versione API. Lascialo impostato come <span class="codeph">d_ver=2</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Parametri di risposta**

Alcuni parametri di risposta fanno parte della richiesta e sono stati definiti nella sezione precedente.

<table id="table_58D0E8876DDC4A81B1F24F845E87EC18"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Parametro </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id_sync_ttl</span> </p> </td> 
   <td colname="col2"> <p>L'intervallo di ri-sincronizzazione, specificato in secondi. L’intervallo predefinito è di 604.800 secondi (7 giorni). </p> </td> 
  </tr> 
 </tbody> 
</table>
