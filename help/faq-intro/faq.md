---
description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'uso del servizio ID.
keywords: Servizio ID
title: Domande frequenti sul servizio ID
exl-id: 4dd2220c-8a9d-4e27-838b-be5ad357cb3e
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 97%

---

# Domande frequenti sul servizio ID{#id-service-faqs}

Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all&#39;uso del servizio ID.

## Funzionalità {#section-659e89f8b9a74cb8afff35587dc96836}

**Che tipo di funzionalità o capacità offre il servizio ID?**

Vedi la [Panoramica](../introduction/overview.md).

**Perché il servizio ID non effettua una chiamata per recuperare l’Experience Cloud ID?**

Questa situazione è difficile da diagnosticare. Una cosa che puoi controllare sono le intestazioni dell&#39;informativa sulla sicurezza dei contenuti sul tuo sito. Se hai una politica di sicurezza restrittiva, quelle impostazioni possono bloccare le chiamate di terze parti effettuate dal servizio ID. Consulta [Informativa sulla sicurezza dei contenuti e il servizio Experience Cloud Identity](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3).

**Archiviazione dei file VisitorAPI.js**

È possibile riscontrare problemi se il file VisitorAPI.js è stato memorizzato come file locale nelle applicazioni per dispositivi mobili. È consigliabile ospitare il file su un server Web.

## Tempi di caricamento delle pagine e latenza {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**In che modo il posizionamento della libreria VisitorAPI.js del servizio ID influisce sui tempi di caricamento delle pagine?**

Posiziona la libreria VisitorAPI.js nella parte superiore della pagina nella `<head>` sezione del tuo codice. Questo consente di garantire che la chiamata per un&#39;ID venga effettuata prima che il corpo della pagina inizi a essere caricato e massimizza le possibilità di restituzione di un&#39;ID.

La chiamata al servizio ID è asincrona ed è l’unica chiamata al [dominio demdex.net](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=it). La chiamata del servizio ID non blocca il caricamento di altri elementi sulla pagina.

Per i [!DNL Target] clienti, il posizionamento del codice del servizio ID nel `<body>` della pagina può aumentare le possibilità che possa bloccare una chiamata [!DNL Target]. Se hai bisogno di posizionare il codice del servizio ID nel corpo della pagina, devi posizionarlo dopo il tag `<body>` aperto.

**Il servizio ID effettua una chiamata al server a ogni caricamento di pagina?**

No, questa chiamata viene effettuata solo al primo rendering della pagina o una volta ogni 7 giorni in seguito. Nel frattempo, le chiamate al server non sono richieste. Il servizio ID funziona in modalità lato client e non deve effettuare una chiamata al server per restituire un ID.

Consulta [Panoramica](../introduction/overview.md).

**Quando si utilizza il servizio ID, cosa può causare rallentamenti ai tempi di caricamento delle pagine o influenzare l’esperienza di utilizzo?**

È difficile catalogare tutte le condizioni possibili. Miliardi di clienti si collegano ai nostri servizi e l&#39;enorme varietà di modi e tempi in cui si connettono influisce sulle prestazioni. Ad esempio:

* Le velocità variano notevolmente sulle reti mobili. Queste reti subiscono inoltre la perdita di segnali e dati o di pacchetti vocali.
* La connettività si riduce sui dispositivi che si collegano tramite WiFi in svariate condizioni. Ad esempio, problemi di velocità e perdita di pacchetti sono comuni in luoghi pubblici, ad esempio i bar, o in altri ambienti, ad esempio gli aerei, in cui i pacchetti devono rimbalzare attraverso un satellite prima di raggiungere le reti terrestri.
* Le reti locali configurate in modo non ottimale possono avere un impatto negativo su connettività e velocità.
* I dispositivi client possono avere problemi propri come memoria insufficiente, scambi eccessivi di dischi o potenza limitata della CPU rispetto ai carichi di lavoro correnti.
* I browser mettono in coda ed eseguono le chiamate al server remoto ed elaborano, persino, le risposte con regole diverse a seconda del produttore e della versione del browser. Questo comportamento influisce su velocità e prestazioni.

**Puoi citare alcuni miglioramenti apportati per ridurre i tempi di caricamento delle pagine?**

Ad esempio, il thread yielding. Abbiamo introdotto il thread yielding per i casi in cui si verificano più richieste di sincronizzazione ID. I rapporti forniti dal laboratorio hanno indicato che per i clienti che eseguono più sincronizzazioni ID, l&#39;interfaccia utente si blocca a causa dei continui calcoli che la CPU deve elaborare. Di conseguenza, abbiamo introdotto il thread yielding per separare le richieste di sincronizzazione ID di 100 msec l’una dall’altra.

Questa modifica migliore le prestazioni per i clienti che usano Visitor 2.3.0+ e DIL 6.10+. I miglioramenti nei tempi di caricamento delle pagine sono mostrati nella figura seguente:

![](assets/id_sync_improvements_copy.png)

**Le richieste del browser che utilizzano CORS influiscono sulle prestazioni della pagina rispetto a quelle che utilizzano JSON-P?**

Le richieste di risorse con CORS sono generalmente preferibili a quelle con JSONP. Con JSONP, alcuni browser mettono in coda e modificano la priorità delle richieste rispetto ad altre chiamate sincrone ed asincrone sulla pagina. CORS garantisce che queste richieste siano trattate con una priorità più alta nello stack di chiamate del browser.

Consulta [Supporto per CORS in Experience Cloud Identity Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Sicurezza {#section-b176b8492fbe4acfb79ebb30ec902f98}

**Il servizio ID supporta CORS?**

Sì. Consulta [Supporto per CORS in Experience Cloud Identity Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Cos’è CORS?**

*`Cross-Origin Resource Sharing`* o CORS è un metodo che i browser usano per richiedere risorse. Il servizio ID richiede sempre risorse usando CORS nei browser che lo supportano. Il servizio ID richiede risorse con JSONP nei browser più datati che non supportano CORS. Consulta [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Cosa succede se i miei requisiti di sicurezza sono così rigidi da impedirmi di usare JSONP?**

Se hai dei requisiti di sicurezza rigidi, imposta la configurazione API del servizio ID `useCORSOnly: true`. Abilita questa modalità solo se sei certo che i visitatori del tuo sito utilizzano browser che supportano CORS.

Consulta [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) e [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [Assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html)
