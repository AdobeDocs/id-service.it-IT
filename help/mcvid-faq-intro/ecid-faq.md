---
description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'uso del servizio ID.
keywords: Servizio ID
seo-description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'uso del servizio ID.
seo-title: Domande frequenti sul servizio ID
title: Domande frequenti sul servizio ID
uuid: e 8 d 8 f 819-3 d 73-4 fa 2-864 c -4867071 c 14 ee
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# Domande frequenti sul servizio ID{#id-service-faqs}

Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all&#39;uso del servizio ID.

## Funzionalità {#section-659e89f8b9a74cb8afff35587dc96836}

**Che tipo di funzionalità o capacità offre il servizio ID?**

Consulta la sezione [Panoramica](../mcvid-introduction/mcvid-overview.md).

**Perché il servizio ID non sta effettuando una chiamata per recuperare l&#39;Experience Cloud ID?**

Questa situazione è difficile da diagnosticare. Una cosa che puoi controllare sono le intestazioni dell&#39;informativa sulla sicurezza dei contenuti sul tuo sito. Se hai una politica di sicurezza restrittiva, quelle impostazioni possono bloccare le chiamate di terze parti effettuate dal servizio ID. Consulta  [Informativa sulla sicurezza dei contenuti e servizio Experience Cloud ID](../mcvid-reference/mcvid-csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**Archiviazione del file VisitorAPI.js**

È possibile riscontrare problemi se il file VisitorAPI.js è stato memorizzato come file locale nelle applicazioni per dispositivi mobili. È consigliabile conservare il file su un server Web.

## Tempi di caricamento della pagina e latenza {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**In che modo il posizionamento della libreria VisitorAPI.js del servizio ID influisce sui tempi di caricamento delle pagine?**

Posiziona la libreria visitorapi. js nella parte superiore della pagina nella `<head>` sezione del codice. Questo consente di garantire che la chiamata per un&#39;ID venga effettuata prima che il corpo della pagina inizi a essere caricato e massimizza le possibilità di restituzione di un&#39;ID.

La chiamata del servizio ID è asincrona ed è l&#39;unica chiamata al [dominio demdex.net](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html). La chiamata del servizio ID non blocca il caricamento di altri elementi sulla pagina.

Per [!DNL Target] i clienti, il posizionamento del codice del servizio `<body>` ID nella pagina può aumentare le possibilità che possa bloccare una [!DNL Target] chiamata. Se devi inserire il codice del servizio ID nel corpo della pagina, devi posizionarlo dopo il `<body>` tag aperto.

**Il servizio ID effettua una chiamata al server a ogni caricamento di pagina?**

No, questa chiamata viene effettuata solo al primo rendering della pagina o una volta ogni 7 giorni in seguito. Nel frattempo, le chiamate al server non sono richieste. Il servizio ID opera nella modalità lato client e non necessita di effettuare una chiamata al server per restituire un ID.

Consultate [Panoramica](../mcvid-introduction/mcvid-overview.md).

**Durante l&#39;uso del servizio ID, cosa può provocare un rallentamento dei tempi di caricamento delle pagine o influire sull&#39;esperienza dell&#39;utente?**

È difficile catalogare tutte le condizioni possibili. Miliardi di clienti si collegano ai nostri servizi e l&#39;enorme varietà di modi e tempi in cui si connettono influisce sulle prestazioni. Ad esempio:

* Le velocità variano notevolmente sulle reti mobili. Queste reti sono soggette anche alla perdita del segnale e del pacchetto dati o voce.
* La connettività si riduce sui dispositivi che si collegano tramite WiFi in svariate condizioni. Ad esempio, problemi dovuti alla velocità o alla perdita di pacchetti sono comuni in luoghi pubblici, come caffetterie, o in altri ambienti come velivoli dovi i pacchetti possono rimbalzare attraverso un satellite prima di raggiungere le reti terrestri.
* Le reti locali caratterizzate da una configurazione scadente possono influire negativamente su connettività e velocità.
* I dispositivi dei clienti possono avere problemi intrinseci come spazio di memoria ridotto, scambi eccessivi sul disco rigido o potenza della CPU limitata rispetto ai carichi di lavoro correnti.
* I browser mettono in coda ed eseguono le chiamate al server remoto ed elaborano, persino, le risposte con regole diverse a seconda del produttore e della versione del browser. Questo comportamento influisce su velocità e prestazioni.

**Puoi nominare alcuni miglioramenti apportati al fine di migliorare i tempi di caricamento delle pagine?**

Ad esempio, il thread yielding. Abbiamo introdotto il thread yielding per i casi in cui si verificano più richieste di sincronizzazione ID. I rapporti forniti dal laboratorio hanno indicato che per i clienti che eseguono più sincronizzazioni ID, l&#39;interfaccia utente si blocca a causa dei continui calcoli che la CPU deve elaborare. Di conseguenza, abbiamo introdotto la tecnica del thread yielding per separare le richieste di sincronizzazione ID di 100 msec l&#39;una dall&#39;altra.

Questa modifica migliore le prestazioni per i clienti che usano Visitor 2.3.0+ e DIL 6.10+. I miglioramenti nei tempi di caricamento delle pagine sono mostrati nell&#39;immagine seguente:

![](assets/id_sync_improvements_copy.png)

**Le richieste del browser effettuate con CORS versus JSONP influiscono sulle prestazioni delle pagine?**

Le richieste di risorse con CORS sono generalmente preferibili a quelle con JSONP. Con JSONP, alcuni browser mettono in coda e modificano la priorità delle richieste rispetto ad altre chiamate sincrone ed asincrone sulla pagina. CORS contribuisce a garantire che a queste richieste sia data una maggiore priorità nello stack delle chiamate del browser.

Consulta  [Supporto per CORS nel servizio Experience Cloud ID](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Sicurezza {#section-b176b8492fbe4acfb79ebb30ec902f98}

**Il servizio ID supporta CORS?**

Sì. Consulta  [Supporto per CORS nel servizio Experience Cloud ID](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Cos&#39;è CORS?**

*`Cross-Origin Resource Sharing`*o CORS è un metodo che i browser usano per richiedere risorse. Il servizio ID richiede sempre risorse usando CORS nei browser che lo supportano. Il servizio ID richiede risorse con JSONP nei browser più datati che non supportano CORS. Consulta  [Experience Cloud](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Cosa succede se i miei requisiti di sicurezza sono così rigidi da impedirmi di usare JSONP?**

Se hai dei requisiti di sicurezza rigidi, imposta la configurazione API del servizio ID `useCORSOnly: true`. Abilita questa modalità solo se sei certo che i visitatori del tuo sito usano browser che supportano CORS.

Consulta  [Experience Cloud](../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758) e [usecorsonly](../mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORE_ LIKE_ THIS]
>
>* [Assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html)

