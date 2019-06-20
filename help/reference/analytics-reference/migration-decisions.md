---
description: Prima di distribuire il servizio Experience Cloud ID, è necessario comprendere in che modo il servizio influisce sul monitoraggio dei visitatori in più domini e sui potenziali problemi relativi alla raccolta di dati con metodi diversi o tramite file javascript.
keywords: Servizio ID
seo-description: Prima di distribuire il servizio Experience Cloud ID, è necessario comprendere in che modo il servizio influisce sul monitoraggio dei visitatori in più domini e sui potenziali problemi relativi alla raccolta di dati con metodi diversi o tramite file javascript.
seo-title: Decisioni relative alla migrazione al servizio Experience Cloud ID
title: Decisioni relative alla migrazione al servizio Experience Cloud ID
uuid: ee 56 b 5 de-fcf 3-4 cfb -9 e 53-762 af 7 c 4 d 2 ff
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Decisioni relative alla migrazione al servizio Experience Cloud ID

Prima di distribuire il servizio Experience Cloud ID, è necessario comprendere in che modo il servizio influisce sul monitoraggio dei visitatori in più domini e sui potenziali problemi relativi alla raccolta di dati con metodi diversi o tramite file javascript.

Le risposte alle domande incluse in questa sezione sono utili per stabilire eventuali passaggi di migrazione da eseguire.

## Disponi di un CNAME di raccolta dati?

Molti clienti possono effettuare la migrazione da un CNAME di raccolta dati durante la migrazione al servizio ID.

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Metodo di raccolta dati </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Con un CNAME </p> </td> 
   <td colname="col2"> <p>Vedi la prossima domanda per stabilire se devi effettuare la migrazione dal CNAME di raccolta dati. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Senza un CNAME </p> </td> 
   <td colname="col2"> <p>Passa a <a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">Se non hai un CNAME di raccolta dati, il tuo server di raccolta dati è *.2o7.net o *.sc.omtrdc.net?</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Se hai un CNAME di raccolta dati, hai più domini?

Se disponi di più domini che inviano dati alla *stessa suite di rapporti*, ti consigliamo di effettuare la raccolta dati usando un CNAME. In questo modo potrai eseguire il monitoraggio dei visitatori tra i domini. Se raccogli i dati in un solo dominio, l&#39;utilizzo di un CNAME per la raccolta dei dati non comporta vantaggi.

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Raccolta dei dati da </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Più domini </p> </td> 
   <td colname="col2"> <p>Se effettui il monitoraggio dei visitatori tra più domini e disponi di un sito di accesso principale in cui i clienti vengono identificati prima dell'accesso agli altri domini, dovresti continuare a usare il CNAME di raccolta dati. Per una spiegazione dettagliata, vedi <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local">CNAME di raccolta dati e monitoraggio tra i domini</a>. </p> <p>Per configurare un CNAME con il servizio ID è necessario specificare due parametri aggiunti per il server di tracciamento, <span class="codeph">visitor.marketingCloudServer</span> e <span class="codeph">visitor.marketingCloudServerSecure</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Un solo dominio </p> </td> 
   <td colname="col2"> <p>L'utilizzo di un solo dominio consente di effettuare la migrazione da un CNAME di raccolta dati, se non desideri gestirlo più. Se il CNAME funziona correttamente, non è necessario cambiarlo. </p> <p>Se rimuovi il CNAME: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Verifica che il nuovo server di monitoraggio sia <a href="https://marketing.adobe.com/resources/help/en_US/whitepapers/rdc/" format="https" scope="external">compatibile con RDC</a>. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">Passa dal CNAME a un server di monitoraggio RDC alcuni mesi prima della migrazione al servizio <span class="keyword">Experience Cloud ID</span>. </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>Non</i> usare un server di monitoraggio <span class="codeph">*.2o7.net</span>. </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">Per configurare la migrazione dei visitatori, contatta l'<a href="https://helpx.adobe.com/marketing-cloud/contact-support.html" format="https" scope="external">assistenza clienti</a>. In questo modo i conteggi dei visitatori rimarranno costanti. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Hai più file JavaScript di Analytics o esegui il monitoraggio di applicazioni o video Flash?

Se disponi di più file JavaScript di Analytics o applicazioni e video Flash che inviano dati alla *stessa suite di rapporti*, devi configurare un periodo di tolleranza in modo che i visitatori possano continuare ad essere identificati in base all&#39;ID Analytics durante il rollout del servizio [!DNL Experience Cloud] ID.

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Raccolta dati con </th> 
   <th colname="col2" class="entry"> Azioni necessarie </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">Più file JavaScript di Analytics </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">Altri metodi di raccolta dati </li> 
    </ul> </td> 
   <td colname="col2"> <p>Ti consigliamo di configurare un periodo di tolleranza per il servizio ID visitatore, in modo da poter effettuare il rollout del servizio ID visitatore in ciascun file JavaScript e nelle librerie di raccolta dati. Consulta <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> Periodo di tolleranza per il servizio ID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Un unico file JavaScript di Analytics </p> </td> 
   <td colname="col2"> <p>Puoi aggiornare il singolo file JavaScript per usare il servizio ID visitatore senza un periodo di tolleranza. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Utilizzi metodi di raccolta dati non supportati?

Potresti dover aggiornare il metodo di monitoraggio dei link o effettuare una migrazione da Silverlight.

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Metodo di raccolta dati </th> 
   <th colname="col2" class="entry"> Azioni necessarie </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript e/o Flash </p> </td> 
   <td colname="col2"> <p>Nessuno. Il servizio <span class="keyword">Experience Cloud ID</span> supporta questi metodi di raccolta dei dati. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>Se i visitatori possono accedere ai contenuti di Silverlight e ad altre sezioni del sito che utilizzano il servizio <span class="keyword">Experience Cloud ID</span>, devi effettuare la migrazione da Silverlight. Silverlight non è supportato dal servizio ID. </p> <p> Se esegui il monitoraggio di un lettore video basato su Silverlight, probabilmente il venditore può fornirti le API JavaScript da utilizzare. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Tag immagine hardcoded </p> </td> 
   <td colname="col2"> <p>Aggiorna i link hardcoded per usare JavaScript. </p> </td> 
  </tr> 
 </tbody> 
</table>

