---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Visualizzazione dei log di chiamata e utilizzo
{: #logging}

Puoi visualizzare i log di chiamata e della cronologia di utilizzo dei tuoi agent vocali dal dashboard {{site.data.keyword.Bluemix_notm}}.
{: shortdesc}

## Informazioni sulla registrazione

La registrazione viene abilitata automaticamente per {{site.data.keyword.iva_full}}. Puoi visualizzare i tuoi log di chiamata dell'agent vocale nel dashboard _Usage_.

Il dashboard _Usage_ ti mostra le statistiche veloci sul tuo utilizzo del servizio per il mese corrente e le rimanenti risorse disponibili nel tuo piano. Queste informazioni includono il numero massimo di connessioni simultanee riscontrate nel mese corrente e il numero massimo di connessioni simultanee disponibili nel tuo piano. Puoi inoltre visualizzare il numero di minuti gratuiti inclusi nel piano e il numero di minuti utilizzati. La sezione _Call logs_ segue le tue _Quick stats_.

Nella sezione _Call logs_, puoi filtrare i log per data e nome dell'agent vocale per ridurre il numero di chiamate visualizzate e isolare i log di chiamata specifici.

Per ulteriori informazioni sulla creazione e la modifica degli agent vocali, vedi [Gestione degli agent vocali](managing.html).

##  Visualizzazione dei log di chiamata

1. Dal tuo dashboard {{site.data.keyword.iva_short}}, passa al dashboard _Usage_ per visualizzare le _Quick stats_ e i _Call logs_. Ogni riga nella tabella _Call logs_ corrisponde a una chiamata.

      Per ogni chiamata, puoi visualizzare il nome e il numero di telefono del tuo agent vocale, le ore di avvio e arresto e la durata della chiamata. Potresti inoltre visualizzare un simbolo di avvertenza accanto al nome dell'agent vocale, che indica che la chiamata non è riuscita.

1.  Puoi filtrare l'elenco delle chiamate visualizzando quelle in una data specifica e filtrandole per nome dell'agent.

1. Per accedere ai log di errore di chiamata di una chiamata individuale, fai clic sull'icona **Logs** nella colonna **Failure Logs** di tale chiamata.

1. Puoi esaminare l'elenco dettagliato dei log di messaggio nella nuova vista utilizzando i seguenti metodi:
  * Ricerca i log di errore
  * Filtra i messaggi in base al tipo di log, **Error** o **Warn**
  * Scarica il tuo dataset
  * Ordina i log di errore per data/ora in ordine ascendente o discendente

1. Per visualizzare ogni messaggio di log di errore nel dettaglio, fai clic sulla freccia all'inizio della riga di cui sei interessato per espandere la vista. Puoi visualizzare ulteriori informazioni dettagliate sui messaggi di log in [Voice Gateway system messages](https://www.ibm.com/support/knowledgecenter/SS4U29/messages.html){:new_window}.

1. Fai clic sull'icona indietro all'inizio della pagina per ritornare al dashboard _Usage_.

## Link correlati
Utilizza le ulteriori informazioni dettagliate sulla registrazione in [Troubleshooting](https://www.ibm.com/support/knowledgecenter/SS4U29/troubleshooting.html){:new_window}, dalla documentazione IBM Voice Gateway.
