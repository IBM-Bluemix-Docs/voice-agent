---

copyright:
  years: 2018
lastupdated: "2018-12-05"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Verbindung zu einem SIP-Trunk herstellen
{: #connect}

Sie können den SIP-Trunk-Provider, den Sie für die Integration mit {{site.data.keyword.iva_full}} verwenden, in der folgenden Liste auswählen.
{: #shortdesc}

* [NetFoundry](#NetFoundry-setup)
* [Twilio](#twilio-setup)
* [AT&T und andere Provider](#att-other)
* [Peering mit {{site.data.keyword.iva_short}}](#peering)
* [Unterstützung für Konfiguration anfordern](#request-setup)

## NetFoundry-SIP-Trunk und -Telefonnummer erstellen
{: #NetFoundry-setup}

**Hinweis:** Für die Erstellung eines Kontos ist eine Kreditkarte erforderlich, die in regelmäßigen Zeitabständen nutzungsabhängig belastet wird. Wenn Sie bereits über ein NetFoundry-Konto verfügen, können Sie das vorhandene Konto verwenden.

1. Erstellen Sie ein Konto auf der Website von [NetFoundry![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson.netfoundry.io/watson-login){: new_window}.

1. Rufen Sie die _Watson-Konto_-Hauptseite auf.

1. Wählen Sie eine Region aus, aus der die Telefonnummer stammen soll.

  **Hinweis:** Überprüfen Sie auf der NetFoundry-Website, welche Regionen verfügbar sind. Neue Regionen werden ständig hinzugefügt.

1. Klicken Sie auf **Kaufen** und führen Sie die Anweisungen in der Anzeige aus, um den Kauf abzuschließen.

1. Nach der erfolgreichen Verarbeitung der Zahlung wird Ihre SIP-Trunk-Telefonnummer in Ihrem Konto angezeigt.

Sie benötigen diese Telefonnummer, einschließlich der Landes- und Ortsnetzkennzahl, zum Einrichten des Sprachagenten und zum Konfigurieren der Anrufübergabe. Informationen hierzu finden Sie in [Sprachagenten erstellen und Verbindung herstellen](getting-started.html#step3).


## Twilio-SIP-Trunk erstellen
{: #twilio-setup}

**Hinweis:** Für die Erstellung eines [Twilio-Kontos ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.twilio.com/try-twilio){: new_window} ist eine Kreditkarte erforderlich, die in regelmäßigen Zeitabständen auf der Basis der Nutzung des von Ihnen konfigurierten SIP-Trunks belastet wird. Wenn Sie bereits über ein Twilio-Konto verfügen, können Sie dieses verwenden.

  1. Erstellen Sie ein Twilio-Konto auf der [Twilio-Website ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.twilio.com/try-twilio){: new_window}.

  1. Erstellen Sie einen SIP-Trunk mit Ihrem Twilio-Konto.

  1. Auf der Twilio-Website gehen Sie zum Dashboard 'Elastisches SIP-Trunking'.

  1. Wählen Sie in der Navigationsleiste **Trunks** aus und erstellen Sie einen SIP-Trunk. Wenn Sie bereits über einen SIP-Trunk verfügen, klicken Sie auf das Pluszeichen (**+**). Geben Sie in dem Dialogfeld, das sich öffnet, einen Namen für Ihren SIP-Trunk ein und klicken Sie auf **Erstellen**.

  1. Wählen Sie auf der Seite für elastische SIP-Trunks Ihren SIP-Trunk aus.

  1. Wählen Sie in der Navigationsleiste den **Ursprung** für Ihren SIP-Trunk aus und konfigurieren Sie den Ursprungs-SIP-URI. Durch Auswahl des Pluszeichens (**+**) können Sie mehrere Hostnamen einbeziehen, um Servicefehler zu verhindern.

  Die IP-Adresse oder der Hostname ist der Wert, den Sie im Dashboard _Einführung_ Ihrer {{site.data.keyword.iva_short}}-Serviceinstanz vermerkt haben. Der Ursprungs-URI muss im SIP-URI-Format konfiguriert werden, z. B. `sip:us-south.voiceagent.cloud.ibm.com/`. Durch die Angabe mehrerer Hostnamen oder IP-Adressen kann der SIP-Trunk-Provider bei einem Fehlschlagen oder Ausfall des ersten Hostendpunkts Anrufe an den nächsten Hostnamen in der Liste weiterleiten.

  1. Wählen Sie in der Navigationsleiste **Nummern** für Ihren SIP-Trunk aus. Erstellen Sie anschließend eine Telefonnummer und weisen Sie diese Ihrem SIP-Trunk zu.

  Klicken Sie auf der Seite 'Nummern' auf **Nummer kaufen** oder, wenn Sie bereits über eine Nummer verfügen, klicken Sie auf das Pluszeichen (**+**). In dem angezeigten Fensterbereich können Sie eine neue Telefonnummer in Ihrer Region angeben. Weisen Sie die Nummer dem SIP-Trunk zu, den Sie erstellt haben, indem Sie zum SIP-Trunk zurückkehren und auf das Symbol für 'Nummer' klicken.

  Sie benötigen diese Telefonnummer, einschließlich der Landes- und Ortsnetzkennzahl, zum Einrichten des Sprachagenten. Informationen hierzu finden Sie in [Sprachagenten erstellen und Verbindung herstellen](getting-started.html#step3).

## Peering mit {{site.data.keyword.iva_short}}
{: #peering}

{{site.data.keyword.iva_short}} unterstützt Peerverbindungen, wie z. B. einen IPSec-Tunnel. Für eine Peerverbindung mit {{site.data.keyword.iva_short}} können Sie die IP-Adressen Ihres Servers in eine Whitelist aufnehmen. 

1. Rufen Sie das Dashboard _Verwalten_ auf und wählen Sie die Registerkarte _Instanz_ aus. 

1. Klicken Sie auf das Symbol **Neue IP-Adresse hinzufügen**, um eine neue IP-Adresse in die Whitelist aufzunehmen. 

1. Fügen Sie einen **Kurznamen für die IP-Adresse** und die **IP-Adresse** selbst hinzu. 

## Verbindung mit AT&T und anderen Providern herstellen
{: #att-other}

{{site.data.keyword.iva_short}} unterstützt Verbindungen mit AT&T&reg; und anderen SIP-Trunking-Providern. Diese Verbindungen können jedoch nicht im Self-Service-Verfahren eingerichtet werden und erfordern zusätzliche Unterstützung. Informationen hierzu finden Sie in [Unterstützung für Konfiguration anfordern](#request-setup).

## Unterstützung für Konfiguration anfordern
{: #request-setup}

Sie können Unterstützung für die Netzkonfiguration anfordern, um eine Verbindung mit AT&T oder anderen SIP-Trunking-Providern herzustellen, eine Peerverbindung mit {{site.data.keyword.iva_short}} herzustellen oder mehr als 50 gleichzeitige Verbindungen anzufordern. Verwenden Sie hierzu den folgenden Prozess.

1. Öffnen Sie ein neues [{{site.data.keyword.Bluemix_notm}}-Support-Ticket](https://cloud.ibm.com/unifiedsupport/tickets/add).

1. Wählen Sie **Technisch** für **Tickettyp** aus.

1. Wählen Sie **Cloud Foundry** für **Ressourcenkontext auswählen** aus.

1. Wählen Sie **Application Services** für **Technischer Bereich der Unterstützung** aus.

1. Wählen Sie die **Region**, die **Organisation** und den **Bereich** für Ihre {{site.data.keyword.iva_short}}-Instanz aus.

1. Wählen Sie Ihre {{site.data.keyword.iva_short}}-Serviceinstanz für **Zugehörige Ressource** aus.

1. Wählen Sie **Prioritätsstufe 4 - Minimaler Einfluss** für **Prioritätsstufe** aus.

1. Geben Sie als **Betreff** `{{site.data.keyword.iva_short}} - Unterstützung für Netzkonfiguration` ein.

1. Beschreiben Sie im Abschnitt **Kurze Beschreibung** die gewünschte Verbindung für den {{site.data.keyword.iva_short}}-Service oder die gewünschte Anforderung von mehr als 50 gleichzeitigen Verbindungen für Ihren Sprachagenten. Eine Peerverbindung ist für Benutzer mit _Standard_- oder _Premium_-Plänen verfügbar. Wenn Sie für Ihre Instanz von einem _Standard_- oder _Premium_-Plan zu einem _Lite_-Plan wechseln oder wenn Sie die Instanz löschen, wird die Peerverbindung inaktiviert.

  Für die Verbindung kann entweder ein SIP-Trunking-Provider oder eine Peerverbindung wie ein IPSec-Tunnel verwendet werden. Sie können im Ticket ein Netzdiagramm Ihrer Netztopologie im PDF- oder Imageformat anhängen. Darüber hinaus können Sie Dokumente anhängen, in denen die gewünschte Servicefunktionalität detailliert beschrieben ist.

  In der **kurzen Beschreibung** die folgenden Informationen angeben:
  * Firmenname
  * {{site.data.keyword.Bluemix_notm}}-Konto-ID
  * {{site.data.keyword.iva_short}}-Service-Dashboard-URL
  * Anwendungsfall
  * Netzdiagramm mit IP-Adresse oder Informationen zum SIP-Trunk-Provider
