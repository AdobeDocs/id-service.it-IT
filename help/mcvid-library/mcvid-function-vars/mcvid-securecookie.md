---
description: Flag booleano facoltativo che aggiunge un attributo "Sicuro" al cookie AMCV.
keywords: Servizio ID
seo-description: Flag booleano facoltativo che aggiunge un attributo "Sicuro" al cookie AMCV.
seo-title: secureCookie
title: secureCookie
uuid: 995 d 19 f 6-9 c 9 d -4493-9 c 9 c -545 b 0 b 5696 b 0
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# secureCookie{#securecookie}

Flag booleano facoltativo che aggiunge un attributo &quot;Sicuro&quot; al cookie AMCV.

Questo attributo di configurazione è disponibile nella versione 3.3.0 di `visitorAPI`.

>[!NOTE]
>
>La `SecureCookie` configurazione non funziona su domini non protetti e potrebbe comportare la mancata ricezione dei valori MID per le visite che utilizzano un protocollo non protetto. La configurazione `secureCookie` deve essere impostata su `true` solo quando si è sicuri che tutte le pagine e i sottodomini usano sempre un protocollo sicuro.

**Sintassi:**`secureCookie: true | false` (predefinito)

**Esempio di codice**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

