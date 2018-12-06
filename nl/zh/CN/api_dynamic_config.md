---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-08"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 使用动态配置连接到第三方服务
{: #dynamic-donfig}

您可以通过在 {{site.data.keyword.conversationshort}} 对话节点中设置“语音转文字”或“文字转语音”来连接第三方语音和文字服务。
{: shortdesc}

要查看代码示例以及有关如何设置状态和启动操作序列的信息，请参阅[使用 API 对语音代理程序编程](api.html)。

## 从 {{site.data.keyword.conversationshort}} 对话节点连接到 Google Speech-to-Text
{: #stt_dialog}

您可以对 {{site.data.keyword.conversationshort}} 进行编程，以使用 `"vgwActSetSTTConfig"` 命令来配置 STT 设置，而不是通过编辑语音代理程序来配置与 Google Speech-to-Text 的连接。请参阅[编辑对话响应中的 JSON](api.html#json-editor)。

1. 在 {{site.data.keyword.conversationshort}} 对话的 JSON 编辑器中，向您的对话节点添加 `"vgwActSetSTTConfig"` 命令。

1. 添加 `parameters`、`thirdPartyCredentials` 和 `credentials`。

  * 确保使用 `"https://stt-adapter"` 作为 `"url"` 凭证的值。
  * 使用 `\\` 来转义特殊字符，例如 `client_email` 中的 `@`。
  {: tip}

  以下示例显示了 {{site.data.keyword.conversationshort}} 发送给 {{site.data.keyword.iva_short}} 的样本凭证和 STT 配置。

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


## 从 {{site.data.keyword.conversationshort}} 对话节点连接到 Google Text-to-Speech
{: #tts_dialog}

您可以对 {{site.data.keyword.conversationshort}} 进行编程，以使用 `"vgwActSetTTSConfig"` 命令来配置 TTS 设置，而不是通过编辑语音代理程序来配置与 Google Text-to-Speech 的连接。请参阅[编辑对话响应中的 JSON](api.html#json-editor)。

1. 在 {{site.data.keyword.conversationshort}} 对话的 JSON 编辑器中，向您的对话节点添加 `"vgwActSetTTSConfig"` 命令。

1. 添加 `parameters`、`thirdPartyCredentials` 和 `credentials`。

  * 确保使用 `"https://tts-adapter"` 作为 `"url"` 凭证的值。
  * 使用 `\\` 来转义特殊字符，例如 `client_email` 中的 `@`。
  {: tip}

  以下示例显示了 {{site.data.keyword.conversationshort}} 发送给 {{site.data.keyword.iva_short}} 的样本凭证和 TTS 配置。

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
