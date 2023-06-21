---
title: Modifiche all’etichettatura SameSite di Google Chrome
description: Documentazione della libreria Adobe ECID (servizio ID).
exl-id: f20b25a4-c9bc-41b9-8e49-79b8424e62a0
source-git-commit: ee4b7f8df5766372034da2a76e7acb81ba2a65f0
workflow-type: ht
source-wordcount: '1064'
ht-degree: 100%

---

# Modifiche all’etichettatura SameSite di Google Chrome {#google-chrome-samesite-labelling-changes}

L’attributo SameSite indica ai browser quando e come attivare i cookie in scenari di prime e terze parti. L’attributo SameSite può avere uno dei tre valori seguenti: `strict`, `lax` o `none`. Chrome, Firefox, Edge, Safari e Opera supportano `strict` e `lax` da novembre 2017, mentre `none` è stato introdotto nel 2018. Tuttavia, alcuni browser meno recenti non supportano questa impostazione.

Nel febbraio 2020, Google ha rilasciato Chrome 80 e ha modificato l’impostazione predefinita da `none` a `lax` quando un cookie non ha un valore dell’attributo SameSite specificato. Questa impostazione impedisce l’utilizzo di un cookie in un contesto di terze parti, noto anche come “cross-site”. I cookie di terze parti che ne derivano devono essere impostati su `SameSite=none` e etichettati come Secure.

I cookie senza un valore di attributo SameSite specificato verranno impostati per impostazione predefinita su `lax`.

Per ulteriori informazioni sugli attributi SameSite, visita il [documento sugli standard dei cookie](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1).

## Valori attributo SameSite

| Valore attributo SameSite | Descrizioni |
| ------ | ------------ |
| `strict` | I cookie con questa impostazione vengono inviati solo se sia la pagina di provenienza che la pagina di destinazione fanno parte dello stesso dominio del cookie. |
| `lax` | I cookie con questa impostazione vengono inviati solo quando il dominio visualizzato nell’URL del browser corrisponde al dominio del cookie. Questa è la nuova impostazione predefinita per i cookie in Chrome. |
| `none` | I cookie con questa impostazione sono disponibili per l’accesso esterno o di terze parti, ad esempio “cross-site”. Prima di questa modifica, `none` era l’impostazione SameSite predefinita per i cookie, quindi l’utilizzo di questa impostazione fa sì che un cookie si comporti in modo simile a quello tradizionale. Google sta tuttavia richiedendo che qualsiasi cookie con questa impostazione specifichi ora il flag Secure, il che significa che il cookie verrà creato e inviato solo con richieste tramite HTTPS. Tutti i cookie cross-site senza il flag Secure verranno rifiutati da Google. |

## Cosa è necessario sapere come cliente di Adobe Experience Cloud

**Non è richiesto alcun aggiornamento JavaScript**

I prodotti Adobe hanno già rilasciato aggiornamenti lato server per impostare cookie di terze parti con gli attributi appropriati. I nostri clienti non necessitano di aggiornamenti della libreria JavaScript.

**Verificare che gli endpoint di terze parti utilizzino HTTPS**

Tutti i clienti devono verificare che la propria configurazione JavaScript utilizzi HTTPS per le chiamate ai servizi Adobe. Target, Audience Manager ed Experience Cloud Identity Service (ECID) stanno reindirizzando le chiamate HTTP di terze parti ai rispettivi endpoint HTTPS, il che può aumentare la latenza. Ciò significa che non è necessario modificare la configurazione. I clienti di Analytics devono aggiornare le proprie implementazioni in modo da utilizzare esclusivamente HTTPS, in quanto i reindirizzamenti specifici di Analytics possono causare la perdita di dati.

**I cookie etichettati correttamente dovrebbero raccogliere i dati come previsto**

Se i cookie sono correttamente etichettati, i browser non intraprenderanno alcuna azione per bloccarli. I consumatori avranno la possibilità di bloccare alcuni tipi di cookie, ma al momento questa sembra essere solo un’impostazione di consenso.

**I cookie di terze parti esistenti senza le etichette aggiornate saranno ignorati**

I cookie di terze parti creati prima che Chrome 80 iniziasse ad applicare le impostazioni SameSite=`none` e flag Secure verranno ignorati da Chrome 80 se tali flag non sono presenti.

Molti dei cookie Adobe di terze parti esistenti non hanno questi flag e dovranno essere aggiornati dai server Edge prima che gli utenti effettuino l’aggiornamento a Chrome 80, altrimenti quei cookie andranno persi. L’aggiornamento dei server Edge avviene automaticamente quando gli utenti visitano qualsiasi sito Web in cui viene utilizzato il cookie.

La maggior parte dei prodotti Adobe dispone già dei flag appropriati assegnati ai cookie. L’eccezione è rappresentata dalle implementazioni di Analytics che utilizzano la raccolta dati di terze parti e non utilizzano ECID. I clienti potrebbero rilevare un lieve aumento temporaneo dei nuovi visitatori che altrimenti sarebbero stati visitatori di ritorno.

