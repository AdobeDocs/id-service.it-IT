---
description: Se disponi di più file JavaScript che inviano dati alla stessa suite di rapporti o se utilizzi altre tecnologie sul tuo sito, ad esempio la misurazione video Flash, ti consigliamo di impostare un periodo di tolleranza.
keywords: Servizio ID
title: Periodo di tolleranza per il servizio ID
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Periodo di tolleranza per il servizio ID {#the-id-service-grace-period}

Se disponi di più file JavaScript che inviano dati alla stessa suite di rapporti o se utilizzi altre tecnologie sul tuo sito, ad esempio la misurazione video Flash, ti consigliamo di impostare un periodo di tolleranza.

Dopo aver distribuito il servizio [!DNL Experience Cloud] ID, i nuovi visitatori non ricevono più l&#39;ID visitatore di Analytics dal server di raccolta dati. Se il servizio [!DNL Experience Cloud] ID non è stato ancora implementato nelle sezioni del sito, quando i visitatori accedono a tali sezioni, l&#39;Experience Cloud ID non viene riconosciuto e ai visitatori viene assegnato un ID visitatore Analytics legacy. Questo può creare conteggi di visite duplicati e attribuzione errata.

Ad esempio, se la sezione di assistenza del sito viene gestita in un CMS separato, dovresti avere un file JavaScript di Analytics separato per tale sezione. Se distribuisci l’ID visitatore sul sito principale prima di distribuire il servizio ID visitatore al sito di assistenza, al momento della visita della sezione di assistenza i nuovi visitatori riceveranno un ID legacy di Analytics e le visite che si estendono a entrambe le sezioni saranno quindi riportate come visite diverse.

Se si distribuisce il servizio [!DNL Experience Cloud] ID in siti che utilizzano più file JavaScript o altre tecnologie (come Flash), possono verificarsi problemi di coordinazione, perché è necessario attivare il servizio ID su tutte le porzioni del sito contemporaneamente. Configurando un periodo di tolleranza, i nuovi visitatori continuano a ricevere un ID visitatore di Analytics dal servizio [!DNL Experience Cloud] ID, in modo da essere identificati correttamente nelle sezioni del sito che non sono state aggiornate per l&#39;uso del servizio ID.

>[!NOTE]
>
>Per il periodo di tolleranza è necessaria la versione 1.3, o una versione successiva, del servizio [!DNL Experience Cloud] ID.

## Ho bisogno di un periodo di tolleranza? {#section-fd34c7ff697348a39f49258b7d39eb42}

Se disponi di un singolo file JavaScript di Analytics e non utilizzi altre librerie AppMeasurement, non è necessario un periodo di tolleranza. Puoi effettuare l&#39;aggiornamento nel file JavaScript, i nuovi visitatori verranno identificati in modo corretto utilizzando il Experience Cloud ID durante l&#39;accesso.

Se disponi di più file JavaScript che inviano dati alla *stessa suite di rapporti* o se utilizzi altre tecnologie sul tuo sito, ad esempio la misurazione video Flash, ti consigliamo di impostare un periodo di tolleranza.

## Come posso attivare un periodo di tolleranza?   {#section-512d5cd8570e483cbdd8b04457a16ced}

Contatta l’[Assistenza clienti](https://helpx.adobe.com/it/marketing-cloud/contact-support.html).
