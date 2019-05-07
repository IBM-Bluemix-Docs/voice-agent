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


# Usando a configuração dinâmica para conectar-se a serviços de terceiro
{: #dynamic-donfig}

É possível conectar os serviços de fala e texto de terceiro configurando Fala para texto ou Texto para fala por meio de um nó de diálogo do {{site.data.keyword.conversationshort}}.
{: shortdesc}

Consulte [Programando os agentes de voz usando a API](/docs/services/voice-agent?topic=voice-agent-api) para obter exemplos de códigos e informações sobre como configurar estados e iniciar sequências de ação.

## Conectando-se ao Google Speech-to-Text por meio de um nó de diálogo do {{site.data.keyword.conversationshort}}
{: #stt_dialog}

Em vez de configurar a conexão com o Google Speech-to-Text editando o agente de voz, é possível programar o {{site.data.keyword.conversationshort}} para definir as configurações STT com o comando `"vgwActSetSTTConfig"`. Consulte [Editando o JSON na resposta do diálogo](/docs/services/voice-agent?topic=voice-agent-api#json-editor).

1. No editor JSON para o diálogo do {{site.data.keyword.conversationshort}}, inclua o comando `"vgwActSetSTTConfig"` no nó de diálogo.

1. Inclua os seus `parameters`, `thirdPartyCredentials` e `credentials`.

  * Certifique-se de usar `"https://stt-adapter"` como o valor para a credencial `"url"`.
  * Use `\\` para escapar caracteres especiais, como `@` no `client_email`.
  {: tip}

  O exemplo a seguir mostra as credenciais de amostra e uma configuração STT que o {{site.data.keyword.conversationshort}} envia para o {{site.data.keyword.iva_short}}.

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


## Conectando-se ao Google Text-to-Speech por meio de um nó de diálogo do {{site.data.keyword.conversationshort}}
{: #tts_dialog}

Em vez de configurar a conexão com o Google Text-to-Speech editando o agente de voz, é possível programar o {{site.data.keyword.conversationshort}} para definir as configurações TTS com o comando `"vgwActSetTTSConfig"`. Consulte [Editando o JSON na resposta do diálogo](/docs/services/voice-agent?topic=voice-agent-api#json-editor).

1. No editor JSON para o diálogo do {{site.data.keyword.conversationshort}}, inclua o comando `"vgwActSetTTSConfig"` no nó de diálogo.

1. Inclua os seus `parameters`, `thirdPartyCredentials` e `credentials`.

  * Certifique-se de usar `"https://tts-adapter"` como o valor para a credencial `"url"`.
  * Use `\\` para escapar caracteres especiais, como `@` no `client_email`.
  {: tip}

  O exemplo a seguir mostra as credenciais de amostra e uma configuração TTS que o {{site.data.keyword.conversationshort}} envia para o {{site.data.keyword.iva_short}}.

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
