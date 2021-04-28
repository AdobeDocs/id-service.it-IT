---
description: Flag booleano facoltativo che aggiunge un attributo "Sicuro" al cookie AMCV.
keywords: Servizio ID
seo-description: Flag booleano facoltativo che aggiunge un attributo "Sicuro" al cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '105'
ht-degree: 100%

---

# secureCookie {#securecookie}

Flag booleano facoltativo che aggiunge un attributo &quot;Sicuro&quot; al cookie AMCV.

Questo attributo di configurazione è disponibile nella `visitorAPI`versione 3.3.0 di.

>[!NOTE]
>
>La `SecureCookie` configurazione non funzionerà sui domini non sicuri e potrebbe comportare la mancata ricezione dei valori MID per le visite che usano un protocollo non sicuro. La `secureCookie` configurazione deve essere impostata su `true` solo quando si è sicuri che tutte le pagine e i sottodomini usano sempre un protocollo sicuro.

**Sintassi:** `secureCookie: true | false` (predefinito)

**Esempio di codice**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```
