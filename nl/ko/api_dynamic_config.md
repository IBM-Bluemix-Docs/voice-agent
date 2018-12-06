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


# 동적 구성을 사용하여 서드파티 서비스에 연결
{: #dynamic-donfig}

{{site.data.keyword.conversationshort}} 대화 노드에서 Speech to Text 또는 Text to Speech를 설정하여 서드파티 음성 및 텍스트 서비스에 연결할 수 있습니다.
{: shortdesc}

상태를 설정하고 조치 순서를 시작하는 방법에 대한 정보와 코드 예제는 [API를 사용한 음성 에이전트 프로그래밍](api.html)을 참조하십시오.

## {{site.data.keyword.conversationshort}} 대화 노드에서 Google Speech-to-Text에 연결
{: #stt_dialog}

음성 에이전트를 편집하여 Google Speech-to-Text에 대한 연결을 구성하는 대신 `"vgwActSetSTTConfig"` 명령을 사용하여 STT 설정을 구성하도록 {{site.data.keyword.conversationshort}}를 프로그래밍할 수 있습니다. [대화 응답에서 JSON 편집](api.html#json-editor)을 참조하십시오.

1. {{site.data.keyword.conversationshort}} 대화에 대한 JSON 편집기에서 `"vgwActSetSTTConfig"` 명령을 대화 노드에 추가하십시오.

1. `parameters`, `thirdPartyCredentials` 및 `credentials`를 추가하십시오.

  * `"https://stt-adapter"`를 `"url"` 인증 정보의 값으로 사용해야 합니다.
  * `client_email`의 `@`과 같은 특수 문자를 이스케이프하려면 `\\`를 사용하십시오.
  {: tip}

  다음 예는 {{site.data.keyword.conversationshort}}에서 {{site.data.keyword.iva_short}}에 전송하는 샘플 인증 정보 및 STT 구성을 보여줍니다.

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


## {{site.data.keyword.conversationshort}} 대화 노드에서 Google Text-to-Speech에 연결
{: #tts_dialog}

음성 에이전트를 편집하여 Google Text-to-Speech에 대한 연결을 구성하는 대신 `"vgwActSetTTSConfig"` 명령을 사용하여 TTS 설정을 구성하도록 {{site.data.keyword.conversationshort}}를 프로그래밍할 수 있습니다. [대화 응답에서 JSON 편집](api.html#json-editor)을 참조하십시오.

1. {{site.data.keyword.conversationshort}} 대화에 대한 JSON 편집기에서 `"vgwActSetTTSConfig"` 명령을 대화 노드에 추가하십시오.

1. `parameters`, `thirdPartyCredentials` 및 `credentials`를 추가하십시오.

  * `"https://tts-adapter"`를 `"url"` 인증 정보의 값으로 사용해야 합니다.
  * `client_email`의 `@`과 같은 특수 문자를 이스케이프하려면 `\\`를 사용하십시오.
  {: tip}

  다음 예는 {{site.data.keyword.conversationshort}}에서 {{site.data.keyword.iva_short}}에 전송하는 샘플 인증 정보 및 TTS 구성을 보여줍니다.

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
