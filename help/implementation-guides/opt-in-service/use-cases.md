---
description: Casi d'uso e soluzioni di esempio per gestire il servizio Opt-in.
seo-description: Casi d'uso e soluzioni di esempio per gestire il servizio Opt-in.
seo-title: Casi d'uso di Opt-in
title: Casi d'uso di Opt-in
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 31%

---


# Casi d&#39;uso di Opt-in {#opt-in-use-cases}

Casi d&#39;uso e soluzioni di esempio per gestire il servizio Opt-in.

## Suggerimenti e risoluzione dei problemi {#section-5c566366410f4a8f89eca0d3f556d99f}

* L&#39;inizializzazione di JS per il visitatore è sincrona e viene eseguita durante il caricamento della pagina. Se state interfacciando con un CMP o con una persistenza di autorizzazioni con latenza elevata, potrebbe essere preferibile utilizzare le funzioni asincrone descritte in Impostazione [](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)consenso.
* Opt-in è un&#39;implementazione per singolo dominio. Non gestirà le implementazioni tra domini diversi.
* Per disabilitare le chiamate di terze parti per una libreria specifica, dovrete configurare tale preferenza separatamente in ciascuna libreria.

## Situazioni che potrebbero verificarsi con Opt-in  {#section-1178053c065c430bba26f82ef383a71c}

Questi casi d&#39;uso sono idee di esempio per usare il servizio Opt-in.

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Requisito </th> 
   <th colname="col2" class="entry"> Soluzioni </th> 
   <th colname="col3" class="entry"> Impatto </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Analytics è accettabile per la raccolta nello stato di pre-consenso, ma tutte le altre librerie non possono essere caricate finché non viene ricevuto il consenso </p> </td> 
   <td colname="col2"> <p>Utilizza il consenso per abilitare la categoria Analytics nello stato precedente il consenso </p> </td> 
   <td colname="col3"> <p>Analytics usa l'identificatore Analytics invece di ECID nella raccolta prima del consenso. Dopo l'approvazione di ECID, verrà utilizzato un nuovo identificatore e il visitatore riceverà un ECID che potrà essere utilizzato per l'attivazione e le integrazioni. </p> <p>È prevista la frammentazione del visitatore nello stato pre/post-consenso. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La misurazione di prima parte è adatta per la raccolta dei dati prima del consenso. Tutti gli altri tipi di utilizzo dei dati impediti fino alla ricezione del consenso. </p> </td> 
   <td colname="col2"> <p>Utilizzate il consenso per abilitare le librerie Analytics + ECID nello stato di pre-consenso. </p> <p>Aggiungi la configurazione "disablethirdpartycookies" alla libreria ECID per bloccare i cookie 3rd party + le sincronizzazioni ID nello stato pre-consenso </p> </td> 
   <td colname="col3"> <p> chiamata Demdex Adobe verrà attivata per il recupero ECID, ma non saranno presenti cookie Demdex, altri cookie di terze parti o sincronizzazioni ID. </p> <p>Mantiene la coerenza del visitatore nello stato che precede/segue il consenso per Analytics. La raccolta nello stato di pre-consenso sarà legata alla raccolta dei dati post-consenso. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La misurazione di prima parte e il targeting è accettabile prima del consenso. Tutti gli altri tipi di utilizzo dei dati impediti fino alla ricezione del consenso. </p> </td> 
   <td colname="col2"> <p>Utilizzate il consenso per abilitare le librerie Analytics + ECID + Target nello stato pre-consenso. </p> <p>Aggiungere la configurazione <span class="codeph">isablethirdpartycookies</span> alla libreria ECID per bloccare il cookie di terze parti e le sincronizzazioni degli ID prima del consenso. Rimuovere il flag nello stato post-consenso. </p> </td> 
   <td colname="col3"> <p> chiamata Demdex Adobe verrà attivata per il recupero ECID, ma non saranno presenti cookie Demdex, altri cookie di terze parti o sincronizzazioni ID. </p> <p>Mantiene la coerenza del visitatore nello stato che precede/segue il consenso per le soluzioni di prima parte. La raccolta nello stato di pre-consenso sarà legata alla raccolta dei dati post-consenso. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Non è consentito impostare cookie in uno stato di pre-consenso </p> </td> 
   <td colname="col2"> <p>Utilizzare il consenso per bloccare il caricamento di tutte le librerie fino alla ricezione del consenso </p> </td> 
   <td colname="col3"> <p>L'implementazione è come previsto e tutte le librerie, incluso ECID, verranno caricate in sequenza corretta nello stato post-consenso. </p> <p>Perdita di dati per i clienti che non danno mai il consenso per essere monitorati. </p> </td> 
  </tr> 
 </tbody> 
</table>

