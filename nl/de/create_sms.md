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


# SMS-Agenten erstellen
{: #sms_config_instance}

Nachdem Sie Ihren {{site.data.keyword.iva_full}}-Service erstellt haben, können Sie einzelne SMS-Agenten über das Dashboard _Verwalten_ erstellen.
{: shortdesc}

1. Navigieren Sie zur Registerkarte _Sprachagenten_ auf dem Dashboard _Verwalten_ und klicken Sie auf **Sprachagenten erstellen**.

1. Wählen Sie bei **Agententyp** die Einstellung _SMS_ aus.

1. In **Name** geben Sie einen eindeutigen Namen für Ihren Sprachagenten an. Beispiel: `Kundendienst - Nordamerika`. Der Name kann aus bis zu 64 Zeichen bestehen.

1. Als **Telefonnummer** fügen Sie die Nummer von Ihrem SIP-Trunk, einschließlich Landes- und Ortsvorwahl, hinzu. Geben Sie beispielsweise für eine 800-er Nummer in den Vereinigten Staaten die Nummer mit 18883334444 an. Die Telefonnummer kann maximal 30 Zeichen umfassen, einschließlich Leerzeichen und + () -Zeichen. Der SMS-Agent unterstützt nur eine einzige Nummer pro Benutzer.

1. Geben Sie unter **SMS-Provider** den Benutzernamen, das Kennwort und die API-URL für Ihren SMS-Provider ein. Falls Sie beispielsweise _Twilio_ nutzen, ist der Benutzername Ihre **Konto-SID**, das Kennwort Ihr **Authentifizierungstoken** und Ihr SMS-Provider `https://api.twilio.com`.

1. Konfigurieren Sie unter **Dialog** die Verbindung zu Ihrer {{site.data.keyword.conversationshort}}-Serviceinstanz. Sie können {{site.data.keyword.conversationshort}}-Serviceinstanzen in {{site.data.keyword.Bluemix_notm}}-Konten verwenden, deren Eigner Sie sind oder deren Eigner ein anderer Benutzer ist. Sie können auch zu jeder dieser Optionen eine Verbindung über eine Service-Orchestrierungsengine (SOE) herstellen.

   * Wenn Sie in der Region 'Dallas' oder 'Washington DC' einen SMS-Agenten erstellen und nicht über eine {{site.data.keyword.conversationshort}}-Serviceinstanz verfügen, können Sie über das Menü **Serviceinstanz** eine Serviceinstanz erstellen.
   * Alternativ können Sie Verbindungen zu anderen Quellen eines {{site.data.keyword.conversationshort}}-Dialogs oder zu einer SOE herstellen, indem Sie den [**Servicetyp**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service) ändern.
   * Wenn Sie mehrere Servicestandorte konfigurieren möchten, klicken Sie auf die Option für den anderen Standort und wählen Sie **Standort aktivieren** aus, um die Verbindung zur anderen {{site.data.keyword.conversationshort}}-Instanz zu konfigurieren. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).

1. Wählen Sie das Kontrollkästchen **Dialog aus eingehenden Nachrichten initiieren** aus, damit Benutzer eine SMS-Sitzung mit Ihrem SMS-Agenten starten können.

1. Wählen Sie das Kontrollkästchen **Bei Sitzungszeitlimitüberschreitung benachrichtigen** aus, damit Ihr SMS-Agent eine SMS-Nachricht an die Benutzer sendet, die sie darüber informiert, dass der Agent eine Zeitlang keine Antwort empfangen hat und deshalb ein Zeitlimit überschritten wurde. 

    - Im Abschnitt [Erweiterte Optionen](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) können Sie sich genauer über die **erweiterten Optionen** informieren, die für Ihren SMS-Agenten verfügbar sind, beispielsweise über das Festlegen einer benutzerdefinierten Dauer, nach der die Sitzung ein Zeitlimit überschreitet.
    - Wählen Sie das Kontrollkästchen nur dann aus, wenn Sie über eine Sitzungszeitlimitüberschreitung benachrichtigt werden wollen.

