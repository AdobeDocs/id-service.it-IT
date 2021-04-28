---
description: Configurazione booleana opzionale che consente di determinare se il servizio ID invia o meno dati ad Adobe Experience Cloud Device Co-op.
keywords: Servizio ID
seo-description: Configurazione booleana opzionale che consente di determinare se il servizio ID invia o meno dati ad Adobe Experience Cloud Device Co-op.
seo-title: isCoopSafe
title: isCoopSafe
uuid: 4dfa1f35-0a88-48d1-9484-d88cb53ad461
exl-id: 827f7819-9f95-4e8d-90c3-dcf86b67715b
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '606'
ht-degree: 100%

---

# isCoopSafe {#iscoopsafe}

Configurazione booleana opzionale che consente di determinare se il servizio ID invia o meno dati ad Adobe Experience Cloud Device Co-op.

Sommario:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> Requisiti </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> Casi d'uso </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> Sintassi ed esempio di codice </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> Parametri POST della chiamata dell'evento </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> API di post-istanziazione </a> </li> 
</ul>

## Requisiti {#section-4883eda6beb8437182bcc82bb58fae41}

Per usare `isCoopSafe` devi:

* Usare il codice del servizio ID versione 2.4 o superiore.
* Partecipare a [Experience Cloud Device Co-op](https://docs.adobe.com/content/help/it-IT/device-co-op/using/about/overview.html). Anche i potenziali membri co-op devono consultare questa documentazione per stabilire se `isCoopSafe` si occupa di possibili problemi relativi al modo in cui i dati vengono utilizzati per creare il grafico del dispositivo.

* Definisci un flag whitelist o blacklist sul tuo account Device Co-op avvalendoti dell&#39;aiuto del tuo consulente [!DNL Adobe]. Non esiste alcun percorso self-service per l&#39;attivazione di questi flag.

## Casi d&#39;uso {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe` aiuta a risolvere 2 casi d&#39;uso relativi alla raccolta di dati da parte di membri attuali o potenziali di Device Co-op. Questi casi d&#39;uso si riferiscono al modo in cui i dati dei visitatori del sito vengono trasmessi al Device Co-op per aiutare a costruire il grafico del dispositivo. La tabella seguente descrive come `isCoopSafe` funziona con questi casi d&#39;uso per bloccare o inviare dati al grafico del dispositivo

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso d'uso </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Visitatori autenticati</b> </p> </td> 
   <td colname="col2"> <p>Aggiungi <span class="codeph">isCoopSafe</span> al tuo codice del servizio ID per controllare il modo in cui vengono usati i dati dal Device Co-op per costruire il grafico del dispositivo per i visitatori autenticati che hanno o meno accettato le Condizioni d'uso. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>DIL su siti di terze parti</b> </p> </td> 
   <td colname="col2"> <p>Aggiungi <span class="codeph">isCoopSafe</span> al tuo codice del servizio ID per l'uso su siti di terze parti in cui: </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">Non è possibile garantire che i visitatori autenticati abbiano o meno accettato le Condizioni d’uso. </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">È necessario controllare in che modo quei dati vengono utilizzati da Device Co-op per costruire il grafico del dispositivo. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Sintassi ed esempio di codice {#section-952f56724a2b4d349340e26fbaf33ddd}

**Sintassi:** `isCoopSafe: true | false`

Le opzioni booleane determinano il modo in cui i dati dei clienti vengono o non vengono usati dal Device Co-op.

* `isCoopSafe: true`: i dati dei visitatori raccolti da un SDK mobile o da un sito Web *possono* essere usati per aiutare a creare il grafico del dispositivo.

* `isCoopSafe: false`: i dati dei visitatori raccolti da un SDK mobile o da un sito Web *non possono* essere usati per aiutare a creare il grafico del dispositivo.

**Esempio di codice**

Imposta questo quando il codice del servizio ID crea un’istanza:

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## Parametri POST della chiamata dell&#39;evento {#section-fcd441933506493faefaa6b51f194a17}

A seconda del flag che hai impostato (`true` o `false`), il servizio ID traduce `isCoopSafe` in questi parametri POST e li invia ad [!DNL Adobe] in una chiamata dell&#39;evento:

* `d_coop_safe=1`
* `d_coop_unsafe=1`

I parametri POST dicono all&#39;[!DNL Experience Cloud] Device Co-op se può o meno includere i dati degli utenti nel grafico del dispositivo. La tabella seguente definisce il rapporto tra i flag booleani `isCoopSafe` e i parametri POST trasmessi durante una chiamata dell&#39;evento. Se non usi `isCoopSafe`, nessuno dei due verrà trasmesso durante una chiamata dell&#39;evento.

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stato di configurazione </th> 
   <th colname="col2" class="entry"> Parametro POST </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>Il Device Co-op può usare i dati dei visitatori per costruire il grafico del dispositivo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>Il Device Co-op non può usare i dati dei visitatori per costruire il grafico del dispositivo. </p> </td> 
  </tr> 
 </tbody> 
</table>

## API di post-istanziazione {#section-9281c39c8b6249d7864100b5cbca7dc6}

Questi API ti consentono di ignorare lo stato `isCoopSafe`. Questi sono necessarie perché ti permettono di modificare lo stato di post-istanziazione/post-login di un visitatore su un sito o in un&#39;app a pagina singola in cui la pagina non viene aggiornata. Ad esempio, dovresti chiamare queste API se un utente si autentica sul tuo sito o sulla tua app e successivamente accetta una policy sulle condizioni d’uso che consente a Device Co-op di utilizzare i propri dati.

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>Imposta il parametro POST <span class="codeph">d_coop_safe=1</span> in tutte le chiamate dell'evento successive. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>Imposta il parametro POST <span class="codeph">d_coop_unsafe=1</span> in tutte le chiamate dell'evento successive. </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [DIL isCoopSafe](https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html)

