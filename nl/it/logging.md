---

copyright:
  years: 2018
lastupdated: "2018-11-12"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Visualizzazione dei log di chiamata e utilizzo
{: #logging}

Puoi visualizzare i log di chiamata e della cronologia di utilizzo dei tuoi Voice Agent dal dashboard {{site.data.keyword.Bluemix_notm}}.
{: shortdesc}

## Informazioni sulla registrazione

La registrazione viene abilitata automaticamente per {{site.data.keyword.iva_full}}. Puoi visualizzare i tuoi log di chiamata del Voice Agent nel dashboard _Utilizzo_.

Il dashboard _Utilizzo_ ti mostra le statistiche veloci sul tuo utilizzo del servizio e le rimanenti risorse disponibili nel tuo piano. Queste informazioni includono il numero massimo di connessioni simultanee riscontrate nel mese corrente e il numero massimo di connessioni simultanee disponibili nel tuo piano. Nella casella _Minuti chiamata_, puoi visualizzare il numero di minuti gratuiti inclusi nel piano e il numero di minuti utilizzati. La sezione _Log chiamate_ segue le tue _Statistiche rapide_.

Puoi filtrare _Log chiamate_ e _Minuti chiamata_ in base alla data e in base a uno o più nomi o numeri di Voice Agent per ridurre il numero di chiamate visualizzate e isolare log di chiamata specifici. Puoi inoltre filtrare i _Log chiamate_ per visualizzare solo le chiamate non riuscite.

Per ulteriori informazioni sulla creazione e la modifica dei Voice Agent, vedi [Gestione dei Voice Agent](/docs/services/voice-agent?topic=voice-agent-managing).

##  Visualizzazione dei log di chiamata

1. Dal tuo dashboard {{site.data.keyword.iva_short}}, passa al dashboard _Utilizzo_ per visualizzare le _Statistiche rapide_ e i _Log chiamate_. Ogni riga nella tabella _Log chiamate_ corrisponde a una chiamata.

      Per ogni chiamata, puoi visualizzare il nome e il numero di telefono del tuo Voice Agent, le ore di avvio e arresto e la durata della chiamata. Potresti inoltre visualizzare un simbolo di avvertenza accanto al nome del Voice Agent, che indica che la chiamata non è riuscita.

1.  Puoi filtrare l'elenco delle chiamate visualizzando quelle in una data specifica e filtrandole in base al nome o al numero di Voice Agent. Puoi anche scegliere di visualizzare solo le chiamate non riuscite.

1. Per accedere ai log di errore di chiamata per una singola chiamata, fai clic sui puntini nella colonna **Azioni** per tale chiamate per espandere il menu. Scegli quindi **Log di errore**. Questa opzione viene visualizzata solo per le chiamate non riuscite.

1. Puoi esaminare l'elenco dettagliato dei log di messaggio nella nuova vista utilizzando i seguenti metodi:
  * Ricerca i log di errore
  * Filtra i messaggi in base al tipo di log, **Errore** o **Avvertenza**
  * Scarica il tuo dataset
  * Ordina i log di errore per data/ora in ordine ascendente o discendente

1. Per visualizzare ogni messaggio di log di errore nel dettaglio, fai clic sulla freccia all'inizio della riga di cui sei interessato per espandere la vista. Puoi visualizzare ulteriori informazioni dettagliate sui messaggi di log in [Voice Gateway system messages](https://www.ibm.com/support/knowledgecenter/SS4U29/messages.html){:new_window}.

1. Fai clic sull'icona indietro all'inizio della pagina per ritornare al dashboard _Utilizzo_.

## Link correlati
Utilizza le ulteriori informazioni dettagliate sulla registrazione in [Troubleshooting](https://www.ibm.com/support/knowledgecenter/SS4U29/troubleshooting.html){:new_window}, dalla documentazione IBM Voice Gateway.
