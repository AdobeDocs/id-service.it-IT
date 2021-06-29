---
description: Casi d'uso e soluzioni di esempio per gestire il servizio Opt-in.
title: Casi d'uso di Opt-in
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '424'
ht-degree: 100%

---

# Casi d&#39;uso di Opt-in {#opt-in-use-cases}

Casi d&#39;uso e soluzioni di esempio per gestire il servizio Opt-in.

## Suggerimenti e risoluzione dei problemi {#section-5c566366410f4a8f89eca0d3f556d99f}

* L&#39;inizializzazione di JS per il visitatore è sincrona e viene eseguita durante il caricamento della pagina. Se ti stai interfacciando con una CMP o con una persistenza delle autorizzazioni con latenza elevata, potrebbe essere preferibile utilizzare le funzioni asincrone descritte in [Configurazione del servizio Opt-in](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* Opt-in è un&#39;implementazione per singolo dominio. Non gestirà le implementazioni tra domini diversi.
* Per disabilitare le chiamate di terze parti per una libreria specifica, dovrai configurare tale preferenza in ogni libreria separatamente.

## Situazioni che potrebbero verificarsi con Opt-in {#section-1178053c065c430bba26f82ef383a71c}

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
   <td colname="col1"> <p>Analytics può raccogliere i dati prima del consenso, ma tutte le altre librerie non possono essere caricate finché non viene ricevuto il consenso </p> </td> 
   <td colname="col2"> <p>Usa il servizio Opt-in per abilitare la categoria Analytics prima del consenso. </p> </td> 
   <td colname="col3"> <p>Analytics usa l'identificatore Analytics invece di ECID nella raccolta prima del consenso. Una volta approvato l’ECID, verrà utilizzato un nuovo identificatore e il visitatore riceverà un ECID che può essere utilizzato per l’attivazione e le integrazioni. </p> <p>È prevista la frammentazione del visitatore nello stato che precede/segue il consenso. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La misurazione di prima parte è adatta per la raccolta dei dati prima del consenso. Tutti gli altri tipi di dati di utilizzo potranno essere raccolti solo dopo la ricezione del consenso. </p> </td> 
   <td colname="col2"> <p>Utilizza il servizio Opt-in per abilitare le librerie di Analytics e ECID prima del consenso. </p> <p>Aggiungi la configurazione “disablethirdpartycookies” alla libreria ECID per bloccare cookie di terze parti e sincronizzazioni degli ID prima del consenso. </p> </td> 
   <td colname="col3"> <p>La chiamata demdex di Adobe verrà attivata per il recupero dell’ECID, ma non saranno presenti il cookie demdex, altri cookie di terze parti né sincronizzazioni degli ID. </p> <p>Mantiene la coerenza del visitatore nello stato che precede/segue il consenso per Analytics. La raccolta prima del consenso verrà associata alla raccolta dati dopo il consenso. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La misurazione di prima parte e il targeting è accettabile prima del consenso. Tutti gli altri tipi di dati di utilizzo potranno essere raccolti solo dopo la ricezione del consenso. </p> </td> 
   <td colname="col2"> <p>Utilizza il servizio Opt-in per abilitare le librerie di Analytics, ECID e Target prima del consenso. </p> <p>Aggiungere la configurazione <span class="codeph">isablethirdpartycookies</span> alla libreria ECID per bloccare il cookie di terze parti e le sincronizzazioni degli ID prima del consenso. Rimuovi il flag dopo il consenso. </p> </td> 
   <td colname="col3"> <p>La chiamata demdex di Adobe verrà attivata per il recupero dell’ECID, ma non saranno presenti il cookie demdex, altri cookie di terze parti né sincronizzazioni degli ID. </p> <p>Mantiene la coerenza del visitatore nello stato che precede/segue il consenso per le soluzioni di prima parte. La raccolta prima del consenso verrà associata alla raccolta dati dopo il consenso. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Non è consentito impostare cookie prima del consenso </p> </td> 
   <td colname="col2"> <p>Usa il servizio Opt-in per bloccare il caricamento di tutte le librerie fino alla ricezione del consenso. </p> </td> 
   <td colname="col3"> <p>L’implementazione avviene come previsto e tutte le librerie, incluse quelle di ECID, verranno caricate nella sequenza corretta dopo il consenso. </p> <p>È necessario tenere traccia della perdita di dati per i clienti che non concedono mai il consenso. </p> </td> 
  </tr> 
 </tbody> 
</table>
