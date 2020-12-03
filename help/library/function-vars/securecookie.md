---
description: Flag booleano facoltativo che aggiunge un attributo "Sicuro" al cookie AMCV.
keywords: ID Service
seo-description: Flag booleano facoltativo che aggiunge un attributo "Sicuro" al cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 100%

---


# secureCookie{#securecookie}

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

