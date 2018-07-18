---

copyright:
  years: 2018
lastupdated: "2018-06-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Anrufübergabe einrichten
{: #call-transfer}

Sie können eine Anrufübergabe einrichten, sodass der Sprachagent im Fall, dass ein Anrufer während eines Dialogs anfordert, mit einem Live-Agenten zu sprechen, den Anruf automatisch übergibt.
{: shortdesc}

## Informationen zur Anrufübergabe
{: #about-ct}

Wenn die Anrufübergabe aktiviert ist und ein Anrufer während eines Dialogs anfordert, mit einem Live-Agenten zu sprechen, leitet der Sprachagent den Anruf um. Sie können eine Anrufübergabe aktivieren, indem Sie einen Beendigungs-URI in der SIP-Providerkonfiguration festlegen. Anschließend definieren Sie das Ziel der Anrufübergabe in einer API-Aktion in einem Dialogknoten Ihrer {{site.data.keyword.conversationshort}}-Instanz. Beim Übergabeziel handelt es sich um einen SIP-URI, der den Beendigungs-URI und die Telefonnummer enthält. Weitere Informationen zu unterstützten Aktionen und zur Anpassung der Sprachagenten finden Sie in [Sprachagenten mithilfe der API programmieren](api.html).

## Schritt 1: Beendigungs-URI
{: #termination-setup}

### Beendigungs-URI in NetFoundry einrichten
{: #termination-netfoundry}

Notieren Sie sich die Telefonnummer, an die der Anruf übergeben werden soll, in Ihrem [NetFoundry-Konto![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson.netfoundry.io/watson-login){: new_window}. Später können Sie diese Telefonnummer und den Beendigungs-URI als Ziel der Anrufübergabe im {{site.data.keyword.conversationshort}}-Dialog angeben. Verwenden Sie keine persönliche Telefonnummer.

Sie können den folgenden NetFoundry-Beendigungs-URI zur Verwendung im Übergabeziel kopieren.

```
dal.watson-va.netfoundry.net
```
{: codeblock}

Sie müssen den Beendigungs-URI in Ihrem NetFoundry-Konto nicht manuell konfigurieren, wenn Sie [{{site.data.keyword.conversationshort}} für die Anrufübergabe konfigurieren](#conversation-setup).

### Beendigungs-URI in Twilio einrichten
{: #termination-Twilio}

1. Navigieren Sie in Ihrem Twilio-Konto zum Dashboard _Elastisches SIP-Trunking_ und wählen Sie **Trunks**.

1. Wählen Sie den Trunk aus, der der Anrufübergabe hinzugefügt werden soll, indem Sie entweder einen vorhandenen Trunk auswählen oder durch Klicken auf das Pluszeichen (**+**) einen neuen erstellen.

  * Wenn Sie einen neuen Trunk erstellen, müssen Sie im Dashboard **Ursprung** den _SIP-Trunk-URI_ konfigurieren.  Weitere Informationen finden Sie in [SIP-Trunk verbinden](connect-SIP.html).

1. Wählen Sie **Beendigung** in Ihrer Navigationsleiste und geben Sie einen Namen für Ihren Beendigungs-URI ein.

  * Die Namen für Beendigungs-URIs müssen eindeutig sein. Twilio überprüft die von Ihnen eingegebenen Namen automatisch auf ihre Verfügbarkeit. [Einstellungen für SIP-Trunk-Beendigung![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window} enthält weitere Details zu den Twilio-Services.

1. Klicken Sie im Abschnitt _Authentifizierung_ auf das Pluszeichen (**+**), um der Liste der Zugriffssteuerungs-IPs eine Sprachagenten-IP-Adresse hinzuzufügen.

  Fügen Sie die folgenden zwei IP-Adressen hinzu:
   * 169.60.154.134 (Serviceregion 'US-South')
   * 169.61.86.179 (Serviceregion 'US-East')

1. Klicken Sie auf **Speichern**, um die Konfiguration Ihres Beendigungs-URI zu beenden.

Notieren Sie sich die Telefonnummer, an die der Anruf übergeben werden soll, und den Beendigungs-URI. Stellen Sie sicher, dass es sich bei der Telefonnummer nicht um eine persönliche Telefonnummer handelt. Sie können die Telefonnummer und den Beendigungs-URI verwenden, um das Übergabeziel im {{site.data.keyword.conversationshort}}-Dialog anzugeben.


## Schritt 2: {{site.data.keyword.conversationshort}} für die Anrufübergabe konfigurieren
{: #conversation-setup}

Weitere Informationen zum Arbeiten mit dem {{site.data.keyword.conversationshort}}-Service finden Sie unter [Informationen zu {{site.data.keyword.conversationshort}}](../conversation/index.html#about).

1. In Ihrem {{site.data.keyword.Bluemix_notm}}-Dashboard wählen Sie die {{site.data.keyword.conversationshort}}-Instanz aus, die Ihr Sprachagent verwendet.

1. Klicken Sie im Dashboard _Einführung_ auf die Schaltfläche **Starttool**.

1. Klicken Sie in **Einführung** auf den Arbeitsbereich, den Sie bearbeiten möchten.

1. Klicken Sie auf **Absicht hinzufügen** und geben Sie einen Namen für die Absicht ein, z. B. _Übertragung_.

  Sie können ausführlichere Informationen eingeben oder später zur Bearbeitung zurückkehren und die Absicht präzisieren.

1. Nachdem Sie Ihre Absicht der Anrufübergabe erstellt haben, wählen Sie die Registerkarte _Dialog_.

1. Klicken Sie auf **Knoten hinzufügen** und geben Sie einen Namen für den Knoten ein, z. B. _Anrufübergabe_.

1. Geben Sie im Abschnitt _Wenn der Bot erkennt:_ **Absicht der Anrufübergabe** ein, um die von Ihnen eingegebene Absicht zu suchen.

1. Im Abschnitt _Dann antworten mit:_ klicken Sie auf das Symbol **&vellip;** und wählen Sie **JSON-Editor öffnen**. Kopieren Sie das folgende Code-Snippet und fügen Sie es in das Feld ein, um den dort vorhandenen Code zu ersetzen.

```json
{
    "output": {
        "text": {
            "values": [ "Bitte warten Sie, während ich eine Verbindung zu einem Live-Agenten herstelle." ],
     "selection_policy": "sequential"
        },
   "vgwAction": {
            "command": "vgwActTransfer",
     "parameters": {
                "transferTarget": "sip:18889990000\\@dal.watson-va.netfoundry.net"
            }
        }
    }
}
```
{: codeblock}

**Denken Sie daran**: Der SIP-URI des Übertragungsziels enthält eine Telefonnummer und den von Ihnen erstellten Beendigungs-URI. Verwenden Sie keine persönliche Telefonnummer für das Übergabeziel. Wenn z. B. die Telefonnummer `18889990000` und Ihr Beendigungs-URI `mysiptrunk.pstn.twilio.com` ist, lautet der vollständige SIP-URI `sip:18889990000\\@mysiptrunk.pstn.twilio.com`. Bei der Verwendung von Netfoundry und der Telefonnummer `18889990000` lautet der vollständige SIP-URI `sip:18889990000\\@dal.watson-va.netfoundry.net`.

## Nächste Schritte
{: #Next}

Testen Sie Ihren Sprachagenten, indem Sie die zugehörige Telefonnummer anrufen und die Schlüsselbegriffe verwenden, die Sie in Ihrer Absicht angegeben haben. Wenn Sie von Ihrem Sprachagenten weitergeleitet werden, hat es funktioniert!

Jetzt können Sie die **Übertragungsabsicht** und den Dialog präzisieren und konfigurieren, sodass dieser auf die Schlüsselbegriffe und -phrasen Ihrer Wahl reagiert.
