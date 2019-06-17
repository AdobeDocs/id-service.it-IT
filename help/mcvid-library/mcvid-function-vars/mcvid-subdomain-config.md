---
description: Modifica il nome di dominio predefinito usato dalle chiamate al servizio Experience Cloud ID con il nome del tuo sottodominio con queste configurazioni.
keywords: Servizio ID
seo-description: Modifica il nome di dominio predefinito usato dalle chiamate al servizio Experience Cloud ID con il nome del tuo sottodominio con queste configurazioni.
seo-title: audienceManagerServer e audienceManagerServerSecure
title: audienceManagerServer e audienceManagerServerSecure
uuid: e 21 cacbf -5151-4 d 34-b 0 f 7-9 e 90275 f 4 c 7 c
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# audienceManagerServer e audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Modifica il nome di dominio predefinito usato dalle chiamate al servizio Experience Cloud ID con il nome del tuo sottodominio con queste configurazioni.

**Sintassi:**

* ` audienceManagerServer: " *`il nome del sottodominio`*.demdex.net"`
* ` audienceManagerServerSecure: " *`il nome del sottodominio`*.demdex.net"`

**Finalità**

Normalmente, il servizio [!DNL Experience Cloud] ID effettua chiamate [!DNL Adobe] a `dpm.demdex.net`. Talvolta potresti non voler effettuare chiamate a questa destinazione perché troppo generica o &quot;di terza parte&quot;. Affinché la chiamata al servizio ID sembri più una chiamata di prima parte, usa queste configurazioni per aggiungere il nome del sottodominio [!DNL Audience Manager] a `demdex.net` come mostrato di seguito. Per maggiori informazioni sulla chiamata `dpm.demdex.net`, vedi [Informazioni sulle chiamate al dominio Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

**Requisiti**

Queste configurazioni richiedono di usare:

* Nome [!DNL Audience Manager] del sottodominio del record della società. Verifica o ottieni questo nome dal tuo consulente.
* Il nome del sottodominio associato al tuo [!DNL Organization ID].
* *Entrambi* i parametri di configurazione con lo stesso nome del sottodominio.

**Esempio di codice**

In questo esempio, supponiamo di avere una società di servizi di intrattenimento media che ha espresso dubbi di natura legale nell&#39;effettuazione delle chiamate a `dpm.demdex.net`. In [!DNL Audience Manager], il nome del sottodominio della società è Musica1. L&#39;esempio di codice seguente dimostra come dotare di un marchio la chiamata dati al servizio ID con il nome del sottodominio specifico del cliente.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

