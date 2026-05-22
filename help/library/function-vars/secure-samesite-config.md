---
description: Configurazione all’interno di ECID che può essere utilizzata per supportare i cookie AMCV sulle pagine Google AMP.
keywords: Servizio ID
title: Configurazioni Secure e SameSite
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 156
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

