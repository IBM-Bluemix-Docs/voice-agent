---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Lernprogramm "Einführung"
{{site.data.keyword.iva_full}} hilft Ihnen, unter Verwendung des Session Initiation Protocol (SIP) eine Gruppe von koordinierten Watson-Services in das Telefonnetz zu integrieren. Dieses Lernprogramm beschreibt das Einrichten eines kognitiven Sprachagenten, den Sie von jedem Telefon aus anrufen können.
{: shortdesc}

Eine Demonstration, wie Sie Ihren ersten Sprachagenten erstellen können, sehen Sie in diesem [{{site.data.keyword.iva_full_notm}}-Lernprogramm: ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/).
{: tip}

## Vorbereitende Schritte
{: #prereqs}

Erstellen Sie ein neues Konto oder melden Sie sich beim vorhandenen Konto in [{{site.data.keyword.Bluemix_short}}](https://console.bluemix.net/) an.

## Schritt 1: {{site.data.keyword.iva_short}}-Serviceinstanz in {{site.data.keyword.Bluemix_notm}} erstellen
{: #step1}

Prüfen Sie auf der [{{site.data.keyword.iva_short}}-Katalogseite](https://console.bluemix.net/catalog/services/voice-agent-with-watson) die Serviceinformationen und klicken Sie auf **Erstellen**.

Nach dem Erstellen des Service vermerken Sie den Endpunkt des Sprachagenten im Dashboard _Einführung_. Zum Konfigurieren Ihres SIP-Trunks benötigen Sie den Endpunkt-SIP-URI.

## Schritt 2: SIP-Trunk für die Weiterleitung von Anrufen an {{site.data.keyword.iva_short}} erstellen
{: #step2}

1. Erstellen Sie einen SIP-Trunk über einen der folgenden unterstützten Provider. Ordnen Sie dann dem SIP-Trunk eine Telefonnummer zu.

  * [NetFoundry](connect-SIP.html#NetFoundry-setup)
  * [Twilio](connect-SIP.html#twilio-setup)
  * [AT&T und andere SIP-Trunking-Provider](connect-SIP.html#att-other)
  * [Peering mit {{site.data.keyword.iva_short}}](connect-SIP.html#peering)

## Schritt 3: Einen Sprachagenten erstellen und eine Verbindung herstellen
{: #step3}

1. Gehen Sie zum Dashboard _Verwalten_ im {{site.data.keyword.iva_short}}-Dashboard und klicken Sie auf **Sprachagenten erstellen**.

2. Gehen Sie zu den Grundeinstellungen für Ihren Sprachagenten:
  * **Name:** Ein eindeutiger Name für Ihren Sprachagenten, z. B. `Kundendienst`
  * **Telefonnummer:** Die vollständige Telefonnummer, die Sie Ihrem SIP-Trunk zugeordnet haben, einschließlich Landes- und Ortsvorwahl. Für eine 800-er Nummer in den Vereinigten Staaten z. B. geben Sie die Nummer mit 18883334444 an. Die Telefonnummer darf Leerzeichen und die Zeichen + ( ) - enthalten.
  * **Beschreibung:** Eine optionale Beschreibung der Verwendung

3. Erstellen Sie für Ihren Sprachagenten die {{site.data.keyword.conversationshort}}-, die {{site.data.keyword.speechtotextshort}}- und die {{site.data.keyword.texttospeechshort}}-Serviceinstanz. Für die Erstellung eines Sprachagenten können Sie eine der folgenden Methoden wählen:
  * Klicken Sie auf **Sprachagenten erstellen**, um alle Services sowie einen Sprachagenten mit der Standardkonfiguration in nur einem Schritt zu erstellen.
  * Alternativ klicken Sie auf die Servicenamen, um die Services selbst zu erstellen. Kehren Sie dann zu {{site.data.keyword.iva_short}} zurück und erstellen Sie separat einen Sprachagenten.

   Wenn Sie eine {{site.data.keyword.conversationshort}}-Serviceinstanz manuell erstellt haben, fügen Sie einen Dialog hinzu, um Ihren Sprachagenten testen zu können.  Für einen schnellen Start klonen Sie den [Beispieldialog![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) aus GitHub und [importieren das Beispiel](../conversation/configure-workspace.html#creating-workspaces) als einen Arbeitsbereich:

   1. Auf der GitHub-Seite mit dem Beispieldialog klicken Sie auf die Zeilennummer `1` und wählen Sie **... > Zeile kopieren** aus. Fügen Sie den kopierten Text in eine Datei ein und speichern Sie diese als JSON-Datei, z. B. `voice-gateway-conversation-en.json`.
   2. Starten Sie das {{site.data.keyword.conversationshort}}-Tool. Klicken Sie auf der Seite _Arbeitsbereiche_ auf das Symbol ![Arbeitsbereich importieren](../conversation/images/workspace_import.png) und importieren Sie die JSON-Datei.

  Alternativ können Sie [einen eigenen Dialog erstellen](https://console.bluemix.net/docs/services/conversation/dialog-build.html), um Ihre Produktionsumgebung zu simulieren. Ihr Dialog muss mindestens einen Knoten mit der Bedingung `conversation_start` und einen Knoten mit einer Standardantwort enthalten.

## Nächste Schritte
{: #next}

Testen Sie Ihren Sprachagenten, indem Sie die zugehörige Telefonnummer anrufen. Wenn Sie eine Antwort hören, ist Ihr Sprachagent aktiv!

Wenn Sie keine Antwort hören, können Sie alle Ihre Anrufprotokolle und die Nutzung des Sprachagenten im Dashboard _Nutzung_ überprüfen. Weitere Informationen hierzu finden Sie im Abschnitt [Nutzung und Anrufprotokolle anzeigen](logging.html).

Über das Dashboard _Verwalten_ können Sie die Einstellungen für den Sprachagenten bearbeiten, Sprachagenten erstellen oder entfernen und mehrere Watson-Servicestandorte zum Sprachagenten hinzufügen. Weitere Informationen finden Sie im Abschnitt [Sprachagenten verwalten](managing.html).

Darüber hinaus können Sie erweiterte Einstellungen konfigurieren, wie z. B. den Schutz der SIP-Verbindung Ihres Twilio-Kontos. Weitere Informationen finden Sie in [Verbindungen schützen](secure-trunking.html).
