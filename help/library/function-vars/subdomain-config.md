---
description: Modifica il nome di dominio predefinito usato dalle chiamate al servizio Experience Cloud Identity con il nome del tuo sottodominio con queste configurazioni.
keywords: Servizio ID
title: audienceManagerServer e audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '218'
ht-degree: 100%

---

# audienceManagerServer e audienceManagerServerSecure {#audiencemanagerserver-and-audiencemanagerserversecure}

Modifica il nome di dominio predefinito usato dalle chiamate al servizio Experience Cloud Identity con il nome del tuo sottodominio con queste configurazioni.

**Sintassi:**

* ` audienceManagerServer: " *`il nome del sottodominio`*.demdex.net"`
* ` audienceManagerServerSecure: " *`il nome del sottodominio`*.demdex.net"`

**Finalità**

Normalmente, il servizio [!DNL Experience Cloud] ID effettua chiamate ad [!DNL Adobe] a `dpm.demdex.net`. Talvolta potresti non voler effettuare chiamate a questa destinazione perché troppo generica o &quot;di terza parte&quot;. Affinché la chiamata al servizio ID sembri più una chiamata di prima parte, usa queste configurazioni per aggiungere il nome del [!DNL Audience Manager] sottodominio a `demdex.net` come mostrato di seguito. Per ulteriori informazioni sulla chiamata `dpm.demdex.net`, vedi [Informazioni sulle chiamate al dominio Demdex](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=it).

**Requisiti**

Per queste configurazioni è necessario usare:

* Il nome del [!DNL Audience Manager] sottodominio registrati della tua azienda. Verifica o ottieni questo nome dal tuo consulente.
* Il nome del sottodominio associato al tuo [!UICONTROL ID organizzazione].
* *Entrambi* i parametri di configurazione con lo stesso nome di sottodominio.

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
