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


# Utilización de la configuración dinámica para conectar con servicios de terceros
{: #dynamic-donfig}

Puede conectar servicios de habla y texto de terceros estableciendo el valor de Habla a texto o de Texto a habla en el nodo de diálogo de {{site.data.keyword.conversationshort}}.
{: shortdesc}

Consulte [Programación de agentes de voz mediante la API](api.html) para ver ejemplos de código e información sobre cómo definir estados e iniciar secuencias de acciones.

## Conexión de Google Speech-to-Text desde un nodo de diálogo de {{site.data.keyword.conversationshort}}
{: #stt_dialog}

En lugar de configurar su conexión con Google Speech-to-Text editando el agente de voz, puede programar su {{site.data.keyword.conversationshort}} para configurar los valores de STT con el mandato `"vgwActSetSTTConfig"`. Consulte [Edición de JSON en la respuesta del diálogo](api.html#json-editor).

1. En el editor de JSON para el diálogo de {{site.data.keyword.conversationshort}}, añada el mandato `"vgwActSetSTTConfig"` al nodo del diálogo.

1. Añada los `parámetros` `thirdPartyCredentials` y `credentials`.

  * Asegúrese de utilizar `"https://stt-adapter"` como valor de la credencial `"url"`.
  * Utilice `\\` como escape de caracteres especiales, como `@` en `client_email`.
  {: tip}

  En el siguiente ejemplo se muestran credenciales de ejemplo y una configuración de STT que {{site.data.keyword.conversationshort}} envía a {{site.data.keyword.iva_short}}.

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


## Conexión de Google Text-to-Speech desde un nodo de diálogo de {{site.data.keyword.conversationshort}}
{: #tts_dialog}

En lugar de configurar su conexión con Google Text-to-Speech editando el agente de voz, puede programar su {{site.data.keyword.conversationshort}} para configurar los valores de TTS con el mandato `"vgwActSetTTSConfig"`. Consulte [Edición de JSON en la respuesta del diálogo](api.html#json-editor).

1. En el editor de JSON para el diálogo de {{site.data.keyword.conversationshort}}, añada el mandato `"vgwActSetTTSConfig"` al nodo del diálogo.

1. Añada los `parámetros` `thirdPartyCredentials` y `credentials`.

  * Asegúrese de utilizar `"https://tts-adapter"` como valor de la credencial `"url"`.
  * Utilice `\\` como escape de caracteres especiales, como `@` en `client_email`.
  {: tip}

  En el siguiente ejemplo se muestran credenciales de ejemplo y una configuración de TTS que {{site.data.keyword.conversationshort}} envía a {{site.data.keyword.iva_short}}.

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
