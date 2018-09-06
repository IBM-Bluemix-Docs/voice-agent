---

copyright:
  years: 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Verbindungen schützen
{: #securing}

Sie können SRTP (Secure Real Time Transport Protocol) und die Verschlüsselung mit TLS (Transport Layer Security) für die SIP-Trunks aktivieren, um die mit {{site.data.keyword.iva_full}} hergestellten Verbindungen zu schützen.

## SRTP in Twilio einrichten
{: #SRTP}

**Hinweis:** Wenn Sie SRTP aktivieren, werden SIP-Nachrichten ebenfalls verschlüsselt. Sie müssen SRTP und die SIP-Nachrichtenverschlüsselung nicht separat aktivieren.

1. Navigieren Sie in Ihrem Twilio-Konto zum Dashboard _Elastisches SIP-Trunking_ und wählen Sie **Trunks**.

1. Wählen Sie den Trunk aus, der mit SRTP geschützt werden soll, indem Sie entweder einen vorhandenen Trunk auswählen oder einen neuen Trunk durch Klicken auf das Symbol **+** erstellen.

  * Wenn Sie einen neuen Trunk erstellen, müssen Sie im Dashboard **Ursprung** den _SIP-Trunk-URI_ konfigurieren.  Weitere Informationen finden Sie in [SIP-Trunk verbinden](connect-SIP.html).

1. Suchen Sie im Dashboard _Allgemein_ den Abschnitt _Sicheres Trunking_. Klicken Sie auf **Inaktiviert**, um die Einstellung für sicheres Trunking in **Aktiviert** zu ändern, und speichern Sie die Änderungen.

## Verschlüsselung nur für SIP-Nachrichten mit TLS in Twilio aktivieren
{: #TLS}

Wenn Sie nur SIP-Nachrichten in {{site.data.keyword.iva_short}} verschlüsseln möchten, ohne SRTP zu verwenden, können Sie einen URI-Endpunkt, der TLS (Transport Layer Security) verwendet, in Twilio auswählen.

1. Navigieren Sie in Ihrem Twilio-Konto zum Dashboard _Elastisches SIP-Trunking_ und wählen Sie **Trunks**.

1. Wählen Sie den Trunk aus, der der Anrufübergabe hinzugefügt werden soll, indem Sie entweder einen vorhandenen Trunk auswählen oder durch Klicken auf das Pluszeichen (**+**) einen neuen erstellen.

1. Wählen Sie **Ursprung** im Menü aus und geben Sie die folgenden sicheren Ursprungs-URIs nacheinander ein. Durch die Angabe mehrerer Hostnamen oder IP-Adressen kann der SIP-Trunk-Provider bei einem Fehlschlagen oder Ausfall des ersten Hostendpunkts Anrufe an den nächsten Hostnamen in der Liste weiterleiten.

```
sip:us-south.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}

Oder

```
sip:us-east.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}
