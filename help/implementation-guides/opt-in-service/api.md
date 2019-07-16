---
description: API per la libreria Opt-in e riferimenti alle impostazioni di configurazione.
seo-description: API per la libreria Opt-in e riferimenti alle impostazioni di configurazione.
seo-title: Riferimenti di Opt-in
title: Riferimenti di Opt-in
uuid: d5023a34-2f3e-464d-b21f-579b2f416ce6
translation-type: tm+mt
source-git-commit: 4fbfefddcf36855f32f2a4047e19ef0b22fc508c

---


# Riferimenti di Opt-in{#opt-in-reference}

API per la libreria Opt-in e riferimenti alle impostazioni di configurazione.

Le impostazioni sul consenso vengono fornite alle funzioni di Opt-in come categorie:

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## Parametri di configurazione Opt-in {#section-d66018342baf401389f248bb381becbf}

Questa sezione illustra come usare l&#39;API per configurare Opt-in. Gran parte della configurazione e dell&#39;implementazione può essere effettuata utilizzando l&#39;estensione Experience Platform Launch.

Le configurazioni di Opt-in vengono fornite nella funzione `getInstance()` di JavaScript per il visitatore che crea l&#39;istanza per l&#39;oggetto globale `adobe`. Di seguito si riporta un elenco delle configurazioni di JS per il visitatore per il servizio Opt-in.

**`doesOptInApply (boolean or function that evaluates to a boolean)`**:

Se falso indica che i visitatori non devono dare il consenso. Comporta la creazione di cookie da parte di Experience Cloud indipendentemente dalle categorie a cui l&#39;utente ha dato o ha negato il consenso. Questa configurazione abilita in modo olistico Opt-in.

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

Definisce quali categorie vengono approvate o negate se il visitatore non ha ancora impostato le preferenze; vengono definiti valori predefiniti dell&#39;organizzazione.

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

Il visitatore ha impostato in modo esplicito le preferenze. In questa configurazione le autorizzazioni sostituiscono i valori predefiniti dell&#39;organizzazione (`previousPermissions` sostituisce `preOptInApprovals`).

**`isOptInStorageEnabled (boolean)`**

Attiva per Opt-in l&#39;archiviazione delle autorizzazioni in un cookie di prima parte (all&#39;interno del dominio dell&#39;attuale cliente).

(Facoltativo) **`optInCookiesDomain (string)`**

Dominio di prima parte o sottodominio da usare per il cookie Opt-in (se `isOptInStorageEnabled` è true).

(Facoltativo) **`optInStorageExpiry (integer)`**

Numero di secondi necessari per ignorare il valore di scadenza predefinito di 13 mesi.

## Modifiche ai parametri di consenso {#section-c3d85403ff0d4394bd775c39f3d001fc}

Mentre visita il sito, il visitatore può impostare le preferenze per la prima volta oppure modificarle usando CMP in qualsiasi momento. Dopo aver inizializzato JS per il visitatore con le impostazioni iniziali, è possibile modificare le autorizzazioni del visitatore usando le funzioni seguenti:

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Funzione che approva oppure dà il consenso del visitatore a tutte le categorie di un elenco. Per altre informazioni sul parametro shouldWaitForComplete consultare [Flusso di lavoro di Opt-in](../../implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5).

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

Funzione che nega o rifiuta il consenso del visitatore a tutte le categorie specificate.

**`adobe.optIn.approveAll()`**:

Se la richiesta di autorizzazione per il sito da creare è formulata in modo che la copertura del visitatore conceda o neghi l&#39;autorizzazione per il sito a creare cookie, usa `approveAll()` o `denyAll()` relativamente alla risposta.

**`adobe.optIn.denyAll()`**:

Se la richiesta di autorizzazione per il sito da creare è formulata in modo che la copertura del visitatore conceda o neghi l&#39;autorizzazione per il sito a creare cookie, usa `approveAll()` o `denyAll()` relativamente alla risposta.

## Parametri dei flussi di lavoro Opt-in {#section-2c5adfa5459c4e72b96d2693123a53c2}

Opt-in supporta un flusso di lavoro in cui è possibile raccogliere le autorizzazioni per più di un ciclo di richiesta, come ad esempio quando le preferenze vengono assegnate tutte insieme. Usando le seguenti funzioni e specificando *true* per l&#39;impostazione `shouldWaitForComplete`, la soluzione è in grado di raccogliere il consenso per una soluzione o un sottoinsieme di tutte le categorie e poi di raccoglierlo per la soluzione o il sottoinsieme di categorie successivo. A partire dalla prima chiamata, la proprietà `adobe.optIn.status` sarà in sospeso fino a quando `adobe.optIn.complete()` non viene chiamata alla fine del flusso. Una volta effettuata la chiamata, lo stato viene impostato su *Complete*.

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Funzione che approva oppure dà il consenso del visitatore a tutte le categorie di un elenco.

