---
description: Configurazione all’interno di ECID che può essere utilizzata per supportare i cookie AMCV sulle pagine Google AMP.
keywords: Servizio ID
title: Configurazioni Secure e SameSite
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 100%

---

# Configurazioni Secure e SameSite

Questa configurazione consente di modificare le impostazioni per i cookie e supportare i [cookie AMCV](../../introduction/cookies.md) sulle pagine Google AMP.

Il servizio ID visitatore di Adobe imposta i cookie ECID con l’impostazione predefinita del browser `SameSite = Lax`, che è inaccessibile se la pagina viene caricata in un iframe come una pagina AMP di Google. Per accedere ai cookie ECID, utilizza le seguenti configurazioni per aggiornare l’impostazione SameSite a `SameSite = None`.

>[!NOTE]
>
>Quando si applica `SameSite = None`, i cookie devono essere impostati su `Secure`, in modo che i dati possano essere trasmessi solo tramite connessioni HTTPS.

**Implementazione**:

Se utilizzi Adobe Experience Platform Launch, aggiorna l’estensione Experience Cloud ID alla versione 5.1.0 e configura `secureCookie: true` e `sameSiteCookie: none`.

Se non utilizzi Experience Platform Launch, esegui l’aggiornamento alla nuova libreria Visitor 5.1.0 e segui le configurazioni riportate di seguito, durante l’inizializzazione dell’istanza Visitor:

**Esempio di codice**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
