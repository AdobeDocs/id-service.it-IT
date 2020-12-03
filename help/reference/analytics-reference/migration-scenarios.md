---
description: Comprende esempi di configurazione del server e i passaggi necessari per la migrazione.
keywords: ID Service
seo-description: Comprende esempi di configurazione del server e i passaggi necessari per la migrazione.
seo-title: Scenari di migrazione al servizio Experience Cloud Identity
title: Scenari di migrazione al servizio Experience Cloud Identity
uuid: 9e229045-6508-48c4-ae39-9537b4941853
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 57%

---


# Scenari di migrazione al servizio Experience Cloud Identity {#experience-cloud-id-service-migration-scenarios}

Comprende esempi di configurazione del server e i passaggi necessari per la migrazione.

## Proprietà Web singola {#section-6ccfea84628d46c99507cb124e7f5445}

* **Cliente**: Società di esempio S.p.a.
* **Experience Cloud abilitato**: No
* **Proprietà** Web: example.com
* **Server** di raccolta dati: metriche.esempio.com, smetriche.esempio.com
* **File** JavaScript di Analytics: Un singolo file per tutte le pagine del sito

Per prima cosa, il cliente deve essere abilitato per Experience Cloud (vedi [requisiti](../../reference/requirements.md)). Poiché il cliente dispone di un singolo file JavaScript, non ha bisogno di un periodo di tolleranza. Questo cliente configurerà anche la migrazione dei visitatori e quindi effettuerà la migrazione dal CNAME di raccolta dati, operazione non necessaria.

## Più file JavaScript, tag immagine hardcoded {#section-a665f6ee202940449198e4e7a5dcac54}

* **Cliente**: Altro esempio S.p.a.
* **Experience Cloud abilitato**: Yes
* **Proprietà** Web: altroesempio.com
* **Server** di raccolta dati: altroesempio.112.2o7.net
* **File** JavaScript di Analytics: Più file JavaScript. Un file per il sito principale, un altro file per la sezione di supporto gestita in un CMS separato.
* **Altri metodi** di raccolta dati: Tag immagine hardcoded su una sezione del sito

Per prima cosa, il cliente deve trovare il proprio ID organizzazione di Adobe Experience Cloud (vedi [requisiti](../../reference/requirements.md)). In seguito, deve configurare un periodo di tolleranza per la migrazione perché utilizza più file JavaScript. Il cliente deve anche configurare la migrazione dei visitatori e quindi effettuare la migrazione da `*.2o7.net` a `*.sc.omtrdc.net`.

Quando il cliente effettua l&#39;aggiornamento al codice JavaScript di Analytics più recente per prepararsi ad eseguire il rollout del servizio [!DNL Experience Cloud] ID, aggiorna anche tutti i tag immagine hardcoded per l&#39;uso di JavaScript.

## Più proprietà Web, più file JavaScript e un lettore video basato su Flash {#section-34647995ff3740b999fdee22d885e515}

* **Cliente**: Un buon cliente LLC
* **Experience Cloud abilitato**: Yes
* **Proprietà** Web: miositoprincipale.com, mioaltrositoA.com, mioaltrositoB.com
* **Server** di raccolta dati: metriche.miositoprincipale.com, smetriche.miositoprincipale.com
* **File** JavaScript di Analytics: Più file JavaScript. Un file per ciascuna proprietà Web.
* **Altri metodi** di raccolta dati: Un lettore video basato su Flash

Per prima cosa, il cliente deve trovare il proprio ID organizzazione di Adobe Experience Cloud (vedi [requisiti](../../reference/requirements.md)). In seguito, deve configurare un periodo di tolleranza per la migrazione perché utilizza più file JavaScript. Il cliente monitora i visitatori tra il dominio principale e i sottodomini, pertanto continuerà a utilizzare il CNAME di raccolta dati con il servizio ID visitatore.

Quando il cliente effettua l&#39;aggiornamento al codice JavaScript di Analytics più recente per prepararsi ad eseguire il rollout del servizio [!DNL Experience Cloud] ID, aggiorna anche il lettore video basato su Flash alla versione più recente di AppMeasurement per Flash.
