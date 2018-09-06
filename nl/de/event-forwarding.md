---

copyright:
  years: 2018
lastupdated: "2018-08-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Ereignisweiterleitung für Sprachagenten aktivieren
{: #event_forwarding}

Sie können die Ereignisweiterleitung aktivieren, um Informationen zu den von Ihren Sprachagenten verarbeiteten Anrufen in {{site.data.keyword.iva_full}} zu erfassen, indem Sie einen {{site.data.keyword.cloudantfull}}-Datenbankservice verwenden.
{: shortdesc}

Möglicherweise möchten Sie Anrufdaten von {{site.data.keyword.iva_short}} erfassen und analysieren, um die Natürlichkeit des Dialogs für den Anrufer zu verbessern. Jeder Sprachagent, den Sie erstellen, kann Berichte an eine angegebene {{site.data.keyword.cloudant_short_notm}} weiterleiten, die Sie verwalten. Zu den berichteten Ereignissen gehören CDR-Ereignisse (Call Detail Record, Datensatz mit Anrufdetails), Transkriptionsereignisse sowie Dialogwechselereignisse. Weitere Informationen über die Typen von Ereignissen, die Sie weiterleiten können, finden Sie im Abschnitt [Berichterstellungsereignisse](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}.

Die Analyse der Daten aus diesen Ereignissen kann helfen, Dialoge anzupassen, Absichten zu präzisieren und das Gesamterlebnis des Anrufers zu verbessern.

Wenn Sie Sprachagenten erstellen oder bearbeiten, können Sie auch die Aktivierung der Ereignisweiterleitung wählen. Weitere Details zur Erstellung und Bearbeitung von Sprachagenten finden Sie unter [Sprachagenten verwalten](managing.html). Zur Aktivierung der Ereignisweiterleitung müssen Sie {{site.data.keyword.cloudant_short_notm}}-Kontoinformationen, einschließlich Kontonamen und Kennwort, angeben.

**Wichtig:** Die CDR-, Transkriptions- und Dialogwechselereignisse enthalten Informationen von Ihren Benutzern, die möglicherweise geschützte Gesundheitsinformationen (Protected Health Information, PHI), persönlich identifizierbare Daten (Personally Identifiable Information, PII) oder Zahlungskarteninformationen (Payment Card Industry Data Security Standard, PCI DSS) enthalten. Um eine Gefährdung der personenbezogenen Daten zu vermeiden, müssen Sie sicherstellen, dass Ihre {{site.data.keyword.cloudant_short_notm}}-Instanz die vertraulichen Informationen, die Ihre Benutzer während des Dialogs freigeben, ordnungsgemäß schützt.


## Ereignisweiterleitung aktivieren
{: #enable-event-forwarding}

Sie können die Ereignisweiterleitung aktivieren, wenn Sie Ihre Sprachagenten im Dashboard _Verwalten_ in der {{site.data.keyword.Bluemix_short}} erstellen oder bearbeiten.

1. Wählen Sie im Abschnitt **Ereignisweiterleitung** nach dem Konfigurationsabschnitt für {{site.data.keyword.texttospeechshort}} die Option **Ereignisweiterleitung aktivieren**.

1. Wählen Sie entweder **Meine {{site.data.keyword.cloudant_short_notm}}-Serviceinstanz** oder **Andere {{site.data.keyword.cloudant_short_notm}}-Serviceinstanz** aus.
  * Wenn Sie **Meine {{site.data.keyword.cloudant_short_notm}}-Serviceinstanz** verwenden, wählen Sie den Namen und Benutzernamen für das **{{site.data.keyword.cloudant_short_notm}}-Konto** aus den entsprechenden Listen aus.
  * Wenn Sie **Andere {{site.data.keyword.cloudant_short_notm}}-Serviceinstanz** verwenden, geben Sie entweder den {{site.data.keyword.cloudant_short_notm}}-Benutzernamen und das entsprechende Kennwort oder den API-Schlüssel für das Konto ein.

1. Wählen Sie **Aktivieren** für jeden Ereignistyp, der weitergeleitet werden soll, und wählen Sie anschließend die Datenbank aus, an die die Ereignisse weitergeleitet werden sollen.
  * CDR-Ereignisse (Call Detail Record, Datensatz mit Anrufdetails)
  * Transkriptionsereignisse
  * Dialogwechselereignisse

1. Lassen Sie sich Ihre Datenbank anzeigen, um sicherzustellen, dass die Ereignisberichte ordnungsgemäß weitergeleitet werden.

## Zugehörige Links
* [IBM Voice Gateway: Berichterstellungsereignisse](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
