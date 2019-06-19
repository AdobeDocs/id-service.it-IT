---
description: Esempi di utilizzo e soluzioni per gestire il servizio di consenso.
seo-description: Esempi di utilizzo e soluzioni per gestire il servizio di consenso.
seo-title: Casi d'uso di Opt-in
title: Casi d'uso di Opt-in
uuid: d 75 a 44 d 5-b 713-43 d 1-b 5 b 6-95 d 1 d 0 d 213 a 7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671

---


# Casi d&#39;uso di Opt-in {#opt-in-use-cases}

Esempi di utilizzo e soluzioni per gestire il servizio di consenso.

## Suggerimenti e risoluzione dei problemi {#section-5c566366410f4a8f89eca0d3f556d99f}

* L&#39;inizializzazione di JS per il visitatore è sincrona e viene eseguita durante il caricamento della pagina. Se si usa una CMP o si affronta la persistenza delle autorizzazioni con latenza elevata, è preferibile usare le funzioni asincrone descritte in [Configurazione di Opt-in](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* Opt-in è un&#39;implementazione per singolo dominio. Non gestisce implementazioni in più domini.
* Al fine di disabilitare le chiamate di terze parti per una libreria specifica, sarà necessario configurare la preferenza in ogni libreria separatamente.

## Situazioni che potrebbero verificarsi con Opt-in {#section-1178053c065c430bba26f82ef383a71c}

Questi casi d&#39;uso sono esempi di idee per l&#39;utilizzo del servizio di consenso.

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
   <td colname="col1"> <p>Analytics permette di raccogliere i dati prima del consenso ma tutte le altre librerie non possono essere caricate fino a quando non si riceve il consenso </p> </td> 
   <td colname="col2"> <p>Usare Opt-in per abilitare la categoria Analytics prima del consenso </p> </td> 
   <td colname="col3"> <p>Analytics usa l'identificatore Analytics invece di ECID nella raccolta prima del consenso. Una volta approvato ECID, verrà usato un nuovo identificatore e il visitatore riceverà un ECID che può essere usato per l'attivazione e le integrazioni. </p> <p>È prevista la frammentazione del visitatore nello stato che precede/segue il consenso. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La misurazione di prima parte è adatta per la raccolta dei dati prima del consenso. Non sono possibili tutti gli altri tipi di utilizzo dei dati fino alla ricezione del consenso. </p> </td> 
   <td colname="col2"> <p>Usare Opt-in per abilitare le librerie di ECID e Analytics prima del consenso. </p> <p>Aggiungere la configurazione "disablethirdpartycookies" alla libreria ECID per bloccare il cookie di terze parti e le sincronizzazioni degli ID prima del consenso </p> </td> 
   <td colname="col3"> <p>La chiamata ad Adobe Demdex verrà attivata per il recupero ECID ma non per il cookie demdex, saranno presenti altri cookie di terze parti o sincronizzazioni degli ID. </p> <p>Mantiene la coerenza del visitatore nello stato che precede/segue il consenso per Analytics. La raccolta prima del consenso verrà collegata alla raccolta dati che segue il consenso. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La misurazione di prima parte e il targeting è accettabile prima del consenso. Non sono possibili tutti gli altri tipi di utilizzo dei dati fino alla ricezione del consenso. </p> </td> 
   <td colname="col2"> <p>Usare Opt-in per abilitare le librerie di ECID, Analytics e Target prima del consenso. </p> <p>Aggiungere la configurazione <span class="codeph">isablethirdpartycookies</span> alla libreria ECID per bloccare il cookie di terze parti e le sincronizzazioni degli ID prima del consenso. Rimuovere il flag dopo aver ricevuto il consenso. </p> </td> 
   <td colname="col3"> <p>La chiamata ad Adobe Demdex attiverà il recupero ECID ma non del cookie demdex, saranno presenti altri cookie di terze parti o sincronizzazioni degli ID. </p> <p>Mantiene la coerenza del visitatore nello stato che precede/segue il consenso per le soluzioni di prima parte. La raccolta prima del consenso verrà collegata alla raccolta dati che segue il consenso. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Prima del consenso non è possibile impostare alcun cookie </p> </td> 
   <td colname="col2"> <p>Usare Opt-in per bloccare il caricamento di tutte le librerie fino alla ricezione del consenso </p> </td> 
   <td colname="col3"> <p>L'implementazione avviene come previsto e tutte le librerie, tra cui ECID, verranno caricate nella corretta sequenza in seguito al consenso. </p> <p>Verrà monitorata la perdita di dati per i clienti che non concedono mai il consenso. </p> </td> 
  </tr> 
 </tbody> 
</table>