`adobe.optIn.deny(categories, shouldWaitForComplete)`

Funzione che nega o rifiuta il consenso del visitatore a tutte le categorie specificate.

`adobe.optIn.complete()`

Funzione che attiva l&#39;aggregazione delle chiamate in esecuzione per approvare() e rifiutare() una richiesta per impostare le preferenze di un visitatore. Quando si sottoscrivono le modifiche di Opt-in (consultare `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe`) di seguito, il callback viene attivato solo quando si chiama questa funzione.

## Parametri di autorizzazione Opt-in del visitatore {#section-7fe57279b5b44b4f8fe47e336df60155}

È possibile usare una delle funzioni di autorizzazione in qualsiasi momento per raccogliere le autorizzazioni Opt-in di un visitatore.

`adobe.optIn.permissions`

Un oggetto in ascolto di tutte le soluzioni Experience Cloud, come categorie, a cui il visitatore ha dato o negato il proprio consenso.

`adobe.optIn.isApproved(categories)`

Se tutte le categorie sono state approvate, questa funzione restituirà true.

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

Recupera l&#39;elenco di autorizzazioni in modo asincrono. Il callback avviene con l&#39;elenco di autorizzazioni, quando il processo di concessione/negazione delle autorizzazioni viene completato. Specificando il valore *true* per `shouldAutoSubscribe` si registra il callback per tutte le future modifiche di Opt-in. le seguenti sono proprietà di `adobe.OptIn`:

**`permissions`**

Un oggetto in ascolto di tutte le soluzioni Experience Cloud, come categorie, a cui il visitatore ha dato o negato il proprio consenso. Ad esempio: `{ aa: true, ecid: false, aam: true... }`

**`status`**

* in sospeso
* modificato
* completato

**`doesOptInApply`**

True o false, rappresenta la configurazione fornita nell&#39;inizializzazione.

**`isPending`**

True o false in base al valore dello stato. Opt-in indica true per questa proprietà per un visitatore che non ha ancora accettato o negato in modo esplicito l&#39;autorizzazione.

**`isComplete`**

True o false in base al valore dello stato. Opt-in potrebbe indicare false per questa proprietà quando è stato avviato un flusso di lavoro di consenso, ma non è stato completato.

## Metodi dell&#39;oggetto Opt-in {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**: una o più categorie da approvare. Ad esempio: `adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`
**`shouldWaitForComplete`**: (facoltativo), parametro booleano, false per impostazione predefinita. Se lo si cambia in true, Opt-in non completa il processo di approvazione fino a quando non si chiama `adobe.optIn.complete()`. Questo processo è simile a un flusso di lavoro.

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* Passare una o più categorie per verificare che sono state approvate.
* Se non viene passata alcuna categoria, vengono controllate TUTTE le categorie disponibili.

**`isApproved(categories)`**

Consente di controllare se una o più categorie sono state approvate dal cliente.

**`isPreApproved(categories)`**

Consente di controllare se una o più categorie sono state preapprovate dal cliente. (Se sono state passate nella `preOptInApprovals` configurazione).

**`fetchPermissions(callback, shouldAutoSubscribe)`**

API asincrona per recuperare l&#39;elenco di autorizzazioni. Il callback avviene con l&#39;elenco di autorizzazioni, quando il processo di concessione/negazione delle autorizzazioni viene completato. **`shouldAutoSubscribe`**: un&#39;utilità helper, sottoscrive automaticamente questo callback a tutti gli eventi futuri. Questo significa che il callback verrà chiamato ogni volta che si attiva un&#39;approvazione o una negazione in Opt-in. In questo modo sarai sempre aggiornato, senza doverti iscrivere agli eventi.

**Esempio**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()`:**

>[!NOTE]
>
>Da usare solo se si è passato il `shouldWaitForComplete` parametro per l&#39;approvazione o la negazione. Questa API completa il processo di approvazione. Esempio: `adobe.optIn.complete()`.

**`approveAll()`:**

Approva tutte le categorie esistenti.

**`denyAll()`**

Nega tutte le categorie esistenti.

## Eventi dell&#39;oggetto Opt-in {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

L&#39;evento completo si attiva quando il processo di approvazione è stato completato. Se si chiama l&#39;approvazione/negazione senza passare `shouldWaitForComplete` o `approveAll`/`denyAll`, si attiva questo evento. Oppure se si passa `shouldWaitForComplete`, questo evento si attiva quando si chiama `complete`.

**Esempio**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
