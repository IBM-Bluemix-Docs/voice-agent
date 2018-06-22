---

copyright:
  years: 2018
lastupdated: "2018-06-11"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Abilitazione dell'inoltro dell'evento per gli agent vocali
{: #event_forwarding}

Puoi abilitare l'inoltro dell'evento per raccogliere le informazioni sulle chiamate gestite dai tuoi agent vocali in {{site.data.keyword.iva_full}} utilizzando un servizio database {{site.data.keyword.cloudantfull}}.
{: shortdesc}

Potresti voler raccogliere ed analizzare i dati della chiamata da {{site.data.keyword.iva_short}} per migliorare quanto naturale la conversazione sembri al chiamante. Ogni agent vocale che crei può inoltrare i report dell'evento a un {{site.data.keyword.cloudant_short_notm}} specificato che gestisci. Gli eventi riportati includono i CDR (call detail record), gli eventi di trascrizione e i report degli eventi del turno. Puoi trovare ulteriori informazioni sui tipi di eventi che puoi inoltrare in [Reporting events](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}.

L'analisi dei dati da questi eventi può esserti utile per modificare i dialoghi, rifinire gli intenti e migliorare l'esperienza del chiamante in generale.

Quando crei o modifichi gli agent vocali, puoi anche scegliere di abilitare l'inoltro dell'evento. Per ulteriori dettagli sulla creazione e la modifica degli agent vocali, vedi [Gestione degli agent vocali](managing.html). Devi fornire le informazioni sull'account {{site.data.keyword.cloudant_short_notm}}, inclusi nome e password dell'account, per abilitare l'inoltro dell'evento.

**Importante:** gli eventi CDR, trascrizione e turno includono informazioni dai tuoi utenti che potrebbero potenzialmente contenere dati Protected Health Information (PHI), personally identifiable information (PII) o PCI Data Security Standard (PCI DSS). Per evitare l'esposizione di informazioni personali, devi assicurarti che la tua istanza {{site.data.keyword.cloudant_short_notm}} protegga in modo appropriato le informazioni confidenziali che i tuoi utenti condividono durante la conversazione.


## Abilitazione dell'inoltro dell'evento
{: #enable-event-forwarding}

Puoi abilitare l'inoltro dell'evento quando stai creando o modificando i tuoi agent vocali nel dashboard _Manage_ in {{site.data.keyword.Bluemix_short}}.

1. Nella sezione **Event forwarding**, dopo la sezione di configurazione per {{site.data.keyword.texttospeechshort}}, seleziona **Enable event forwarding**.

1. Seleziona **My {{site.data.keyword.cloudant_short_notm}} service instance** o **Other {{site.data.keyword.cloudant_short_notm}} service instance**.
  * Se stai utilizzando **My {{site.data.keyword.cloudant_short_notm}} service instance**, seleziona il nome dell'**account {{site.data.keyword.cloudant_short_notm}}** e il nome utente dagli elenchi.
  * Se stai utilizzando **Other {{site.data.keyword.cloudant_short_notm}} service instance**, immetti il nome utente e la password {{site.data.keyword.cloudant_short_notm}} dell'account.

1. Seleziona **Enable** per ogni tipo di evento che vuoi inoltrare e poi scegli il database a cui vuoi inoltrare gli eventi.
  * Eventi CDR (Call detail record)
  * Eventi di trascrizione
  * Eventi di turno

1. Visualizza il tuo database per assicurarti che i report dell'evento vengano inoltrati correttamente.

## Link correlati
* [IBM Voice Gateway: Reporting events](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
