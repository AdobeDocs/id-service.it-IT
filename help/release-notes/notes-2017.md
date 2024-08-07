---
description: Versioni future, aggiornamenti o modifiche a Experience Cloud Identity Service per il 2017.
keywords: Servizio ID
title: Note sulla versione 2017
exl-id: 0b51d3b1-e405-4473-9e1a-f89a55250e5e
source-git-commit: 384b292413bbc7e43ade97e442ab7195f3b26c7a
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 99%

---

# Note sulla versione 2017 {#release-notes}

Versioni future, aggiornamenti o modifiche a Experience Cloud Identity Service per il 2017.

Queste modifiche vengono riportate anche nelle [note sulla versione di Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=it).

>[!NOTE]
>
>Non esistono note sulla versione rivolte al clienti o modifiche del codice per marzo, aprile, maggio e ottobre 2017. Per questi mesi, il codice del servizio ID resta immutato alla versione v2.1.

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
   <td colname="col2"> <p>Questa API asincrona restituisce per impostazione predefinita identificatori per Analytics, il servizio ID, la rinuncia alla raccolta di dati, la geolocalizzazione, e contenuti di metadati BLOB. Inoltre, è possibile controllare gli ID che dovranno essere restituiti con l'enum opzionale <span class="codeph">visitor.FIELDS</span>. Consulta <a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correzioni di bug e altre modifiche**

* È stato corretto un bug relativo a Chrome a causa del quale il servizio ID generava un errore quando si faceva clic sul pulsante Indietro in questo browser.
* Il servizio ID ora riavvia la sincronizzazione degli ID quando l’ID di regione cambia nella risposta alla chiamata dell’evento.
* È stata aggiunta della nuova documentazione, [Policy di sicurezza dei contenuti ed Experience Cloud Identity Service](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3), che spiega come inserire nella whitelist le chiamate ai domini Adobe usati dal servizio ID.

<!-- ## Version 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

August, 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>An optional, Boolean configuration that determines if the ID service sends (or does not send) data to the Adobe Experience Cloud Device Co-op. See <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Revised Documentation**

Updated and revised the [FAQs](/help/faq-intro/faq-intro.md) to include separate FAQs for different [!DNL Experience Cloud] solutions. -->

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
   <td colname="col2"> <p>Quando viene aggiunta alla funzione <span class="codeph">Visitor.getInstance</span>, questa configurazione consente di escludere l'intervallo di scadenza predefinito di Supplemental Data ID (SDID) quando questo viene passato da una pagina a un'altra. Puoi usare <span class="codeph">sdidParamExpiry</span> con la funzione helper <span class="codeph">appendSupplimentalDataTo</span>. Vedi <a href="../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local">sdidParamExpiry</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>Questa funzione è stata progettata in particolare per aiutare i clienti A4T a risolvere problemi relativi all'utilizzo degli ID su app oppure siti/schermate a pagina singola. Vedi <a href="../library/get-set/resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local">resetState</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correzioni di bug e altre modifiche**

* È stato corretto un bug in VisitorAPI.js v2.2 che impediva al servizio ID e a Target di funzionare in contemporanea in Internet Explorer.
* È stato rivisto il codice per migliorare il modo in cui il servizio ID invia i dati all&#39;iFrame di pubblicazione di destinazione. Questo consente di ridurre l’utilizzo della CPU.

## Versione 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

Data di rilascio: giugno 2017

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funzione </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain e whitelistIframeDomains </a> </p> </td> 
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
   <td colname="col1"> <p> <a href="../faq-intro/faq.md" format="dita" scope="local">Domande frequenti</a> </p> </td> 
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
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer e audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p>Link aggiunti alla documentazione di <span class="keyword">Audience Manager</span> che descrive le chiamate al dominio <span class="codeph">demdex.net</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> Informazioni sulla sincronizzazione degli ID e sui tassi di corrispondenza </a> </p> </td> 
   <td colname="col2"> <p>Sezione <span class="keyword">Media Optimizer</span> rivista per descrivere la chiamata a <span class="codeph">cm.eversttech.net</span>. Questa è una sincronizzazione ID automatica che il servizio ID esegue con <span class="keyword">Media Optimizer</span>. Questa funzione è stata rilasciata a gennaio 2017. Vedi la <a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">Versione 2.0</a> seguente. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versione 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

Data di rilascio: febbraio 2017

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
   <td colname="col1"> <p> Proprietà API del servizio ID, <span class="codeph"> idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>Questa proprietà imposta l'ID del contenitore utilizzato da <span class="keyword">Audience Manager</span> per la sincronizzazione degli ID. Consulta <a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external"> idSyncContainerID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Metodo API del servizio ID, <span class="codeph">appendSupplementalDataIDTo(<span class="varname"> URL</span>, <span class="varname">SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>Questo metodo pubblico aggiunge a un URL di reindirizzamento il codice <span class="wintitle">Supplemental Data ID</span> (SDID) sotto forma di parametro della stringa di interrogazione. Consulta <a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> appendSupplementalDataIDTo</a>. (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correzioni**

È stato corretto un bug a causa del quale il servizio ID effettuava chiamate ridondanti al server per richiedere un ID invece di utilizzare l’ID memorizzato nel cookie AMCV. (MCID-296)

**Nuova documentazione**

[Usare il prefetch di DNS con soluzioni e servizi Experience Cloud diversi](https://experienceleague.adobe.com/docs/core-services/interface/more-resources/dns-prefetch.html?lang=it)

## Versione 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

Gennaio 2017

>[!IMPORTANT]
>
>Per impostazione predefinita, il codice v2.0 del servizio ID sincronizza automaticamente gli ID con Adobe Media Optimizer. Questo significa che vedrai una chiamata dalla pagina a `cm.eversttech.net`, che è il dominio [!DNL Media Optimizer] legacy controllato da [!DNL Adobe]. Consulta anche [Informazioni sulla sincronizzazione degli ID e sui tassi di corrispondenza](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Correzioni e miglioramenti**

* È stato corretto un bug che impediva ad AppMeasurement di effettuare chiamate di tracciamento ad Analytics. (MCID-254, MCID-256, MCID-286)
* È stato corretto un bug che impediva al servizio ID di fallire immediatamente quando un visitatore aveva abilitato un ad blocker la cui configurazione escludeva il dominio demdex.net. Si tratta di un bug raro e insolito perché la maggior parte degli strumenti di ad blocking non bloccano il dominio demdex.net. (MCID-233)
* È stato corretto un bug causato dalle interazioni tra il codice del servizio ID e uno script personalizzato sul sito Web di un cliente. Questo problema impediva a Internet Explorer 9 di caricare le pagine Web. (MCID-206)

## Anni precedenti {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

Note sulle versioni precedenti del servizio ID.
