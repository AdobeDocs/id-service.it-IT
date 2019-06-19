---
description: Le implementazioni meno recenti usano Dynamic Tag Management (DTM) per configurare, distribuire e integrare il servizio Experience Cloud ID con le altre soluzioni Experience Cloud.
keywords: Servizio ID
seo-description: Le implementazioni meno recenti usano Dynamic Tag Management (DTM) per configurare, distribuire e integrare il servizio Experience Cloud ID con le altre soluzioni Experience Cloud.
seo-title: Implementazione con Gestione tag dinamica
title: Implementazione con Gestione tag dinamica
uuid: c 4 f 752 c 4-392 e -4909-b 178-911706857064
translation-type: tm+mt
source-git-commit: 4dc668afd37cd1d6f9104adb1b102f1dd4c5746e

---


# Implementazione con Gestione tag dinamica{#implementation-with-dynamic-tag-management}

Le implementazioni meno recenti usano Dynamic Tag Management (DTM) per configurare, distribuire e integrare il servizio Experience Cloud ID con le altre soluzioni Experience Cloud.

## Implementazione con Gestione tag dinamica {#topic-6f4ed5d96977406ca991e50f3fbd5b01}

Le implementazioni meno recenti usano Dynamic Tag Management (DTM) per configurare, distribuire e integrare il servizio Experience Cloud ID con le altre soluzioni Experience Cloud.

