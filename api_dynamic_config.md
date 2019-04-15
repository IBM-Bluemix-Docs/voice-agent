---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-08"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Using dynamic configuration to connect to third-party services
{: #dynamic-donfig}

You can connect third-party speech and text services by setting the Speech to Text or Text to Speech from a {{site.data.keyword.conversationshort}} dialog node.
{: shortdesc}

See [Programming voice agents using the API](/docs/services/voice-agent?topic=voice-agent-api) for code examples and information about how to set states and initiate action sequences.

## Connecting to Google Speech-to-Text from a {{site.data.keyword.conversationshort}} dialog node
{: #stt_dialog}

Instead of configuring your connection to Google Speech-to-Text by editing your voice agent, you can program your {{site.data.keyword.conversationshort}} to configure the STT settings with the `"vgwActSetSTTConfig"` command. See [Editing JSON in the dialog response](/docs/services/voice-agent?topic=voice-agent-api#json-editor).

1. In the JSON editor for the {{site.data.keyword.conversationshort}} dialog, add the `"vgwActSetSTTConfig"` command to your dialog node.

1. Add your `parameters`, `thirdPartyCredentials`, and `credentials`.

  * Make sure that you use `"https://stt-adapter"` as the value for the `"url"` credential.
  * Use `\\` to escape special characters, such as `@` in your `client_email`.
  {: tip}

  The following example shows sample credentials and an STT configuration that {{site.data.keyword.conversationshort}} sends to {{site.data.keyword.iva_short}}.

  ```json
        {
          "command": "vgwActSetSTTConfig",
          "parameters": {
            "config": {
              "languageCode": "en-US"
            },
            "credentials": {
              "url": "https://stt-adapter"
            },
            "thirdPartyCredentials": {
              "type": "service_account",
              "auth_uri": "https://accounts.google.com/o/oauth2/auth",
              "client_id": "100033044440506077880901",
              "token_uri": "https://accounts.google.com/o/oauth2/token",
              "project_id": "my_google_project",
              "private_key": "-----BEGIN PRIVATE ... \n-----END PRIVATE KEY-----\n",
              "client_email": "developer1\\@my_google_project.iam.gserviceaccount.com",
              "private_key_id": "d2e45f67gh8i90123j4klm565opq7rs8901t1234",
              "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/developer1@my_google_project.iam.gserviceaccount.com",
              "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs"
            }
          }
        }
  ```
  {: codeblock}


## Connecting to Google Text-to-Speech from a {{site.data.keyword.conversationshort}} dialog node
{: #tts_dialog}

Instead of configuring your connection to Google Text-to-Speech by editing your voice agent, you can program your {{site.data.keyword.conversationshort}} to configure the TTS settings with the `"vgwActSetTTSConfig"` command. See [Editing JSON in the dialog response](/docs/services/voice-agent?topic=voice-agent-api#json-editor).

1. In the JSON editor for the {{site.data.keyword.conversationshort}} dialog, add the `"vgwActSetTTSConfig"` command to your dialog node.

1. Add your `parameters`, `thirdPartyCredentials`, and `credentials`.

  * Make sure that you use `"https://tts-adapter"` as the value for the `"url"` credential.
  * Use `\\` to escape special characters, such as `@` in your `client_email`.
  {: tip}

  The following example shows sample credentials and an TTS configuration that {{site.data.keyword.conversationshort}} sends to {{site.data.keyword.iva_short}}.

  ```json
      {
          "command": "vgwActSetTTSConfig",
          "parameters": {
            "config": {
              "audioConfig": {
                "speakingRate": 2
              },
              "voiceConfig": {
                "ssmGender": "MALE",
                "languageCode": "en-US"
              }
            },
            "credentials": {
              "url": "https://tts-adapter"
            },
            "thirdPartyCredentials": {
              "type": "service_account",
              "auth_uri": "https://accounts.google.com/o/oauth2/auth",
              "client_id": "100033044440506077880901",
              "token_uri": "https://accounts.google.com/o/oauth2/token",
              "project_id": "my_google_project",
              "private_key": "-----BEGIN PRIVATE ... \n-----END PRIVATE KEY-----\n",
              "client_email": "developer1\\@my_google_project.iam.gserviceaccount.com",
              "private_key_id": "d2e45f67gh8i90123j4klm565opq7rs8901t1234",
              "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/developer1@my_google_project.iam.gserviceaccount.com",
              "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs"
            }
          }
        }
  ```
  {: codeblock}
