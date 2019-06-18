---
description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud ID per il 2017.
keywords: Servizio ID
seo-description: Versioni future, aggiornamenti o modifiche al servizio Experience Cloud ID per il 2017.
seo-title: Note sulla versione 2017
title: Note sulla versione 2017
uuid: 79452 df 0-49 db -42 b 8-96 fe -01 aa 7629 fbb 5
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# Note sulla versione 2017 {#release-notes}

Versioni future, aggiornamenti o modifiche al servizio Experience Cloud ID per il 2017.

Queste modifiche vengono anche riportate nelle [note sulla versione di Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/). Per le note sulle versioni del servizio ID più datate, consulta le [note sulle versioni precedenti](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html) o i link in fondo a questa pagina.

>[!NOTE]
>
>Non sono disponibili note sulla versione rivolte al cliente o modifiche al codice per marzo, aprile, maggio e ottobre 2017. Per questi mesi, il codice del servizio ID resta immutato alla versione v2.1.

## Versione 2.5 {#section-27b441509124493f80984ed09bd9e88b}

Settembre 2017

<!--
<p>
<note type="important">
ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funzione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>Questa API asincrona restituisce per impostazione predefinita identificatori per Analytics, il servizio ID, la rinuncia alla raccolta di dati, la geolocalizzazione, e contenuti di metadati BLOB. Inoltre, è possibile controllare gli ID che dovranno essere restituiti con l'enum opzionale <span class="codeph">visitor.FIELDS</span>. Consulta <a href="../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getvisitorvalues</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correzioni di bug e altre modifiche**

