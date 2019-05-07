---

copyright:
  years: 2018
lastupdated: "2018-10-30"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Eventi dell'Activity Tracker
{: #activity-tracker}

Utilizza il servizio {{site.data.keyword.cloudaccesstrailfull}} per tracciare il modo in cui utenti e applicazioni interagiscono con il servizio {{site.data.keyword.iva_full}} in {{site.data.keyword.Bluemix}}.
{: shortdesc}

Il servizio {{site.data.keyword.cloudaccesstrailfull_notm}} registra le attività avviate dall'utente che modificano lo stato di un servizio in {{site.data.keyword.Bluemix_notm}}. Per ulteriori informazioni, vedi [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started#getting-started).

## Elenco di eventi
{: #event-List}

La seguente tabella elenca le azioni che generano un evento.

|Azione| Descrizione |
| --- | ---- |
| `create agent: POST /config/submitconfig` | Crea un nuovo Voice Agent |
| `update agent: POST /config/submitconfig` | Aggiorna un Voice Agent |
| `Update concurrency: POST /config/updatemax` | Aggiorna la simultaneità di chiamate massima |
| `delete agent: POST /config/submitconfig` | Elimina un Voice Agent |
{: caption="Tabella 1. Azioni che generano eventi" caption-side="top"}

## Dove visualizzare gli eventi attività
{: #view-event}

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} sono disponibili nel dominio dell'account {{site.data.keyword.cloudaccesstrailshort}} disponibile nella regione {{site.data.keyword.Bluemix_notm}} dove gli eventi vengono generati.

## Filtro di eventi
{: #filter_events}

### Filtro in base all'ID Voice Agent
{: #filter_id}

Puoi filtrare l'elenco di eventi attività per uno specifico Voice Agent in base al suo ID istanza.

1. Vai alla pagina **Manage** in {{site.data.keyword.cloudaccesstrailshort}}.
2. Immetti `target.name_str` nel **Search Field** e il tuo ID istanza Voice Agent nel campo **Search** come una stringa. Controlla che l'ID istanza Voice Agent sia codificato in percentuale e che utilizzi una ricerca con caratteri jolly, _*_ .

Ad esempio, per cercare il tuo ID istanza Voice Agent, `serviceInstanceId=crn%3A...`.

  * **Search Field**: `target.name_str`
  * **Search**: `"*crn%3A...*"`

### Filtro in base all'evento azione
{: #filter_action}

Puoi anche filtrare l'elenco di eventi attività per specifici eventi azione

1. Vai alla pagina **Manage** in {{site.data.keyword.cloudaccesstrailshort}} e immetti il seguente valore di configurazione per ciascuno dei campi.

  * **View logs**: `Space logs`
  * **Search Field**: `action_str`
  * **Search**: `"action string"`

## Creazione di filtri avanzati
{: #advanced_filters}

Puoi anche creare dei filtri avanzati utilizzando `AND` o `OR` per combinare i termini di ricerca nel campo **Search**.

Ad esempio, filtra in base a uno specifico ID istanza Voice Agent e una specifica azione.

* **View logs**: `Space logs`
* **Search Field**: `target.name_str`
* **Search**: `"*crn%3A...*" AND action_str:"action string"`

**Ricorda**: controlla che l'ID istanza Voice Agent sia codificato in percentuale e che utilizzi una ricerca con caratteri jolly, _*_ .
