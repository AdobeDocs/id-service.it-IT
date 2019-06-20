---
description: Il  Children’s Online Privacy Protection Act  (COPPA) proibisce la raccolta online di dati personali di bambini di età inferiore ai 13 anni senza disporre del consenso verificabile dei genitori. I clienti interessati dal COPPA possono aggiungere una variabile opzionale al codice del servizio Experience Cloud ID che impedisce l'impostazione di cookie nel dominio di un browser di terze parti.
keywords: Servizio ID
seo-description: Il  Children’s Online Privacy Protection Act  (COPPA) proibisce la raccolta online di dati personali di bambini di età inferiore ai 13 anni senza disporre del consenso verificabile dei genitori. I clienti interessati dal COPPA possono aggiungere una variabile opzionale al codice del servizio Experience Cloud ID che impedisce l'impostazione di cookie nel dominio di un browser di terze parti.
seo-title: Supporto per COPPA nel servizio Experience Cloud ID
title: Supporto per COPPA nel servizio Experience Cloud ID
uuid: 621 b 5 ebd -92 e 7-4635-be 85-8 d 7 e 36589 fcb
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Supporto per COPPA nel servizio Experience Cloud ID {#coppa-support-in-the-experience-cloud-id-service}

Il  Children’s Online Privacy Protection Act  (COPPA) proibisce la raccolta online di dati personali di bambini di età inferiore ai 13 anni senza disporre del consenso verificabile dei genitori. I clienti interessati dal COPPA possono aggiungere una variabile opzionale al codice del servizio Experience Cloud ID che impedisce l&#39;impostazione di cookie nel dominio di un browser di terze parti.

>[!NOTE]
>
>Per le versioni a partire dalla 1.5.3.

**Cookie e monitoraggio**

Quando viene caricata una pagina Web, il servizio [!DNL Experience Cloud] ID effettua una chiamata a un server di raccolta dati (DCS) [!DNL Adobe]. La risposta del DCS include un cookie Experience Cloud e un cookie demdex.net.

* Il cookie Experience Cloud è impostato nel dominio di prime parti. Non può essere usato per il monitoraggio dei visitatori nei diversi domini, a meno che tali domini non collaborino per consentire l&#39;accesso.
* Il cookie demdex.net è impostato nel dominio di terze parti. Contiene un identificatore univoco che può essere utilizzato per il monitoraggio dei visitatori nei diversi domini.

**Cookie e conformità COPPA**

I cookie di terze parti che eseguono il monitoraggio dei visitatori tra i diversi domini nei siti Web destinati principalmente ai bambini, attivano i requisiti del consenso dei genitori per il COPPA. Per assicurare più facilmente la conformità con il COPPA per l&#39;analisi interna dei siti Web, aggiungi la variabile `disableThirdPartyCookies:true` alla funzione `Visitor.getInstance` come mostrato di seguito.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Quando viene impostato su `true`, l&#39;oggetto `disableThirdPartyCookies` impedisce al DCS di restituire il cookie demdex.net di terze parti. Se il visitatore del sito dispone già del cookie nel proprio browser, il servizio ID non lo utilizza per creare un nuovo [!DNL Experience Cloud] ID o per restituire un ID esistente. Il servizio [!DNL Experience Cloud] ID crea un nuovo ID casuale nel cookie di prime parti. Una volta attivato, è possibile raccogliere i dati con il servizio ID e condividerlo tra diverse soluzioni [!DNL Experience Cloud], comprese le altre operazioni interne consentite dal COPPA.

>[!MORE_ LIKE_ THIS]
>
>* [Centro per la privacy Adobe](http://www.adobe.com/privacy.html)
>* [Cos&#39;è il COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

