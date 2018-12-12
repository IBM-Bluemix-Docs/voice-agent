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


# Utilizzo della configurazione dinamica per il collegamento a servizi di terze parti
{: #dynamic-donfig}

Puoi collegare i servizi di discorso e testo di terze parti configurando Speech to Text o Text to Speech da un nodo di dialogo {{site.data.keyword.conversationshort}}.
{: shortdesc}

Consulta [Programmazione degli agent vocali utilizzando l'API](api.html) per informazioni ed esempi di codice su come configurare e avviare le sequenze di azioni.

## Collegamento a Google Speech-to-Text da un nodo di dialogo {{site.data.keyword.conversationshort}} 
{: #stt_dialog}

Invece di configurare la tua connessione a Google Speech-to-Text modificando il tuo agent vocale, puoi programmare {{site.data.keyword.conversationshort}} per configurare le impostazioni STT con il comando `"vgwActSetSTTConfig"`. Consulta [Modifica del JSON nella risposta del dialogo](api.html#json-editor).

1. Nell'editor JSON della finestra di dialogo {{site.data.keyword.conversationshort}}, aggiungi il comando `"vgwActSetSTTConfig"` al tuo nodo di dialogo.

1. Aggiungi i tuoi valori per `parameters`, `thirdPartyCredentials` e `credentials`.

  * Assicurati di utilizzare `"https://stt-adapter"` per il valore della credenziale `"url"`.
  * Utilizza `\\` per indicare i caratteri speciali, come ad esempio `@` in `client_email`.
  {: tip}

  Il seguente esempio mostra le credenziali di esempio e una configurazione STT che {{site.data.keyword.conversationshort}} invia a {{site.data.keyword.iva_short}}.

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


## Collegamento a Google Text-to-Speech da un nodo di dialogo {{site.data.keyword.conversationshort}} 
{: #tts_dialog}

Invece di configurare la tua connessione a Google Text-to-Speech modificando il tuo agent vocale, puoi programmare {{site.data.keyword.conversationshort}} per configurare le impostazioni TTS con il comando `"vgwActSetTTSConfig"`. Consulta [Modifica del JSON nella risposta del dialogo](api.html#json-editor).

1. Nell'editor JSON della finestra di dialogo {{site.data.keyword.conversationshort}}, aggiungi il comando `"vgwActSetTTSConfig"` al tuo nodo di dialogo.

1. Aggiungi i tuoi valori per `parameters`, `thirdPartyCredentials` e `credentials`.

  * Assicurati di utilizzare `"https://tts-adapter"` per il valore della credenziale `"url"`.
  * Utilizza `\\` per indicare i caratteri speciali, come ad esempio `@` in `client_email`.
  {: tip}

  Il seguente esempio mostra le credenziali di esempio e una configurazione TTS che {{site.data.keyword.conversationshort}} invia a {{site.data.keyword.iva_short}}.

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
