---
description: Il Children’s Online Privacy Protection Act (COPPA) proibisce la raccolta online di dati personali di bambini di età inferiore ai 13 anni senza disporre del consenso verificabile dei genitori. I clienti interessati dal COPPA possono aggiungere una variabile opzionale al codice del servizio Experience Cloud Identity che impedisce l’impostazione di cookie nel dominio di un browser di terze parti.
keywords: Servizio ID
seo-description: Il Children’s Online Privacy Protection Act (COPPA) proibisce la raccolta online di dati personali di bambini di età inferiore ai 13 anni senza disporre del consenso verificabile dei genitori. I clienti interessati dal COPPA possono aggiungere una variabile opzionale al codice del servizio Experience Cloud Identity che impedisce l’impostazione di cookie nel dominio di un browser di terze parti.
seo-title: Supporto per COPPA nel servizio Experience Cloud Identity
title: Supporto per COPPA nel servizio Experience Cloud Identity
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: ht
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2

---


# Supporto per COPPA nel servizio Experience Cloud Identity {#coppa-support-in-the-experience-cloud-id-service}

Il Children’s Online Privacy Protection Act (COPPA) proibisce la raccolta online di dati personali di bambini di età inferiore ai 13 anni senza disporre del consenso verificabile dei genitori. I clienti interessati dal COPPA possono aggiungere una variabile opzionale al codice del servizio Experience Cloud Identity che impedisce l’impostazione di cookie nel dominio di un browser di terze parti.

>[!NOTE]
>
>Per le versioni a partire dalla 3.0.0.

**Cookie e monitoraggio**

Quando viene caricata una pagina Web, il servizio [!DNL Experience Cloud] ID effettua una chiamata a un server di raccolta dati (DCS) [!DNL Adobe]. La risposta del DCS include un cookie Experience Cloud e un cookie demdex.net.

* Il cookie Experience Cloud è impostato nel dominio di prime parti. Non può essere usato per il monitoraggio dei visitatori nei diversi domini, a meno che tali domini non collaborino per consentire l'accesso.
* Il cookie demdex.net è impostato nel dominio di terze parti. Contiene un identificatore univoco che può essere utilizzato per il monitoraggio dei visitatori nei diversi domini.

**Cookie e conformità COPPA**

I cookie di terze parti che eseguono il monitoraggio dei visitatori tra i diversi domini nei siti Web destinati principalmente ai bambini, attivano i requisiti del consenso dei genitori per il COPPA. Per assicurare più facilmente la conformità con il COPPA per l'analisi interna dei siti Web, aggiungi la variabile `disableThirdPartyCookies:true` alla `Visitor.getInstance` funzione come mostrato di seguito.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Quando viene impostato su `true`, `disableThirdPartyCookies` l'oggetto impedisce al DCS di restituire il cookie demdex.net di terze parti. Se il visitatore del sito dispone già del cookie nel proprio browser, il servizio ID non lo utilizza per creare un nuovo [!DNL Experience Cloud] ID o per restituire un ID esistente. Il servizio [!DNL Experience Cloud] ID crea un nuovo ID casuale nel cookie di prime parti. Una volta attivato, è possibile raccogliere i dati con il servizio ID e condividerlo tra diverse [!DNL Experience Cloud] soluzioni, comprese le altre operazioni interne consentite dal COPPA.

>[!MORE_LIKE_THIS]
>
>* [ Centro per la privacy Adobe](http://www.adobe.com/it/privacy.html)
>* [Cos'è il COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

