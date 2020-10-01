---
title: Modifiche all'etichettatura di Google Chrome SameSite
seo-title: Modifiche all'etichettatura di Google Chrome SameSite
description: Documentazione della libreria Adobe ECID (servizio ID).
seo-description: Documentazione della libreria Adobe ECID (servizio ID).
translation-type: tm+mt
source-git-commit: f74a028532e95ab17f5d2e64697d69eb64e03391
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 4%

---


# Modifiche all&#39;etichettatura di Google Chrome SameSite {#google-chrome-samesite-labelling-changes}

L&#39;attributo SameSite indica ai browser quando e come attivare i cookie in scenari di prime e terze parti. L&#39;attributo SameSite può avere uno dei tre valori seguenti: `strict`, `lax`o `none`. Chrome, Firefox, Edge, Safari e Opera sono supportati `strict` e `lax` da novembre 2017, mentre `none` è stato introdotto nel 2018. Tuttavia, alcuni browser meno recenti non supportano questa impostazione.

Nel febbraio 2020, Google ha rilasciato Chrome 80 e ha modificato l&#39;impostazione predefinita da `none` a `lax` quando un cookie non ha un valore attributo SameSite specificato. Questa impostazione impedisce l&#39;utilizzo di un cookie in un contesto di terze parti, noto anche come &quot;cross-site&quot;. I cookie di terze parti che ne derivano devono essere impostati su `SameSite=none` e contrassegnati come sicuri.

I cookie senza un valore di attributo SameSite specificato verranno impostati come predefiniti su `lax`.

Per ulteriori informazioni sugli attributi SameSite, visitate il documento [standard](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) dei cookie.

## Valori attributo SameSite

| Valore attributo SameSite | Descrizioni |
| ------ | ------------ |
| `strict` | I cookie con questa impostazione vengono inviati solo se la pagina di provenienza e la pagina di destinazione fanno parte dello stesso dominio del cookie. |
| `lax` | I cookie con questa impostazione vengono inviati solo quando il dominio visualizzato nell’URL del browser corrisponde al dominio del cookie. Questa è la nuova impostazione predefinita per i cookie in Chrome. |
| `none` | I cookie con questa impostazione sono disponibili per l&#39;accesso esterno o di terze parti, ad esempio &quot;cross-site&quot;. Prima di questa modifica, `none` era l&#39;impostazione predefinita SameSite per i cookie, quindi l&#39;utilizzo di questa impostazione fa sì che un cookie si comporti in modo simile a quello che tradizionalmente ha funzionato. Google sta tuttavia richiedendo che qualsiasi cookie con questa impostazione specifichi ora il flag sicuro, il che significa che il cookie verrà creato e inviato solo con richieste tramite HTTPS. Tutti i cookie cross-site senza la bandiera protetta verranno rifiutati da Google. |

## Cosa devi sapere come cliente Adobe Experience Cloud

**Nessun aggiornamento JavaScript richiesto**

 prodotti di Adobe hanno già rilasciato aggiornamenti lato server per impostare cookie di terze parti con gli attributi appropriati. I nostri clienti non necessitano di aggiornamenti della libreria JavaScript.

**Verificare che gli endpoint di terze parti utilizzino HTTPS**

Tutti i clienti devono confermare che la propria configurazione JavaScript utilizza HTTPS per le chiamate ai servizi  Adobe. Target,  Audience Manager e il  Experience Cloud Identity Service (ECID) stanno reindirizzando le chiamate HTTP di terze parti ai rispettivi endpoint HTTPS, il che può aumentare la latenza. Ciò significa che non è necessario modificare la configurazione. I clienti Analytics devono aggiornare le proprie implementazioni in modo da utilizzare esclusivamente HTTPS, in quanto i reindirizzamenti specifici ad Analytics possono causare la perdita di dati.

**I cookie etichettati correttamente dovrebbero raccogliere i dati come previsto**

Fintanto che i cookie sono correttamente etichettati, i browser non intraprenderanno alcuna azione per bloccarli. I consumatori avranno la possibilità di bloccare alcuni tipi di cookie, ma al momento questa impostazione sembra essere solo un&#39;impostazione di consenso.

**I cookie di terze parti esistenti senza le etichette aggiornate verranno ignorati**

I cookie di terze parti creati prima che Chrome 80 iniziasse ad applicare le impostazioni SameSite=`none` e i flag protetti verranno ignorati da Chrome 80 se questi flag non sono presenti.

Molti dei cookie  Adobe di terze parti esistenti non hanno questi flag e dovranno essere aggiornati dai server Edge prima che gli utenti aggiornino Chrome 80 o quei cookie andranno persi. L&#39;aggiornamento dei server Edge avviene automaticamente quando gli utenti visitano qualsiasi sito Web in cui viene utilizzato il cookie.

