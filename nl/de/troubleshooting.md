---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Fehlerbehebung und Support
{: #troubleshooting}

Sie haben Probleme mit {{site.data.keyword.iva_full}}? Lesen Sie die Tipps zur Fehlerbehebung für häufig auftretende Probleme und wenden Sie sich mit Fragen an die Community.
{: shortdesc}

## Fehlerbehebung für {{site.data.keyword.iva_short}}
{: #how-to}

Zur Fehlerbehebung für Probleme, die bei Ihren Sprachagenten auftreten können, können Sie Protokolle, Nutzungsdaten und die Ereignisweiterleitung verwenden, um nach Aufzeichnungen zu Fehlern und Ausfällen zu suchen. Anhand dieser Aufzeichnungen können Sie Probleme, die bei den Sprachagenten auftreten, diagnostizieren und beheben. Wenn bei {{site.data.keyword.iva_short}} Probleme auftreten, führen Sie die folgenden Schritte aus.

1. Wenn ein Anruf fehlschlägt, liefert der letzte {{site.data.keyword.conversationshort}}-Dialogwechsel möglicherweise die Erklärung für den Fehler.

1. Nutzungsprotokolle enthalten alle Fehler, die möglicherweise während eines bestimmten Anrufs aufgetreten sind. Weitere Informationen hierzu finden Sie im Abschnitt [Nutzung und Anrufprotokolle anzeigen](/docs/services/voice-agent?topic=voice-agent-logging).

1. Überprüfen Sie die Protokolle des Service-Providers auf möglicher Signalfehler. Twilio stellt beispielsweise Protokolle für jeden bereitgestellten SIP-Trunk zur Verfügung.

1. Wenn Sie die [Ereignisweiterleitung für Sprachagenten aktivieren](/docs/services/voice-agent?topic=voice-agent-event_forwarding), können Sie den Sprachagenten so konfigurieren, dass CDRs (Call Detail Records, Datensätze mit Anrufdetails) an eine Cloudant-Datenbank weitergeleitet werden und die Fehlerursache ermittelt wird. Andere Ereignisse, wie z. B. {{site.data.keyword.conversationshort}}-Dialogwechselereignisse, können Details zu jedem Dialogwechsel innerhalb eines Anrufs liefern.

**Wichtig:** Die CDR-, Transkriptions- und Dialogwechselereignisse enthalten Informationen von Ihren Benutzern, die möglicherweise geschützte Gesundheitsinformationen (Protected Health Information, PHI), persönlich identifizierbare Daten (Personally Identifiable Information, PII) oder Zahlungskarteninformationen (Payment Card Industry Data Security Standard, PCI DSS) enthalten. Um eine Gefährdung der personenbezogenen Daten zu vermeiden, müssen Sie sicherstellen, dass Ihre {{site.data.keyword.cloudant_short_notm}}-Instanz die vertraulichen Informationen, die Ihre Benutzer während des Dialogs freigeben, ordnungsgemäß schützt.


## Hilfe aufrufen
{: #help}

Wenn Sie Hilfe benötigen, nehmen Sie an unserer Entwickler-Community teil, indem Sie Ihre Fragen oder Kommentare an einem der folgenden Orte posten, die alle aktiv überwacht werden.

* Zum Posten im [dwAnswers-Forum ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/topics/voice-agent/) verwenden Sie den Tag `voice-agent`
* Zum Posten in [StackOverflow ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://stackoverflow.com/questions/tagged/voice-agent){: new_window} verwenden Sie den Tag `voice-agent`
* Besuchen Sie uns in Slack im [IBM Cloud Technology ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://slack-invite-ibm-cloud-tech.mybluemix.net/)-Team unter dem Kanal `#ibmvoicegateway`

**Denken Sie daran**: Bevor Sie Protokolle oder Aufzeichnungen von Anrufen weiterleiten, müssen Sie alle personenbezogenen Daten entfernen, die die Anrufer möglicherweise während der Dialoge angegeben haben.

## Tipps zur Fehlerbehebung
{: #troubleshooting-tips}

### Warum erhalte ich keine Antwort am Telefon, wenn ich meinen Sprachagenten anrufe?

Ihr Anruf hat wahrscheinlich keine Verbindung zu den Services hergestellt. Dieses Problem tritt auf, wenn die {{site.data.keyword.iva_short}}-Serviceinstanz nicht ordnungsgemäß eingerichtet ist. Aktivieren Sie die folgenden Einstellungen für den Sprachagenten:

* Stellen Sie sicher, dass die Telefonnummer im Dashboard _Verwalten_ des Sprachagenten mit der Telefonnummer des SIP-Trunking-Providers, wie z. B. NetFoundry oder Twilio, übereinstimmt.

   **Hinweis:** Bei der Angabe der Telefonnummer im Dashboard _Verwalten_ des Sprachagenten muss die Landes- und Ortskennzahl mit angegeben werden. Beispiel: `18884253968`.

* Überprüfen Sie, ob die Watson-Serviceberechtigungsnachweise, die URLs und die {{site.data.keyword.conversationshort}}-Arbeitsbereich-ID alle gültig sind.
* Überprüfen Sie, ob der Dialog im {{site.data.keyword.conversationshort}}-Skill korrekt erstellt wurde.
  * Sie können den [Beispieldialog![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) von GitHub für einen vorgefertigten Skill importieren. Details zum Speichern des Beispieldialogs als JSON-Datei und späteren Importieren der Datei als Skill im Tool {{site.data.keyword.conversationshort}} finden Sie in [Schritt 3 im *Lernprogramm "Einführung"*](/docs/services/voice-agent?topic=voice-agent-getting-started#step3).
  * Wenn Sie Ihren eigenen {{site.data.keyword.conversationshort}}-Dialog erstellt haben, überprüfen Sie, ob der Dialog einen Knoten mit der Bedingung `conversation_start` und einen Knoten mit einer Standardantwort enthält. Ausführliche Anweisungen finden Sie unter [Dialog erstellen](/docs/services/assistant?topic=assistant-getting-started#getting-started-build-dialog) in der {{site.data.keyword.conversationshort}}-Dokumentation.
* Sehen Sie im Dashboard _Nutzung_ des Sprachagenten nach, ob Ihr Telefonanruf dort aufgelistet ist. Wenn für Ihren Telefonanruf ein Eintrag vorhanden ist, hat Ihr Sprachagent eine Verbindung zum Watson-Service hergestellt.

### Warum kann ich beim Erstellen eines Sprachagenten keine Telefonnummer angeben?

Überprüfen Sie, ob die von Ihnen angegebene Telefonnummer von einem vorhandenen Sprachagenten verwendet wird. Für eine Telefonnummer können Sie jeweils nur einen Sprachagenten haben. Sie können eine andere Telefonnummer Ihres SIP-Trunking-Providers angeben und diese zum Erstellen eines anderen Sprachagenten verwenden. Alternativ dazu können Sie [den vorhandenen Sprachagenten im Dashboard _Verwalten_ löschen](/docs/services/voice-agent?topic=voice-agent-managing#delete_va), um die Telefonnummer freizugeben, und anschließend einen neuen Sprachagenten erstellen.

### Warum treten bei meinen Anrufen häufig Fehler auf?

Bei Sprachagenten können Probleme auftreten, wenn Anrufe fehlschlagen, da eine Serviceorchestrierungsengine (Service Orchestration Engine, SOE) eine Transaktion mit langer Laufzeit initiiert und keine zeitnahe Antwort an den Sprachagenten sendet. Wenn eine Transaktion das {{site.data.keyword.conversationshort}}-Standardzeitlimit überschreitet, schlägt der Anruf fehl. Um das Fehlschlagen von Anrufen zu vermeiden, kann die SOE den {{site.data.keyword.conversationshort}}-Standardzeitlimitwert mithilfe der Statusvariablen `vgwConversationResponseTimeout` ändern. Informationen hierzu finden Sie in [Im {{site.data.keyword.conversationshort}}-Dialog festgelegte Variablen](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html#variables-conv).


### Verschiedene Einschränkungen

* Für die Region **Dallas** oder die Region **Washington DC** ist die Erstellung neuer Watson-Serviceinstanzen direkt im Dashboard _Sprachagenten erstellen_ möglich. Zum Verbinden Ihres Sprachagenten mit Watson-Services in anderen Regionen müssen Sie die Watson-Services vor dem Erstellen des Sprachagenten im Dashboard _Verwalten_ erstellen.

* Nur Verbindungen zum öffentlichen Telefonnetz werden unterstützt.

* Alle Sprachagentenkonfigurationen müssen mittels der API im {{site.data.keyword.conversationshort}}-Service angegeben werden.
