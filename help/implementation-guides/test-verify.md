---
description: Istruzioni, strumenti e procedure utili per determinare se il servizio ID funziona correttamente. Questi test sono applicabili al servizio ID in generale e per diverse combinazioni del servizio ID e della soluzione Experience Cloud.
keywords: Servizio ID
seo-description: Istruzioni, strumenti e procedure utili per determinare se il servizio ID funziona correttamente. Questi test sono applicabili al servizio ID in generale e per diverse combinazioni del servizio ID e della soluzione Experience Cloud.
seo-title: Verificare e verificare il servizio Experience Cloud ID
title: Verificare e verificare il servizio Experience Cloud ID
uuid: 442 de 9 c 3-c 265-4412-89 bd-aeaa 286 ddad 6
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Test and verify the Experience Cloud ID Service{#test-and-verify-the-experience-cloud-id-service}

Istruzioni, strumenti e procedure utili per determinare se il servizio ID funziona correttamente. Questi test sono applicabili al servizio ID in generale e per diverse combinazioni del servizio ID e della soluzione Experience Cloud.

## Prima di iniziare {#section-b1e76ad552ed4eb793b6e521a55127d4}

Informazioni importanti da conoscere prima di iniziare a testare e verificare il servizio ID.

**Ambienti browser**

Se esegui il test in una normale sessione browser, cancella la cache del browser prima di ogni test.

In alternativa, verifica il servizio ID in una sessione browser anonima. In una sessione anonima, non devi cancellare i cookie o la cache del browser prima di ogni test.

**Strumenti**

Utilizzando [Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) e il [proxy HTTP Charles](https://www.charlesproxy.com/) puoi determinare se il servizio ID è stato configurato in modo da funzionare correttamente con Analytics. Le informazioni di questa sezione si basano sui risultati restituiti da Adobe Debugger e Charles. Puoi anche usare un altro strumento o debugger di tua preferenza.

## Test con Adobe Debugger {#section-861365abc24b498e925b3837ea81d469}

Your service integration is configured properly when you see a [!DNL Experience Cloud ID] (MID) in the [!DNL Adobe] debugger response. See [Cookies and the Experience Cloud ID Service](../introduction/cookies.md) for more information about the MID.

To verify the status of the ID service with the [!DNL Adobe] [debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html):

1. Cancella i cookie del browser o apri una sessione browser anonima.
1. Carica la pagina di prova contenente il codice del servizio ID.
1. Open the [!DNL Adobe] debugger.
1. Individua un identificatore MID nei risultati.

## Understanding Adobe Debugger results {#section-bd2caa6643d54d41a476d747b41e7e25}

The MID is stored in a key-value pair that uses this syntax: `MID= *`Experience Cloud ID`*`. Queste informazioni sono presentate nel modo seguente.

**Corretto**

Il servizio ID è stato implementato correttamente se la risposta è simile all&#39;esempio seguente:

```
mid=20265673158980419722735089753036633573
```

Se sei un cliente [!DNL Analytics], oltre all&#39;identificatore MID potresti vedere un identificatore [!DNL Analytics] ID (AID). Ciò accade nelle seguenti situazioni:

* Per alcuni visitatori di lunga data.
* Se hai impostato un periodo di tolleranza.

**Errore**

Contatta l&#39;[assistenza clienti](https://helpx.adobe.com/marketing-cloud/contact-support.html) se il debugger:

* non restituisce un valore MID;
* restituisce un messaggio di errore che indica che non è stato effettuato il provisioning del tuo ID partner.

## Testing with the Charles HTTP proxy {#section-d9e91f24984146b2b527fe059d7c9355}

Per verificare lo stato del servizio ID con Charles:

1. Cancella i cookie del browser o apri una sessione browser anonima.
1. Avvia Charles.
1. Carica la pagina di prova contenente il codice del servizio ID.
1. Verifica le chiamate di richiesta e risposta e i dati descritti di seguito.

## Understanding Charles results {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Questa sezione descrive quali informazioni cercare e dove cercarle quando usi Charles per monitorare le chiamate HTTP.

**Richieste di servizio ID completate in Charles**

Il codice del servizio ID funziona correttamente se la funzione `Visitor.getInstance` effettua una chiamata JavaScript a `dpm.demdex.net`. Una richiesta corretta include il tuo [ID organizzazione](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). The Organization ID is passed as a key-value pair that uses this syntax: `d_orgid= *`organization ID`*`. Look for the `dpm.demdex.net` and the JavaScript calls under the [!DNL Structure] tab. Look for your Organization ID under the [!DNL Request] tab.

![](assets/charles_request.png)

**Risposte corrette al servizio ID in Charles**

Il provisioning del tuo account per il servizio ID è corretto se la risposta dai [Data Collection Servers](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) restituisce un valore MID. The MID is returned as a key-value pair that uses this syntax: `d_mid: *`visitor Experience Cloud ID`*`. Look for the MID in the [!DNL Response] tab as shown below.

![](assets/charles_response_success.png)

**Risposte errate al servizio ID in Charles**

Il provisioning del tuo account per il servizio ID non è corretto se la risposta DCS non contiene l&#39;identificatore MID. An unsuccessful response returns an error code and message in the [!DNL Response] tab as shown below. Se ricevi questo messaggio di errore nella risposta DCS, contatta l&#39;assistenza clienti.

![](assets/charles_response_unsuccessful.png)

Per informazioni sui codici di errore, vedi [Codici di errore, messaggi ed esempi DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html).
