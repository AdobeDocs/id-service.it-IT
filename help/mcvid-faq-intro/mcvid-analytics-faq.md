---
description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'uso di Analytics con il servizio ID.
keywords: Servizio ID
seo-description: Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all'uso di Analytics con il servizio ID.
seo-title: Domande frequenti su Analytics e sul servizio ID
title: Domande frequenti su Analytics e sul servizio ID
uuid: 35 ed 79 a 9-eccc -4 b 54-8451-606 f 091 c 73 b 7
translation-type: tm+mt
source-git-commit: 4dc668afd37cd1d6f9104adb1b102f1dd4c5746e

---


# Domande frequenti su Analytics e sul servizio ID{#analytics-and-id-service-faqs}

Domande frequenti sulle caratteristiche, sulle funzionalità e sui problemi correlati all&#39;uso di Analytics con il servizio ID.

## Server di tracciamento {#section-9a2ad7842e364c869e1650480d17f8ef}

**Come trovo informazioni sul server di tracciamento?**

Ogni frammento di codice AppMeasurement configurato in maniera appropriata contiene informazioni sul server di tracciamento.

Tuttavia, talvolta, i clienti possono suddividere il file Analytics AppMeasurement in file separati. Ad esempio, alcuni clienti possono inserire in un file variabili di configurazione, usare un secondo file per i plug-in e quindi inserire un codice AppMeasurement in un terzo file. Questo tipo di operazione non è consigliato.

Se non riesci a trovare informazioni sul server di tracciamento, l&#39;istanza di Analytics potrebbe non essere stata configurata in maniera appropriata. Contatta l&#39;[Assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html) se non riesci a trovare informazioni sul server di tracciamento.

**Che succede se uso il servizio ID e cambio il server di tracciamento?**

Per gli utenti che sono già stati identificati dal servizio ID, non cambia nulla. I visitatori precedenti che non sono stati trasferiti al servizio ID e sono ancora identificati con un cookie Analytics verranno soggetti a cliff. Il numero di utenti interessati dipende da quanto tempo è attivo il servizio ID. Ad esempio, un&#39;implementazione con servizio ID attivo da una settimana avrà più utenti precedenti rispetto a un&#39;implementazione con servizio ID attivo da 6 mesi: in quest&#39;ultimo caso, infatti, ci saranno stati più utenti che avranno visitato nuovamente il sito e quindi che sono già stati migrati.

## Implementazione e configurazione {#section-6028f55d5b514ae6a631c6a79f42fb89}

**Devo impostare un CNAME per il monitoraggio dei visitatori tra i domini?**

Se utilizzi un sito di accesso principale per l&#39;identificazione dei clienti prima che visitino altri domini, un CNAME consente il monitoraggio tra più domini nei browser che non accettano i cookie di terze parti (ad es. Safari).

Nei browser che accettano i cookie di terze parti, durante la richiesta, un cookie viene impostato nel [dominio demdex.net](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) per recuperare l&#39;ID visitatore. Questo cookie consente al servizio ID di restituire lo stesso ID visitatore Experience Cloud a tutti i domini configurati usando lo stesso ID organizzazione. Nei browser che rifiutano i cookie di terze parti, a ciascun dominio viene assegnato un nuovo ID visitatore Experience Cloud.

Anche se è configurato un CNAME, se il principale sito di accesso non viene visitato per primo, i visitatori vengono identificati in modo diverso sul sito secondario nei browser che non accettano i cookie di terze parti.

**Perché il parametro Experience Cloud ID (MID) non è incluso nella richiesta Analytics?**

Se il servizio ID restituisce correttamente le informazioni ma il parametro `MID` non viene visualizzato, verifica di avere effettuato l&#39;aggiornamento a una versione supportata di AppMeasurement.

**Posso usare nel mio sito il codice H e AppMeasurement per JavaScript con il servizio ID?**

Sì. Poiché entrambi i file fanno riferimento allo stesso file VisitorAPI.js, puoi usare sia il codice H che AppMeasurement per JavaScript nel sito.

Tuttavia, il codice H non è supportato con il codice visitorAPI.js versione 1.6 o successiva. Se desideri aggiornare a visitorAPI.js versione 1.6 (o successiva), non puoi continuare a usare il codice H.

**Cos&#39;è un periodo di tolleranza e come lo configuro?**

Consulta [Periodo di tolleranza per il servizio ID](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) e contatta [l&#39;Assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html).

**Perché devo migrare alla raccolta dati regionali (RDC) per usare il servizio ID?**

RDC offre vantaggi a livello di prestazioni globali ed è richiesto per rendere l&#39;implementazione pronta per funzioni imminenti che sfruttano la rete globale Adobe di Edge Notes. Vedi [Requisiti di Analytics: raccolta dati regionali (RDC)](../mcvid-reference/mcvid-requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## Reporting {#section-123cd55a32e54a45a23beb140becfa8f}

**Quali sono alcune delle possibili cause di discrepanze quando si utilizza Analytics con il servizio ID?**

Alcune cause comuni di discrepanze quando si usa il servizio ID sono le seguenti:

* Uso continuo del cookie s_vi legacy. Questo contribuisce a creare discrepanze nella raccolta dei dati.
* Doppio conteggio dei visitatori quando navigano da un sondaggio a un pop-up.

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**Cosa succede in Analytics quando il servizio ID non riesce a impostare il cookie AMCV?**

Esistono tre possibili situazioni in cui questa casistica influisce sui dati Analytics per i nuovi visitatori:

1. Un utente finale lascia una pagina prima che i cookie AMCV siano stati impostati correttamente (entro la finestra di timeout di 30 secondi).

   Se un visitatore lascia una pagina prima che questa sia stata caricata, l&#39;hit Analytics non viene inviato. Analytics non riceverà alcun dato da questa situazione e considererà quei dati come persi a causa di una chiusura anticipata della pagina. Sulla base dei test svolti che includevano le geografie remote, abbiamo scoperto che questa situazione rappresentava una percentuale inferiore all&#39;1% del traffico medio. È importante notare che questo scenario si verifica talvolta anche senza la presenza del servizio MCID, un artefatto dell&#39;inclusione del codice di raccolta dati di Analytics in fondo alla pagina.

1. A un utente finale non viene assegnato un servizio ID o un ID di Analytics entro la finestra di timeout di 30 secondi a causa di collegamenti lenti o del caricamento del browser.

   Né il servizio ID né l&#39;ID di Analytics verranno impostati e al visitatore verrà assegnato un ID lato client. Nonostante i dati Analytics possano essere raccolti, il profilo del visitatore verrà interrotto quando un ID di Analytics viene impostato su una pagina successiva. Inoltre, l&#39;ID lato client non corrisponderà ad alcun profilo di visitatori esistenti archiviato nell&#39;Audience Manager o in Analytics. In aggiunta, se due domini separati vengono inviati nella stessa suite di rapporti, l&#39;ID lato client verrà visualizzato come due visitatori diversi in Analytics.

1. A un utente finale non viene assegnato un ID del servizio ID entro la finestra di timeout di 30 secondi, ma un ID di tracciamento di Analytics standard, e il periodo di tolleranza non viene attivato. 

   La situazione 3 ha lo stesso risultato della situazione 2 in cui viene utilizzato un ID basato su lato client.

>[!TIP]
>
>L&#39;utilizzo degli ultimi aggiornamenti di visitorapi. js e appmeasurement. js con le impostazioni predefinite dovrebbe evitare un impatto grave o percepibile dei tre scenari improbabili riportati sopra.

>[!MORE_ LIKE_ THIS]
>
>* [Assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html)

