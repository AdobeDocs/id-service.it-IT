---
description: Implementare il servizio Opt-in come unico punto di riferimento usato dalle soluzioni Experience Cloud (definite anche Categorie in Opt-in) per definire se è necessario creare cookie sul dispositivo di un visitatore.
seo-description: Implementare il servizio Opt-in come unico punto di riferimento usato dalle soluzioni Experience Cloud (definite anche Categorie in Opt-in) per definire se è necessario creare cookie sul dispositivo di un visitatore.
seo-title: Configurazione del servizio Opt-in
title: Configurazione del servizio Opt-in
uuid: f1c27139-cef2-4122-af12-c839cfc82e6e
exl-id: 6e8a6531-9924-4523-a842-cb4614a7a7a0
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '941'
ht-degree: 100%

---

# Configurazione del servizio Opt-in {#setting-up-opt-in-service}

Implementare il servizio Opt-in come unico punto di riferimento usato dalle soluzioni Experience Cloud (definite anche Categorie in Opt-in) per definire se è necessario creare cookie sul dispositivo di un visitatore.

Il servizio Opt-in è una libreria JavaScript abbinata con Experience Cloud ID (ECID) ed esiste in JS per il visitatore nell&#39;oggetto globale `adobe` come oggetto`adobe.optIn`. Il servizio Opt-in installato consente di specificare se un visitatore può dare il consenso esplicito a tutte le soluzioni Adobe in una sola volta oppure deve darlo per ogni soluzione seguendo la sequenza di autorizzazioni per ognuna di esse. La funzionalità di gestione del consenso del servizio Opt-in consente di implementare diverse configurazioni per i requisiti di privacy specifici.

Il servizio Opt-in consente di specificare se un visitatore può dare il consenso esplicito a tutte le soluzioni Adobe in una sola volta oppure deve darlo per ogni soluzione seguendo la sequenza di autorizzazioni per ognuna di esse. Quando il processo di approvazione è stato completato e registrato dal cliente, è possibile recuperare le approvazioni del visitatore CMP da tutte le soluzioni Adobe per rispondere con le relative chiamate di consenso.

