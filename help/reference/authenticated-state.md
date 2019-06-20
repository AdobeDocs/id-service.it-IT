---
description: Oltre all'ID visitatore di Experience Cloud, puoi associare altri ID cliente e uno stato di autenticazione a ciascun visitatore.
keywords: Servizio ID
seo-description: Oltre all'ID visitatore di Experience Cloud, puoi associare altri ID cliente e uno stato di autenticazione a ciascun visitatore.
seo-title: ID cliente e stati di autenticazione
title: ID cliente e stati di autenticazione
uuid: 643 df 363-224 a -463 e-a 332-be 59926 b 47 e 7
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# ID cliente e stati di autenticazione {#customer-ids-and-authentication-states}

Oltre all&#39;ID visitatore di Experience Cloud, puoi associare altri ID cliente e uno stato di autenticazione a ciascun visitatore.

## Stati di autenticazione {#section-68ad4065dfaa437d9070832d6e2bf85c}

Il metodo `setCustomerIDs` accetta più ID cliente per lo stesso visitatore. In questo modo puoi identificare o indirizzare un singolo utente in più dispositivi. Ad esempio, puoi caricare gli ID come [attributi del cliente](https://marketing.adobe.com/resources/help/en_US/mcloud/?f=attributes.html) in [!DNL Experience Cloud] e accedere ai dati dalle diverse soluzioni.

>[!IMPORTANT]
>
>`setCustomerIDs` (Sincronizzazione ID cliente) è necessaria per gli attributi del cliente e le funzionalità dei servizi core. La sincronizzazione degli ID cliente è un metodo di identificazione facoltativo per [!DNL Analytics]. [!DNL Target] richiede `Visitor.AuthState.AUTHENTICATED` che gli attributi del cliente funzionino. Alcuni esempi sono disponibili in [Servizi principali - Come attivare le proprie soluzioni](https://marketing.adobe.com/resources/help/en_US/mcloud/?f=core_services).

Beginning with Experience Cloud ID Service v1.5+, `setCustomerIDs` includes the optional `AuthState` object. `AuthState` identifica i visitatori in base al loro stato di autenticazione (ad es. connessi o disconnessi). Lo stato di autenticazione deve essere impostato con uno stato indicato nella tabella. Lo stato di autenticazione viene restituito come numero intero.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stato di autenticazione </th> 
   <th colname="col2" class="entry"> Numero intero di stato </th> 
   <th colname="col3" class="entry"> Stato dell'utente </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>Utente sconosciuto o mai autenticato. </p> <p> Lo stato Sconosciuto viene applicato per impostazione predefinita quando <span class="codeph">AuthState</span> non viene usato con un ID visitatore o non è impostato in modo esplicito su ciascuna pagina o contesto dell'applicazione. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>Utente autenticato per un'istanza, pagina o applicazione specifica. </p> <p> <p>Attenzione: per funzionare correttamente, gli attributi cliente per <span class="keyword">Target</span> devono avere questo stato. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 2 </span> </p> </td> 
   <td colname="col3"> <p>Utente disconnesso. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Casi d&#39;uso per gli stati di autenticazione {#section-fe9560cc490943b29dac2c4fb6efd72c}

È possibile assegnare gli stati di autenticazione agli utenti, a seconda delle azioni che questi eseguono sulle proprietà Web e del fatto che siano autenticati o meno. Nella tabella di seguito sono illustrati alcuni esempi:

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stato di autenticazione </th> 
   <th colname="col2" class="entry"> Caso d'uso </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>Questo stato potrebbe essere usato quando: </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">si legge un'e-mail (questa azione probabilmente indica che il lettore è il destinatario desiderato, ma l'e-mail potrebbe anche essere stata inoltrata) </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">si fa clic su un elemento dell'e-mail che conduce a una pagina di destinazione. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>Al momento l'utente è autenticato con una sessione attiva sul sito Web o sull'app. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>L'utente si è autenticato ma si è disconnesso in modo attivo. L'utente desiderava disconnettersi dallo stato autenticato. L'utente non desidera più essere trattato come utente autenticato. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Impostazione degli ID cliente e degli stati di autenticazione {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

Gli ID cliente possono includere combinazioni di ID e stati di identificazione, come indicato nei seguenti esempi.

>[!IMPORTANT]
>
>* Gli ID sono sensibili all&#39;uso di maiuscole e minuscole.
>* Per gli ID, usa solo valori non codificati.
>* Gli ID dei clienti e gli stati di autenticazione non vengono memorizzati nel cookie ID visitatore. Devono essere impostati per ciascuna pagina o contesto dell&#39;applicazione.
>* Negli ID cliente non devono essere incluse informazioni identificative della persona. Invece di utilizzare informazioni di questo tipo per identificare un visitatore (ad esempio l&#39;indirizzo e-mail), consigliamo di memorizzare una versione con hash o codificata di queste informazioni.
>



```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## Restituzione degli ID cliente e degli stati di autenticazione {#section-71a610546188478fa9a3185a01d6e83b}

Per restituire gli ID cliente e i relativi stati di autenticazione, utilizza `getCustomerIDs`. Questo metodo restituisce lo stato di autenticazione del visitatore sotto forma di numero intero.

**Sintassi**

`getCustomerIDs` restituisce i dati con la seguente sintassi.

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**Esempi**

Gli ID cliente e i dati sullo stato di autenticazione restituiti devono essere simili ai seguenti esempi.

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"puuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "puuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## Supporto per l&#39;SDK {#section-861c6b3b1ba645dda133dccb22ec7bb0}

Il servizio [!DNL Experience Cloud] ID supporta gli ID dei clienti e gli stati di autenticazione nel nostro codice SDK per Android e iOS. Vedi le seguenti librerie di codice:

* [Metodi SDK per Android](https://marketing.adobe.com/resources/help/en_US/mobile/android/?f=c_marketing_cloud.html)
* [Metodi SDK per iOS](https://marketing.adobe.com/resources/help/en_US/mobile/ios/?f=marketing_cloud.html)

## Avviso per i clienti Analytics e Audience Manager {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

Se trasferisci ID dichiarati ad [!DNL Audience Manager], l&#39;oggetto `userid` deve corrispondere al codice di integrazione associato a un&#39;origine dati. For more information, see the [!DNL Visitor ID Service] section in the [Configure Merge Rules Code](https://marketing.adobe.com/resources/help/en_US/aam/?f=merge-rules-configure-code.html) documentation.