>[!NOTE]
>
>[Attualmente, Launch, di Adobe](https://docs.adobelaunch.com/) è lo strumento di implementazione preferito e consigliato perché semplifica le attività di gestione tag complesse e automatizza la posizione del codice oltre le funzionalità di DTM. Consultate [Implementazione con Launch](../mcvid-implementation-guides/ecid-implement-with-launch.md).

## Dynamic Tag Management e servizio ID {#section-4a4c4fac5d0a4cbbaff8e1833f73657c}

[Gestione tag dinamica](https://marketing.adobe.com/resources/help/en_US/dtm/) ti consente di configurare, implementare e gestire la tua istanza del servizio ID e le relative [!DNL Experience Cloud] integrazioni di soluzioni. DTM semplifica il processo di implementazione grazie alla stretta integrazione con il servizio ID e altre soluzioni Experience Cloud. È sufficiente aggiungere e configurare lo strumento Experience Cloud ID e specificare informazioni quali:

* ID organizzazione Experience Cloud (popolato automaticamente se collegato a Experience Cloud)
* Server per tracking di Analytics (protetto e non protetto)
* Server Experience Cloud (per server per tracking di prime parti)

DTM è disponibile gratuitamente per tutti i clienti di [!DNL Experience Cloud].

**Guida introduttiva a Gestione dinamica dei tag**

Dynamic Tag Management è uno strumento semplice ma molto potente. Se non lo usi già, ti consigliamo vivamente di iniziare a farlo. Leggi la [documentazione](https://marketing.adobe.com/resources/help/en_US/dtm/c_overview.html) di Dynamic Tag Management e guarda i [video DTM Jump Start](https://marketing.adobe.com/resources/help/en_US/dtm/jump-start-videos.html). Per istruzioni su come impostare il servizio ID con Dynamic Tag Management, leggi le informazioni e procedure riportate di seguito.

## Linee guida per l&#39;implementazione {#concept-54a2ec49af8f4bfca9207b1d404e8e1a}

Leggi i requisiti e le procedure seguenti prima di provare a implementare il servizio Experience Cloud ID con Dynamic Tag Management (DTM).

<!--
mcvid-dtm-deployment.xml
-->

**Provisioning dell&#39;account**

Prima di iniziare, assicuratevi che sia stato eseguito il provisioning della vostra organizzazione e delle vostre soluzioni per [!DNL Experience Cloud] la vostra esperienza [!DNL Dyanamic Tag Management]. Questa documentazione rappresenta un buon punto di partenza:

* [Abilita le soluzioni per i servizi di base](https://marketing.adobe.com/resources/help/en_US/mcloud/core_services.html): Implementa Experience Cloud e diventa amministratore. Questa procedura consente di modernizzare le soluzioni per i servizi di base come gli attributi del cliente e Experience Cloud Audiences.
* [Guida introduttiva di Dynamic Tag Management](https://marketing.adobe.com/resources/help/en_US/dtm/get_started.html)
* [Video Jump Start](https://marketing.adobe.com/resources/help/en_US/dtm/jump-start-videos.html): Una serie di brevi video che dimostrano come eseguire attività di base DTM.

**Inserimento e ordine di caricamento del codice del servizio ID**

Il servizio ID richiede e riceve un ID univoco dai server [!DNL Adobe] di raccolta dati. Per funzionare correttamente, il codice del servizio ID deve essere:

* Il primo blocco di codice [!DNL Adobe] che viene eseguito sulla pagina.
* Posizionato il più alto possibile sulla pagina, in genere all&#39;interno del `<head>` blocco di codice.

Finché mantieni tutte le soluzioni e le librerie di codice [!DNL Adobe] in Dynamic Tag Management, il codice del servizio ID sarà inserito nella posizione giusta e attivato al momento giusto.

**Convalida della raccolta dati regionali**

I clienti devono fornire un CNAME o utilizzare [!DNL *.sc.omtrdc] per [la raccolta](https://marketing.adobe.com/resources/help/en_US/whitepapers/rdc/) dati regionali (RDC). Per ottenere le impostazioni RDC specifiche, rivolgiti al tuo consulente [!DNL Adobe].

**Configurazione delle suite di rapporti di Analytics**

I nuovi clienti [!DNL Analytics] devono [creare una suite di rapporti](https://marketing.adobe.com/resources/help/en_US/reference/new_report_suite.html) per la raccolta dei dati.

## Implementazione del servizio Experience Cloud ID con DTM {#task-a659cf19dea84ad48edabe0b72ef9f5c}

Segui questi passaggi per implementare il servizio ID con Dynamic Tag Management (DTM).

**Prerequisiti**

* Abilita le tue soluzioni per [!DNL Experience Cloud] e verifica di disporre delle autorizzazioni di livello amministratore. Consultate [Abilitare le soluzioni per i servizi di base](https://marketing.adobe.com/resources/help/en_US/mcloud/core_services.html).

* Crea una proprietà Web in Dynamic Tag Management. Consulta la documentazione di Dynamic Tag Management su come [creare una proprietà Web](https://marketing.adobe.com/resources/help/en_US/dtm/web_property.html) o guarda il [video Admin Jump Start](https://marketing.adobe.com/resources/help/en_US/dtm/admin-jump-start.html).

<!--
mcvid-dtm-implement.xml
-->

**Passaggi di implementazione** Per implementare il servizio ID con Gestione dinamica dei tag:

1. Nel [!DNL Dashboard] di Dynamic Tag Management, fai clic sulla proprietà Web che desideri usare.
1. Nella scheda **[!UICONTROL Panoramica]** della proprietà Web selezionata, fai clic **[!UICONTROL su Aggiungi uno strumento]**.
1. Nell&#39;elenco **[!UICONTROL Tipo]** strumento, fai clic **[!UICONTROL su Servizio Experience Cloud ID]**.

   >[!NOTE]
   >
   >Questa azione compila la **[!UICONTROL casella ID]** organizzazione Experience Cloud con l&#39;ID organizzazione. Se il tuo account di Dynamic Tag Management non è collegato a [!DNL Experience Cloud], devi fornire manualmente questo ID. Per collegare il tuo account, consulta [Collegare gli account in Experience Cloud](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html). Per informazioni su come reperire l&#39;ID organizzazione, vedi la sezione sui [requisiti](../mcvid-reference/mcvid-requirements.md#section-a02f537129a64ffbb690d5738d360c26).

1. Digita il nome del server di tracciamento nella casella **[!UICONTROL Server]** tracciamento. Se non sei sicuro di come trovare il server di tracciamento, consulta [le domande frequenti](../mcvid-faq-intro/mcvid-faq.md) e [Aggiunta corretta delle variabili trackingserver e trackingserversecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).
1. Fate clic su **[!UICONTROL Crea strumento]** e **[!UICONTROL Salva modifiche]**.

   Dopo il salvataggio, il servizio ID è impostato come strumento in Dynamic Tag Management. Tuttavia non è ancora pronto all&#39;uso. Lo strumento Dynamic Tag Management deve ancora essere sottoposto al processo di pubblicazione e approvazione di Dynamic Tag Management e potrebbe essere necessario configurare altri parametri. Per informazioni sul processo di approvazione di Dynamic Tag Management, guarda il video [User Basics Jump Start](https://marketing.adobe.com/resources/help/en_US/dtm/user-basics-jump-start.html). Per informazioni sugli altri parametri che puoi aggiungere a Dynamic Tag Management, vedi [Impostazioni del servizio Experience Cloud ID per DTM](../mcvid-implementation-guides/mcvid-standard.md#concept-fb6cb6a0e6cc4f10b92371f8671f6b59).

>[!MORE_ LIKE_ THIS]
>
>* [Proprietà Web](https://marketing.adobe.com/resources/help/en_US/dtm/web_property.html)


## Impostazioni del servizio Experience Cloud ID per Dynamic Tag Management {#concept-fb6cb6a0e6cc4f10b92371f8671f6b59}

Descrive i [!DNL Organization ID]campi e [!DNL General][!DNL Customer Settings] i campi e come vengono usati dal [!DNL Experience Cloud] servizio ID.

<!--
mcvid-dtm-settings.xml
-->

## Come trovo queste impostazioni? {#section-c5b2d1c928944ae2b8565c1b182fe575}

Queste impostazioni diventano disponibili dopo che il servizio ID è stato aggiunto e salvato come strumenti in Dynamic Tag Management. Puoi anche accedere a queste impostazioni facendo clic sull&#39;icona a forma di ingranaggio dalla [!DNL Installed Tools] sezione della proprietà Web di Gestione dinamica dei tag.

![](assets/installedTools.png)

## ID organizzazione {#section-949b5a0d8af940558b04ff675cf53f77}

Questo ID è richiesto da e associato alla società con provisioning [!DNL Experience Cloud]. Per organizzazione si intende l&#39;entità che consente all&#39;amministratore di configurare gruppi e utenti e di controllare l&#39;accesso single sign-on in [!DNL Experience Cloud]. L&#39;ID organizzazione è una stringa alfanumerica composta da 24 caratteri, seguita da (e deve includere) @AdobeOrg. Gli amministratori di [!DNL Experience Cloud] possono trovare questo ID in [Experience Cloud &gt; Strumenti](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html).

![](assets/orgID.png)

Vedi anche [Cookie e il servizio Experience Cloud ID](../mcvid-introduction/mcvid-cookies.md).

## Impostazioni generali {#section-071d358e40f84629a8901b893dd61392}

Queste impostazioni consentono di specificare i server di tracciamento, le versioni del codice e altre variabili.

![](assets/generalSettings.png)

Nella tabella seguente sono elencate e definite [!DNL General] le impostazioni.

**Richiedi automaticamente ID visitatore**

Quando questa opzione è selezionata, Gestione tag dinamica chiama automaticamente il `getMarketingCloudVisitorID()` metodo prima di caricare una delle soluzioni Adobe che utilizzano il servizio Experience Cloud ID.

Consulta [getmarketingcloudvisitorid](../mcvid-library/mcvid-get-set/mcvid-getmcvid.md).

**Server di tracciamento Analytics**

Nome del server di tracciamento usato per la raccolta di dati Analytics. Si tratta del dominio in cui vengono scritti la richiesta di immagini e il cookie (esempio: [!DNL http://site.omtrdc.net]).

Se non conosci gli URL del server di tracciamento, controlla i tuoi `s_code.js` o `AppMeasurement.js` i file. Individua l&#39;URL impostato dalla variabile `s.trackingServer`.

Vedi [trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) e [Aggiunta corretta delle variabili trackingServer e trackingServerSecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

**Server di tracciamento protetto**

Nome del server di tracciamento protetto utilizzato per la raccolta dati Analytics. Si tratta del dominio in cui vengono scritti la richiesta di immagini e il cookie (esempio: [!DNL https://site.omtrdc.net]).

Se non conosci gli URL del server di tracciamento, controlla i tuoi `s_code.js` o `AppMeasurement.js` i file. Individua l&#39;URL impostato dalla variabile `s.trackingServerSecure`.

Vedi [trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) e [Aggiunta corretta delle variabili trackingServer e trackingServerSecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

**Server Experience Cloud**

Se l&#39;azienda utilizza la raccolta dati di prime parti (CNAME) per utilizzare cookie di prime parti in un contesto terze parti, specifica il server di tracciamento (esempio: [!DNL http://metrics.company.com]).

**Server Experience Cloud protetto**

Se l&#39;azienda utilizza la raccolta dati di prime parti (CNAME) per utilizzare cookie di prime parti in un contesto terze parti, specifica il server di tracciamento (esempio: [!DNL https://metrics.company.com]).

**Versione libreria**

Imposta la versione della libreria del codice del servizio ID (`VisitorAPI.js`) che desideri usare. Non puoi modificare queste opzioni di menu.

**Impostazioni**

Questi campi consentono di aggiungere [variabili di funzioni](../mcvid-library/mcvid-function-vars/mcvid-function-vars.md) sotto forma di coppie chiave-valore. Fai clic su **[!UICONTROL Aggiungi]per aggiungere una o più variabili all&#39;implementazione del servizio ID.**

![](assets/dtmVars.png)

>[!IMPORTANT]
>
>Imposta la `cookieDomain` variabile qui. Questa variabile è obbligatoria per i domini di livello superiore con più parti, se una delle ultime due parti dell&#39;URL comprende più di due caratteri. Consulta la documentazione sulle variabili di configurazione dal collegamento fornito qui sopra.

## Impostazioni cliente {#section-238d1272c1504d148fe38fb0ae5d71c2}

Campi aggiuntivi che consentono di aggiungere codice di integrazione o lo stato di autenticazione.

![](assets/customerSettings.png)

**Codice integrazione**

Un codice di integrazione è un ID cliente univoco. Il codice di integrazione deve contenere il valore utilizzato per [creare un&#39;origine dati](https://marketing.adobe.com/resources/help/en_US/aam/create-datasource.html) in [!DNL Audience Manager].

**Valore**

Il valore deve essere un elemento di dati contenente l&#39;ID utente. Gli elementi di dati sono contenitori idonei per valori dinamici, come gli ID da un sistema interno specifico per il cliente.

**Stato autenticazione**

Opzioni che definiscono o identificano i visitatori in base al loro stato di autenticazione (connessi o disconnessi). Consulta [ID cliente e stati di autenticazione](../mcvid-reference/mcvid-authenticated-state.md).

## Verificare e verificare il servizio Experience Cloud ID {#concept-644fdbef433b46ba9c0634ac95eaa680}

Istruzioni, strumenti e procedure utili per determinare se il servizio ID funziona correttamente. Questi test sono applicabili al servizio ID in generale e per diverse combinazioni del servizio ID e della soluzione [!DNL Experience Cloud].

<!--
mcvid-test-verify.xml
-->

## Prima di iniziare {#section-b1e76ad552ed4eb793b6e521a55127d4}

Informazioni importanti da conoscere prima di iniziare a testare e verificare il servizio ID.

**Ambienti browser**

Se esegui il test in una normale sessione browser, cancella la cache del browser prima di ogni test.

In alternativa, verifica il servizio ID in una sessione browser anonima. In una sessione anonima, non devi cancellare i cookie o la cache del browser prima di ogni test.

**Strumenti**

Utilizzando [Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) e il [proxy HTTP Charles](https://www.charlesproxy.com/) puoi determinare se il servizio ID è stato configurato in modo da funzionare correttamente con Analytics. Le informazioni di questa sezione si basano sui risultati restituiti da Adobe Debugger e Charles. Puoi anche usare un altro strumento o debugger di tua preferenza.

## Test con Adobe Debugger {#section-861365abc24b498e925b3837ea81d469}

L&#39;integrazione del servizio è configurata correttamente quando si visualizza un [!DNL Experience Cloud ID] (MID) nella risposta [!DNL Adobe] debugger. Per ulteriori informazioni sull&#39;identificatore MID, vedi [Cookie e Servizio](../mcvid-introduction/mcvid-cookies.md) Experience Cloud ID.

Per verificare lo stato del servizio ID con il [!DNL Adobe][debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html):

1. Cancella i cookie del browser o apri una sessione browser anonima.
1. Carica la pagina di prova contenente il codice del servizio ID.
1. Aprire il [!DNL Adobe] debugger.
1. Individua un identificatore MID nei risultati.

## Informazioni sui risultati di Adobe Debugger {#section-bd2caa6643d54d41a476d747b41e7e25}

L&#39;identificatore MID viene memorizzato in una coppia chiave-valore che utilizza la sintassi: `MID= *`Experience Cloud ID`*`. Queste informazioni sono presentate nel modo seguente.

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

## Test con il proxy HTTP Charles {#section-d9e91f24984146b2b527fe059d7c9355}

Per verificare lo stato del servizio ID con Charles:

1. Cancella i cookie del browser o apri una sessione browser anonima.
1. Avvia Charles.
1. Carica la pagina di prova contenente il codice del servizio ID.
1. Verifica le chiamate di richiesta e risposta e i dati descritti di seguito.

## I risultati di Charles {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Questa sezione descrive quali informazioni cercare e dove cercarle quando usi Charles per monitorare le chiamate HTTP.

**Richieste di servizio ID completate in Charles**

Il codice del servizio ID funziona correttamente se la funzione `Visitor.getInstance` effettua una chiamata JavaScript a `dpm.demdex.net`. Una richiesta corretta include il tuo [ID organizzazione](../mcvid-reference/mcvid-requirements.md#section-a02f537129a64ffbb690d5738d360c26). L&#39;ID organizzazione viene passato come coppia chiave-valore che utilizza la sintassi: `d_orgid= *`ID organizzazione`*`. Cercare le `dpm.demdex.net` chiamate javascript sotto la [!DNL Structure] scheda. Cerca l&#39;ID organizzazione sotto la [!DNL Request] scheda.

![](assets/charles_request.png)

**Risposte corrette al servizio ID in Charles**

Il provisioning del tuo account per il servizio ID è corretto se la risposta dai [Data Collection Servers](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) restituisce un valore MID. L&#39;identificatore MID viene restituito come coppia chiave-valore che utilizza la sintassi: `d_mid: *`Experience Cloud ID`*`. Cerca l&#39;identificatore MID nella [!DNL Response] scheda come mostrato di seguito.

![](assets/charles_response_success.png)

**Risposte errate al servizio ID in Charles**

Il provisioning del tuo account per il servizio ID non è corretto se la risposta DCS non contiene l&#39;identificatore MID. Una risposta non riuscita restituisce un codice di errore e un messaggio nella [!DNL Response] scheda come mostrato di seguito. Se ricevi questo messaggio di errore nella risposta DCS, contatta l&#39;assistenza clienti.

![](assets/charles_response_unsuccessful.png)

Per informazioni sui codici di errore, vedi [Codici di errore, messaggi ed esempi DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html).