**Possibile riduzione della corrispondenza dei cookie per i partner di destinazione e di marketplace (solo Audience Manager)**

Adobe ha il controllo sull’aggiornamento dei propri cookie, ma non può obbligare i partner ad apportare le modifiche necessarie. La corrispondenza dei cookie può diminuire per i clienti di Audience Manager che utilizzano partner di destinazione o di marketplace che non hanno effettuato questi aggiornamenti.

**Cookie di terze parti compatibili con Analytics (solo cookie `s_vi` di Analytics)**

Alcune implementazioni di Analytics utilizzano un alias CNAME di Analytics per abilitare la creazione del cookie `s_vi` nel dominio di tale CNAME. Se il CNAME si trova nello stesso dominio del sito Web, verrà designato come cookie di prime parti. Tuttavia, se possiedi più domini e utilizzi lo stesso CNAME per la raccolta dati in tutti i tuoi domini, verrà designato come cookie di terze parti per gli altri domini.

Ora che `lax` è la nuova impostazione SameSite predefinita in Chrome, il CNAME non è più visibile sugli altri domini.

Per adattarsi alla modifica, Analytics ora imposta esplicitamente il valore SameSite del cookie `s_vi` su `lax`. Per utilizzare questo cookie in un contesto di terze parti semplice, imposta il valore SameSite su `none`, il che significa anche che devi sempre utilizzare HTTPS. Contatta l’Assistenza clienti per far sì che il valore SameSite venga modificato per i CNAME Secure.

>[!IMPORTANT]
>
>Questa azione non è necessaria per i clienti di Analytics che utilizzano ECID, per i clienti che utilizzano un CNAME separato per ciascuno dei loro domini o per i clienti che utilizzano solo la raccolta dati di Analytics di terze parti.

## Cookie visitatore standard di Adobe

Solo i cookie visitatore standard comuni sono elencati nella tabella seguente. Per ulteriori configurazioni dei cookie, consulta la documentazione specifica per il prodotto o contatta il rappresentante Adobe.

### ECID

| Cookie | Tipo | Attributo SameSite | Attributo Secure |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Prime parti lato client | Nessun valore aggiunto *Chrome utilizza `lax` per impostazione predefinita | Configurabile |
| AMCVS_###@AdobeOrg | Prime parti lato client | Nessun valore aggiunto *Chrome utilizza `lax` per impostazione predefinita | Configurabile |
| s_ecid | Prime parti lato server | SameSite==`lax` | Non impostato |

### Audience Manager

| Cookie | Tipo | Attributo SameSite | Attributo Secure |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Terze parti | `none` | Imposta su Secure |
| Dextp | Terze parti | `none` | Imposta su Secure |

### Analytics

| Cookie | Tipo | Attributo SameSite | Attributo Secure |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Prime parti lato server se si utilizza `CNAME` </li> <li>Terze parti se si utilizza 2o7.net o omtrdc.net</li></ul> | <ul><li>`lax` se prime parti</li> <li>`none` se terze parti</li></ul> *I clienti possono modificare l’impostazione tramite segnalazione all’Assistenza clienti per i domini di prime parti* | Impostato, se si utilizzano `none` e richiesta HTTPS |
| s_fid | Prime parti lato client | Nessun valore aggiunto *Chrome utilizza `lax` per impostazione predefinita | Non impostato |

### Target

| Cookie | Tipo | Attributo SameSite | Attributo Secure |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Prime parti | Nessun valore aggiunto *Chrome utilizza `lax` per impostazione predefinita | Non impostato |

### Ad Cloud

| Cookie | Tipo | Attributo SameSite | Attributo Secure |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Terze parti | `none` *Solo su Google Chrome e browser basati su Chromium* | Impostato, se si utilizzano `none` e richiesta HTTPS |
| data_adcloud | Prime parti | Nessun valore aggiunto *Chrome utilizza `lax` per impostazione predefinita | Non impostato |
| ev_tm | Terze parti | `none` *Solo su Google Chrome e browser basati su Chromium* | Impostato, se si utilizzano `none` e richiesta HTTPS |

### Bizible

| Cookie | Tipo | Attributo SameSite | Attributo Secure |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Terze parti | `none` | Secure |

### Marketo Munchkin

| Cookie | Tipo | Attributo SameSite | Attributo Secure |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Prime parti lato client | Nessun valore aggiunto *Chrome utilizza `lax` per impostazione predefinita | Configurabile per pagine esterne |

>  I cookie di terze parti Adobe sono impostati sul lato server.

Per ulteriori informazioni, consulta il documento sui [Criteri di Target per SameSite di Google Chrome](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/google-chrome-samesite-cookie-policies.html?lang=it).
