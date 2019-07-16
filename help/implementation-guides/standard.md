---
description: Le versioni precedenti usano Dynamic Tag Management (DTM) per configurare, implementare e integrare il servizio Identità Experience Platform con le altre soluzioni Experience Cloud.
keywords: Servizio ID
seo-description: Le versioni precedenti usano Dynamic Tag Management (DTM) per configurare, implementare e integrare il servizio Identità Experience Platform con le altre soluzioni Experience Cloud.
seo-title: Implementazione con Dynamic Tag Management
title: Implementazione con Dynamic Tag Management
uuid: c4f752c4-392e-4909-b178-911706857064
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Implementazione con Dynamic Tag Management{#implementation-with-dynamic-tag-management}

Le versioni precedenti usano Dynamic Tag Management (DTM) per configurare, implementare e integrare il servizio Identità Experience Platform con le altre soluzioni Experience Cloud.

## Implementazione con Dynamic Tag Management {#topic-6f4ed5d96977406ca991e50f3fbd5b01}

Le versioni precedenti usano Dynamic Tag Management (DTM) per configurare, implementare e integrare il servizio Identità Experience Platform con le altre soluzioni Experience Cloud.

>[!NOTE]
>
>Currently, [Adobe Experience Platform Launch](https://docs.adobelaunch.com/) is the preferred and recommended implementation tool because it helps simplify complex tag management tasks and automates code placement beyond the capabilities of DTM. Vedi [Implementare con Launch](../implementation-guides/ecid-implement-with-launch.md).

## Dynamic Tag Management e servizio ID {#section-4a4c4fac5d0a4cbbaff8e1833f73657c}

[Gestione tag dinamica](https://marketing.adobe.com/resources/help/en_US/dtm/) ti consente di configurare, implementare e gestire la tua istanza del servizio ID e le relative [!DNL Experience Cloud] integrazioni di soluzioni. DTM semplifica il processo di implementazione grazie alla stretta integrazione con il servizio ID e altre soluzioni Experience Cloud. È sufficiente aggiungere e configurare lo strumento Experience Cloud ID e specificare informazioni quali:

* ID organizzazione Experience Cloud (popolato automaticamente se collegato a Experience Cloud)
* Server per tracking di Analytics (protetto e non protetto)
* Server Experience Cloud (per server per tracking di prime parti)

DTM è disponibile gratuitamente per tutti i [!DNL Experience Cloud] clienti di.

**Guida introduttiva a Dynamic Tag Management**

Dynamic Tag Management è uno strumento semplice ma molto potente. Se non lo usi già, ti consigliamo vivamente di iniziare a farlo. Leggi la [documentazione](https://marketing.adobe.com/resources/help/en_US/dtm/c_overview.html) di Dynamic Tag Management e guarda i [video DTM Jump Start](https://marketing.adobe.com/resources/help/en_US/dtm/jump-start-videos.html). Per istruzioni su come impostare il servizio ID con Dynamic Tag Management, leggi le informazioni e procedure riportate di seguito.

## Linee guida per l&#39;implementazione {#concept-54a2ec49af8f4bfca9207b1d404e8e1a}

Leggi i requisiti e le procedure seguenti prima di provare a implementare il servizio Identità Experience Platform con Gestione dinamica dei tag.

<!--
mcvid-dtm-deployment.xml
-->

**Provisioning dell&#39;account**

Prima di iniziare, assicurati che sia stato fatto il provisioning dell&#39;organizzazione e delle soluzioni per [!DNL Experience Cloud] e acquisisci familiarità con [!DNL Dyanamic Tag Management]. Questa documentazione rappresenta un buon punto di partenza:

* [Abilita le soluzioni per i servizi di base](https://marketing.adobe.com/resources/help/en_US/mcloud/core_services.html): Implementa Experience Cloud e diventa amministratore. Questa procedura consente di modernizzare le soluzioni per i servizi di base come gli attributi del cliente e Experience Cloud Audiences.
* [Guida introduttiva di Dynamic Tag Management](https://marketing.adobe.com/resources/help/en_US/dtm/get_started.html)
* [Video Jump Start](https://marketing.adobe.com/resources/help/en_US/dtm/jump-start-videos.html): Una serie di brevi video che dimostrano come eseguire attività di base DTM.

**Inserimento e ordine di caricamento del codice del servizio ID**

Il servizio ID richiede e riceve un ID univoco dai server [!DNL Adobe] di raccolta dati. Per funzionare correttamente, il codice del servizio ID deve essere:

* Il primo blocco di [!DNL Adobe] codice che viene eseguito sulla pagina.
* Inserito in una posizione quanto più alta possibile sulla pagina, solitamente nel `<head>` blocco di codice.

Finché mantieni tutte le soluzioni e le librerie di codice [!DNL Adobe] in Dynamic Tag Management, il codice del servizio ID sarà inserito nella posizione giusta e attivato al momento giusto.

**Convalida della raccolta dati regionali**

Customers must provide a CNAME or use [!DNL *.sc.omtrdc] for [regional data collection](https://marketing.adobe.com/resources/help/en_US/whitepapers/rdc/) (RDC). Per ottenere le impostazioni RDC specifiche, rivolgiti al tuo consulente [!DNL Adobe].

**Configurare le suite di rapporti di Analytics**

I nuovi clienti [!DNL Analytics] devono [creare una suite di rapporti](https://marketing.adobe.com/resources/help/en_US/reference/new_report_suite.html) per la raccolta dei dati.

## Implement the Experience Platform Identity Service with DTM {#task-a659cf19dea84ad48edabe0b72ef9f5c}

Segui questi passaggi per implementare il servizio ID con Dynamic Tag Management (DTM).

**Prerequisiti**

* Abilita le tue soluzioni per [!DNL Experience Cloud] e verifica di disporre delle autorizzazioni di livello amministratore. See [Enable your solutions for core services](https://marketing.adobe.com/resources/help/en_US/mcloud/core_services.html).

* Crea una proprietà Web in Dynamic Tag Management. Consulta la documentazione di Dynamic Tag Management su come [creare una proprietà Web](https://marketing.adobe.com/resources/help/en_US/dtm/web_property.html) o guarda il [video Admin Jump Start](https://marketing.adobe.com/resources/help/en_US/dtm/admin-jump-start.html).

<!--
mcvid-dtm-implement.xml
-->

**Passaggi per l&#39;implementazione** Per implementare il servizio ID con DTM:

1. Nel [!DNL Dashboard] di Dynamic Tag Management, fai clic sulla proprietà Web che desideri usare.
1. Nella scheda **[!UICONTROL Panoramica]** della proprietà Web selezionata, fai clic su **[!UICONTROL Aggiungi uno strumento]**.
1. In the **[!UICONTROL Tool Type]** list, click **[!UICONTROL Experience Platform Identity Service]**.

   >[!NOTE]
   >
   >La casella **[!UICONTROL ID organizzazione Experience Cloud]** viene compilata con l&#39;ID organizzazione. Se il tuo account di Dynamic Tag Management non è collegato a [!DNL Experience Cloud], devi fornire manualmente questo ID. Per collegare il tuo account, consulta [Collegare gli account in Experience Cloud](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html). Per informazioni su come reperire l&#39;ID organizzazione, vedi la sezione sui [requisiti](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26).

1. Digita il nome del server di tracciamento nella casella **[!UICONTROL Server tracciamento]**. If you&#39;re not sure how to find your tracking server see the [FAQ](../faq-intro/faq.md) and [Correctly Populate the trackingServer and trackingServerSecure variables](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).
1. Fai clic su **[!UICONTROL Crea strumento]** e **[!UICONTROL Salva modifiche]**.

   Dopo il salvataggio, il servizio ID è impostato come strumento in Dynamic Tag Management. Tuttavia non è ancora pronto all&#39;uso. Lo strumento Dynamic Tag Management deve ancora essere sottoposto al processo di pubblicazione e approvazione di Dynamic Tag Management e potrebbe essere necessario configurare altri parametri. Per informazioni sul processo di approvazione di Dynamic Tag Management, guarda il video [User Basics Jump Start](https://marketing.adobe.com/resources/help/en_US/dtm/user-basics-jump-start.html). Per informazioni sugli altri parametri che puoi aggiungere a Dynamic Tag Management, vedi [Impostazioni servizio identità piattaforma Experience per DTM](../implementation-guides/standard.md#concept-fb6cb6a0e6cc4f10b92371f8671f6b59).

>[!MORE_LIKE_THIS]
>
>* [Proprietà Web](https://marketing.adobe.com/resources/help/en_US/dtm/web_property.html)


## Experience Platform Identity Service Settings for DTM {#concept-fb6cb6a0e6cc4f10b92371f8671f6b59}

Descrive i campi [!DNL Organization ID], [!DNL General] e [!DNL Customer Settings] e come vengono usati dal servizio ID [!DNL Experience Cloud].

<!--
mcvid-dtm-settings.xml
-->

## Dove si trovano queste impostazioni? {#section-c5b2d1c928944ae2b8565c1b182fe575}

Queste impostazioni diventano disponibili dopo che il servizio ID è stato aggiunto e salvato come strumenti in Dynamic Tag Management. Puoi anche accedere a queste impostazioni facendo clic sull&#39;icona dell&#39;ingranaggio nella sezione [!DNL Installed Tools] della proprietà Web di Dynamic Tag Management.

![](assets/installedTools.png)

## ID organizzazione {#section-949b5a0d8af940558b04ff675cf53f77}

Questo ID è richiesto da e associato alla società con provisioning [!DNL Experience Cloud]. Per organizzazione si intende l&#39;entità che consente all&#39;amministratore di configurare gruppi e utenti e di controllare l&#39;accesso single sign-on in [!DNL Experience Cloud]. L&#39;ID organizzazione è una stringa alfanumerica composta da 24 caratteri, seguita da (e deve includere) @AdobeOrg. Gli amministratori di [!DNL Experience Cloud] possono trovare questo ID in [Experience Cloud &gt; Strumenti](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html).

![](assets/orgID.png)

See also [Cookies and the Experience Platform Identity Service](../introduction/cookies.md).

## Impostazioni generali {#section-071d358e40f84629a8901b893dd61392}

Queste impostazioni consentono di specificare i server di tracciamento, le versioni del codice e altre variabili.

![](assets/generalSettings.png)

Nella seguente tabella sono elencate e definite le impostazioni [!DNL General].

**Richiedi automaticamente ID visitatore**

When checked, dynamic tag management to automatically calls the `getMarketingCloudVisitorID()` method before loading any of the Adobe solutions that use the Experience Platform Identity Service.

Consulta [getMarketingCloudVisitorID](../library/get-set/getmcvid.md).

**Server di tracciamento Analytics**

Nome del server di tracciamento usato per la raccolta di dati Analytics. Si tratta del dominio in cui vengono scritti la richiesta di immagini e il cookie (esempio: [!DNL http://site.omtrdc.net]).

Se non conosci l&#39;URL del server di tracciamento, controlla i tuoi file `s_code.js` o `AppMeasurement.js`. Individua l&#39;URL impostato dalla `s.trackingServer` variabile.

Vedi [trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) e [Aggiunta corretta delle variabili trackingServer e trackingServerSecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

**Server di tracciamento protetto**

Nome del server di tracciamento protetto utilizzato per la raccolta dati Analytics. Si tratta del dominio in cui vengono scritti la richiesta di immagini e il cookie (esempio: [!DNL https://site.omtrdc.net]).

Se non conosci l&#39;URL del server di tracciamento, controlla i tuoi file `s_code.js` o `AppMeasurement.js`. Individua l&#39;URL impostato dalla `s.trackingServerSecure` variabile.

Vedi [trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) e [Aggiunta corretta delle variabili trackingServer e trackingServerSecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

**Server Experience Cloud**

Se l&#39;azienda utilizza la raccolta dati di prime parti (CNAME) per utilizzare cookie di prime parti in un contesto terze parti, specifica il server di tracciamento (esempio: [!DNL http://metrics.company.com]).

**Server Experience Cloud protetto**

Se l&#39;azienda utilizza la raccolta dati di prime parti (CNAME) per utilizzare cookie di prime parti in un contesto terze parti, specifica il server di tracciamento (esempio: [!DNL https://metrics.company.com]).

**Versione libreria**

Imposta la versione della libreria del codice del servizio ID (`VisitorAPI.js`) che desideri usare. Non puoi modificare queste opzioni di menu.

**Impostazioni**

Questi campi consentono di aggiungere [variabili di funzioni](../library/function-vars/function-vars.md) sotto forma di coppie chiave-valore. Fai clic su **[!UICONTROL Aggiungi]** per aggiungere una o più variabili all&#39;implementazione del servizio ID.

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

Opzioni che definiscono o identificano i visitatori in base al loro stato di autenticazione (connessi o disconnessi). Vedi [Impostazione degli ID cliente e degli stati di autenticazione](../reference/authenticated-state.md).

## Test and verify the Experience Platform Identity Service {#concept-644fdbef433b46ba9c0634ac95eaa680}

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

Utilizzando [Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) e il [proxy HTTP Charles](https://www.charlesproxy.com/) puoi determinare se il servizio ID è stato configurato in modo da funzionare correttamente con Analytics. Le informazioni di questa sezione si basano sui risultati restituiti da Adobe Debugger e Charles. Puoi anche usare un altro strumento o debugger di tua preferenza.

## Test con Adobe Debugger {#section-861365abc24b498e925b3837ea81d469}

L&#39;integrazione del servizio è configurata correttamente se vedi un identificatore [!DNL Experience Cloud ID] (MID) nella risposta di [!DNL Adobe] Debugger. See [Cookies and the Experience Platform Identity Service](../introduction/cookies.md) for more information about the MID.

To verify the status of the ID service with the [!DNL Adobe] [debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html):

1. Cancella i cookie del browser o apri una sessione browser anonima.
1. Carica la pagina di prova contenente il codice del servizio ID.
1. Apri [!DNL Adobe] Debugger.
1. Individua un identificatore MID nei risultati.

## I risultati di Adobe Debugger {#section-bd2caa6643d54d41a476d747b41e7e25}

L&#39;identificatore MID viene memorizzato in una coppia chiave-valore con sintassi: `MID= *`Experience Cloud ID`*`. Queste informazioni sono presentate nel modo seguente.

**Operazione riuscita**

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

**Richieste corrette per il servizio ID in Charles**

Il codice del servizio ID funziona correttamente se la funzione `Visitor.getInstance` effettua una chiamata JavaScript a `dpm.demdex.net`. Una richiesta corretta include il tuo [ID organizzazione](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). L&#39;ID organizzazione viene passato sotto forma di coppia chiave-valore con sintassi: `d_orgid= *`ID organizzazione`*`. Cerca il `dpm.demdex.net` e la chiamata JavaScript nella scheda [!DNL Structure]. Cerca l&#39;ID organizzazione nella scheda [!DNL Request].

![](assets/charles_request.png)

**Risposte corrette per il servizio ID in Charles**

Il provisioning del tuo account per il servizio ID è corretto se la risposta dai [Data Collection Servers](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) restituisce un valore MID. L&#39;identificatore MID viene restituito come una coppia chiave-valore con sintassi: `d_mid: *`Experience Cloud ID visitatore`*`. Cerca l&#39;identificatore MID nella scheda [!DNL Response], come illustrato di seguito.

![](assets/charles_response_success.png)

**Risposte errate per il servizio ID in Charles**

Il provisioning del tuo account per il servizio ID non è corretto se la risposta DCS non contiene l&#39;identificatore MID. Una risposta errata restituisce un codice di errore e un messaggio nella scheda [!DNL Response], come illustrato di seguito. Se ricevi questo messaggio di errore nella risposta DCS, contatta l&#39;assistenza clienti.

![](assets/charles_response_unsuccessful.png)

Per informazioni sui codici di errore, vedi [Codici di errore, messaggi ed esempi DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html).
