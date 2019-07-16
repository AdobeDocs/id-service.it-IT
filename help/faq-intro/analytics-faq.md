---
description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'utilizzo di Analytics con Experience Platform Identity Service.
keywords: Servizio identità piattaforma Experience
seo-description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'utilizzo di Analytics con il servizio identità.
seo-title: Domande frequenti su Analytics e Servizio identità
title: Domande frequenti su Analytics e Servizio identità
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Analytics and Identity Service FAQs{#analytics-and-id-service-faqs}

Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all&#39;utilizzo di Analytics con il servizio identità.

## Server di tracciamento {#section-9a2ad7842e364c869e1650480d17f8ef}

**Come trovo informazioni sul server di tracciamento?**

Ogni frammento di codice AppMeasurement configurato in maniera appropriata contiene informazioni sul server di tracciamento.

Tuttavia, talvolta, i clienti possono suddividere il file Analytics AppMeasurement in file separati. Ad esempio, alcuni clienti possono inserire in un file variabili di configurazione, usare un secondo file per i plug-in e quindi inserire un codice AppMeasurement in un terzo file. Questo tipo di operazione non è consigliato.

Se non riesci a trovare informazioni sul server di tracciamento, l&#39;istanza di Analytics potrebbe non essere stata configurata in maniera appropriata. Contatta l&#39;[Assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html) se non riesci a trovare informazioni sul server di tracciamento.

**Cosa succede se uso il servizio Identità e cambi il server di tracciamento?**

Per gli utenti che sono già stati identificati dal Servizio identità non verrà modificato nulla. I visitatori precedenti che non sono stati trasferiti al servizio Identità e sono ancora identificati con un cookie Analytics verrebbero soggetti a cliff. La quantità di utenti interessati dipende da quanto tempo è attivo il servizio identità. Ad esempio, un&#39;implementazione in cui è stato attivo il servizio identità per 1 settimane potrebbe avere utenti più legacy rispetto a un&#39;implementazione in cui il servizio identità è stato attivo per 6 mesi, perché gli utenti che ritornano al sito sarebbero stati migrati.

## Implementazione e configurazione {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Devo impostare un CNAME per il monitoraggio dei visitatori tra i domini?**

Se utilizzi un sito di accesso principale per l&#39;identificazione dei clienti prima che visitino altri domini, un CNAME consente il monitoraggio tra più domini nei browser che non accettano i cookie di terze parti (ad es. Safari).

Nei browser che accettano i cookie di terze parti, durante la richiesta, un cookie viene impostato nel [dominio demdex.net](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) per recuperare l&#39;ID visitatore. Questo cookie consente al servizio identità di restituire lo stesso ID visitatore Experience Cloud a tutti i domini configurati usando lo stesso ID organizzazione. Nei browser che rifiutano i cookie di terze parti, a ciascun dominio viene assegnato un nuovo ID visitatore Experience Cloud.

Anche se è configurato un CNAME, se il principale sito di accesso non viene visitato per primo, i visitatori vengono identificati in modo diverso sul sito secondario nei browser che non accettano i cookie di terze parti.

**Perché il parametro Experience Cloud ID (MID) non è incluso nella richiesta Analytics?**

If the Identity Service is returning information correctly but you do not see the `MID` parameter, make sure that you&#39;ve upgraded to a supported version of AppMeasurement.

**Posso usare il codice H e appmeasurement per javascript con il servizio identità?**

Sì. Poiché entrambi i file fanno riferimento allo stesso file VisitorAPI.js, puoi usare sia il codice H che AppMeasurement per JavaScript nel sito.

Tuttavia, il codice H non è supportato con il codice visitorAPI.js versione 1.6 o successiva. Se desideri aggiornare a visitorAPI.js versione 1.6 (o successiva), non puoi continuare a usare il codice H.

**Cos&#39;è un periodo di tolleranza e come lo configuro?**

See [The Identity Service Grace Period](../reference/analytics-reference/grace-period.md) and contact [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Perché devo effettuare la migrazione alla raccolta dati in tempo reale (RDC) per utilizzare il servizio identità?**

RDC offre vantaggi a livello di prestazioni globali ed è richiesto per rendere l&#39;implementazione pronta per funzioni imminenti che sfruttano la rete globale Adobe di Edge Notes. Vedi [Requisiti di Analytics: raccolta dati regionali (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Reporting {#section-123cd55a32e54a45a23beb140becfa8f}

**Quali sono alcune delle possibili cause di discrepanze quando si utilizza Analytics con il servizio identità?**

Cause comuni di discrepanze quando si usa il servizio identità:

* Uso continuo del cookie s_vi legacy. Questo contribuisce a creare discrepanze nella raccolta dei dati.
* Doppio conteggio dei visitatori quando navigano da un sondaggio a un pop-up.

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Cosa succede in Analytics quando il servizio identità non è in grado di impostare il cookie AMCV?**

Esistono tre possibili situazioni in cui questa casistica influisce sui dati Analytics per i nuovi visitatori:

1. Un utente finale lascia una pagina prima che i cookie AMCV siano stati impostati correttamente (entro la finestra di timeout di 30 secondi).

   Se un visitatore lascia una pagina prima che questa sia stata caricata, l&#39;hit Analytics non viene inviato. Analytics non riceverà alcun dato da questa situazione e considererà quei dati come persi a causa di una chiusura anticipata della pagina. Sulla base dei test svolti che includevano le geografie remote, abbiamo scoperto che questa situazione rappresentava una percentuale inferiore all&#39;1% del traffico medio. È importante notare che questo scenario si verifica talvolta anche senza la presenza del servizio identità, un artefatto dell&#39;inclusione del codice di raccolta dati di Analytics nella parte inferiore della pagina.

1. A un utente finale non viene assegnato un servizio identità o un ID di Analytics entro la finestra di timeout di 30 secondi a causa di collegamenti lenti o di &quot;rotazione&quot; del browser.

   Sia il servizio Identità che l&#39;ID di Analytics non vengono impostati e al visitatore viene assegnato un ID lato client. Nonostante i dati Analytics possano essere raccolti, il profilo del visitatore verrà interrotto quando un ID di Analytics viene impostato su una pagina successiva. Inoltre, l&#39;ID lato client non corrisponderà ad alcun profilo di visitatori esistenti archiviato nell&#39;Audience Manager o in Analytics. In aggiunta, se due domini separati vengono inviati nella stessa suite di rapporti, l&#39;ID lato client verrà visualizzato come due visitatori diversi in Analytics.

1. A un utente finale non viene assegnato un ID servizio identità entro la finestra di timeout di 30 secondi, ma viene assegnato un ID di tracciamento Analytics standard e il periodo di tolleranza non viene attivato.

   La situazione 3 ha lo stesso risultato della situazione 2 in cui viene utilizzato un ID basato su lato client.

>[!TIP]
>
>L&#39;uso degli ultimi aggiornamenti di VisitorAPI.js e AppMeasurement.js con le impostazioni predefinite dovrebbe evitare gli impatti gravi o percepibili causati dalle tre situazioni improbabili soprastanti.

>[!MORE_LIKE_THIS]
>
>* [Assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html)

