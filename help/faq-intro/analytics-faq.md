---
description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all’uso di Analytics con il servizio Experience Cloud Identity.
keywords: Experience Cloud Identity Service
seo-description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all’uso di Analytics con il servizio Identity.
seo-title: Domande frequenti su Analytics e sul servizio Identity
title: Domande frequenti su Analytics e sul servizio Identity
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Domande frequenti su Analytics e sul servizio Identity{#analytics-and-id-service-faqs}

Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all’uso di Analytics con il servizio Identity.

## Server di tracciamento {#section-9a2ad7842e364c869e1650480d17f8ef}

**Come trovo le informazioni sul server di tracciamento?**

Ogni frammento di codice AppMeasurement configurato correttamente contiene le informazioni sul server di tracciamento.

Tuttavia, talvolta, i clienti possono suddividere il file Analytics AppMeasurement in file separati. Ad esempio, alcuni clienti possono inserire in un file variabili di configurazione, usare un secondo file per i plug-in e quindi inserire un codice AppMeasurement in un terzo file. Questo non è consigliato.

Se non riesci a trovare informazioni sul server di tracciamento, l&#39;istanza di Analytics potrebbe non essere stata configurata in maniera appropriata. Se non riesci a trovare le informazioni sul server di tracciamento, contatta l’ [Assistenza](https://helpx.adobe.com/it/marketing-cloud/contact-support.html) clienti.

**Che succede se uso il servizio Identity e cambio il server di tracciamento?**

Per gli utenti che sono già stati identificati dal servizio Identity, non cambia nulla. I visitatori precedenti che non sono stati trasferiti al servizio Identity e sono ancora identificati con un cookie Analytics verranno soggetti a cliff. Il numero di utenti interessati dipende da quanto tempo è attivo il servizio Identity. Ad esempio, un’implementazione con il servizio Identity attivo da una settimana avrà più utenti precedenti rispetto a un’implementazione con il servizio Identity attivo da 6 mesi: in quest’ultimo caso, infatti, ci saranno stati più utenti che avranno visitato nuovamente il sito e quindi che sono già stati migrati.

## Implementazione e configurazione {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Devo impostare un CNAME per monitorare i visitatori tra i domini?**

Se hai un sito di accesso principale in cui i clienti possono essere identificati prima che visitino altri domini, allora un CNAME può abilitare il tracciamento tra domini nei browser che non accettano i cookie di terze parti (come Safari).

In browsers that accept third-party cookies, a cookie is set in the [demdex.net domain](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/demdex-calls.html) during the request to retrieve a visitor ID. Questo cookie consente al servizio Identity di restituire lo stesso ID visitatore Experience Cloud a tutti i domini configurati usando lo stesso ID organizzazione. Nei browser che rifiutano i cookie di terze parti, a ciascun dominio viene assegnato un nuovo ID visitatore Experience Cloud.

Anche se è configurato un CNAME, se il sito di accesso principale non viene visitato per primo, i visitatori vengono identificati in modo diverso sul sito secondario e sul sito principale nei browser che non accettano i cookie di terze parti.

**Perché il parametro Experience Cloud ID (MID) non è incluso nella richiesta Analytics?**

Se il servizio Identity restituisce correttamente le informazioni ma il parametro `MID` non viene visualizzato, verifica di avere effettuato l’aggiornamento a una versione supportata di AppMeasurement.

**Posso usare nel mio sito il codice H e AppMeasurement per JavaScript con il servizio Identity?**

Sì. Purché entrambi i file facciano riferimento allo stesso file VisitorAPI.js, puoi usare un insieme di codice H e AppMeasurement per JavaScript nel tuo sito.

Tuttavia, il codice H non è supportato con il codice visitorAPI.js versione 1.6 o successiva. Se desiderate effettuare l’aggiornamento a visitorAPI.js v 1.6 (o versione successiva), non potete continuare a utilizzare il codice H.

**Cos&#39;è un periodo di tolleranza e come lo configuro?**

Consulta [il periodo di tolleranza per il servizio Identity](../reference/analytics-reference/grace-period.md) e contatta [l’Assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html).

**Perché devo migrare alla raccolta dati regionali (RDC) per usare il servizio Identity?**

RDC offre vantaggi in termini di prestazioni globali ed è necessaria per garantire che l’implementazione sia pronta per le prossime funzionalità che sfruttano la rete globale di note a margine di Adobe. See [Analytics Requirements: Regional Data Collection (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Reporting {#section-123cd55a32e54a45a23beb140becfa8f}

**Quali sono alcune delle possibili cause di discrepanze quando si utilizza Analytics con il servizio Identity?**

Alcune cause comuni di discrepanze quando si usa il servizio Identity sono le seguenti:

* Uso continuo del cookie s_vi legacy. Ciò contribuisce a creare discrepanze nella raccolta dei dati.
* Doppio conteggio dei visitatori quando navigano da un sondaggio a un pop-up.

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Cosa succede in Analytics quando il servizio Identity non riesce a impostare il cookie AMCV?**

Esistono tre possibili scenari in cui questo influisce sui dati di Analytics per i nuovi visitatori:

1. Un utente finale lascia una pagina prima che i cookie AMCV vengano impostati correttamente (entro la finestra di timeout di 30 secondi).

   Se un visitatore lascia una pagina prima che questa sia stata caricata, l&#39;hit Analytics non viene inviato. Analytics non riceverà alcun dato da questa situazione e considererà quei dati come persi a causa di una chiusura anticipata della pagina. Sulla base dei test svolti che includevano le geografie remote, abbiamo scoperto che questa situazione rappresentava una percentuale inferiore all&#39;1% del traffico medio. È importante notare che talvolta questa situazione si verifica anche senza la presenza del servizio Identity; si tratta di un artefatto dovuto all’inclusione del codice di raccolta dati di Analytics in fondo alla pagina.

1. A un utente finale non viene assegnato un ID del servizio Identity o di Analytics entro la finestra di timeout di 30 secondi a causa di collegamenti lenti o del caricamento del browser.

   Né l’ID del servizio Identity né quello di Analytics verranno impostati e al visitatore verrà assegnato un ID lato client. Nonostante i dati Analytics possano essere raccolti, il profilo del visitatore verrà interrotto quando un ID di Analytics viene impostato su una pagina successiva. Inoltre, l&#39;ID lato client non corrisponderà ad alcun profilo di visitatori esistenti archiviato nell&#39;Audience Manager o in Analytics. Questo ID lato client apparirà anche come due visitatori diversi in Analytics se due domini separati vengono inviati nella stessa suite di rapporti.

1. A un utente finale non viene assegnato un ID del servizio Identity entro la finestra di timeout di 30 secondi, ma un ID di tracciamento di Analytics standard, e il periodo di tolleranza non viene attivato.

   La situazione 3 ha lo stesso risultato della situazione 2 in quanto viene utilizzato un ID basato su lato client.

>[!TIP]
>
>L&#39;uso degli ultimi aggiornamenti di VisitorAPI.js e AppMeasurement.js con le impostazioni predefinite dovrebbe evitare gli impatti gravi o percepibili causati dalle tre situazioni improbabili soprastanti.

>[!MORELIKETHIS]
>
>* [Assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html)

