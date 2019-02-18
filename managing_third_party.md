---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-16"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Connecting with third-party speech and text services
{: #third-party}

You can connect third-party speech and text services when creating, cloning, or editing your voice agent on the _Manage_ dashboard.
{: shortdesc}

Alternatively, to configure your speech and text service connections on the fly, you can [use dynamic configuration with {{site.data.keyword.conversationshort}}](/docs/services/voice-agent/api_dynamic_config.html). This allows you to change your voice agent configuration with action tags and state variables.

## Connecting to Google Speech-to-Text from {{site.data.keyword.iva_short}}
{: #stt_va}

Instead of using a {{site.data.keyword.speechtotextfull}} instance, you can choose to connect your voice agent to a third-party speech to text service, such as [Google Cloud Speech-to-Text ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.google.com/speech-to-text/).

1. Navigate to the _Voice agents_ tab on your _Manage_ dashboard, and select either **Edit** an existing voice agent or **Create new voice agent**.

1. In your _Speech to Text_ service configuration, choose **Google Speech to Text service instance**.

1. Choose the **Language** for your service instance.

1. Enter your Google Cloud Speech-to-Text service credentials.
  * You can generate your service credentials in the Google Cloud Platform as a JSON key when you [set up a service account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). The following code example contains the sample credential fields you generate on the Google Cloud Platform.

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

1. **Optional** Select **Show Advanced** to enter special configuration settings defined by Google in a valid JSON format.
  The following example shows the Google configuration settings to enable a profanity filter for a US English instance.
  ```json
  {
    "languageCode": "en-US",
    "profanityFilter": false
  }
  ```
  {: codeblock}

  If you select a language in the service configuration that is different from the language you define in `languageCode`, {{site.data.keyword.iva_short}} overwrites your selection with the language defined by the `languageCode` JSON configuration.
  {: tip}

## Connecting to Google Text-to-Speech from {{site.data.keyword.iva_short}}
{: #tts_va}

Instead of using a {{site.data.keyword.texttospeechfull}} instance, you can choose to connect your voice agent to a third-party speech to text service, such as [Google Cloud Text-to-Speech ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.google.com/text-to-speech/).

1. Navigate to the _Voice agents_ tab on your _Manage_ dashboard, and select either **Edit** an existing voice agent or **Create new voice agent**.

1. In your _Text to Speech_ service configuration, choose **Google Text to Speech service instance**.

1. Choose the **Language** and **Voice** for your service instance.

1. Enter your Google Cloud Text-to-Speech service credentials.
  * You can generate your service credentials in the Google Cloud Platform as a JSON key when you [set up a service account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). The following code example contains the sample credential fields you generate on the Google Cloud Platform.

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

1. **Optional** Select **Show Advanced** to enter special configuration settings defined by Google in a valid JSON format.
  The following example shows the Google configuration settings for a female voice speaking German.

  If you select a language in the service configuration that is different from the language you define in `languageCode`, {{site.data.keyword.iva_short}} overwrites your selection with the language defined by the `languageCode` JSON configuration.
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
