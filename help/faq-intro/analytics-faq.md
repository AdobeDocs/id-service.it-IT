---
description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all’uso di Analytics con il servizio Experience Cloud Identity.
keywords: Servizio Experience Cloud Identity
seo-description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all’uso di Analytics con il servizio Identity.
seo-title: Domande frequenti su Analytics e sul servizio Identity
title: Domande frequenti su Analytics e sul servizio Identity
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Domande frequenti su Analytics e sul servizio Identity{#analytics-and-id-service-faqs}

Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all’uso di Analytics con il servizio Identity.

## Server di tracciamento {#section-9a2ad7842e364c869e1650480d17f8ef}

**Come trovo informazioni sul server di tracciamento?**

Ogni frammento di codice AppMeasurement configurato in maniera appropriata contiene informazioni sul server di tracciamento.

Tuttavia, talvolta, i clienti possono suddividere il file Analytics AppMeasurement in file separati. Ad esempio, alcuni clienti possono inserire in un file variabili di configurazione, usare un secondo file per i plug-in e quindi inserire un codice AppMeasurement in un terzo file. Questo tipo di operazione non è consigliato.

Se non riesci a trovare informazioni sul server di tracciamento, l'istanza di Analytics potrebbe non essere stata configurata in maniera appropriata. Se non riesci a trovare informazioni sul server di tracciamento, contatta [l'assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html).

**Che succede se uso il servizio Identity e cambio il server di tracciamento?**

Per gli utenti che sono già stati identificati dal servizio Identity, non cambia nulla. I visitatori precedenti che non sono stati trasferiti al servizio Identity e sono ancora identificati con un cookie Analytics verranno soggetti a cliff. Il numero di utenti interessati dipende da quanto tempo è attivo il servizio Identity. Ad esempio, un’implementazione con il servizio Identity attivo da una settimana avrà più utenti precedenti rispetto a un’implementazione con il servizio Identity attivo da 6 mesi: in quest’ultimo caso, infatti, ci saranno stati più utenti che avranno visitato nuovamente il sito e quindi che sono già stati migrati.

## Implementazione e configurazione {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Devo impostare un CNAME per il monitoraggio dei visitatori tra i domini?**

Se utilizzi un sito di accesso principale per l'identificazione dei clienti prima che visitino altri domini, un CNAME consente il monitoraggio tra più domini nei browser che non accettano i cookie di terze parti (ad es. Safari).

Nei browser che accettano i cookie di terze parti, durante la richiesta viene impostato un cookie nel [dominio demdex.net ](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) per recuperare un ID visitatore. Questo cookie consente al servizio Identity di restituire lo stesso ID visitatore Experience Cloud a tutti i domini configurati usando lo stesso ID organizzazione. Nei browser che rifiutano i cookie di terze parti, a ciascun dominio viene assegnato un nuovo ID visitatore Experience Cloud.

Anche se è configurato un CNAME, se il principale sito di accesso non viene visitato per primo, i visitatori vengono identificati in modo diverso sul sito secondario nei browser che non accettano i cookie di terze parti.

**Perché il parametro Experience Cloud ID (MID) non è incluso nella richiesta Analytics?**

Se il servizio Identity restituisce correttamente le informazioni ma il parametro `MID` non viene visualizzato, verifica di avere effettuato l’aggiornamento a una versione supportata di AppMeasurement.

**Posso usare nel mio sito il codice H e AppMeasurement per JavaScript con il servizio Identity?**

Sì. Poiché entrambi i file fanno riferimento allo stesso file VisitorAPI.js, puoi usare sia il codice H che AppMeasurement per JavaScript nel sito.

Tuttavia, il codice H non è supportato con il codice visitorAPI.js versione 1.6 o successiva. Se desideri aggiornare a visitorAPI.js versione 1.6 (o successiva), non puoi continuare a usare il codice H.

**Cos'è un periodo di tolleranza e come lo configuro?**

Consulta [Periodo di tolleranza per il servizio Identity](../reference/analytics-reference/grace-period.md) e contatta l’[assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html).

**Perché devo migrare alla raccolta dati regionali (RDC) per usare il servizio Identity?**

RDC offre vantaggi a livello di prestazioni globali ed è richiesto per rendere l'implementazione pronta per funzioni imminenti che sfruttano la rete globale Adobe di Edge Notes. Vedi [Requisiti di Analytics: raccolta dati regionali (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Reporting {#section-123cd55a32e54a45a23beb140becfa8f}

**Quali sono alcune delle possibili cause di discrepanze quando si utilizza Analytics con il servizio Identity?**

Alcune cause comuni di discrepanze quando si usa il servizio Identity sono le seguenti:

* Uso continuo del cookie s_vi legacy. Questo contribuisce a creare discrepanze nella raccolta dei dati.
* Doppio conteggio dei visitatori quando navigano da un sondaggio a un pop-up.

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Cosa succede in Analytics quando il servizio Identity non riesce a impostare il cookie AMCV?**

Esistono tre possibili situazioni in cui questa casistica influisce sui dati Analytics per i nuovi visitatori:

1. Un utente finale lascia una pagina prima che i cookie AMCV siano stati impostati correttamente (entro la finestra di timeout di 30 secondi).

   Se un visitatore lascia una pagina prima che questa sia stata caricata, l'hit Analytics non viene inviato. Analytics non riceverà alcun dato da questa situazione e considererà quei dati come persi a causa di una chiusura anticipata della pagina. Sulla base dei test svolti che includevano le geografie remote, abbiamo scoperto che questa situazione rappresentava una percentuale inferiore all'1% del traffico medio. È importante notare che talvolta questa situazione si verifica anche senza la presenza del servizio Identity; si tratta di un artefatto dovuto all’inclusione del codice di raccolta dati di Analytics in fondo alla pagina.

1. A un utente finale non viene assegnato un ID del servizio Identity o di Analytics entro la finestra di timeout di 30 secondi a causa di collegamenti lenti o del caricamento del browser.

   Né l’ID del servizio Identity né quello di Analytics verranno impostati e al visitatore verrà assegnato un ID lato client. Nonostante i dati Analytics possano essere raccolti, il profilo del visitatore verrà interrotto quando un ID di Analytics viene impostato su una pagina successiva. Inoltre, l'ID lato client non corrisponderà ad alcun profilo di visitatori esistenti archiviato nell'Audience Manager o in Analytics. In aggiunta, se due domini separati vengono inviati nella stessa suite di rapporti, l'ID lato client verrà visualizzato come due visitatori diversi in Analytics.

1. A un utente finale non viene assegnato un ID del servizio Identity entro la finestra di timeout di 30 secondi, ma un ID di tracciamento di Analytics standard, e il periodo di tolleranza non viene attivato.

   La situazione 3 ha lo stesso risultato della situazione 2 in quanto viene utilizzato un ID basato su lato client.

>[!TIP]
>
>L'uso degli ultimi aggiornamenti di VisitorAPI.js e AppMeasurement.js con le impostazioni predefinite dovrebbe evitare gli impatti gravi o percepibili causati dalle tre situazioni improbabili soprastanti.

>[!MORE_LIKE_THIS]
>
>* [Assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html)

