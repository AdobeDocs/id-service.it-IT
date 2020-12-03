---
description: Dopo aver abilitato l'oggetto Opt-in sul sito Web, usa i metodi di convalida per verificare che il servizio funzioni come previsto usando gli strumenti per sviluppatori nel browser.
seo-description: Dopo aver abilitato l'oggetto Opt-in sul sito Web, usa i metodi di convalida per verificare che il servizio funzioni come previsto usando gli strumenti per sviluppatori nel browser.
seo-title: Convalida del servizio Opt-in
title: Convalida del servizio Opt-in
uuid: 1743360a-d757-4e50-8697-0fa92b302cbc
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 40%

---


# Convalida del servizio Opt-in{#validating-opt-in-service}

Dopo aver abilitato l&#39;oggetto Opt-in sul sito Web, usa i metodi di convalida per verificare che il servizio funzioni come previsto usando gli strumenti per sviluppatori nel browser.

## Caso d&#39;uso 1: abilitare Opt-in {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

Prima di caricare la pagina, cancellare la cache e i cookie.

In Chrome fai clic con il pulsante destro del mouse sulla pagina Web e seleziona Controlla. Come nella schermata precedente, selezionate la scheda *Rete* per visualizzare le richieste effettuate dal browser.

Nell&#39;esempio precedente, sulla pagina sono installati i seguenti tag JS  Adobe: ECID, AAM, Analytics e Target.

**Come verificare che Opt-in funzioni come previsto:**

Non devono essere visualizzate richieste  server di Adobe:

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>È possibile che venga visualizzata una chiamata a `http://dpm.demdex.net/optOutStatus`; si tratta di un endpoint di SOLA LETTURA usato per recuperare lo stato di Opt-out del visitatore. Questo endpoint non comporterà la creazione di cookie di terze parti e non raccoglierà informazioni dalla pagina.

Non dovrebbero essere visualizzati cookie creati dai tag del Adobe : (AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)

In Chrome, andate alla scheda *Applicazione* , espandete la sezione *Cookies* in *Storage*, quindi selezionate il nome di dominio del sito Web:

![](assets/use_case_1_2.png)

## Caso d&#39;uso 2: abilitare Opt-in e l&#39;archiviazione  {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

L&#39;unica differenza nel caso d&#39;uso 2 è che verrà visualizzato *un nuovo cookie* che conterrà le autorizzazioni Opt-in fornite dal visitatore: **adobeujs-optin**

## Caso d&#39;uso 3: abilitare Opt-in e preapprovare Adobe Analytics  {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Poiché  Adobe Analytics è già stato approvato, nella scheda Rete verranno visualizzate le richieste sul server di tracciamento:

![](assets/use_case_3_1.png)

e vedrai i cookie di Analytics nella scheda Applicazione:

![](assets/use_case_3_2.png)

## Caso d&#39;uso 4: abilitare Opt-in e IAB  {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**Come visualizzare il consenso IAB corrente sulla pagina:**

Apri gli strumenti per sviluppatori e seleziona la scheda *Console*. Incollate il frammento di codice seguente e premete Invio:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

Di seguito è riportato un output di esempio con l&#39;approvazione delle finalità 1, 2 e 5 e l&#39;ID fornitore del Audience Manager  è approvato:

* demdex.net/id: La presenza di questa chiamata dimostra che ECID ha richiesto un ID da demdex.net
* demdex.net/event: La presenza di questa chiamata dimostra che la chiamata di raccolta dati DIL funziona come previsto.
* demdex.net/dest5.html: La presenza di questa chiamata dimostra che le sincronizzazioni ID vengono attivate.

![](assets/use_case_4_1.png)

Se uno dei seguenti elementi non è valido, non verranno visualizzate richieste ai server di  Adobe né cookie  Adobe:

* Le finalità 1, 2 O 5 non sono approvate.
* L&#39;ID fornitore del Audience Manager  non è approvato.