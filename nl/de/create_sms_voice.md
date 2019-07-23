---

copyright:
  years: 2019
lastupdated: "2019-06-24"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# SMS-fähigen Sprachagenten erstellen
{: #sms_voice_config_instance}

Nachdem Sie Ihren {{site.data.keyword.iva_full}}-Service erstellt haben, können Sie einzelne Sprachagenten mit SMS-Funktionalität oder Sprachagenten mit ausschließlich SMS-Funktionalität über das Dashboard _Verwalten_ erstellen. Sie können Ihre {{site.data.keyword.iva_full}}-Instanz so konfigurieren, dass eingehende Anrufe empfangen und abhängig von dem durch den Benutzer empfangenen Sprachbefehl durch ausgehende SMS-Nachrichten beantwortet werden. Zum Konfigurieren fügen Sie einen Knoten und eine Absicht zu Ihrem {{site.data.keyword.conversationshort}}-Service hinzu.
{: shortdesc}


1. Navigieren Sie zur Registerkarte _Sprachagenten_ auf dem Dashboard _Verwalten_ und klicken Sie auf **Sprachagenten erstellen**.

1. Wählen Sie bei **Agententyp** die Einstellung _Sprache + SMS_ aus.

1. Befolgen Sie die Anweisungen im Abschnitt [Sprachangenten erstellen](/docs/services/voice-agent?topic=voice-agent-config_instance).

1. Wählen Sie das Kontrollkästchen **Dialog aus eingehenden Nachrichten initiieren** aus, damit Benutzer eine SMS-Sitzung mit Ihrem SMS-Agenten starten können.

1. Wählen Sie die Option **Bei Sitzungszeitlimitüberschreitung benachrichtigen** aus, damit Ihr SMS-Agent eine SMS-Nachricht an die Benutzer sendet, die sie darüber informiert, dass der Agent eine Zeitlang keine Antwort empfangen hat und deshalb ein Zeitlimit überschritten wurde. 

   - Im Abschnitt [Erweiterte Optionen](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) können Sie sich genauer über die **erweiterten Optionen** informieren, die für Ihren SMS-Agenten verfügbar sind, beispielsweise über das Festlegen einer benutzerdefinierten Dauer, nach der die Sitzung ein Zeitlimit überschreitet.

1. Befolgen Sie zum Erstellen eines SMS-Agenten die Anweisungen unter [SMS-Agenten erstellen](/docs/services/voice-agent?topic=voice-agent-sms_config_instance).

1. _**HINWEIS:**_ Damit ein Agent sowohl über die Sprach- als auch über die SMS-Integration verfügt (z. B. Spracheingabe empfangen und als Antwort eine ausgehende SMS-Nachricht zurücksenden), **müssen** Sie eine Ihrer **Sprachnummern** für den **SMS-Agenten** verwenden.

### Watson Assistant für Sprach- und SMS-Integration konfigurieren
{: #sms_outbound}

1. In Ihrem {{site.data.keyword.Bluemix_notm}}-Dashboard wählen Sie die {{site.data.keyword.conversationshort}}-Instanz aus, die Ihr Sprachagent verwendet.

1. Erstellen Sie im Dashboard eine **Absicht für ausgehende SMS**.

1. Fügen Sie im Dashboard einen **Knoten für ausgehende SMS** hinzu.

1. Wählen Sie im Abschnitt _Falls Assistent Folgendes erkennt:_ das Attribut **Absicht für ausgehende SMS** aus, das Sie zuvor erstellt haben.

1. Fügen Sie die Antwort zum Knoten hinzu. Kopieren Sie das folgende Code-Snippet und fügen Sie es in das Feld ein, um den dort vorhandenen Code zu ersetzen.

    ```json
        {
            "output": {
                "text": {
                "values": [
                    "OK. Ich sende Ihnen nun eine Textnachricht."
                ],
     "selection_policy": "sequential"
                },
                "vgwActionSequence": [
                {
                    "command": "vgwActSendSMS",
                    "parameters": {
                    "message": "Dies ist eine Testnachricht von Watson Assistant"
                    }
                },
                {
                    "command": "vgwActPlayText"
                }
                ]
            }
        }
    ```
    {: codeblock}


1. Rufen Sie Ihren Agenten auf und lösen Sie den Knoten für den Empfang einer Textnachricht auf dem Telefon aus, von dem aus Sie anrufen. 

Weitere Informationen zum Arbeiten mit dem {{site.data.keyword.conversationshort}}-Service finden Sie unter [Informationen zu {{site.data.keyword.conversationshort}}](/docs/services/assistant?topic=assistant-index#indext).
