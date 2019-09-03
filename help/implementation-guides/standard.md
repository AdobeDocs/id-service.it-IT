---
description: Le implementazioni meno recenti usano Dynamic Tag Management (DTM) per configurare, distribuire e integrare il servizio Experience Cloud Identity con le altre soluzioni Experience Cloud.
keywords: Servizio ID
seo-description: Le implementazioni meno recenti usano Dynamic Tag Management (DTM) per configurare, distribuire e integrare il servizio Experience Cloud Identity con le altre soluzioni Experience Cloud.
seo-title: Implementazione con Dynamic Tag Management
title: Implementazione con Dynamic Tag Management
uuid: c4f752c4-392e-4909-b178-911706857064
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Implementazione con Dynamic Tag Management {#implementation-with-dynamic-tag-management}

Le implementazioni meno recenti usano Dynamic Tag Management (DTM) per configurare, distribuire e integrare il servizio Experience Cloud Identity con le altre soluzioni Experience Cloud.

## Implementazione con Dynamic Tag Management {#topic-6f4ed5d96977406ca991e50f3fbd5b01}

Le implementazioni meno recenti usano Dynamic Tag Management (DTM) per configurare, distribuire e integrare il servizio Experience Cloud Identity con le altre soluzioni Experience Cloud.

>[!NOTE]
>
>Al momento, [Adobe Experience Platform Launch](https://docs.adobelaunch.com/) è lo strumento di implementazione preferito e consigliato perché consente di semplificare attività di gestione dei tag complesse e automatizza il posizionamento del codice oltre le funzionalità di DTM. Vedi [Implementare con Launch](../implementation-guides/ecid-implement-with-launch.md).

## Dynamic Tag Management e servizio ID {#section-4a4c4fac5d0a4cbbaff8e1833f73657c}

[Dynamic Tag Management](https://marketing.adobe.com/resources/help/en_US/dtm/) consente di configurare, implementare e gestire la tua istanza del servizio ID e le relative integrazioni di soluzioni [!DNL Experience Cloud]. DTM semplifica il processo di implementazione grazie alla stretta integrazione con il servizio ID e altre soluzioni Experience Cloud. È sufficiente aggiungere e configurare lo strumento Experience Cloud ID e specificare informazioni quali:

* ID organizzazione Experience Cloud (popolato automaticamente se collegato a Experience Cloud)
* Server per tracking di Analytics (protetto e non protetto)
* Server Experience Cloud (per server per tracking di prime parti)

DTM è disponibile gratuitamente per tutti i clienti di [!DNL Experience Cloud].

**Guida introduttiva a Dynamic Tag Management**

Dynamic Tag Management è uno strumento semplice ma molto potente. Se non lo usi già, ti consigliamo vivamente di iniziare a farlo. Per iniziare a usare il servizio, consulta la [documentazione DTM ](https://marketing.adobe.com/resources/help/en_US/dtm/c_overview.html) e [Video introduttivi DTM](https://marketing.adobe.com/resources/help/en_US/dtm/jump-start-videos.html). Per istruzioni su come impostare il servizio ID con Dynamic Tag Management, leggi le informazioni e procedure riportate di seguito.

## Linee guida per l'implementazione {#concept-54a2ec49af8f4bfca9207b1d404e8e1a}

Leggi i requisiti e le procedure seguenti prima di provare a implementare il servizio Experience Cloud Identity con Dynamic Tag Management (DTM).

<!--
mcvid-dtm-deployment.xml
-->

**Provisioning dell'account**

Prima di iniziare, assicurati che sia stato fatto il provisioning dell'organizzazione e delle soluzioni per [!DNL Experience Cloud] e acquisisci familiarità con [!DNL Dyanamic Tag Management]. Questa documentazione rappresenta un buon punto di partenza:

* [Abilita le soluzioni per i servizi principali](https://marketing.adobe.com/resources/help/it_IT/mcloud/core_services.html): implementa Experience Cloud e diventa amministratore. Questa procedura consente di modernizzare le soluzioni per i servizi di base come gli attributi del cliente e Experience Cloud Audiences.
* [Guida introduttiva alla Dynamic Tag Management](https://marketing.adobe.com/resources/help/en_US/dtm/get_started.html)
* [Video introduttivi](https://marketing.adobe.com/resources/help/en_US/dtm/jump-start-videos.html): una serie di brevi video che mostrano come eseguire attività di base DTM.

**Inserimento e ordine di caricamento del codice del servizio ID**

Il servizio ID richiede e riceve un ID univoco dai server [!DNL Adobe] di raccolta dati. Per funzionare correttamente, il codice del servizio ID deve essere:

* Il primo blocco di [!DNL Adobe] codice che viene eseguito sulla pagina.
* Inserito in una posizione quanto più alta possibile sulla pagina, solitamente nel `<head>` blocco di codice.

Finché mantieni tutte le soluzioni e le librerie di codice [!DNL Adobe] in Dynamic Tag Management, il codice del servizio ID sarà inserito nella posizione giusta e attivato al momento giusto.

**Convalida della raccolta dati regionali**

I clienti devono fornire un CNAME o utilizzare `*.sc.omtrdc` per la [raccolta dati regionali](https://marketing.adobe.com/resources/help/en_US/whitepapers/rdc/) (RDC). Per ottenere le impostazioni RDC specifiche, rivolgiti al tuo consulente [!DNL Adobe].

**Configurare le suite di rapporti di Analytics**

I nuovi clienti [!DNL Analytics] devono [creare una suite di rapporti](https://marketing.adobe.com/resources/help/en_US/reference/new_report_suite.html) per la raccolta di dati.

## Implementazione del servizio Experience Cloud Identity con DTM {#task-a659cf19dea84ad48edabe0b72ef9f5c}

Segui questi passaggi per implementare il servizio ID con Dynamic Tag Management (DTM).

**Prerequisiti**

* Abilita le tue soluzioni per [!DNL Experience Cloud] e verifica di disporre delle autorizzazioni di livello amministratore. Consulta [Abilita le soluzioni per i servizi principali](https://marketing.adobe.com/resources/help/it_IT/mcloud/core_services.html).

* Crea una proprietà Web in Dynamic Tag Management. Consulta [Crea una proprietà Web di DTM ](https://marketing.adobe.com/resources/help/en_US/dtm/web_property.html) o i [Video introduttivi dell'amministratore](https://marketing.adobe.com/resources/help/en_US/dtm/admin-jump-start.html).

<!--
mcvid-dtm-implement.xml
-->

**Passaggi per l'implementazione** Per implementare il servizio ID con DTM:

1. Nel [!UICONTROL Dashboard] di Dynamic Tag Management, fai clic sulla proprietà Web che desideri usare.
1. Nella scheda **[!UICONTROL Panoramica]** della proprietà Web selezionata, fai clic su **[!UICONTROL Aggiungi uno strumento]**.
1. Nell’elenco **[!UICONTROL Tipo strumento]**, fai clic su **[!UICONTROL Servizio Experience Cloud Identity]**.

   >[!NOTE]
   >
   >La casella **[!UICONTROL ID organizzazione Experience Cloud]** viene compilata con l'ID organizzazione. Se il tuo account di Dynamic Tag Management non è collegato a [!DNL Experience Cloud], devi fornire manualmente questo ID. Per collegare l'account, consulta [Collegare gli account in Experience Cloud](https://marketing.adobe.com/resources/help/it_IT/mcloud/organizations.html). Per informazioni su come reperire l'ID organizzazione, vedi la sezione sui [requisiti](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26).

1. Digita il nome del server di tracciamento nella casella **[!UICONTROL Server tracciamento]**. Se non sei sicuro di come trovare il server di tracciamento, consulta le [domande frequenti](../faq-intro/faq.md) e [Compilare correttamente le variabili trackingServer e trackingServerSecure ](https://helpx.adobe.com/it/analytics/kb/determining-data-center.html#).
1. Fai clic su **[!UICONTROL Crea strumento]** e **[!UICONTROL Salva modifiche]**.

   Dopo il salvataggio, il servizio ID è impostato come strumento in Dynamic Tag Management. Tuttavia non è ancora pronto all'uso. Lo strumento Dynamic Tag Management deve ancora essere sottoposto al processo di pubblicazione e approvazione di Dynamic Tag Management e potrebbe essere necessario configurare altri parametri. Per informazioni sul processo di approvazione di Dynamic Tag Management, consulta il video [utente introduttivo di base ](https://marketing.adobe.com/resources/help/en_US/dtm/user-basics-jump-start.html). Per informazioni sugli altri parametri che puoi aggiungere a DTM, consulta [Impostazioni del servizio Experience Cloud Identity per Dynamic Tag Management](../implementation-guides/standard.md#concept-fb6cb6a0e6cc4f10b92371f8671f6b59).

>[!MORE_LIKE_THIS]
>
>* [Proprietà Web](https://marketing.adobe.com/resources/help/en_US/dtm/web_property.html)


## Impostazioni del servizio Experience Cloud Identity per Dynamic Tag Management {#concept-fb6cb6a0e6cc4f10b92371f8671f6b59}

Descrive i campi [!UICONTROL ID organizzazione], [!UICONTROL Impostazioni generali] e [!UICONTROL Impostazioni cliente] e come vengono usati dal servizio [!DNL Experience Cloud] ID.

<!--
mcvid-dtm-settings.xml
-->

## Dove si trovano queste impostazioni? {#section-c5b2d1c928944ae2b8565c1b182fe575}

Queste impostazioni diventano disponibili dopo che il servizio ID è stato aggiunto e salvato come strumenti in Dynamic Tag Management. Puoi anche accedere a queste impostazioni facendo clic sull'icona dell'ingranaggio nella sezione [!UICONTROL Strumenti installati] della proprietà Web di Dynamic Tag Management.

![](assets/installedTools.png)

## ID organizzazione {#section-949b5a0d8af940558b04ff675cf53f77}

Questo ID è richiesto da e associato alla società con provisioning [!DNL Experience Cloud]. Per organizzazione si intende l'entità che consente all'amministratore di configurare gruppi e utenti e di controllare l'accesso single sign-on in [!DNL Experience Cloud]. L'ID organizzazione è una stringa alfanumerica composta da 24 caratteri, seguita da (e deve includere) @AdobeOrg. Gli amministratori [!DNL Experience Cloud] possono trovare questo ID in [Experience Cloud &gt; Strumenti](https://marketing.adobe.com/resources/help/it_IT/mcloud/admin_getting_started.html).

![](assets/orgID.png)

Consulta anche [Cookie e il servizio Experience Cloud Identity](../introduction/cookies.md).

## Impostazioni generali {#section-071d358e40f84629a8901b893dd61392}

Queste impostazioni consentono di specificare i server di tracciamento, le versioni del codice e altre variabili.

![](assets/generalSettings.png)

Nella seguente tabella sono elencate e definite le impostazioni [!UICONTROL Generali].

**Richiedi automaticamente ID visitatore**

Quando questa opzione è selezionata, Dynamic Tag Management chiama automaticamente il metodo `getMarketingCloudVisitorID()` prima di caricare le soluzioni Adobe che utilizzano il servizio Experience Cloud Identity.

Consulta [getMarketingCloudVisitorID](../library/get-set/getmcvid.md).

**Server di tracciamento Analytics**

Nome del server di tracciamento usato per la raccolta di dati Analytics. Si tratta del dominio in cui vengono scritti la richiesta di immagini e il cookie (esempio: `http://site.omtrdc.net`).

Se non conosci l'URL del server di tracciamento, controlla i tuoi file `s_code.js` o `AppMeasurement.js`. Individua l'URL impostato dalla `s.trackingServer` variabile.

Consulta [trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) e [Compilare correttamente le variabili trackingServer e trackingServerSecure](https://helpx.adobe.com/it/analytics/kb/determining-data-center.html#).

**Server di tracciamento protetto**

Nome del server di tracciamento protetto utilizzato per la raccolta dati Analytics. Si tratta del dominio in cui vengono scritti la richiesta di immagini e il cookie (esempio: `https://site.omtrdc.net`).

Se non conosci l'URL del server di tracciamento, controlla i tuoi file `s_code.js` o `AppMeasurement.js`. Individua l'URL impostato dalla `s.trackingServerSecure` variabile.

Consulta [trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) e [Compilare correttamente le variabili trackingServer e trackingServerSecure](https://helpx.adobe.com/it/analytics/kb/determining-data-center.html#).

**Server Experience Cloud**

Se l'azienda utilizza la raccolta dati di prime parti (CNAME) per utilizzare cookie di prime parti in un contesto terze parti, specifica il server di tracciamento (esempio: `http://metrics.company.com`).

**Server Experience Cloud protetto**

Se l'azienda utilizza la raccolta dati di prime parti (CNAME) per utilizzare cookie di prime parti in un contesto terze parti, specifica il server di tracciamento (esempio: `https://metrics.company.com`).

**Versione libreria**

Imposta la versione della libreria del codice del servizio ID (`VisitorAPI.js`) che desideri usare. Non puoi modificare queste opzioni di menu.

**Impostazioni**

Questi campi consentono di aggiungere [variabili di funzioni](../library/function-vars/function-vars.md) sotto forma di coppie chiave-valore. Fai clic su **[!UICONTROL Aggiungi]** per aggiungere una o più variabili all'implementazione del servizio ID.

![](assets/dtmVars.png)

>[!IMPORTANT]
>
>Imposta la `cookieDomain` variabile qui. Questa variabile è obbligatoria per i domini di livello superiore con più parti, se una delle ultime due parti dell'URL comprende più di due caratteri. Consulta la documentazione sulle variabili di configurazione dal collegamento fornito qui sopra.

## Impostazioni cliente {#section-238d1272c1504d148fe38fb0ae5d71c2}

Campi aggiuntivi che consentono di aggiungere codice di integrazione o lo stato di autenticazione.

![](assets/customerSettings.png)

**Codice integrazione**

Un codice di integrazione è un ID cliente univoco. Il codice di integrazione deve contenere il valore utilizzato [per creare una sorgente dati](https://marketing.adobe.com/resources/help/en_US/aam/create-datasource.html) in [!DNL Audience Manager].

**Valore**

Il valore deve essere un elemento di dati contenente l'ID utente. Gli elementi di dati sono contenitori idonei per valori dinamici, come gli ID da un sistema interno specifico per il cliente.

**Stato autenticazione**

Opzioni che definiscono o identificano i visitatori in base al loro stato di autenticazione (connessi o disconnessi). Vedi [Impostazione degli ID cliente e degli stati di autenticazione](../reference/authenticated-state.md).

## Test e verifica del servizio Experience Cloud Identity {#concept-644fdbef433b46ba9c0634ac95eaa680}

Istruzioni, strumenti e procedure utili per determinare se il servizio ID funziona correttamente. Questi test sono applicabili al servizio ID in generale e per diverse combinazioni del servizio ID e della soluzione [!DNL Experience Cloud].

<!--
mcvid-test-verify.xml
-->

## Prima di iniziare {#section-b1e76ad552ed4eb793b6e521a55127d4}

Informazioni importanti da conoscere prima di iniziare il test e la verifica del servizio ID.

**Ambienti browser**

Se esegui il test in una normale sessione browser, cancella la cache del browser prima di ogni test.

In alternativa, verifica il servizio ID in una sessione browser anonima. In una sessione anonima, non devi cancellare i cookie o la cache del browser prima di ogni test.

**Strumenti**

Con [Adobe debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) e [proxy HTTP Charles](https://www.charlesproxy.com/) puoi determinare se il servizio ID è stato configurato per funzionare correttamente con Analytics. Le informazioni di questa sezione si basano sui risultati restituiti da Adobe Debugger e Charles. Puoi anche usare un altro strumento o debugger di tua preferenza.

## Test con Adobe Debugger {#section-861365abc24b498e925b3837ea81d469}

L'integrazione del servizio è configurata correttamente se vedi un identificatore [!DNL Experience Cloud ID] (MID) nella risposta di [!DNL Adobe] Debugger. Per maggiori informazioni sull’identificatore MID, consulta [Cookie e il servizio Experience Cloud Identity](../introduction/cookies.md).

Per verificare lo stato del servizio ID con il [!DNL Adobe] [debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html):

1. Cancella i cookie del browser o apri una sessione browser anonima.
1. Carica la pagina di prova contenente il codice del servizio ID.
1. Apri [!DNL Adobe] Debugger.
1. Individua un identificatore MID nei risultati.

## I risultati di Adobe Debugger {#section-bd2caa6643d54d41a476d747b41e7e25}

L'identificatore MID viene memorizzato in una coppia chiave-valore con sintassi: `MID= *`Experience Cloud ID`*`. Queste informazioni sono presentate nel modo seguente.

**Operazione riuscita**

Il servizio ID è stato implementato correttamente se la risposta è simile all'esempio seguente:

```
mid=20265673158980419722735089753036633573
```

Se sei un cliente [!DNL Analytics], oltre all'identificatore MID potresti vedere un identificatore [!DNL Analytics] ID (AID). Ciò accade nelle seguenti situazioni:

* Per alcuni visitatori di lunga data.
* Se hai impostato un periodo di tolleranza.

**Errore**

Contatta l'[assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html) se il debugger:

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

### Richieste corrette per il servizio ID in Charles

Il codice del servizio ID funziona correttamente se la funzione `Visitor.getInstance` effettua una chiamata JavaScript a `dpm.demdex.net`. Una richiesta corretta include il tuo [ID organizzazione](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). L'ID organizzazione viene passato sotto forma di coppia chiave-valore con sintassi: `d_orgid= *`ID organizzazione`*`. Cerca le chiamate `dpm.demdex.net` e JavaScript nella scheda [!UICONTROL Struttura]. Cerca l’ID organizzazione nella scheda [!UICONTROL Richiesta].

![](assets/charles_request.png)

### Risposte corrette per il servizio ID in Charles

Il provisioning del tuo account per il servizio ID è corretto quando la risposta dai [Server di raccolta dati](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) restituisce un identificatore MID. L’identificatore MID viene restituito come coppia chiave-valore con la seguente sintassi: `d_mid: visitor Experience Cloud ID`. Cerca l’identificatore MID nella scheda [!UICONTROL Risposta], come illustrato di seguito.

![](assets/charles_response_success.png)

### Risposte errate per il servizio ID in Charles

Il provisioning del tuo account per il servizio ID non è corretto se la risposta DCS non contiene l’identificatore MID. Una risposta errata restituisce un codice di errore e un messaggio nella scheda [!UICONTROL Risposta], come illustrato di seguito. Se ricevi questo messaggio di errore nella risposta DCS, contatta l'assistenza clienti.

![](assets/charles_response_unsuccessful.png)

Per ulteriori informazioni sui codici di errore, vedi [Codici di errore DCS, messaggi ed esempi](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html).
