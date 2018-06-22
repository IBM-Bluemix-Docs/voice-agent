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

# Sprachagenten mithilfe der API programmieren
{: #api}

Das Verhalten Ihres Sprachagenten kann durch Definieren von Aktionstags und Statusvariablen im {{site.data.keyword.conversationfull}}-Service gesteuert werden. Aktionstags initiieren Aktionen, die Ihr Sprachagent während einer Dialogsitzung unternimmt; Statusvariablen definieren Eigenschaften des Sprachagenten, die während des ganzen Dialogs bestehen bleiben, sofern sie nicht geändert werden.
{: shortdesc}

Da {{site.data.keyword.iva_full}} auf IBM Voice Gateway basiert, funktioniert die API auf gleiche Weise. Wenn Sie mit Voice Gateway vertraut sind, können Sie in Ihren {{site.data.keyword.conversationshort}}-Dialogen mit {{site.data.keyword.iva_short}} die gleichen Aktionen und Statusvariablen verwenden. In [Aktionstags und Statusvariablen in der Voice Gateway-API](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html) finden Sie weitere Informationen.
{: tip}

## JSON in der Dialogantwort bearbeiten
{: #json-editor}

Sowohl Aktionen als auch Status werden in einer Dialogknotenantwort im JSON-Format definiert. Zum Bearbeiten des JSON-Codes öffnen Sie den JSON-Editor.

1. Wählen Sie im {{site.data.keyword.Bluemix_short}}-Dashboard Ihre {{site.data.keyword.conversationshort}}-Serviceinstanz aus.
1. Starten Sie das {{site.data.keyword.conversationshort}}-Tool.
1. Klicken Sie auf den Arbeitsbereich, der den zu bearbeitenden Dialog enthält.
1. Wechseln Sie zur Registerkarte **Dialog** und wählen Sie den Knoten aus, an dem Sie eine Aktion oder einen Status festlegen möchten.
1. Klicken Sie in der Antwort auf das Symbol ![Erweiterte Antwort](../conversation/images/kabob.png) und wählen Sie **JSON-Editor öffnen**.

Im JSON-Editor können Sie Aktionen für die Eigenschaft `output` und die Status für die Eigenschaft `context` definieren, wie in den folgenden Abschnitten beschrieben.

## Aktionen initiieren
{: #defining-actions}

Um während eines Anrufs Aktionen im Sprachagenten zu initiieren, können Sie in der Eigenschaft `output` im JSON-Format Aktionstags für einen {{site.data.keyword.conversationshort}}-Dialogknoten definieren. Sie können entweder eine Einzelaktion im Tag `vgwAction` oder eine Aktionssequenz im Tag `vgwActionSequence` definieren. Jede Aktion setzt sich aus einer Eigenschaft `command`, gefolgt von einer optionalen Eigenschaft `parameter`, zusammen, um Attribute für Befehle zu definieren, die sie benötigen.

### Einzelaktionen
{: #single-actions}

Um eine Einzelaktion durchzuführen, definieren Sie die Aktion im Tag `vgwAction` zusammen mit allen notwendigen Parameterattributen. Im `text`-Block der Eigenschaft `output` können Sie optional eine Äußerung einschließen, die der Sprachagent nach Ausführung der Aktion abspielt.

Die folgende Einzelaktion im Tag `vgwAction` fordert den Sprachagenten auf, den Anruf zu beenden, sobald die Knotenantwort ausgelöst wird. Da der Befehl `vgwActHangup` über keine Parameter verfügt, sind keine definiert.
```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActHangup"
    }
  }
}
```
{: codeblock}

Die folgende Aktion weist den Sprachagenten an, DTMF-Eingaben (Dual-Tone Multi-Frequency Signaling) zu erfassen und den definierten Text für den Anrufer abzuspielen.

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActCollectDtmf",
      "parameters": {
        "dtmfTermKey": "#"
      }
    },
    "text": {
      "values": [
        "Geben Sie Ihre Telefonnummer ein."
      ]
    }
  }
}
```
{: codeblock}

### Aktionssequenzen
{: #action-sequences}

Um eine oder mehr Aktionen für einen einzelnen Dialogwechsel auszuführen, können Sie im Tag `vgwActionSequence` eine Sequenz von Aktionen als JSON-Liste definieren. Die Aktionen werden in der Reihenfolge ausgeführt, wie Sie sie definieren.

Anders als bei Einzelaktionen muss die Aktionsliste die Aktion `vgwActPlayText` enthalten, wenn der Sprachagent unter Verwendung des Tags `vgwActionSequence` eine Äußerung abspielen soll. Anders als beim Tag `vgwAction` wird eine Äußerung im Feld `output.text` nicht automatisch abgespielt.
{: tip}

Im folgenden, etwas komplexeren Beispiel fordern die im Tag `vgwActionSequence` definierten Aktionen den Sprachagenten auf, die Sprache-Text-Verarbeitung zu inaktivieren und DTMF-Eingaben zu erfassen, während der die Äußerung abspielt.

```json
{
  "output": {
    "vgwActionSequence": [
      {
        "command": "vgwActPauseSTT"
      },
      {
        "command": "vgwActCollectDtmf",
        "parameters": {
          "dtmfTermKey": "#"
        }
      },
      {
        "command": "vgwActPlayText",
        "parameters": {
          "text": [
            "Geben Sie Ihre Sozialversicherungsnummer ein."
          ]
        }
      }
    ]
  }
}

```
{: codeblock}


### Aktionsbefehle und Attribute
{: #actions-and-attributes}

In der folgenden Tabelle sind die Aktionen aufgelistet, die Sie im {{site.data.keyword.conversationshort}}-Dialog angeben können, sowie alle Attribute, die Sie für die einzelnen Aktionen definieren können.

| Aktionsbefehl | Beschreibung | Attribute |
| ----- | ----- | ----- |
| `vgwActPlayText`| Spielt eine Äußerung ab, die vom {{site.data.keyword.texttospeechshort}}-Service in Sprache umgewandelt wird. | <ul><li>`text`: Eine Liste von abzuspielenden Äußerungen. Optional. <p>Beispiel:<br/><code>"text": [<br/>&nbsp;&nbsp;&nbsp;"Hallo. Wie kann ich Ihnen heute helfen?"<br/>&nbsp;&nbsp;&nbsp;]</code><p> Standardmäßig spielt die Aktion eine Liste von Äußerungen ab, die im Feld `output.text` konfiguriert sind. </li><li>`errAudioURL`: Eine URL zu einer Audiodatei, die abgespielt wird, wenn der Sprachagent keine Verbindung zum {{site.data.keyword.texttospeechshort}}-Service aufbauen kann, um die Aktion auszuführen. Die Audiodatei muss das WAV-Format haben.</li></ul>|
| `vgwActPlayUrl` | Spielt eine Audiodatei ab, sobald der einbezogene Text wiedergegeben wird, z. B. für eine Warteschleifenmusik (Music on Hold, MOH) oder für allgemeine einmalige Äußerungen. Wurde kein Text einbezogen, wird die Audiodatei sofort abgespielt. Die Datei muss einkanalig (Mono) und PCM-codiert sein und eine Abtastrate von 8000 Hz bei 16 Bit pro Sample aufweisen. | <ul><li>`url`: Die URL zur abzuspielenden Audiodatei. Erforderlich.</li><li> `playURLInLoop`: Optional auf `Ja` oder `Nein` festgelegt, um anzugeben, ob die URL in einer Schleife abgespielt werden soll. Der Standardwert ist `Nein`.</li></ul> |
| `vgwActHangup` | Beendet den Anruf. | Keine Attribute. |
| `vgwActSetSTTConfig` | Wendet eine Gruppe von Parametern an, die der Sprachagent an den {{site.data.keyword.speechtotextshort}}-Service weiterleiten soll. Der {{site.data.keyword.conversationshort}}-Service definiert die Parameter dynamisch auf Grundlage des Anrufs. | Die Attribute werden transparent als JSON-Eigenschaften an den {{site.data.keyword.speechtotextshort}}-Service weitergeleitet. |
| `vgwActSetTTSConfig` | Wendet eine Gruppe von Parametern an, die der Sprachagent an den {{site.data.keyword.texttospeechshort}}-Service weiterleiten soll. Der {{site.data.keyword.conversationshort}}-Service definiert die Parameter dynamisch auf Grundlage des Anrufs. |  Die Attribute werden transparent als JSON-Eigenschaften an den {{site.data.keyword.texttospeechshort}}-Service weitergeleitet.  |
| `vgwActSetConversationConfig` | Wendet eine Gruppe von Parametern an, mit denen der Sprachagent einen {{site.data.keyword.conversationshort}}-Arbeitsbereich definieren soll. Der {{site.data.keyword.conversationshort}}-Service definiert die Parameter dynamisch auf Grundlage des Anrufs. | <ul><li>`url`: Der `url` Berechtigungsnachweis für die {{site.data.keyword.conversationshort}}-Service-API.</li><li>`workspaceID`: {{site.data.keyword.conversationshort}}-Arbeitsbereich-ID</li><li>`username`: Der `username`-Berechtigungsnachweis für den {{site.data.keyword.conversationshort}}-Service.</li><li>`password`: Der `password`-Berechtigungsnachweis für den {{site.data.keyword.conversationshort}}-Service.</li></ul> |
| `vgwActCollectDtmf` | Weist den Sprachagenten an, DTMF (Dual-Tone Multi-Frequency Signaling)-Eingaben zu erfassen. | Eines der folgenden Attribute muss definiert sein. <ul><li> `dtmfTermKey`: Der DTMF-Beendigungsschlüssel, der das Ende der DTMF-Eingabe signalisiert. Beispiel: "`#`". </li><li> `dtmfCount`: Die Anzahl der zu erfassenden DTMF-Ziffern.</li></ul> Wenn eine dieser Bedingungen erfüllt ist, stoppt der Sprachagent die Erfassung der DTMF-Eingabe. |
| `vgwActPauseDTMF` | Inaktiviert DTMF-Eingaben. Alle DTMF-Eingaben werden ignoriert, bis sie durch die Aktion `vgwActUnPauseDTMF` wieder aktiviert werden. | Keine Attribute. |
| `vgwActUnPauseDTMF` | Aktiviert DTMF-Eingaben erneut, die durch die Aktion `vgwActPauseDTMF` inaktiviert wurden. | Keine Attribute. |
| `vgwActExcludeFromTTSCache` | Weist den Sprachagenten an, die Antwort vom {{site.data.keyword.texttospeechshort}}-Service nicht zwischenzuspeichern. Zum Beispiel sollten Antworten, die sensible PHI-, PII- und PCI DSS-Daten oder dynamische Information wie Kundennamen oder Geburtsdaten enthalten, ausgeschlossen werden. <br/>Dieser Aktionstag muss für jede Äußerung, die nicht zwischengespeichert werden soll, auf dem {{site.data.keyword.conversationshort}}-Dialogknoten festgelegt werden. | Keine Attribute. |
| `vgwActPauseSTT` | Hält die Sprache-Text-Verarbeitung an, bis sie durch die Aktion `vgwActUnPauseSTT` wieder aktiviert wird. Wenn die Aufzeichnung aktiviert und die Sprache-Text-Verarbeitung angehalten ist, wird kein Ton des Anrufers erfasst. | Keine Attribute. |
| `vgwActUnPauseSTT` | Nimmt die Sprache-Text-Verarbeitung wieder auf, die zuvor durch die Aktion `vgwActPauseSTT` angehalten wurde. | Keine Attribute. |
| `vgwActEnableSpeechBargeIn` | Aktiviert das Einsprechen (in eine laufende Bandansage), sodass Anrufer die Wiedergabe des Sprachagenten durch eigenes Sprechen unterbrechen können. | Keine Attribute. |
| `vgwActDisableSpeechBargeIn` | Inaktiviert das Einsprechen (in eine laufende Bandansage), sodass die Wiedergabe des Sprachagenten nicht durch das Sprechen von Anrufern unterbrochen wird. | Keine Attribute. |
| `vgwActEnableDTMFBargeIn`| Aktiviert das DTMF-Einsprechen (in eine laufende Bandansage), sodass Anrufer die Wiedergabe des Sprachagenten durch Drücken einer Taste unterbrechen können. | Keine Attribute. |
| `vgwActDisableDTMFBargeIn` | Inaktiviert das DTMF-Einsprechen (in eine laufende Bandansage), sodass die Wiedergabe des Sprachagenten nicht durch das Drücken von Tasten durch die Anrufern unterbrochen wird. | Keine Attribute. |
| `vgwActForceNoInputTurn` | Erzwingt einen neuen Dialogwechsel, ohne dass auf Eingaben des Anrufers gewartet wird. | Keine Attribute. |
{: caption="Tabelle 1. Aktionen, die über den {{site.data.keyword.conversationshort}}-Service initiiert werden können" caption-side="top"}

## Status festlegen
{: #setting-states}

Um eine Änderung des Status anzugeben, der zwischen den Dialogwechseln verbleibt, tauscht der Sprachagent mit dem konfigurierten {{site.data.keyword.conversationfull}}-Service Statusvariablen aus. Diese Statusvariablen werden in einem {{site.data.keyword.conversationshort}}-Dialogknoten als [Kontextvariablen](https://console.bluemix.net/docs/services/conversation/dialog-build.html#context) im JSON-Format definiert.

Sie können z. B. die folgende Statusvariable definieren, um die Nachricht festzulegen, die an den Anrufer gestreamt wird, wenn die Verbindung zum {{site.data.keyword.conversationshort}}-Service fehlschlägt.

```json
{
  "context": {
    "vgwConversationFailedMessage": "Ich kann leider keine Verbindung zu unserer Hotline herstellen. Bitte versuchen Sie es später noch einmal."
  }
}
```
{: codeblock}

Der Sprachagent geht davon aus, dass der {{site.data.keyword.conversationshort}}-Service statusunabhängig ist und dass alle Status beim Sprachagenten zwischen den Austauschvorgängen mit dem {{site.data.keyword.conversationshort}}-Service beibehalten werden. Der Status für jeden Dialogwechsel innerhalb eines Anrufs wird an den {{site.data.keyword.conversationshort}}-Service geleitet und im Abschnitt `context` der REST-Nachrichten vom Service zurückerhalten.

### Im {{site.data.keyword.conversationshort}}-Dialog festgelegte Statusvariablen
{: #state-variables-conv}

Folgende Statusvariablen können im {{site.data.keyword.conversationshort}}-Dialog festgelegt werden, um das Verhalten Ihres Sprachagenten zu modifizieren.

| Name der Statusvariablen | Erwarteter Wert | Beschreibung |
| -------------- | ------ | ----------- |
| `vgwByeCustomHeader` | Benutzerdefiniert | Definiert einen angepassten Header in einer ausgehenden SIP-Nachricht 'BYE'. Der angepasste Header wird durch die `vgwByeCustomHeaderVal`-Statusvariablen definiert.  |
| `vgwByeCustomHeaderVal` | Benutzerdefiniert | Definiert den Wert eines angepassten Headers in einer ausgehenden SIP-Nachricht 'BYE'. Der Wert des angepassten Headers wird durch die `vgwByeCustomHeader`-Statusvariablen definiert. |
| `vgwPostResponseTimeoutCount` | Zeit in Millisekunden | Die Zeit, die auf eine neue Äußerung gewartet wird, nachdem die Antwort an den Anrufer wiedergegeben wurde. Wird dieser Wert überschritten, empfängt {{site.data.keyword.conversationshort}} eine Textaktualisierung mit dem Wort "vgwPostResponseTimeout", das angibt, dass eine Zeitlimitüberschreitung aufgetreten ist.|
| `vgwConversationFailedMessage` | Textzeichenfolge | Eine Nachricht, die an den Anrufer gestreamt wird, wenn der {{site.data.keyword.conversationshort}}-Service fehlschlägt. Sie können Ihren {{site.data.keyword.conversationshort}}-Dialog so konfigurieren, dass diese Variable beim ersten Dialogwechsel festgelegt wird. |
| `vgwSessionInactivityTimeout` | Zeit in Minuten <br/><br/>Standardwert: `2` | Das Intervall für das Inaktivitätszeitlimit. Der Wert für das Zeitlimitintervall gibt in Minuten an, wie lange der Sprachagent Inaktivität in einer Sitzung zulässt. Läuft das Zeitlimit ab, beendet der Sprachagent die Sitzung. |
| `vgwErrAudioURL` | Benutzerdefiniert | Eine URL zu einer Audiodatei, die abgespielt wird, wenn der {{site.data.keyword.texttospeechshort}}-Service beim Versuch des Sprachagenten, eine Antwort wiederzugeben, nicht kontaktiert werden kann. Die Audiodatei muss das WAV-Format haben. |
{: caption="Tabelle 2. Vom {{site.data.keyword.conversationshort}}-Service festgelegte Variablen" caption-side="top"}

### Vom Sprachagenten festgelegte Statusvariablen
{: #state-variables-iva}

| Name der Statusvariablen | Erwarteter Wert | Beschreibung |
| -------------- | ----- | ----------- |
| `vgwSessionID`   | Benutzerdefiniert <br/><br/> Standardwert: `Anruf-ID` | Ein angepasster Header mit der Sitzungs-ID, die aus der SIP-Anforderung 'INVITE' extrahiert wurde. Der Wert stellt die globale Sitzungs-ID dar, die in allen Auditprotokollen des Sprachagenten im Zusammenhang mit der Sitzung verwendet wird. |
| `vgwSIPCallID` | SIP `Anruf-ID` | Die SIP-Anruf-ID, die dem Anruf zugeordnet ist. |
| `vgwSIPRequestURI` | SIP-`Anforderungs-URI` | Der SIP-Anforderungs-URI, der den Anruf gestartet hat. |
| `vgwSIPToURI` | SIP-`An`-URI | Der SIP-`An`-URI, der dem Anruf zugeordnet ist. |
| `vgwSIPFromURI` | SIP-`Von`-URI | Der SIP-`Von`-URI, der dem Anruf zugeordnet ist. |
| `vgwBargeInOccurred` | `Ja` / `Nein` | Gibt an, ob ein Einsprechen (in eine laufende Bandansage) stattgefunden hat. |
| `vgwHangUp` | `Ja` / `Nein` | Gibt an, ob der Dialog beendet wurde. |
| `vgwHangupReason` | Zeichenfolge | Wenn ein Abbruch initiiert wird, sei es durch den Anrufer oder aufgrund eines Fehlers, wird diese Variable an den {{site.data.keyword.conversationshort}}-Service gesendet, um anzugeben, wodurch der Anruf abgebrochen wurde. Der Text in der Nachrichtenanforderung, die an den {{site.data.keyword.conversationshort}}-Service gesendet wird, schließt auch "vgwHangUp" ein. |
| `vgwConversationResponseTimeout` | Zeit in Sekunden<br/><br/>Standardwert: `5`  | Die Zeit in Sekunden, die der Sprachagent auf eine Antwort vom {{site.data.keyword.conversationshort}}-Service wartet. Wird diese Zeit überschritten, versucht der Sprachagent erneut, den {{site.data.keyword.conversationshort}}-Service zu kontaktieren. Kann der Service weiterhin nicht erreicht werden, schlägt der Anruf fehl. |
| `vgwSTTResponse` | JSON-Objekt | Die abschließende Antwort vom {{site.data.keyword.speechtotextshort}}-Service im JSON-Format, einschließlich der Aufzeichnung und des Konfidenzscores für die bevorzugte Hypothese und eventueller Alternativen. <p>Beispiel: Das folgende Format stimmt genau mit dem Format überein, das vom {{site.data.keyword.speechtotextshort}}-Service erhalten wird:</p><p><code>{<br/>&nbsp;&nbsp;"result_index": 0,<br/>&nbsp;&nbsp;"warnings": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;"Unknown arguments: continuous."<br/>&nbsp;&nbsp;],<br/>&nbsp;&nbsp;"results": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"final": true,<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"alternatives": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello world",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.758<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello wooled",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.358<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;]<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}.</code></p> |
| `vgwIsDTMF` | `Ja` / `Nein` | Gibt an, ob es sich bei der Eingabe an den {{site.data.keyword.conversationshort}}-Service um DTMF (Dual-Tone Multi-Frequency)-Signale handelt. |
{: caption="Tabelle 3. Vom Sprachagenten festgelegte Variablen" caption-side="top"}