## Prerequisiti  {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID versione 4.0

   [Scarica](https://github.com/Adobe-Marketing-Cloud/id-service/releases) la versione di ECID più recente.

1. Librerie di supporto:

   * ECID 4.0 o successivo
   * AppMeasurement 2.11 o versione successiva
   * DIL 9.0
   * AT.js versione 1.7.0
   * Estensione AT.js Launch versione 9.0
   * Per Analytics, App Measurement 2.11 con estensione 1.6
   * Per Target, estensione 0.9.1

1. Acquisisci familiarità con il framework di gestione dei consensi che utilizzerai con il servizio Opt-in e comprendi eventuali prerequisiti aggiuntivi.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. I requisiti di privacy dell&#39;azienda saranno specifici in base alla scelta di rispettare il RGPD. Tieni presente quali librerie i team aziendali per la privacy possono usare prima del consenso.

Se utilizzi [Adobe Launch](https://docs.adobe.com/content/help/it-IT/launch/using/overview.html), sfrutta l’[estensione Opt-in](../../implementation-guides/opt-in-service/launch.md) per configurare il servizio Opt-in.

## Categorie di Opt-in {#section-9ab0492ab4414f0ca16dc08d3a905f47}

Le preferenze Opt-in di un visitatore sono relative a una soluzione Adobe Experience Cloud, dove ogni soluzione è rappresentata come una categoria. Le categorie vengono fornite `adobe.OptInCategories` dall&#39;oggetto dove, ad esempio, il componente ECID viene indicato come `adobe.OptInCategories`. `ECID`. Di seguito la definizione di `adobe.OptInCategories`:

Le impostazioni di Opt-in vengono mantenute per ciascuna categoria, dove ogni soluzione Experience Cloud è rappresentata da una categoria:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

Il servizio Opt-in consente di impostare le preferenze di autorizzazione dei visitatori per ciascuna soluzione Adobe sul tuo sito. Include una libreria per salvare le impostazioni del visitatore mediante una categoria approvata e supporta un flusso sequenziale dove il processo di approvazione riceve le preferenze di &quot;conferma&quot; o &quot;rifiuto&quot; una alla volta per ogni categoria. Puoi impostare il consenso di tutte le soluzioni/categorie insieme oppure per ogni singola soluzione. 
Tutte le librerie lato client delle soluzioni Adobe dipendono dal servizio Opt-in e non genereranno cookie a meno che non sia stata concessa l&#39;autorizzazione alla soluzione. L&#39;oggetto Opt-in supporta diversi approcci per fornire e aggiornare le impostazioni di consenso per il visitatore attuale. Questa sezione contiene degli esempi su come impostare le preferenze del servizio Opt-in. Consulta i [riferimenti alle API di Opt-in](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) per un elenco completo delle funzioni e dei parametri.

Le configurazioni del servizio Opt-in vengono fornite nella `getInstance()` funzione di JS per il visitatore che creano l&#39;istanza per `adobe` l&#39;oggetto globale. Di seguito un elenco delle [impostazioni di configurazione](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) di JS per il visitatore per il servizio Opt-in.

**Configurazione di esempio di Opt-in nell&#39;inizializzazione dell&#39;`Visitor`oggetto** globale 

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

Mentre visita il sito, il visitatore può scegliere di impostare le preferenze per la prima volta o modificarle usando CMP in qualsiasi momento. Dopo aver inizializzato JS per il visitatore con le impostazioni iniziali, è possibile modificare le autorizzazioni del visitatore. Consulta [Modifiche di consenso](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) per un elenco delle funzioni per la gestione del consenso.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Flussi di lavoro di Opt-in {#section-70cd243dec834c8ea096488640ae20a5}

Il servizio Opt-in supporta un flusso di lavoro in cui è possibile raccogliere le autorizzazioni per più di un ciclo di richiesta e le preferenze vengono assegnate tutte insieme. Usando le seguenti funzioni e specificando *true* per `shouldWaitForComplete`, la soluzione è in grado di raccogliere il consenso per una categoria o un sottoinsieme di tutte le categorie e poi di raccoglierlo per la categoria o il sottoinsieme di categoria successivo. A partire dalla prima chiamata, la proprietà `adobe.optIn.status` sarà *in sospeso* fino a quando `adobe.optIn.complete()` non viene chiamata alla fine del flusso. Una volta effettuata la chiamata, lo stato viene impostato su *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Consulta le [impostazioni di configurazione del flusso di lavoro](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## Controllare le autorizzazioni Opt-in del visitatore {#section-f136a9024e054d84881e6667fb7c94eb}

Man mano che i visitatori modificano le proprie autorizzazioni, avrai bisogno di maggiori informazioni sulle autorizzazioni risultanti per sincronizzare l&#39;archivio dei consensi con le modifiche apportate nel servizio Opt-in. Controlla le preferenze del visitatore utilizzando le [funzioni di autorizzazione](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155), ad esempio:

**esempio di fetchPermissions**

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

Consulta la [documentazione delle API](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) per maggiori informazioni su tutte le funzioni, le proprietà o le configurazioni citate in questo documento.

## Memorizzazione delle preferenze del visitatore {#section-ef2884ae67e34879bf7c7c3372706c9f}

Il servizio Opt-in consente di memorizzare le preferenze di consenso adatte a un ambiente di sviluppo o a un ambiente in cui non è possibile usare un CRM. Imposta la proprietà di configurazione `isOptInStorageEnabled` su *true* per attivare il servizio Opt-in e creare un cookie sul sistema del visitatore nel tuo dominio.

`adobe.optIn` L&#39;oggetto è senza stato e non fornisce alcun meccanismo di archiviazione. Ti consente invece di gestire le impostazioni di consenso di Adobe nella Piattaforma di gestione dei consensi (Consent Management Platform, CMP) se questa permette di memorizzare dati personalizzati. In alternativa è possibile memorizzare le preferenze del visitatore in un cookie sul browser del visitatore. Puoi fornire le preferenze dell&#39;utente al servizio Opt-in in due modi:

* Se la soluzione di persistenza del consenso, che si tratti di CMP o di un cookie sul browser del visitatore, consente un recupero tempestivo delle preferenze del visitatore, è possibile fornirle al servizio Opt-in durante l&#39;inizializzazione di Visitatore.
* Tuttavia, se il recupero è un processo lungo o in alternativa viene eseguito meglio come processo asincrono, puoi usare la `approve()` funzione del servizio per fornire tali impostazioni una volta caricate correttamente.
