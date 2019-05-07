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


# 使用動態配置來連接至協力廠商服務
{: #dynamic-donfig}

您可以從 {{site.data.keyword.conversationshort}} 對話節點設定語音轉文字或文字轉語音，來連接協力廠商語音及文字服務。
{: shortdesc}

如需程式碼範例和如何設定狀態及起始動作序列的相關資訊，請參閱[使用 API 程式設計語音代理程式](/docs/services/voice-agent?topic=voice-agent-api)。

## 從 {{site.data.keyword.conversationshort}} 對話節點連接至 Google Speech-to-Text
{: #stt_dialog}

您可以程式設計 {{site.data.keyword.conversationshort}}，用 `"vgwActSetSTTConfig"` 指令配置 STT 設定，而不必編輯語音代理程式來配置 Google Speech-to-Text 的連線。請參閱[編輯對話回應中的 JSON](/docs/services/voice-agent?topic=voice-agent-api#json-editor)。

1. 在 {{site.data.keyword.conversationshort}} 對話的 JSON 編輯器中，新增 `"vgwActSetSTTConfig"` 指令至您的對話節點。

1. 新增您的 `parameters`、`thirdPartyCredentials` 及 `credentials`。

  * 確定您使用 `"https://stt-adapter"` 作為 `"url"` 認證的值。
  * 使用 `\\` 跳出特殊字元，例如 `client_email` 中的 `@`。
  {: tip}

  下列範例顯示 {{site.data.keyword.conversationshort}} 傳送至 {{site.data.keyword.iva_short}} 的範例認證和 STT 配置。

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


## 從 {{site.data.keyword.conversationshort}} 對話節點連接至 Google Text-to-Speech
{: #tts_dialog}

您可以程式設計 {{site.data.keyword.conversationshort}}，用 `"vgwActSetTTSConfig"` 指令配置 TTS 設定，而不必編輯語音代理程式來配置 Google Speech-to-Text 的連線。請參閱[編輯對話回應中的 JSON](/docs/services/voice-agent?topic=voice-agent-api#json-editor)。

1. 在 {{site.data.keyword.conversationshort}} 對話的 JSON 編輯器中，新增 `"vgwActSetTTSConfig"` 指令至您的對話節點。

1. 新增您的 `parameters`、`thirdPartyCredentials` 及 `credentials`。

  * 確定您使用 `"https://tts-adapter"` 作為 `"url"` 認證的值。
  * 使用 `\\` 跳出特殊字元，例如 `client_email` 中的 `@`。
  {: tip}

  下列範例顯示 {{site.data.keyword.conversationshort}} 傳送至 {{site.data.keyword.iva_short}} 的範例認證和 TTS 配置。

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
