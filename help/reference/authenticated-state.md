---
description: Oltre all’ID visitatore di Experience Cloud, puoi associare altri ID cliente e uno stato di autenticazione a ciascun visitatore.
keywords: Servizio ID
title: ID cliente e stati di autenticazione
exl-id: 0215225c-20f5-4e44-a368-b2df683aca9d
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 100%

---

# ID cliente e stati di autenticazione {#customer-ids-and-authentication-states}

Oltre all’ID visitatore di Experience Cloud, puoi associare altri ID cliente e uno stato di autenticazione a ciascun visitatore.

## Stati di autenticazione {#section-68ad4065dfaa437d9070832d6e2bf85c}

Il `setCustomerIDs` metodo accetta più ID cliente per lo stesso visitatore. In questo modo puoi identificare o indirizzare un singolo utente in più dispositivi. Ad esempio, puoi caricare gli ID come [attributi del cliente](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=it) in [!DNL Experience Cloud] e accedere ai dati dalle diverse soluzioni.

>[!IMPORTANT]
>
>`setCustomerIDs` (sincronizzazione ID cliente) è richiesto per gli attributi dei clienti e le funzionalità dei servizi principali. La sincronizzazione degli ID cliente è un metodo di identificazione facoltativo per [!DNL Analytics]. [!DNL Target] richiede `Visitor.AuthState.AUTHENTICATED` per il funzionamento degli attributi cliente. Alcuni esempi sono disponibili in [Servizi principali - Come attivare le proprie soluzioni](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/solutions-core-services.html?lang=it).

A partire dalla versione 1.5 di Experience Cloud Identity Service, `setCustomerIDs` include l’oggetto facoltativo `AuthState`. `AuthState` identifica i visitatori in base al loro stato di autenticazione (ad es. connessi o disconnessi). Lo stato di autenticazione si imposta con uno dei valori di stato elencati nella tabella. Lo stato di autenticazione viene restituito come numero intero.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stato di autenticazione </th> 
   <th colname="col2" class="entry"> Numero intero dello stato </th> 
   <th colname="col3" class="entry"> Stato dell’utente </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>Utente sconosciuto o mai autenticato. </p> <p> Lo stato Sconosciuto viene applicato per impostazione predefinita quando <span class="codeph">AuthState</span> non viene usato con un ID visitatore o non è impostato in modo esplicito su ciascuna pagina o contesto dell’applicazione. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>Utente autenticato per un’istanza, pagina o applicazione specifica. </p> <p> <p>Attenzione: per funzionare correttamente, gli attributi cliente per <span class="keyword">Target</span> devono avere questo stato. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 2 </span> </p> </td> 
   <td colname="col3"> <p>Utente disconnesso. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Casi d’uso per gli stati di autenticazione {#section-fe9560cc490943b29dac2c4fb6efd72c}

È possibile assegnare gli stati di autenticazione agli utenti, a seconda delle azioni che questi eseguono sulle proprietà Web e del fatto che siano autenticati o meno. La tabella seguente riporta alcuni esempi:

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stato di autenticazione </th> 
   <th colname="col2" class="entry"> Caso d’uso </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>Questo stato può essere utilizzato per scenari quali: </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">si legge un’e-mail (questa azione probabilmente indica che il lettore è il destinatario desiderato, ma l’e-mail potrebbe anche essere stata inoltrata) </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">si fa clic su un elemento dell’e-mail che conduce a una pagina di destinazione. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>Al momento l’utente è autenticato con una sessione attiva sul sito Web o sull’app. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>L’utente si è autenticato ma si è disconnesso in modo attivo. L’utente desiderava disconnettersi dallo stato autenticato. L’utente non desidera più essere trattato come utente autenticato. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Impostazione degli ID cliente e degli stati di autenticazione {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

Gli ID cliente possono includere combinazioni di ID e stati di identificazione, come indicato nei seguenti esempi.

>[!IMPORTANT]
>
>* Gli ID sono sensibili all’uso di maiuscole e minuscole.
>* Per gli ID, usa solo valori non codificati.
>* Gli ID cliente e gli stati di autenticazione non sono memorizzati nel cookie dell’ID visitatore. Devono essere impostati per ciascuna pagina o contesto dell’applicazione.
>* Negli ID cliente non devono essere incluse informazioni identificative della persona (Personally Identifiable Information, PII). Invece di utilizzare informazioni PII per identificare un visitatore (ad esempio l’indirizzo e-mail), consigliamo di memorizzare una versione con hashing o codificata di queste informazioni. La libreria ECID supporta l’hashing degli identificatori utente. Consulta [Supporto di hashing SHA-256 per setCustomerIDs](/help/reference/hashing-support.md).

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
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
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
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## Restituzione degli ID cliente e degli stati di autenticazione {#section-71a610546188478fa9a3185a01d6e83b}

Per restituire gli ID cliente e i relativi stati di autenticazione, utilizza `getCustomerIDs`. Questo metodo restituisce lo stato di autenticazione di un visitatore sotto forma di numero intero.

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

Gli ID cliente e i dati sullo stato di autenticazione restituiti saranno simili agli esempi seguenti.

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
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## Supporto per l’SDK {#section-861c6b3b1ba645dda133dccb22ec7bb0}

Il servizio [!DNL Experience Cloud] ID supporta gli ID dei clienti e gli stati di autenticazione nel nostro codice SDK per Android e iOS. Consulta le seguenti librerie di codice:

* [Metodi SDK per Android](https://experienceleague.adobe.com/docs/mobile-services/android/overview.html?lang=it)
* [Metodi SDK per iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/overview.html?lang=it)

## Avviso per i clienti Analytics e Audience Manager {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

Se trasferisci ID dichiarati ad [!DNL Audience Manager], l’oggetto `userid` deve corrispondere al codice di integrazione associato a un’origine dati. Per ulteriori informazioni, consulta la sezione [!UICONTROL Servizio ID visitatore] nel documento [Configurazione codice delle regole di unione](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html?lang=it#configure-merge-rule-code).