1. Sie können auch die Ereignisweiterleitung aktivieren, um Informationen zu den von Ihren Sprachagenten verarbeiteten Anrufen in {{site.data.keyword.cloudantfull}} zu erfassen. Weitere Informationen finden Sie unter [Ereignisweiterleitung für Sprachagenten aktivieren](/docs/services/voice-agent?topic=voice-agent-event_forwarding). Weitere Konfigurationsoptionen finden Sie in [Sprachagenten konfigurieren](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1.  Klicken Sie auf **Sprachagenten erstellen**, um Ihren SMS-Agenten und alle etwaigen neuen Services zu erstellen.

1. Stellen Sie anhand der [Anweisungen](/docs/services/voice-agent?topic=voice-agent-connect-sms) eine Verbindung zu einem SMS-Provider her.

Nach dem Erstellen des SMS-Agenten testen Sie Ihren SMS-Agenten, indem Sie eine SMS an seine Telefonnummer senden. Details zu Ihrer Interaktion können Sie über das Dashboard _Nutzung_ anzeigen. Weitere Informationen hierzu enthält der Abschnitt [Nutzung und Protokolle anzeigen](/docs/services/voice-agent?topic=voice-agent-logging).

Damit SMS-Nachrichten zwischen Kunden und einem Sprachagenten während eines Sprachanrufs gesendet werden können, muss die SMS-Nummer mit der Nummer für den Sprachanruf übereinstimmen.
{: tip}

Bevor Sie einen SMS-Agenten erstellen oder SMS-Funktionalität zu Ihrem Sprachagenten hinzufügen, **müssen** Sie die geeigneten Berechtigungsnachweise eingerichtet und einen API-Schlüssel für die Programmierung Ihrer SMS-Nummer generiert haben. Weitere Informationen finden Sie unter [API-Schlüssel generieren und Berechtigungsnachweise festlegen](/docs/services/voice-agent?topic=voice-agent-connect-sms#sms_access).

Sie **müssen** ebenfalls Ihren SIP-Trunk für SMS-Funktionalität konfigurieren. Gehen Sie hierzu anhand der Anweisungen vor, die vom Provider (z. B. Twilio) bereitgestellt werden. Falls Sie keine Twilio-Telefonnummer besitzen, lesen Sie den Abschnitt [Twilio-SIP-Trunk erstellen](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup).

Nachdem Sie eine Twilio-Nummer erhalten haben, müssen Sie sie für die SMS-Funktionalität konfigurieren. Weitere Informationen finden Sie unter [Twilio für SMS konfigurieren](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

Falls bei der Erstellung von Berechtigungsnachweisen Probleme auftreten, bitten Sie den Administrator Ihrer Serviceinstanz, Ihnen die Zugriffsberechtigung *Manager* oder *Schreibberechtigter* zu erteilen.
{: tip}

## Erweiterte Optionen für SMS-Agenten
{: #sms_advanced}

Klicken Sie nach dem Feld **Telefonnummer** auf **Erweiterte Optionen anzeigen** .

1. Legen Sie optional einen Wert für **Zeitlimitüberschreitung beim Lesen des Dialogs** fest. Dieser Wert gibt in Sekunden an, wie lange SMS Gateway auf eine Antwort von Watson Assistant wartet. Bei Überschreitung des angegebenen Zeitraums versucht SMS Gateway erneut, Kontakt zu Watson Assistant aufzunehmen. Kann der Service weiterhin nicht erreicht werden, schlägt die SMS/MMS-Nachricht fehl. Standardmäßig ist ein Zeitraum von 30 Sekunden festgelegt.

1. Legen Sie optional einen Wert für **Sitzungszeitlimit** fest. Dieser Wert gibt die Anzahl der Sekunden an, nach der die Sitzung abläuft, falls SMS Gateway keine Antwort vom Benutzer empfängt.

1. Legen Sie eine **Antwortnachricht bei Dialogfehler** fest. Dies ist die Standardantwortnachricht, die gesendet wird, wenn Watson Assistant nicht erreicht werden kann. Der Standardwert lautet `Ihre Nachricht kann leider nicht beantwortet werden`.

### SMS-Agenten für Beendigung der Sitzung konfigurieren
{: #sms_terminate}

Der SMS-Agent von {{site.data.keyword.iva_full}} beendet eine Sitzung gemäß dem Wert für die Sitzungszeitlimitüberschreitung, der konfigurierbar ist und standardmäßig 30 Sekunden beträgt. 

Sie können außerdem einen Knoten zu Ihrem {{site.data.keyword.conversationshort}}-Service hinzufügen, um einen Befehl für das Beenden der Sitzung zu beantworten, der vom Benutzer ausgegeben wird. 

1. In Ihrem {{site.data.keyword.Bluemix_notm}}-Dashboard wählen Sie die {{site.data.keyword.conversationshort}}-Instanz aus, die Ihr Sprachagent verwendet.

1. Erstellen Sie im Dashboard eine **SMS-Beendigungsabsicht**. Alternativ können Sie eine bestehende Absicht modifizieren, die Sie bereits für den Sprachagenten nutzen, z. B. _Anruf beenden_.

1. Fügen Sie im Dashboard einen **SMS-Beendigungsknoten** hinzu.

1. Fügen Sie im Abschnitt _Falls Assistent Folgendes erkennt:_ das Attribut **SMS-Beendigungsabsicht** hinzu, das Sie zuvor erstellt haben.

1. Fügen Sie die Antwort zum Knoten hinzu. Kopieren Sie das folgende Code-Snippet und fügen Sie es in das Feld ein, um den dort vorhandenen Code zu ersetzen.

    ```json
        {
            "output": {
                 "text": {
                    "values": [
                        "Vielen Dank für die Nutzung des Service. Auf Wiedersehen!"
                    ],
                    "selection_policy”: “sequential"
                },
                "smsAction": {
                    "command": "terminateSession"
                }
            }
        }
    ```
    {: codeblock}

Nach dem Erstellen des Sprachagenten testen Sie Ihren Sprachagenten, indem Sie je nach Typ des Agenten eine Telefonnummer anrufen oder eine SMS senden. Details zu Ihrer Interaktion können Sie über das Dashboard _Nutzung_ anzeigen. Weitere Informationen hierzu enthält der Abschnitt [Nutzung und Protokolle anzeigen](/docs/services/voice-agent?topic=voice-agent-logging).
