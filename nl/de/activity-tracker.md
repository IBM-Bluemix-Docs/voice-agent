---

copyright:
  years: 2018
lastupdated: "2018-10-30"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Activity Tracker-Ereignisse
{: #activity-tracker}

Mit dem {{site.data.keyword.cloudaccesstrailfull}}-Service können Sie die Interaktion von Benutzern und Anwendungen mit dem {{site.data.keyword.iva_full}}-Service in {{site.data.keyword.Bluemix}} verfolgen. {: shortdesc}

Der {{site.data.keyword.cloudaccesstrailfull_notm}}-Service zeichnet die vom Benutzer initiierten Aktivitäten auf, die den Status eines Service in {{site.data.keyword.Bluemix_notm}} ändern. Weitere Informationen finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}](../cloud-activity-tracker/index.html#getting-started-with-cla).

## Ereignisliste
{: #event-List}

In der folgenden Tabelle sind die Aktionen aufgeführt, durch die ein Ereignis generiert wird.

|Aktion| Beschreibung |
| --- | ---- |
| `Agenten erstellen: POST /config/submitconfig` | Neuen Sprachagenten erstellen |
| `Agenten aktualisieren: POST /config/submitconfig` | Sprachagenten aktualisieren |
| `Gleichzeitige Ausführung aktualisieren: POST /config/updatemax` | Maximum für gleichzeitige Aufrufe aktualisieren |
| `Agenten löschen: POST /config/submitconfig` | Sprachagenten löschen |
{: caption="Tabelle 1. Aktionen, die Ereignisse generieren" caption-side="top"}

## Aktivitätsereignisse anzeigen
{: #view-event}

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse sind in der {{site.data.keyword.cloudaccesstrailshort}}-Kontodomäne verfügbar, die in der {{site.data.keyword.Bluemix_notm}}-Region zur Verfügung steht, in der die Ereignisse generiert werden.

## Ereignisse filtern
{: #filter_events}

### Nach Sprachagenten-ID filtern
{: #filter_id}

Die Liste der Aktivitätsereignisse kann für einen bestimmten Sprachagenten anhand der Instanz-ID gefiltert werden.

1. Rufen Sie die Seite **Verwalten** in {{site.data.keyword.cloudaccesstrailshort}} auf.
2. Geben Sie `target.name_str` im **Suchfeld** und die ID der Sprachagenteninstanz als Zeichenfolge im Feld **Suche** ein. Stellen Sie sicher, dass die ID der Sprachagenteninstanz mit einer Prozentcodierung codiert ist und dass eine Platzhaltersuche, _*_, verwendet wird.

Beispiel: Geben Sie zum Suchen nach der ID der Sprachagenteninstanz `serviceInstanceId=crn%3A...` ein.

  * **Suchfeld**: `target.name_str`
  * **Suche**: `"*crn%3A...*"`

### Nach Aktionsereignis filtern
{: #filter_action}

Darüber hinaus kann die Liste der Aktivitätsereignisse für bestimmte Aktionsereignisse gefiltert werden.

1. Rufen Sie die Seite **Verwalten** in {{site.data.keyword.cloudaccesstrailshort}} auf und geben Sie die folgenden Konfigurationswerte für die jeweiligen Felder ein.

  * **Protokolle anzeigen**: `Bereichsprotokolle`
  * **Suchfeld**: `action_str`
  * **Suche**: `"action string"`

## Erweiterte Filter erstellen
{: #advanced_filters}

Erweiterte Filter können erstellt werden, indem `AND` oder `OR` zum Kombinieren von Suchbegriffen im Feld **Suche** verwendet werden.

Beispiel: Sie können anhand einer bestimmten Sprachagenteninstanz-ID und einer bestimmten Aktion filtern.

* **Protokolle anzeigen**: `Bereichsprotokolle`
* **Suchfeld**: `target.name_str`
* **Suche**: `"*crn%3A...*" AND action_str:"action string"`

**Nicht vergessen**: Stellen Sie sicher, dass die ID der Sprachagenteninstanz mit einer Prozentcodierung codiert ist und dass eine Platzhaltersuche, _*_, verwendet wird.
