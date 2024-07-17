---
description: Comprende esempi di configurazione del server e i passaggi necessari per la migrazione.
keywords: Servizio ID
title: Scenari di migrazione a Experience Cloud Identity Service
exl-id: 419532bf-399f-4646-a95f-31c35535d6fc
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 85%

---

# Scenari di migrazione a Experience Cloud Identity Service {#experience-cloud-id-service-migration-scenarios}

Comprende esempi di configurazione del server e i passaggi necessari per la migrazione.

## Proprietà Web singola {#section-6ccfea84628d46c99507cb124e7f5445}

* **Cliente**: Società di esempio S.p.a.
* **Experience Cloud abilitato**: No
* **Proprietà web**: esempio.com
* **Server di raccolta dati**: metriche.esempio.com, smetriche.esempio.com
* **File JavaScript di Analytics**: un singolo file per tutte le pagine del sito

Per prima cosa, il cliente deve essere abilitato per l&#39;Experience Cloud (vedi [requisiti](../../reference/requirements.md)). Inoltre, dato che dispongono di un singolo file JavaScript, questo cliente non ha bisogno di un periodo di tolleranza. Il cliente deve anche configurare la migrazione dei visitatori e quindi effettuare la migrazione dal proprio CNAME di raccolta dati, che non è più necessario.

## Più file JavaScript, tag immagine hardcoded {#section-a665f6ee202940449198e4e7a5dcac54}

* **Cliente**: Altro esempio S.p.a.
* **Experience Cloud abilitato**: sì
* **Proprietà web**: altroesempio.com
* **Server di raccolta dati**: altroesempio.112.2o7.net
* **File JavaScript di Analytics**: più file JavaScript. Un file per il sito principale, un altro file per la sezione di assistenza gestita in un altro CMS.
* **Altri metodi di raccolta dati**: tag immagine hardcoded in una sezione del sito

Innanzitutto, il cliente deve trovare il proprio ID organizzazione Adobe Experience Cloud (vedi [requisiti](../../reference/requirements.md)). In seguito, deve configurare un periodo di tolleranza per la migrazione perché utilizza più file JavaScript. Il cliente deve anche configurare la migrazione dei visitatori e quindi effettuare la migrazione da `*.2o7.net` a `*.sc.omtrdc.net`.

Quando il cliente effettua l&#39;aggiornamento al codice JavaScript di Analytics più recente per prepararsi ad eseguire il rollout del servizio [!DNL Experience Cloud] ID, aggiorna anche tutti i tag immagine hardcoded per l&#39;uso di JavaScript.

## Più proprietà Web, più file JavaScript e un lettore video basato su Flash {#section-34647995ff3740b999fdee22d885e515}

* **Cliente**: Un buon cliente LLC
* **Experience Cloud abilitato**: sì
* **Proprietà web**: miositoprincipale.com, mioaltrositoA.com, mioaltrositoB.com
* **Server di raccolta dati**: metriche.miositoprincipale.com, smetriche.miositoprincipale.com
* **File JavaScript di Analytics**: più file JavaScript. Un file per ogni proprietà web.
* **Altri metodi di raccolta dati**: lettore video basato su Flash

Innanzitutto, il cliente deve trovare il proprio ID organizzazione Adobe Experience Cloud (vedi [requisiti](../../reference/requirements.md)). In seguito, deve configurare un periodo di tolleranza per la migrazione perché utilizza più file JavaScript. Questo cliente tiene traccia dei visitatori tra il suo dominio primario e i suoi sottodomini, quindi continuerà a utilizzare il proprio CNAME di raccolta dati con il servizio ID visitatore.

Quando il cliente effettua l&#39;aggiornamento al codice JavaScript di Analytics più recente per prepararsi ad eseguire il rollout del servizio [!DNL Experience Cloud] ID, aggiorna anche il lettore video basato su Flash alla versione più recente di AppMeasurement per Flash.
