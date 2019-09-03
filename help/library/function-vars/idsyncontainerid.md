---
description: Questa proprietà imposta l'ID del contenitore della sorgente dati che desideri usare per le sincronizzazioni ID.
keywords: Servizio ID
seo-description: Questa proprietà imposta l'ID del contenitore della sorgente dati che desideri usare per le sincronizzazioni ID.
seo-title: idSyncContainerID
title: idSyncContainerID
uuid: e35dc48b-1aa1-41e3-91c1-ef1e9d2d8b90
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# idSyncContainerID{#idsynccontainerid}

Questa proprietà imposta l'ID del contenitore della sorgente dati che desideri usare per le sincronizzazioni ID.

Sommario:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> Sintassi ed esempio di codice </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local"> Cosa sono i contenitori e quando dovrei usarli? </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> Impostazione degli ID dei contenitori quando usi DIL e VisitorAPI.js </a> </li> 
</ul>

## Sintassi ed esempio di codice {#section-b0c50732b1c84bed8616e82e8e83d58c}

**Sintassi:** ` idSyncContainerID: *`valore ID contenitore`*`

**Esempio di codice:**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## Cosa sono i contenitori e quando dovrei usarli? {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**Contenitori**

I contenitori sono oggetti creati da [!DNL Audience Manager]. Sebbene non siano accessibili dall'esterno, i contenitori elencano tutte le sorgenti dati che:

* Hai a disposizione, ma non usi, per la sincronizzazione ID.
* Sono state usate per la sincronizzazione ID.

Anche se non sei un [!DNL Audience Manager] cliente, il tuo account avrà questi contenitori se stai scambiando ID con varie sorgenti dati su pagine diverse all'interno del tuo dominio. Questo perché [!DNL Audience Manager] offre la tecnologia e la funzionalità di back-end che consente la sincronizzazione ID.

**Casi d'uso**

A seconda della situazione, potresti aver bisogno o meno di aggiungere questa configurazione al codice del servizio ID.

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Condizione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Non necessario</b> </p> </td> 
   <td colname="col2"> <p>Non hai bisogno di usare questa configurazione se: </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">Usi il servizio ID con qualsiasi soluzione <span class="keyword">Experience Cloud</span> e non esegui sincronizzazioni ID con altre sorgenti dati. In questo caso, il tuo account ha un contenitore predefinito con ID 0 e non è richiesta alcuna azione. </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">Tutte le tue sorgenti dati si trovano in un unico contenitore. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Necessario</b> </p> </td> 
   <td colname="col2"> <p>Hai bisogno di usare questa configurazione quando sono applicabili tutte queste condizioni: </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">Non usi <span class="keyword">Audience Manager </span>. </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">Devi sincronizzare gli ID con altre sorgenti dati che sono organizzate per contenitori. </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">Devi sincronizzare gli ID con sorgenti dati presenti in contenitori diversi su pagine diverse all'interno del tuo dominio. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Impostazione degli ID dei contenitori quando usi DIL e VisitorAPI.js {#section-f283cb69c8de4348b5316cc4e02a3e9e}

Se hai implementato [!UICONTROL DIL] *e* VisitorAPI.js sulla stessa pagina:

* Il codice del servizio ID del visitatore ha la precedenza rispetto a DIL per le sincronizzazioni ID.
* Imposta la configurazione `idSyncContainerID` solo nel codice del servizio ID.

