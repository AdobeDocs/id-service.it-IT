---
description: Il servizio Experience Cloud ID (ECID) supporta l'algoritmo di hash SHA -256 che consente di trasmettere ID cliente o indirizzi e-mail e di trasmettere gli ID con hash. Questo è un metodo Javascript facoltativo per l'invio di identificatori hash a Experience Cloud. Puoi continuare a utilizzare i tuoi metodi di hashing prima di inviare gli ID cliente.
keywords: Servizio ID
seo-description: Il servizio Experience Cloud ID (ECID) supporta l'algoritmo di hash SHA -256 che consente di trasmettere ID cliente o indirizzi e-mail e di trasmettere gli ID con hash. Questo è un metodo Javascript facoltativo per l'invio di identificatori hash a Experience Cloud. Puoi continuare a utilizzare i tuoi metodi di hashing prima di inviare gli ID cliente.
seo-title: SHA 256 Hashing Support for setcustomerids
title: SHA 256 Hashing Support for setcustomerids
translation-type: tm+mt
source-git-commit: 0311d57391a0a9d5ac5a0bba255ca71bdffd67c0

---


# SHA256 Hashing Support for `setCustomerIDs` {#hashing-support}

Il servizio Experience Cloud ID (ECID) supporta l'algoritmo di hash SHA -256 che consente di trasmettere ID cliente o indirizzi e-mail e di trasmettere gli ID con hash. Questo è un metodo Javascript facoltativo per l'invio di identificatori hash a Experience Cloud. Puoi continuare a utilizzare i tuoi metodi di hashing prima di inviare gli ID cliente.
Esistono due modi per implementare il supporto di hash con setcustomerids, come descritto nelle sezioni seguenti:

* Utilizzare il metodo setcustomerids in ECID
* Aggiunta di un'azione in Adobe Experience Platform Launch

## Use the `setCustomerIDs` method in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) method.

Prima di eseguire l'hash, la libreria ECID esegue la normalizzazione dei dati sugli customerids. Questo processo taglia le whitelist degli customerids su entrambe le estremità e converte tutti i caratteri in minuscole. Ad esempio, per indirizzi e-mail: " ecid@adobe.com "diventa" ecid@adobe.com "

Consultate sotto un esempio di codice come impostare un singolo ID cliente (l'indirizzo e-mail indicato sopra) con hash SHA -256.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

Oltre all'ID visitatore di Experience Cloud, puoi associare altri ID cliente, lo stato di autenticazione e il tipo hash (SHA -256) a ogni visitatore. Se non si fornisce alcun tipo hash, questo verrà considerato come non hash.

Il `setCustomerIDs` metodo accetta più ID cliente per lo stesso visitatore. In questo modo puoi identificare o indirizzare un singolo utente in più dispositivi. Ad esempio, puoi caricare gli ID come [attributi del cliente](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) in Experience Cloud e accedere ai dati dalle diverse soluzioni.

Customer IDs, authenticated states and hash type *are not* stored in a cookie to be used later. Instead, Customer IDs, authenticated states and hash type should be stored in an instance variable, to be retrieved using [`getCustomerIDs`](/help/library/get-set/getcustomerids.md), as shown below:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

Using the `setCustomerIDs` method results in a call to the Experience Cloud ID Service, to `dpm.demdex.net`, with the addition of the `d_cid_ic` query parameter, which contains the hashed customer ID. Una chiamata di esempio potrebbe essere simile a quella riportata di seguito. Sono state aggiunte interruzioni di riga per chiarezza.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

See the table below for a description of the `d_cid_ic` parameter and authentication state.

| Parametro | Descrizione |
|------------|----------|
| `d_cid_ic` | Trasmette il codice di integrazione, l'ID utente univoco (DPUUID) e un ID di stato autenticato al servizio ID. Separate the Integration Code and DPUUID with the non-printing control character, <code>%01</code>: <br> Example: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>Stato di autenticazione</b> <br> Questo è un ID opzionale nel parametro d_ cid_ ic. Espresso sotto forma di numero intero, identifica gli utenti a seconda del loro stato di autenticazione come mostrato di seguito: <br> <ul><li>0 (Sconosciuto o non autenticato)</li><li>1 (autenticato per il contesto di istanza/pagina/app)</li><li>2 (disconnesso)</li></ul> <br> Esempi: <br> <ul><li>Sconosciuto: ...d_cid=123%01456%01<b>0</b></li><li>Autenticato: ...d_cid=123%01456%01<b>1</b></li><li>Disconnesso: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Add an Action in Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launch è la nuova generazione di funzionalità di gestione tag di Adobe. Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/en/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

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

Esempio di esempio di codice:

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Similarly to the `setCustomerIDs` method described in the first section, this results in a call to the Experience Cloud ID Service, with the addition of the `d_cid_ic` query parameter.