---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-16"

keywords: thrid party, google cloud platform, text service

subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:deprecated: .deprecated}
{:external: target="_blank" .external}


# Connecting with third-party speech and text services
{: #third-party}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances, and access to free instances will be removed. Existing paid instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

You can connect third-party speech and text services when you are creating, cloning, or editing your agent on the _Manage_ dashboard.
{: shortdesc}

Alternatively, to configure your speech and text service connections as needed, you can [use dynamic configuration with {{site.data.keyword.conversationshort}}](/docs/voice-agent?topic=voice-agent-dynamic-donfig). This  configuration allows you to change your agent configuration with action tags and state variables.

## Connecting to Google Speech-to-Text from {{site.data.keyword.iva_short}}
{: #stt_va}

Instead of using a {{site.data.keyword.speechtotextfull}} instance, you can choose to connect your agent to a third-party speech to text service, such as [Google Cloud Speech-to-Text ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.google.com/speech-to-text/).

1. Go to the _Agents_ tab on your _Manage_ dashboard, and select either **Edit** an existing agent or **Create new agent**.

1. In your _Speech to Text_ service configuration, choose **Google Speech to Text service instance**.

1. Choose the **Language** for your service instance. If your preferred language is not listed in the dropdown menu, you can always choose **Other** and set it through [advanced configuration](/docs/voice-agent?topic=voice-agent-third-party#advanced).

1. Enter your Google Cloud Speech-to-Text service credentials, with a limit up to 3072 characters.
  * You can generate your service credentials in the Google Cloud Platform as a JSON key when you [set up a service account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). The following code example contains the sample credential fields that you generate on the Google Cloud Platform.

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

  If you select a language in the service configuration that is different from the language you define in `languageCode`, {{site.data.keyword.iva_short}} overwrites your selection with the language that is defined by the `languageCode` JSON configuration.
  {: tip}

## Connecting to Google Text-to-Speech from {{site.data.keyword.iva_short}}
{: #tts_va}

Instead of using a {{site.data.keyword.texttospeechfull}} instance, you can choose to connect your agent to a third-party speech to text service, such as [Google Cloud Text-to-Speech ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.google.com/text-to-speech/).

1. Go to the _Agents_ tab on your _Manage_ dashboard, and select either **Edit** an existing agent or **Create new agent**.

1. In your _Text to Speech Service configuration, choose **Google Text to Speech Service instance**.

1. Choose the **Language** and **Voice** for your service instance. If your preferred language is not listed in the dropdown menu, you can always choose **Other** and set it through [advanced configuration](/docs/voice-agent?topic=voice-agent-third-party#advanced).

1. Enter your Google Cloud Text to Speech Service credentials, with a limit up to 3072 characters.
  * You can generate your service credentials in the Google Cloud Platform as a JSON key when you [set up a service account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). The following code example contains the sample credential fields that you generate on the Google Cloud Platform.

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
1. **Optional** Select **Show Advanced** to enter special configuration settings defined by Google in a valid JSON format.
  The following example shows the Google configuration settings for a female voice that is speaking German.

  If you select a language in the service configuration that is different from the language you define in `languageCode`, {{site.data.keyword.iva_short}} overwrites your selection with the language that is defined by the `languageCode` JSON configuration.
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
