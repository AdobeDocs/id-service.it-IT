---
description: Un'informativa sulla sicurezza dei contenuti (CSP) è un'intestazione HTTP e una funzione di sicurezza che offre ai browser il controllo sul tipo di risorse caricate su una pagina Web. Consulta questa sezione se usi il servizio ID e hai una CSP rigida che adotta delle whitelist per accettare le risorse dai domini fidati. Dovrai aggiungere i domini Adobe elencati di seguito alle whitelist della CSP.
keywords: ID Service
seo-description: Un'informativa sulla sicurezza dei contenuti (CSP) è un'intestazione HTTP e una funzione di sicurezza che offre ai browser il controllo sul tipo di risorse caricate su una pagina Web. Consulta questa sezione se usi il servizio ID e hai una CSP rigida che adotta delle whitelist per accettare le risorse dai domini fidati. Dovrai aggiungere i domini Adobe elencati di seguito alle whitelist della CSP.
seo-title: Informativa sulla sicurezza dei contenuti e servizio Experience Cloud Identity
title: Informativa sulla sicurezza dei contenuti e servizio Experience Cloud Identity
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 100%

---


# Informativa sulla sicurezza dei contenuti e servizio Experience Cloud Identity {#content-security-policies-and-the-experience-cloud-id-service}

Un&#39;informativa sulla sicurezza dei contenuti (CSP) è un&#39;intestazione HTTP e una funzione di sicurezza che offre ai browser il controllo sul tipo di risorse caricate su una pagina Web. Consulta questa sezione se usi il servizio ID e hai una CSP rigida che adotta delle whitelist per accettare le risorse dai domini fidati. Dovrai aggiungere i domini Adobe elencati di seguito alle whitelist della CSP.

## Consulta CSP {#section-5fde5c00a678455c914b8307a8caab82}

La CSP usa l&#39;intestazione HTTP `Content-Security-Policy` per controllare il tipo di risorse che i browser accettano o caricano su una pagina. L’applicazione di una CSP può essere utile per impedire:

* Il caricamento dei file JavaScript se l’origine è sconosciuta o non è inclusa in una whitelist.
* Gli attacchi di cross-site scripting (XXS).
* Attacchi di iniezione di dati.
* Attacchi di defacing del sito.
* Distribuzione di malware.

L&#39;uso della CSP è comune e noto. Questa documentazione non ha l&#39;obiettivo di spiegare in maniera dettagliata la CSP (per maggiori informazioni consulta i link alle informazioni correlate). Ciò che è importante è capire quali nomi dei domini Adobe devi aggiungere a una CSP se ne usi una e se hai delle politiche di sicurezza restrittive. L’aggiunta di questi domini consente ai browser dei visitatori che accedono al tuo sito di effettuare chiamate importanti alle risorse Experience Cloud che utilizzi.

## Domini Experience Cloud per la creazione di whitelist {#section-30693e9a96834edfbf04de9e698cf2aa}

Aggiungi questi nomi di dominio o URL alla tua CSP per ogni soluzione o servizio Experience Cloud che utilizzi.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Soluzione o servizio Experience Cloud </th> 
   <th colname="col2" class="entry"> Descrizione </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>Modifica la tua CSP in modo che includa quanto segue: </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtrdc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p>Modifica la tua CSP in modo che includa <span class="codeph">*.tt.omtrdc.net</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Servizio di Experience Cloud ID e Audience Manager </b> </p> </td> 
   <td colname="col2"> <p>Modifica la tua CSP in modo che includa i seguenti domini.</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>Se utilizzi Adobe Launch per distribuire i tag, devi aggiungere anche <code>https://assets.adobedtm.com</code> all’elenco dei domini.</li></ul></p> <p>Le chiamate al dominio <span class="codeph">demdex.net</span> vengono utilizzate per generare i <a href="../introduction/cookies.md" format="dita" scope="local">cookie e il servizio Experience Cloud Identity</a> e per le sincronizzazioni degli ID. Vedi anche <a href="https://docs.adobe.com/content/help/it-IT/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Informazioni sulle chiamate al dominio demdex</a>. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Plug-in Activity Map</b> </p> </td> 
 <td colname="col2"> <p>Modifica la tua CSP in modo che includa *.adobe.com. **Nota**: se hai installato Activity Map prima di gennaio 2020, il browser visualizzerà comunque una richiesta iniziale a *.omniture.com ma verrà reindirizzato a *.adobe.com. </p></td> 
 </tr>
 <tr>
 <td colname="col1"> <p> <b>Advertising Analytics</b> </p> </td> 
 <td colname="col2"> <p>Se disponi di controlli sui parametri delle stringhe query, accertati di inserire in una whitelist i parametri 's_kwcid' e 'ef_id'. Tecnicamente Advertising Analytics utilizza solo 's_kwcid', ma se selezioni Ad Cloud Search o DSP utilizza anche 'ef_id'. Questi parametri delle stringhe query sono alfanumerici. Il parametro 's_kwcid' utilizza il carattere “!” e il parametro 'ef_id' utilizza il carattere “:”. Se blocchi il carattere “!” nell’URL, inseriscilo a sua volta nella whitelist.</p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [Riferimento all’informativa sulla sicurezza dei contenuti](https://content-security-policy.com/)
>* [MDN: informativa sulla sicurezza dei contenuti](https://developer.mozilla.org/it/docs/Web/HTTP/CSP)
>* [Wikipedia: informativa sulla sicurezza dei contenuti](https://en.wikipedia.org/wiki/Content_Security_Policy)

