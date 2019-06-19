---
description: Implementa il servizio di consenso come punto di riferimento singolo utilizzato dalle soluzioni Experience Cloud (altrimenti denominato Categorie in Consenso) per determinare se creare o meno cookie sul dispositivo di un visitatore.
seo-description: Implementa il servizio di consenso come punto di riferimento singolo utilizzato dalle soluzioni Experience Cloud (altrimenti denominato Categorie in Consenso) per determinare se creare o meno cookie sul dispositivo di un visitatore.
seo-title: Configurazione del servizio di consenso
title: Configurazione del servizio di consenso
uuid: f 1 c 27139-cef 2-4122-af 12-c 839 cfc 82 e 6 e
translation-type: tm+mt
source-git-commit: 746f8937c59d318dcf7245c7f8484884974601dc

---


# Configurazione del servizio di consenso{#setting-up-opt-in-service}

Implementa il servizio di consenso come punto di riferimento singolo utilizzato dalle soluzioni Experience Cloud (altrimenti denominato Categorie in Consenso) per determinare se creare o meno cookie sul dispositivo di un visitatore.

Il servizio Opt-in è una libreria javascript fornita con Adobe Experience Platform Identity Service ed esiste in JS visitatore nell&#39;oggetto globale `adobe` come `adobe.optIn` oggetto. Il servizio di consenso installato consente di specificare se un visitatore può optare per le soluzioni Adobe alla volta o per presentare soluzioni in sequenza per ogni autorizzazione. La funzione di gestione del consenso del servizio di consenso consente di implementare diverse configurazioni per i requisiti di privacy specifici.

Il servizio di consenso consente di specificare se un visitatore può optare per le soluzioni Adobe alla volta oppure per presentare soluzioni in sequenza per ogni tipo di autorizzazione. Quando il processo di approvazione è stato completato e registrato dal cliente, è possibile recuperare le approvazioni del visitatore CMP da tutte le soluzioni Adobe per rispondere con le relative chiamate di consenso.

