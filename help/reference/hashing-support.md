---
description: Il servizio Experience Cloud ID (ECID) supporta l’algoritmo di hashing SHA-256 che consente di ricevere gli ID o indirizzi e-mail dei clienti e di inoltrare gli ID con hashing. Questo è un metodo JavaScript facoltativo per l’invio di identificatori con hashing a Experience Cloud. Puoi continuare a utilizzare i tuoi attuali metodi di hashing prima di inviare gli ID dei clienti.
keywords: ID Service
seo-description: Il servizio Experience Cloud ID (ECID) supporta l’algoritmo di hashing SHA-256 che consente di ricevere gli ID o indirizzi e-mail dei clienti e di inoltrare gli ID con hashing. Questo è un metodo JavaScript facoltativo per l’invio di identificatori con hashing a Experience Cloud. Puoi continuare a utilizzare i tuoi attuali metodi di hashing prima di inviare gli ID dei clienti.
seo-title: Supporto di hashing SHA-256 per setCustomerIDs
title: Supporto di hashing SHA-256 per setCustomerIDs
translation-type: tm+mt
source-git-commit: ac1131be75fd04b51cd1d646086e1802a43afb18
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 91%

---


# Supporto di hashing SHA-256 per `setCustomerIDs` {#hashing-support}

Il servizio Experience Cloud ID (ECID) supporta l’algoritmo di hashing SHA-256 che consente di ricevere gli ID o indirizzi e-mail dei clienti e di inoltrare gli ID con hashing. Questo è un metodo JavaScript facoltativo per l’invio di identificatori con hashing a Experience Cloud. Puoi continuare a utilizzare i tuoi attuali metodi di hashing prima di inviare gli ID dei clienti.
Esistono due modi per implementare il supporto dell’hashing per setCustomerIDs, descritti nelle sezioni seguenti:

* [Utilizzare il metodo setCustomerIDs in ECID](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Aggiungere un’azione in Adobe Experience Platform Launch](/help/reference/hashing-support.md#add-action-launch)

## Utilizzare il metodo `setCustomerIDs` in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) method.

Prima di eseguire l’hashing, la libreria ECID esegue la normalizzazione dei dati sugli identificatori customerID. Durante questo processo vengono eliminati gli spazi bianchi a entrambe le estremità degli identificatori customerID e tutti i caratteri vengono convertiti in minuscole. Ad esempio, l’indirizzo e-mail &quot; ecid@adobe.com &quot; diventa &quot;ecid@adobe.com&quot;

Di seguito trovi un esempio di codice per impostare un singolo ID cliente (l’indirizzo e-mail indicato qui sopra) con hashing SHA-256.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

Oltre all’ID visitatore di Experience Cloud, puoi associare a ciascun visitatore altri ID cliente, lo stato di autenticazione e il tipo di hashing (SHA-256). Se non fornisci il tipo di hashing, l’impostazione verrà considerata come “senza hashing”.

Il `setCustomerIDs` metodo accetta più ID cliente per lo stesso visitatore. In questo modo puoi identificare o indirizzare un singolo utente in più dispositivi. For example, you can upload these IDs as [customer attributes](https://docs.adobe.com/content/help/it-IT/core-services/interface/customer-attributes/attributes.html) to the Experience Cloud and access this data across the different solutions.

Gli ID cliente, gli stati di autenticazione e il tipo di hashing *non sono* memorizzati in un cookie da utilizzare in un secondo momento. Al contrario, gli ID cliente, gli stati di autenticazione e il tipo hashing devono essere memorizzati in una variabile di istanza, da recuperare mediante [`getCustomerIDs`](/help/library/get-set/getcustomerids.md), come illustrato di seguito:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

Quando si utilizza il metodo `setCustomerIDs` si verifica una chiamata al servizio Experience Cloud ID, a `dpm.demdex.net`, con l’aggiunta del parametro di query `d_cid_ic` che contiene l’ID cliente con hashing. Di seguito riportiamo un esempio di chiamata. Per chiarezza, sono state aggiunte delle interruzioni di riga.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

Per una descrizione del parametro `d_cid_ic` e dello stato di autenticazione, consulta la tabella seguente.

| Parametro | Descrizione |
|------------|----------|
| `d_cid_ic` | Trasmette al servizio ID il codice di integrazione, l’ID utente univoco (DPUUID) e un ID di stato di autenticazione. Separa il codice integrazione e il DPUUID con il carattere di controllo non stampabile %01</code>: <br> Esempio: d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>Stato di autenticazione</b> <br> Questo è un ID opzionale nel parametro d_cid_ic. Espresso sotto forma di numero intero, identifica gli utenti a seconda del loro stato di autenticazione come mostrato di seguito: <br> <ul><li>0 (utente sconosciuto o mai autenticato)</li><li>1 (attualmente autenticato per il contesto di questa istanza/pagina/app)</li><li>2 (disconnesso)</li></ul> <br> Esempi: <br> <ul><li>Sconosciuto: ...d_cid=123%01456%01<b>0</b></li><li>Autenticato: ...d_cid=123%01456%01<b>1</b></li><li>Disconnesso: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Aggiungere un’azione in Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launch è la soluzione Adobe di nuova generazione per la gestione dei tag. Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/it-IT/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/it-IT/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

<br> 

Dopo aver confermato la configurazione, Launch racchiude i dati in un oggetto, come segue:

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

Esempio di codice:

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

In modo analogo al metodo `setCustomerIDs` descritto nella prima sezione, si verifica una chiamata al servizio Experience Cloud ID, con l’aggiunta del parametro di query `d_cid_ic`.