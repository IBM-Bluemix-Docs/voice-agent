---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-08"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Aktionstags und Statusvariablen in der API
{: #api}

Verwenden Sie das Referenzmaterial, um nach Aktionstags zu suchen, die Aktionen initiieren, die Ihr Sprachagent während einer Dialogsitzung unternimmt, bzw. um nach Statusvariablen zu suchen, die Merkmale des Sprachagenten definieren, die während des ganzen Dialogs bestehen bleiben, sofern sie nicht geändert werden.
{: shortdesc}

Codebeispiele und Beispiele zum Festlegen von Status und zum Einleiten von Aktionsfolgen finden Sie unter [Sprachagenten mithilfe der API programmieren](api.html).

Da {{site.data.keyword.iva_full}} auf IBM Voice Gateway basiert, funktioniert die API auf gleiche Weise. Wenn Sie mit Voice Gateway vertraut sind, können Sie in Ihren {{site.data.keyword.conversationshort}}-Dialogen mit {{site.data.keyword.iva_short}} die gleichen Aktionen und Statusvariablen verwenden. In [Aktionstags und Statusvariablen in der Voice Gateway-API](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html) finden Sie weitere Informationen.
{: tip}

## Aktionsbefehle und Attribute
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

## Im {{site.data.keyword.conversationshort}}-Dialog festgelegte Statusvariablen
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

## Vom Sprachagenten festgelegte Statusvariablen
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
