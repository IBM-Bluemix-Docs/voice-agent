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


# 動的構成を使用してサード・パーティー・サービスに接続する
{: #dynamic-donfig}

{{site.data.keyword.conversationshort}} のダイアログ・ノードから、音声認識または音声合成を設定してサード・パーティーの音声テキスト変換サービスに接続できます。
{: shortdesc}

状態を設定してアクション・シーケンスを開始する方法を示すサンプル・コードや情報については、[API を使用したボイス・エージェントのプログラミング](api.html)を参照してください。

## {{site.data.keyword.conversationshort}} ダイアログ・ノードから Google Speech-to-Text に接続する
{: #stt_dialog}

ボイス・エージェントを編集して Google Speech-to-Text への接続を構成する代わりに、`"vgwActSetSTTConfig"` コマンドを使用して STT 設定を構成するように、{{site.data.keyword.conversationshort}} をプログラミングできます。 [ダイアログ応答での JSON の編集](api.html#json-editor)を参照してください。

1. {{site.data.keyword.conversationshort}} ダイアログ用の JSON エディターで、`"vgwActSetSTTConfig"` コマンドをダイアログ・ノードに追加します。

1. `parameters`、`thirdPartyCredentials`、`credentials` を追加します。

  * `"url"` 資格情報の値には、`"https://stt-adapter"` を使用してください。
  * `client_email` 内の `@` のような特殊文字は、`\\` を使用してエスケープしてください。
  {: tip}

  以下の例は、{{site.data.keyword.conversationshort}} が {{site.data.keyword.iva_short}} に送信する資格情報と STT 構成のサンプルを示しています。

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


## {{site.data.keyword.conversationshort}} ダイアログ・ノードから Google Text-to-Speech に接続する
{: #tts_dialog}

ボイス・エージェントを編集して Google Text-to-Speech への接続を構成する代わりに、`"vgwActSetTTSConfig"` コマンドを使用して TTS 設定を構成するように、{{site.data.keyword.conversationshort}} をプログラミングできます。 [ダイアログ応答での JSON の編集](api.html#json-editor)を参照してください。

1. {{site.data.keyword.conversationshort}} ダイアログ用の JSON エディターで、`"vgwActSetTTSConfig"` コマンドをダイアログ・ノードに追加します。

1. `parameters`、`thirdPartyCredentials`、`credentials` を追加します。

  * `"url"` 資格情報の値には、`"https://tts-adapter"` を使用してください。
  * `client_email` 内の `@` のような特殊文字は、`\\` を使用してエスケープしてください。
  {: tip}

  以下の例は、{{site.data.keyword.conversationshort}} が {{site.data.keyword.iva_short}} に送信する資格情報と TTS 構成のサンプルを示しています。

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