* È stato corretto un bug relativo a Chrome a causa del quale il servizio ID generava un errore quando si faceva clic sul pulsante Indietro in tale browser.
* Il servizio ID ora avvia di nuovo la sincronizzazione degli ID quando l&#39;ID regione cambia nella risposta della chiamata dell&#39;evento.
* Alla documentazione è stata aggiunta la sezione  [Informativa sulla sicurezza dei contenuti e il servizio Experience Cloud ID](/help/mcvid-reference/mcvid-csp.md#concept-968c423a7392479db0a0d821ae9783e3) che spiega come la whitelist effettua la chiamata ai domini Adobe usati dal servizio ID.

## Versione 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

Agosto 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funzione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>Configurazione booleana opzionale che consente di determinare se il servizio ID invia o meno dati ad Adobe Experience Cloud Device Co-op. Vedi <a href="../mcvid-library/mcvid-function-vars/mcvid-coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local">isCoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Documentazione rivista**

È stata aggiornata e rivista la sezione  [Domande frequenti](/help/mcvid-faq-intro/ecid-faq-intro.md) per includere domande frequenti separate per [!DNL Experience Cloud] soluzioni diverse.

## Versione 2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

Luglio 2017

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funzione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>Quando viene aggiunta alla funzione <span class="codeph">Visitor.getInstance</span>, questa configurazione consente di escludere l'intervallo di scadenza predefinito di Supplemental Data ID (SDID) quando questo viene passato da una pagina a un'altra. Puoi usare <span class="codeph">sdidParamExpiry</span> con la funzione helper <span class="codeph">appendSupplimentalDataTo</span>. Vedi <a href="../mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local">sdidParamExpiry</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>Questa funzione è stata progettata in particolare per aiutare i clienti A4T a risolvere problemi relativi all'utilizzo degli ID su app oppure siti/schermate a pagina singola. Vedi <a href="../mcvid-library/mcvid-get-set/mcvid-resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local">resetState</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correzioni di bug e altre modifiche**

* È stato corretto un bug in VisitorAPI.js v2.2 a causa del quale il servizio ID e Target non potevano funzionare insieme in Internet Explorer.
* È stato rivisto il codice per migliorare il modo in cui il servizio ID invia i dati all&#39;iFrame di pubblicazione di destinazione, per ridurre l&#39;utilizzo della CPU.

## Versione 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

Data di rilascio: Giugno 2017

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funzione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain e whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>Queste configurazioni consentono a diverse istanze del codice del servizio ID implementate in un iFrame e sulla pagina padre di comunicare tra di loro. Risolvono problemi rilevati per 2 casi d'uso specifici in cui si può controllare o meno la pagina padre o il dominio e si carica il codice del servizio ID nell'iFrame di un dominio controllato. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Aggiornamenti della documentazione per maggio {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Argomento </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-faq-intro/ecid-faq.md" format="dita" scope="local">Domande frequenti</a> </p> </td> 
   <td colname="col2"> <p>Aggiornamento della sezione <span class="keyword">Analytics</span> con istruzioni su come trovare le informazioni sul server di tracciamento. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Aggiornamenti della documentazione per aprile {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Argomento </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer e audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p>Link aggiunti alla documentazione di <span class="keyword">Audience Manager</span> che descrive le chiamate al dominio <span class="codeph">demdex.net</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md" format="dita" scope="local"> Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza </a> </p> </td> 
   <td colname="col2"> <p>Sezione <span class="keyword">Media Optimizer</span> rivista per descrivere la chiamata a <span class="codeph">cm.eversttech.net</span>. Questa è una sincronizzazione ID automatica che il servizio ID esegue con <span class="keyword">Media Optimizer</span>. Questa funzione è stata rilasciata a gennaio 2017. Vedi la <a href="../mcvid-release-notes/mcvid-notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">Versione 2.0</a> seguente. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versione 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

Data di rilascio: Febbraio 2017

**Funzioni**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funzione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> Proprietà API del servizio ID, <span class="codeph">idSyncContainerID </span></p> </td> 
   <td colname="col2"> <p>Questa proprietà imposta l'ID del contenitore utilizzato da <span class="keyword">Audience Manager</span> per la sincronizzazione degli ID. Consulta <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-idsyncontainerid.html" format="https" scope="external">idSyncContainerID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Metodo API del servizio ID, <span class="codeph"> appendSupplementalDataIDTo( <span class="varname"> URL </span>, <span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>Questo metodo pubblico aggiunge a un URL di reindirizzamento il codice <span class="wintitle">Supplemental Data ID</span> (SDID) sotto forma di parametro della stringa di interrogazione. Vedere <a href="../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> appendsupplementaldataidto</a>. (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correzioni**

È stato corretto un bug a causa del quale il servizio ID effettuava chiamate ridondanti al server per richiedere un ID invece di utilizzare l&#39;ID registrato nel cookie AMCV. (MCID-296)

**Nuova documentazione**

[Utilizzo del recupero preventivo del DNS con diverse soluzioni e servizi di Experience Cloud `Learn how to use DNS prefetch to help reduce page load times.`](https://marketing.adobe.com/resources/help/en_US/mcloud/dns-prefetch.html)

## Versione 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

Gennaio 2017

>[!IMPORTANT]
>
>Per impostazione predefinita, il codice del servizio ID v 2.0 sincronizza automaticamente gli ID con Adobe Media Optimizer. Ciò significa che vedrai una chiamata dalla pagina a `cm.eversttech.net`, che è un [!DNL Media Optimizer] dominio legacy controllato da [!DNL Adobe]. Consultare anche [Informazioni sulla sincronizzazione degli ID e sulle percentuali di corrispondenza](../mcvid-introduction/mcvid-match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab). 

**Correzioni e miglioramenti**

* È stato risolto un bug che impediva ad AppMeasurement di effettuare chiamate di tracciamento ad Analytics. (MCID-254, MCID-256, MCID-286)
* È stato risolto un bug che impediva al servizio ID di generare immediatamente un errore in presenza di un ad blocker abilitato e configurato per escludere il dominio demdex.net. Si tratta di un bug raro e insolito, perché la maggior parte degli ad blocker non bloccano il dominio demdex.net. (MCID-233)
* È stato risolto un bug causato da interazioni tra il codice del servizio ID e uno script personalizzato sul sito Web del cliente. Questo problema impediva a Internet Explorer 9 di caricare le pagine Web. (MCID-206)

## Anni precedenti {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

Note sulle versioni precedenti del servizio ID.