## Prerequisiti {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID versione 4.0

   [Scarica](https://github.com/Adobe-Marketing-Cloud/id-service/releases) la versione di ECID più recente.

1. Librerie di supporto:

   * ECID 4.0 o versione successiva
   * AppMeasurement 2.11 o versione successiva
   * DIL 9.0
   * AT.js versione 1.7.0
   * Estensione di Launch di AT.js versione 9.0
   * Per Analytics, AppMeasurement 2.11 con estensione 1.6
   * Per Target, estensione 0.9.1

1. Approfondisci le conoscenze relative al framework di gestione dei consensi che userai con Opt-in e individua eventuali prerequisiti aggiuntivi.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. I requisiti di privacy dell&#39;azienda saranno specifici in base alla scelta di rispettare il RGPD. Verifica quali librerie i team di privacy dell&#39;azienda desiderano usare in uno stato che precede il consenso.

Se usi [Adobe Launch](https://docs.adobelaunch.com/) usa [Estensione di consenso](../../implementation-guides/opt-in-service/launch.md) per configurare il servizio di consenso.

## Categorie di consenso {#section-9ab0492ab4414f0ca16dc08d3a905f47}

Le preferenze Opt-in di un visitatore sono relative a una soluzione Adobe Experience Cloud, dove ogni soluzione è rappresentata come una categoria. Le categorie vengono fornite dall&#39;oggetto `adobe.OptInCategories` dove, ad esempio, il componente ECID viene indicato come `adobe.OptInCategories`. `ECID`. Di seguito la definizione di `adobe.OptInCategories`:

Le impostazioni di Opt-in vengono mantenute per ciascuna categoria, dove ogni soluzione Experience Cloud è rappresentata da una categoria:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

Il servizio Consenso consente di impostare le preferenze di autorizzazione dei visitatori per ciascuna soluzione Adobe utilizzata sul sito. Include una libreria per salvare le impostazioni del visitatore mediante una categoria approvata e supporta un flusso sequenziale dove il processo di approvazione riceve le preferenze di &quot;conferma&quot; o &quot;rifiuto&quot; una alla volta per ogni categoria. Puoi impostare il consenso di tutte le soluzioni/categorie insieme oppure per ogni singola soluzione.
Tutte le librerie lato client delle soluzioni Adobe dipendono dal servizio Opt-in e non generano cookie a meno che non sia stata concessa l&#39;autorizzazione. L&#39;oggetto Opt-in supporta diversi approcci per fornire e aggiornare le impostazioni di consenso per il visitatore attuale. In questa sezione sono forniti alcuni esempi per impostare le preferenze del servizio Opt-in. Per [un elenco completo delle funzioni e dei parametri, consultate il Riferimento](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) API di consenso.

Le configurazioni del servizio opt-in sono fornite nella funzione JS visitatore `getInstance()` che crea un&#39;istanza dell&#39;oggetto globale `adobe` . Di seguito sono elencate le impostazioni [di configurazione JS visitatore](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) per il servizio di consenso.

**Esempio di configurazione di consenso all&#39;inizializzazione dell&#39;`Visitor`oggetto globale**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**Gestire le modifiche al consenso**

Mentre visita il sito, il visitatore può scegliere di impostare le preferenze per la prima volta o modificarle usando CMP in qualsiasi momento. Dopo aver inizializzato JS per il visitatore con le impostazioni iniziali, è possibile modificare le autorizzazioni del visitatore. Vedere [Modifiche al consenso](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) per un elenco delle funzioni di gestione del consenso.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Flussi di lavoro di consenso {#section-70cd243dec834c8ea096488640ae20a5}

Il servizio di consenso facilitato supporta un flusso di lavoro in cui le autorizzazioni possono essere raccolte su più di un ciclo di richiesta e le preferenze ne vengono fornite una alla volta. Usando le seguenti funzioni e specificando *true* per `shouldWaitForComplete`, la soluzione è in grado di raccogliere il consenso per una categoria o un sottoinsieme di tutte le categorie e poi di raccoglierlo per la categoria o il sottoinsieme di categoria successivo. A partire dalla prima chiamata, la `adobe.optIn.status` proprietà sarà *in sospeso* finché `adobe.optIn.complete()` non viene chiamata alla fine del flusso. Una volta effettuata la chiamata, lo stato viene impostato su *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Consultate [Impostazioni di configurazione Flusso di lavoro](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## Controllare le autorizzazioni Opt-in del visitatore {#section-f136a9024e054d84881e6667fb7c94eb}

Man mano che i visitatori aprono le loro autorizzazioni, dovrai avere bisogno di approfondimenti sulle autorizzazioni risultanti per sincronizzare l&#39;archivio di autorizzazione con le modifiche apportate al servizio di consenso. Controlla le preferenze del visitatore usando le [funzioni di autorizzazione](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155), ad esempio:

**fetchPermissions**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

Consulta la [documentazione sulle API](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) per maggiori informazioni su tutte le funzioni, le proprietà o le configurazioni citate in questo documento.

## Memorizzazione delle preferenze dei visitatori {#section-ef2884ae67e34879bf7c7c3372706c9f}

Il servizio Consenso fornisce un&#39;opzione per memorizzare preferenze di consenso adatte a un ambiente di sviluppo o a un ambiente in cui non è possibile utilizzare un CRM. Specifica della proprietà di configurazione `isOptInStorageEnabled` come *attiva* attivazione del servizio Opt-in per creare un cookie sul sistema del visitatore all&#39;interno del dominio.

L&#39;oggetto `adobe.optIn` è senza stato e non fornisce alcun meccanismo di archiviazione. Ti consente invece di gestire le impostazioni di consenso di Adobe nella Piattaforma di gestione dei consensi (Consent Management Platform, CMP) se questa permette di memorizzare dati personalizzati. In alternativa è possibile memorizzare le preferenze del visitatore in un cookie sul browser del visitatore. Sono disponibili due opzioni per fornire le preferenze dell&#39;utente al servizio di consenso:

* Se la soluzione di persistenza del consenso, se si tratta di un CMP o di un cookie sul browser del visitatore, consente di recuperare rapidamente le preferenze dei visitatori, puoi fornire quelle al servizio di consenso durante l&#39;inizializzazione del visitatore.
* Tuttavia, se il recupero può essere un processo molto lungo o altrimenti viene utilizzato come processo asincrono, potete utilizzare la `approve()` funzione del servizio per fornire tali impostazioni una volta che sono state caricate correttamente.

