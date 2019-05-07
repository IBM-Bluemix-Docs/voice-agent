---

copyright:
  years: 2019
lastupdated: "2019-01-30"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Abilitazione dell'inoltro dell'evento per i Voice Agent
{: #event_forwarding}

Puoi abilitare l'inoltro dell'evento per raccogliere le informazioni sulle chiamate gestite dai tuoi Voice Agent in {{site.data.keyword.iva_full}} utilizzando un servizio database {{site.data.keyword.cloudantfull}}.
{: shortdesc}

Potresti voler raccogliere ed analizzare i dati della chiamata da {{site.data.keyword.iva_short}} per migliorare quanto naturale la conversazione sembri al chiamante. Ogni Voice Agent che crei può inoltrare i report dell'evento a un {{site.data.keyword.cloudant_short_notm}} specificato che gestisci. Gli eventi riportati includono i CDR (call detail record), gli eventi di trascrizione e i report degli eventi del turno. Puoi trovare ulteriori informazioni sui tipi di eventi che puoi inoltrare in [Reporting events](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}.

L'analisi dei dati da questi eventi può esserti utile per modificare i dialoghi, rifinire gli intenti e migliorare l'esperienza del chiamante in generale.

Quando crei o modifichi i Voice Agent, puoi anche scegliere di abilitare l'inoltro dell'evento. Per ulteriori dettagli sulla creazione e la modifica dei Voice Agent, vedi [Gestione dei Voice Agent](/docs/services/voice-agent?topic=voice-agent-managing). Devi fornire le informazioni sull'account {{site.data.keyword.cloudant_short_notm}}, inclusi nome e password dell'account, per abilitare l'inoltro dell'evento.

**Importante:** gli eventi CDR, trascrizione e turno includono informazioni dai tuoi utenti che potrebbero potenzialmente contenere dati Protected Health Information (PHI), personally identifiable information (PII) o PCI Data Security Standard (PCI DSS). Per evitare l'esposizione di informazioni personali, devi assicurarti che la tua istanza {{site.data.keyword.cloudant_short_notm}} protegga in modo appropriato le informazioni confidenziali che i tuoi utenti condividono durante la conversazione. Consulta [Informazioni sulla sicurezza e sulla privacy dei dati: inoltro dell'evento](/docs/services/voice-agent?topic=voice-agent-infosec#event_forwarding) e [{{site.data.keyword.cloudant_short_notm}}: sicurezza](/docs/services/Cloudant/offerings?topic=cloudant-security#security).


## Abilitazione dell'inoltro dell'evento
{: #enable-event-forwarding}

Puoi abilitare l'inoltro dell'evento quando stai creando o modificando i tuoi Voice Agent nel dashboard _Manage_ in {{site.data.keyword.Bluemix_short}}.

1. Nella sezione **Event forwarding**, dopo la sezione di configurazione per {{site.data.keyword.texttospeechshort}}, seleziona **Enable event forwarding**.

1. Seleziona **My {{site.data.keyword.cloudant_short_notm}} service instance** o **Other {{site.data.keyword.cloudant_short_notm}} service instance**.
  * Se stai utilizzando **My {{site.data.keyword.cloudant_short_notm}} service instance**, seleziona il nome dell'**account {{site.data.keyword.cloudant_short_notm}}** e il nome utente dagli elenchi.
  * Se stai creando un Voice Agent nella regione Dallas o Washington DC e non hai un'istanza del servizio {{site.data.keyword.cloudant_short_notm}}, puoi crearne una dal menu **Cloudant account**.
  * Se stai utilizzando **Other {{site.data.keyword.cloudant_short_notm}} service instance**, immetti il nome utente e la password {{site.data.keyword.cloudant_short_notm}} (fino a 128 e 256 caratteri, rispettivamente) oppure la chiave API per l'account (fino a 64 caratteri).

1. Seleziona **Enable** per ogni tipo di evento che vuoi inoltrare e poi scegli il database a cui vuoi inoltrare gli eventi.
  * Eventi CDR (Call detail record)
  * Eventi di trascrizione
  * Eventi di turno

1. Visualizza il tuo database per assicurarti che i report dell'evento vengano inoltrati correttamente.

## Link correlati
{: #related-links-forwarding}
* [IBM Voice Gateway: Reporting events](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
* [Informazioni sulla sicurezza e sulla privacy dei dati](/docs/services/voice-agent?topic=voice-agent-infosec)
* [{{site.data.keyword.cloudant_short_notm}}: sicurezza](/docs/services/Cloudant/offerings?topic=cloudant-security#security)
