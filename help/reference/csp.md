---
description: Un'informativa sulla sicurezza dei contenuti (CSP) è un'intestazione HTTP e una funzione di sicurezza che offre ai browser il controllo sul tipo di risorse caricate su una pagina Web. Consulta questa sezione se usi il servizio ID e hai una CSP rigida che adotta delle whitelist per accettare le risorse dai domini fidati. Dovrai aggiungere i domini Adobe elencati di seguito alle whitelist della CSP.
keywords: ID Service
seo-description: Un'informativa sulla sicurezza dei contenuti (CSP) è un'intestazione HTTP e una funzione di sicurezza che offre ai browser il controllo sul tipo di risorse caricate su una pagina Web. Consulta questa sezione se usi il servizio ID e hai una CSP rigida che adotta delle whitelist per accettare le risorse dai domini fidati. Dovrai aggiungere i domini Adobe elencati di seguito alle whitelist della CSP.
seo-title: Informativa sulla sicurezza dei contenuti e servizio Experience Cloud Identity
title: Informativa sulla sicurezza dei contenuti e servizio Experience Cloud Identity
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: fbfea06bc2a4493b6d9b84a8f367749e1d803650

---


# Informativa sulla sicurezza dei contenuti e servizio Experience Cloud Identity {#content-security-policies-and-the-experience-cloud-id-service}

Un'informativa sulla sicurezza dei contenuti (CSP) è un'intestazione HTTP e una funzione di sicurezza che offre ai browser il controllo sul tipo di risorse caricate su una pagina Web. Consulta questa sezione se usi il servizio ID e hai una CSP rigida che adotta delle whitelist per accettare le risorse dai domini fidati. Dovrai aggiungere i domini Adobe elencati di seguito alle whitelist della CSP.

## Consulta CSP {#section-5fde5c00a678455c914b8307a8caab82}

La CSP usa l'intestazione HTTP `Content-Security-Policy` per controllare il tipo di risorse che i browser accettano o caricano su una pagina. L'applicazione di una CSP può aiutarti a impedire:

* Il caricamento dei file JavaScript se la fonte è sconosciuta o non inclusa in una whitelist.
* L'attacco di vulnerabilità cross-site scripting (XXS).
* L'attacco dell'iniezione di dati.
* L'attacco del defacement del sito.
* La distribuzione del malware.

L'uso della CSP è comune e noto. Questa documentazione non ha l'obiettivo di spiegare in maniera dettagliata la CSP (per maggiori informazioni consulta i link alle informazioni correlate). Ciò che è importante è capire quali nomi dei domini Adobe devi aggiungere a una CSP se ne usi una e se hai delle politiche di sicurezza restrittive. L'aggiunta di questi domini consente al browser dei visitatori che accedono al sito di chiamare le importanti risorse di Experience Cloud usate.

## Domini Experience Cloud per la creazione di whitelist {#section-30693e9a96834edfbf04de9e698cf2aa}

Aggiungi questi nomi o URL di domini alla tua CSP per ogni soluzione o servizio Experience Cloud che utilizzi.

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
   <td colname="col1"> <p> <b>Servizio ID visitatori</b> </p> </td> 
   <td colname="col2"> <p>Modifica la tua CSP in modo che includa <span class="codeph">*.demdex.net</span>. </p> <p>Le chiamate al dominio <span class="codeph"> demdex.net</span> vengono utilizzate per generare i cookie <a href="../introduction/cookies.md" format="dita" scope="local"> e il servizio Experience Cloud Identity</a> e per le sincronizzazioni degli ID. Vedi anche <a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external">Informazioni sulle chiamate al dominio demdex</a>. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Plug-in Activity Map</b> </p> </td> 
 <td colname="col2"> <p>Modificate la vostra CSP per includere *omniture.com </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [Riferimento all’informativa sulla sicurezza dei contenuti](https://content-security-policy.com/)
>* [MDN: informativa sulla sicurezza dei contenuti](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [Wikipedia: informativa sulla sicurezza dei contenuti](https://en.wikipedia.org/wiki/Content_Security_Policy)

