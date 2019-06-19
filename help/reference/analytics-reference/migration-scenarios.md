---
description: Comprende esempi di configurazione del server e i passaggi necessari per la migrazione.
keywords: Servizio ID
seo-description: Comprende esempi di configurazione del server e i passaggi necessari per la migrazione.
seo-title: Scenari di migrazione al servizio Experience Platform Identity
title: Scenari di migrazione al servizio Experience Platform Identity
uuid: 9 e 229045-6508-48 c 4-ae 39-9537 b 4941853
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Scenari di migrazione al servizio Experience Platform Identity {#experience-cloud-id-service-migration-scenarios}

Comprende esempi di configurazione del server e i passaggi necessari per la migrazione.

## Proprietà Web singola {#section-6ccfea84628d46c99507cb124e7f5445}

* **Cliente**: Società di esempio S.p.a.
* **Experience Cloud abilitato**: No
* **Proprietà Web**: esempio.com
* **Server di raccolta dati**: metriche.esempio.com, smetriche.esempio.com
* **File JavaScript di Analytics**: un unico file per tutte le pagine del sito

Per prima cosa, il cliente deve essere abilitato per Experience Cloud (vedi [requisiti](../../reference/requirements.md)). Poiché dispone di un unico file JavaScript, il cliente non ha bisogno di un periodo di tolleranza. Il cliente configurerà anche la migrazione dei visitatori, quindi effettuerà la migrazione dal proprio CNAME di raccolta dati, non più necessario.

## Più file JavaScript, tag immagine hardcoded {#section-a665f6ee202940449198e4e7a5dcac54}

* **Cliente**: Altro esempio S.p.a.
* **Experience Cloud abilitato**: sì
* **Proprietà Web**: altroesempio.com
* **Server di raccolta dati**: altroesempio.112.2o7.net
* **File JavaScript di Analytics**: più file JavaScript. Un file per il sito principale e un altro file per la sezione dell&#39;assistenza, gestita in un CMS separato.
* **Altri metodi di raccolta dati**: tag immagine hardcoded in una sezione del sito

Per prima cosa, il cliente deve trovare il proprio ID organizzazione di Adobe Experience Cloud (vedi [requisiti](../../reference/requirements.md)). In seguito, deve configurare un periodo di tolleranza per la migrazione perché utilizza più file JavaScript. Il cliente conterrà anche la migrazione dei visitatori e quindi `*.2o7.net``*.sc.omtrdc.net`la migrazione.

Quando il cliente effettua l&#39;aggiornamento al codice JavaScript di Analytics più recente per prepararsi ad eseguire il rollout del servizio [!DNL Experience Cloud] ID, aggiorna anche tutti i tag immagine hardcoded per l&#39;uso di JavaScript.

## Più proprietà Web, più file JavaScript e un lettore video basato su Flash {#section-34647995ff3740b999fdee22d885e515}

* **Cliente**: Un buon cliente LLC
* **Experience Cloud abilitato**: sì
* **Proprietà Web**: miositoprincipale.com, mioaltrositoA.com, mioaltrositoB.com
* **Server di raccolta dati**: metriche.miositoprincipale.com, smetriche.miositoprincipale.com
* **File JavaScript di Analytics**: più file JavaScript. Un file per ciascuna proprietà Web.
* **Altri metodi di raccolta dati**: un lettore video basato su Flash

Per prima cosa, il cliente deve trovare il proprio ID organizzazione di Adobe Experience Cloud (vedi [requisiti](../../reference/requirements.md)). In seguito, deve configurare un periodo di tolleranza per la migrazione perché utilizza più file JavaScript. Il cliente monitora i visitatori tra il dominio principale e i sottodomini, pertanto continua a usare i propri CNAME di raccolta dati con il servizio ID visitatore.

Quando il cliente effettua l&#39;aggiornamento al codice JavaScript di Analytics più recente per prepararsi ad eseguire il rollout del servizio [!DNL Experience Cloud] ID, aggiorna anche il lettore video basato su Flash alla versione più recente di AppMeasurement per Flash.