La maggior parte dei prodotti  Adobe dispone già dei flag appropriati assegnati ai cookie. L&#39;eccezione è rappresentata dalle implementazioni di Analytics che utilizzano la raccolta dati di terze parti e non utilizzano ECID. I clienti potrebbero rilevare un lieve aumento temporaneo dei nuovi visitatori che altrimenti sarebbero stati visitatori di ritorno.

**Possibile riduzione della corrispondenza dei cookie per i partner di destinazione e di mercato (solo  Audience Manager)**

Mentre  Adobe ha il controllo sull&#39;aggiornamento dei cookie,  Adobe non può obbligare i partner a apportare le modifiche necessarie. La corrispondenza dei cookie può diminuire per  clienti Audienci Manager che utilizzano partner di destinazione o partner di mercato che non hanno effettuato questi aggiornamenti.

**Cookie di terze parti semplici per Analytics (solo`s_vi`cookie di Analytics)**

Alcune implementazioni di Analytics utilizzano un alias CNAME di Analytics per abilitare la creazione del `s_vi` cookie nel dominio di tale CNAME. Se il CNAME si trova nello stesso dominio del sito Web, verrà designato come cookie di prime parti. Tuttavia, se possiedi più domini e utilizzi lo stesso CNAME per la raccolta dati in tutti i tuoi domini, verrà designato come cookie di terze parti per gli altri domini.

Con `lax` la nuova impostazione predefinita SameSite in Chrome, il CNAME non è più visibile sugli altri domini.

Per apportare le modifiche, Analytics ora sta impostando esplicitamente il valore SameSite del `s_vi` cookie su `lax`. Per utilizzare questo cookie in un contesto di terze parti semplice, imposta il valore SameSite su `none`, il che significa anche che devi sempre utilizzare HTTPS. Contatta l&#39;Assistenza clienti per far sì che il valore SameSite venga modificato per i CNAME protetti.

> [!IMPORTANT] Questa azione non è necessaria per i clienti di Analytics che utilizzano ECID, per i clienti che utilizzano un CNAME separato per ciascuno dei loro domini o per i clienti che utilizzano solo la raccolta dati di Analytics di terze parti.

## Cookie visitatore standard  Adobe

Solo i cookie standard comuni dei visitatori sono elencati nella tabella seguente. Per ulteriori configurazioni di cookie, consultate la documentazione specifica per il prodotto o contattate il rappresentante del Adobe .

### ECID

| Cookie | Tipo | Attributo SameSite | Attributi protetti |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Di prime parti lato client | Nessun valore aggiunto *Cromo utilizza per impostazione predefinita `lax` | Configurabile |
| AMCVS_###@AdobeOrg | Di prime parti lato client | Nessun valore aggiunto *Cromo utilizza per impostazione predefinita `lax` | Configurabile |
| s_ecid | Lato server di prime parti | SameSite==`lax` | Non impostato |

### Audience Manager

| Cookie | Tipo | Attributo SameSite | Attributi protetti |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Terze parti | `none` | Imposta su sicuro |
| Dextp | Terze parti | `none` | Imposta su sicuro |

### Analytics

| Cookie | Tipo | Attributo SameSite | Attributi protetti |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Prima parte lato server se si utilizza `CNAME` </li> <li>Terze parti se utilizzate 2o7.net o omtrdc.net</li></ul> | <ul><li>`lax` if first-party</li> <li>`none` se terzi</li></ul> *I clienti possono modificare l&#39;impostazione tramite il ticket di assistenza clienti per i domini di prime parti* | Set, se si utilizza `none` e richiesta HTTPS |
| s_fid | Di prime parti lato client | Nessun valore aggiunto *Chrome predefinito `lax` impostazione | Non impostato |

### Target

| Cookie | Tipo | Attributo SameSite | Attributi protetti |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Prime parti | Nessun valore aggiunto *Cromo utilizza per impostazione predefinita `lax` | Non impostato |

###  Ad Cloud

| Cookie | Tipo | Attributo SameSite | Attributi protetti |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Terze parti | `none` *Solo su Google Chrome e browser basati su Cromo* | Set, se si utilizza `none` e richiesta HTTPS |
| data_adcloud | Prime parti | Nessun valore aggiunto *Cromo utilizza per impostazione predefinita `lax` | Non impostato |
| ev_tm | Terze parti | `none` *Solo su Google Chrome e browser basati su Cromo* | Set, se si utilizza `none` e richiesta HTTPS |

### Bizible

| Cookie | Tipo | Attributo SameSite | Attributi protetti |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Terze parti | `none` | Secure |

### Marketo Munchkin

| Cookie | Tipo | Attributo SameSite | Attributi protetti |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Di prime parti lato client | Nessun valore aggiunto *Cromo utilizza per impostazione predefinita `lax` | Configurabile per pagine esterne |

> !![IMPORTANT]  cookie di terze parti Adobi impostati sul lato server

Per ulteriori informazioni, vedete il documento sui criteri Google Chrome SameSite di [Target](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html).