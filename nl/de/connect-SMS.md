---

copyright:
  years: 2019
lastupdated: "2019-06-21"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Verbindung zu SMS-Providern herstellen
{: #connect-sms}

Sie können den SMS-Provider, den Sie für die Integration mit {{site.data.keyword.iva_full}} verwenden, in der folgenden Liste auswählen.
{: #shortdesc}

* [Twilio](#twilio-setup)

## API-Schlüssel generieren und Berechtigungsnachweise festlegen
{: #sms_access}

Sie können Berechtigungsnachweise nur für Rollen erstellen, die bereits in Ihrem Konto aktiv sind. Für SMS-Agenten sowie Agenten für Sprache + SMS muss Ihnen entweder die Rolle *Schreibberechtigter* oder *Manager* zugewiesen sein. Weitere Informationen enthält [Schritt 9 unter 'Benutzer einladen und Anfangszugriffsberechtigungen zuweisen'](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. Klicken Sie im *Dashboard* Ihrer {{site.data.keyword.iva_short}}-Instanz auf **Neuer Berechtigungsnachweis (+)**. 
2. Geben Sie im aufgerufenen Dialogfeld 'Neu' einen **Namen** ein und wählen Sie im Dropdown-Menü **Rolle** die Option *Schreibberechtigter* oder *Manager* aus. 
    - **HINWEIS:** Sie **_müssen_** für jede SMS-bezogene Funktionalität entweder die Rolle *Schreibberechtigter* oder die Rolle *Manager* auswählen. 
3. Klicken Sie auf **Hinzufügen**.
4. Klicken Sie neben den neu erstellten Berechtigungsnachweisen auf **Berechtigungsnachweise anzeigen**. Notieren Sie den Wert, der im JSON-Script für `APIKEY` angegeben ist; Sie verwenden ihn später bei der [Konfiguration von Twilio für SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

## Twilio für SMS konfigurieren
{: #twilio-setup}

1. Greifen Sie [hier](https://www.twilio.com/console/phone-numbers/) auf Ihre Twilio-Telefonnummern zu und wählen Sie die Telefonnummer aus, die Ihrem _SMS-Agenten_ oder Ihrem _Agenten für Sprache + SMS_ zugewiesen ist. 

1. Blättern Sie vor bis zum Abschnitt **Messaging**. Wählen Sie im Feld _KONFIGURIEREN MIT_ im Dropdown-Menü die Option **Webhooks, TwiML-Bins, Funktionen, Studio oder Proxy** aus.

1. Wählen Sie im Feld _NACHRICHTENEINGANG IN_ die Option **Webhook** im Dropdown-Menü aus.

1. Befolgen Sie für das leere URL-Feld neben **Webhook** die entsprechenden Anweisungen für die Region Ihres Agenten. 

    - Falls der von Ihnen erstellte Agent die Regionsbasis 'Washington' verwendet, schreiben Sie die Zeichenfolge `https://apikey:IHR_API-SCHLÜSSEL@sms-east.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` in das Feld.
    - Falls der von Ihnen erstellte Agent die Regionsbasis 'Dallas' verwendet, schreiben Sie die Zeichenfolge `https://apikey:IHR_API-SCHLÜSSEL@sms-south.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` in das Feld.
    - Ersetzen Sie in den obigen URLs die Variable `IHR_API-SCHLÜSSEL` durch den Wert für `APIKEY` aus dem zuvor erstellten Berechtigungsnachweis. Weitere Informationen finden Sie unter [API-Schlüssel generieren und Berechtigungsnachweise festlegen](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_access). 

1. Klicken Sie auf **Speichern**. 
