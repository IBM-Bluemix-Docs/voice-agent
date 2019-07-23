---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Verbindung zu Sprach- und Textservices von anderen Anbietern herstellen
{: #third-party}

Sie können beim Erstellen, Klonen oder Bearbeiten Ihres Sprachagenten im Dashboard _Verwalten_ eine Verbindung zu Sprach- und Textservices anderer Anbieter herstellen.
{: shortdesc}

Alternativ dazu können Sie zur Konfiguration Ihrer Sprach- und Textserviceverbindungen während des Betriebs die [dynamische Konfiguration mit {{site.data.keyword.conversationshort}}](/docs/services/voice-agent?topic=voice-agent-dynamic-donfig) nutzen. Dies ermöglicht Ihnen die Änderung Ihrer Sprachagentenkonfiguration mit Aktionstags und Statusvariablen.

## Verbindung zu Google Speech-to-Text über {{site.data.keyword.iva_short}} herstellen
{: #stt_va}

Anstelle einer Verbindung zur {{site.data.keyword.speechtotextfull}}-Instanz können Sie für den Sprachagenten auch eine Verbindung mit dem Speech-to-Text-Service eines anderen Anbieters, z. B. [Google Cloud Speech-to-Text ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.google.com/speech-to-text/), herstellen.

1. Navigieren Sie zur Registerkarte _Sprachagenten_ im Dashboard _Verwalten_ und wählen Sie entweder die Option zum **Bearbeiten** eines vorhandenen Sprachagenten oder die Option **Neuen Sprachagenten erstellen** aus.

1. Wählen Sie in der _Speech to Text_-Servicekonfiguration die **Google Speech-to-Text-Serviceinstanz** aus.

1. Wählen Sie die **Sprache** für Ihre Serviceinstanz aus. Falls Ihre bevorzugte Sprache im Dropdown-Menü nicht aufgeführt ist, können Sie die Option **Andere** auswählen und die Sprache über die [erweiterte Konfiguration](/docs/services/voice-agent?topic=voice-agent-third-party#advanced) festlegen.

1. Geben Sie Ihre Google Cloud Speech-to-Text-Serviceberechtigungsnachweise ein. Beachten Sie dabei die Begrenzung auf maximal 3072 Zeichen.
  * Sie können die Serviceberechtigungsnachweise auf der Google Cloud-Plattform als JSON-Schlüssel generieren, wenn Sie [ein Servicekonto einrichten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). Das folgende Codebeispiel enthält die Beispielberechtigungsnachweisfelder, die Sie auf der Google Cloud-Plattform generieren.

    ```json
    {
      "type": "",
      "auth_uri": "",
      "client_id": "",
      "token_uri": "",
      "project_id": "",
      "private_key": "",
      "client_email": "",
      "private_key_id": "",
      "client_x509_cert_url": "",
      "auth_provider_x509_cert_url": ""
    }
    ```
    {: codeblock}

1. **Optional** Wählen Sie **Erweiterte Optionen anzeigen** aus, um spezielle Konfigurationseinstellungen einzugeben, die von Google in einem gültigen JSON-Format definiert wurden.
  Das folgende Beispiel zeigt die Einstellungen für die Google-Konfiguration, um einen Schimpfwortfilter für eine englische Instanz (US-Englisch) zu aktivieren.
  ```json
  {
    "languageCode": "en-US",
    "profanityFilter": false
  }
  ```
  {: codeblock}

  Wenn Sie eine Sprache in der Servicekonfiguration auswählen, die sich von der Sprache unterscheidet, die Sie in `languageCode` definiert haben, überschreibt {{site.data.keyword.iva_short}} Ihre Auswahl mit der Sprache, die durch die JSON-Konfiguration `languageCode` definiert ist.
  {: tip}

## Verbindung zu Google Text-to-Speech über {{site.data.keyword.iva_short}} herstellen
{: #tts_va}

Anstelle einer Verbindung zur {{site.data.keyword.texttospeechfull}}-Instanz können Sie für den Sprachagenten auch eine Verbindung mit dem Speech-to-Text-Service eines anderen Anbieters herstellen, z. B. [Google Cloud Text-to-Speech ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.google.com/text-to-speech/).

1. Navigieren Sie zur Registerkarte _Sprachagenten_ im Dashboard _Verwalten_ und wählen Sie entweder die Option zum **Bearbeiten** eines vorhandenen Sprachagenten oder die Option **Neuen Sprachagenten erstellen** aus.

1. Wählen Sie in der Servicekonfiguration _Text to Speech_ die Option **Google Text to Speech-Serviceinstanz** aus.

1. Wählen Sie die Optionen für die Landessprache und für die Sprache für Ihre Serviceinstanz aus. Falls Ihre bevorzugte Sprache im Dropdown-Menü nicht aufgeführt ist, können Sie die Option **Andere** auswählen und die Sprache über die [erweiterte Konfiguration](/docs/services/voice-agent?topic=voice-agent-third-party#advanced) festlegen.

1. Geben Sie Ihre Google Cloud Text-to-Speech-Serviceberechtigungsnachweise ein. Beachten Sie dabei die Begrenzung auf maximal 3072 Zeichen.
  * Sie können die Serviceberechtigungsnachweise auf der Google Cloud-Plattform als JSON-Schlüssel generieren, wenn Sie [ein Servicekonto einrichten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). Das folgende Codebeispiel enthält die Beispielberechtigungsnachweisfelder, die Sie auf der Google Cloud-Plattform generieren.

    ```json
    {
      "type": "",
      "auth_uri": "",
      "client_id": "",
      "token_uri": "",
      "project_id": "",
      "private_key": "",
      "client_email": "",
      "private_key_id": "",
      "client_x509_cert_url": "",
      "auth_provider_x509_cert_url": ""
    }
    ```
    {: codeblock}

{: #advanced}
1. **Optional** Wählen Sie **Erweiterte Optionen anzeigen** aus, um spezielle Konfigurationseinstellungen einzugeben, die von Google in einem gültigen JSON-Format definiert wurden.
  Das folgende Beispiel zeigt die Einstellungen für die Google-Konfiguration für eine weibliche Stimme, die Deutsch spricht.

  Wenn Sie eine Sprache in der Servicekonfiguration auswählen, die sich von der Sprache unterscheidet, die Sie in `languageCode` definiert haben, überschreibt {{site.data.keyword.iva_short}} Ihre Auswahl mit der Sprache, die durch die JSON-Konfiguration `languageCode` definiert ist.
  {: tip}

  ```json
  {
  "config": {
    "audioConfig": {
      "speakingRate": 1.3
    },
    "voiceConfig": {
      "ssmGender": "FEMALE",
      "languageCode": "de-DE"
    }
  }
  }
  ```
  {: codeblock}
