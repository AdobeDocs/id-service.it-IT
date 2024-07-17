---
description: Questa proprietà imposta l'ID del contenitore della sorgente dati che desideri usare per le sincronizzazioni ID.
keywords: Servizio ID
title: idSyncContainerID
exl-id: 6c4cd41b-902b-4872-8c3f-475a834b76f4
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 100%

---

# idSyncContainerID{#idsynccontainerid}

Questa proprietà imposta l&#39;ID del contenitore della sorgente dati che desideri usare per le sincronizzazioni ID.

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

I contenitori sono oggetti creati da [!DNL Audience Manager]. Sebbene non siano accessibili esternamente, questi contenitori elencano tutte le origini dati che:

* sono disponibili ma non utilizzati per la sincronizzazione ID;
* vengono utilizzati per la sincronizzazione ID.

Anche se non sei un [!DNL Audience Manager] cliente, il tuo account avrà questi contenitori se stai scambiando ID con varie sorgenti dati su pagine diverse all&#39;interno del tuo dominio. Questo perché [!DNL Audience Manager] offre la tecnologia e la funzionalità di back-end che consente la sincronizzazione ID.

**Casi d&#39;uso**

A seconda della situazione, potresti dover o meno aggiungere questa configurazione al codice del servizio ID.

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
   <td colname="col2"> <p>Non è necessario utilizzare questa configurazione nei seguenti casi: </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">Usi il servizio ID con qualsiasi soluzione <span class="keyword">Experience Cloud</span> e non esegui sincronizzazioni ID con altre sorgenti dati. In questo caso, il tuo account dispone di un contenitore predefinito con ID 0 e non è richiesta alcuna azione. </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">Tutte le origini dati si trovano in un unico contenitore. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Necessario</b> </p> </td> 
   <td colname="col2"> <p>Devi utilizzare questa configurazione quando si applicano tutte queste condizioni: </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">Non usi <span class="keyword">Audience Manager </span>. </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">Devi sincronizzare gli ID con altre origini dati organizzate per contenitori. </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">Devi sincronizzare gli ID con le sorgenti dati in contenitori diversi su pagine diverse all’interno del tuo dominio. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Impostazione degli ID dei contenitori quando usi DIL e VisitorAPI.js {#section-f283cb69c8de4348b5316cc4e02a3e9e}

Se hai implementato [!UICONTROL DIL ]* e* VisitorAPI.js sulla stessa pagina:

* Il codice del servizio ID del visitatore ha la precedenza rispetto a DIL per le sincronizzazioni ID.
* Imposta la configurazione `idSyncContainerID` solo nel codice del servizio ID.
