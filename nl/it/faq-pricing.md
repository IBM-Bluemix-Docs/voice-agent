---

copyright:
  years: 2019
lastupdated: "2019-06-17"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# FAQ sui prezzi
{: #faq-pricing}

## Qual è il prezzo di utilizzo del servizio standard {{site.data.keyword.iva_short}}?
{: #faq-pricing-zero}
{: faq}

 Per ulteriori informazioni, vedi la [pagina dei prezzi](https://cloud.ibm.com/catalog/services/voice-agent-with-watson){: external}. 

## Cosa significa "prezzo al minuto"?
{: #faq-pricing-one}
{: faq}

Il prezzo si basa sulla quantità (numero di minuti) di audio che invii al servizio. Il prezzo non dipende da quanto tempo serve al servizio per elaborare l'audio.


## Il tempo viene calcolato al minuto più vicino per ogni chiamata all'API 
{: #faq-pricing-two}
{: faq}

'{{site.data.keyword.IBM_notm}} non calcola la lunghezza dell'audio di ogni chiamata API ricevuta dal servizio al minuto più vicino. Invece, {{site.data.keyword.IBM_notm}} aggrega l'utilizzo del mese e poi calcola il minuto più vicino al termine del mese. La durata di ogni chiamata viene arrotondata al minuto successivo. Ad esempio, se effettui la prima chiamata di 3.1 secondi e la seconda di 25.9 secondi, {{site.data.keyword.IBM_notm}} calcola la prima chiamata per 4 secondi e la seconda per 26. Successivamente la durata dell'audio totale viene calcolata con un (1) minuto.'


## Come viene calcolata la connessione simultanea e dove viene applicata?
{: #faq-pricing-three}
{: faq}

La connessione simultanea si applica solo alle chiamate vocali (non SMS). La connessione simultanea viene calcolata come il numero di connessioni a tutti i numeri di telefono definiti simultaneamente nell'istanza del servizio. Il numero massimo giornaliero reale delle connessioni simultanee utilizzate viene fatturato con un addebito mensile su base proporzionale.

## Qual è la definizione di connessione simultanea massima e come è possibile modificarla?

{: #faq-pricing-four}
{: faq}

La connessione simultanea massima è il numero massimo di connessioni consentite in qualsiasi momento e si tratta del numero massimo di connessioni che viene fatturato. Le connessioni simultanee massime possono essere definite e modificate nel [dashboard](https://cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-edit_concurrency). La capacità simultanea massima su un piano standard è 50 connessioni e se hai bisogno di un numero maggiore puoi aprire un ticket di supporto.

## Come vengono fatturati i messaggi SMS/MMS in entrata e uscita?

{: #faq-pricing-five}
{: faq}

I messaggi in entrata non vengono fatturati finché non viene inviata una risposta all'utente. Viene creata una sessione quando un messaggio in uscita viene inviato all'utente tramite il Voice Gateway o come una risposta a un messaggio in entrata. Sia i messaggi in entrata che in uscita a cui viene data una risposta vengono fatturati, se applicabile.
Sia i messaggi in entrata che in uscita vengono fatturati fino al timeout della sessione. Dopo il timeout della sessione, il contesto della conversazione viene eliminato. Il timeout della sessione predefinito è 3600 secondi e gli utenti possono configurarne la durata sul dashboard.
