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


# Nutzung und Anrufprotokolle anzeigen
{: #logging}

Sie können die Nutzungsgeschichte und die Anrufprotokolle für Ihre Sprachagenten über das {{site.data.keyword.Bluemix_notm}}-Dashboard anzeigen.
{: shortdesc}

## Informationen zur Protokollierung

Die Protokollierung ist für {{site.data.keyword.iva_full}} automatisch aktiviert. Sie können die Anrufprotokolle Ihres Sprachagenten im Dashboard _Nutzung_ einsehen.

Das Dashboard _Nutzung_ zeigt Ihnen Schnellstatistiken zu Ihrer Servicenutzung sowie die nach Ihrem Plan verbleibenden verfügbaren Ressourcen an. Diese Informationen umfassen die maximale Anzahl der Verbindungen, die im laufenden Monat gleichzeitig aufgetreten sind, sowie die maximale Anzahl an Verbindungen, die laut Ihrem Plan verfügbar sind, an. Im Feld _Anrufe - Minuten_ können Sie die Anzahl freier Minuten einsehen, die im Plan enthalten sind, sowie die Anzahl der bereits verbrauchten Minuten. Der Abschnitt _Anrufprotokolle_ folgt Ihren _Schnellstatistiken_.

Sie können _Anrufprotokolle_ und _Anrufe - Minuten_ nach Datum sowie entweder nach Name(n) oder nach Nummer(n) des Sprachagenten filtern, um die Anzahl der angezeigten Anrufe zu reduzieren und bestimmte Anrufprotokolle zu isolieren. Darüber hinaus können Sie _Anrufprotokolle_ so filtern, dass nur fehlgeschlagene Anrufen angezeigt werden.

Weitere Informationen zur Erstellung und Bearbeitung von Sprachagenten finden Sie unter [Sprachagenten verwalten](/docs/services/voice-agent?topic=voice-agent-managing).

##  Anrufprotokolle anzeigen

1. Navigieren Sie von Ihrem {{site.data.keyword.iva_short}}-Dashboard aus zum Dashboard _Nutzung_, um die _Schnellstatistiken_ und _Anrufprotokolle_ anzuzeigen. Jede Zeile in der Tabelle _Anrufprotokolle_ entspricht einem Anruf.

      Für jeden Anruf können Sie den Namen und die Telefonnummer Ihres Sprachagenten, die Start- und Stoppzeiten und die Dauer des Anrufs anzeigen. Möglicherweise wird Ihnen neben dem Namen des Sprachagenten auch ein Warnsymbol angezeigt, das angibt, dass der Anruf fehlgeschlagen ist.

1.  Sie können die Liste der Anrufe filtern, indem Sie Anrufe eines bestimmten Datums anzeigen und die Anrufe nach Namen oder Nummern des Sprachagenten filtern. Es ist auch möglich, nur fehlgeschlagene Anrufe anzuzeigen.

1. Für den Zugriff auf Anruffehlerprotokolle für einen einzelnen Anruf klicken Sie auf die Punkte in der Spalte **Aktionen** für den betreffenden Anruf, um das Menü zu erweitern. Wähle Sie dann **Fehlerprotokolle** aus. Diese Option wird nur für fehlgeschlagene Anrufe angezeigt.

1. Sie können die detaillierte Liste von Nachrichtenprotokollen in der neuen Ansicht mithilfe der folgenden Methoden prüfen:
  * Die Fehlerprotokolle durchsuchen
  * Nachrichten basierend auf dem Protokolltyp, entweder **Fehler** oder **Warnung**, filtern
  * Ihren Datensatz herunterladen
  * Die Fehlerprotokolle nach Zeitmarke aufsteigend oder absteigend sortieren

1. Um eine beliebige Fehlerprotokollnachricht detaillierter anzuzeigen, klicken Sie auf den Pfeil am Anfang der betreffenden Zeile, sodass die Ansicht erweitert wird. Weitere Detailinformationen zu Protokollnachrichten finden Sie in den [Voice Gateway-Systemnachrichten](https://www.ibm.com/support/knowledgecenter/SS4U29/messages.html){:new_window}.

1. Klicken Sie auf den rückwärts gerichteten Pfeil am Seitenanfang, um zum Dashboard _Nutzung_ zurückzukehren.

## Zugehörige Links
Ausführliche Informationen zum Protokollieren finden Sie im Abschnitt [Fehlerbehebung](https://www.ibm.com/support/knowledgecenter/SS4U29/troubleshooting.html){:new_window} in der IBM Voice Gateway-Dokumentation.
