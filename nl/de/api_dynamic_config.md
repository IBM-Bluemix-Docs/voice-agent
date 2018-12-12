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


# Dynamische Konfiguration für die Verbindung zu Services anderer Anbieter verwenden
{: #dynamic-donfig}

Sie können eine Verbindung zu Sprach- und Textservices anderer Anbieter herstellen, indem Sie die Speech to Text- oder Text to Speech-Funktion von einem {{site.data.keyword.conversationshort}}-Dialogknoten aus festlegen.
{: shortdesc}

Codebeispiele und Informationen zum Festlegen von Status und zum Einleiten von Aktionsfolgen finden Sie unter [Sprachagenten mithilfe der API programmieren](api.html).

## Verbindung zu Google Speech-to-Text über einen {{site.data.keyword.conversationshort}}-Dialogknoten herstellen
{: #stt_dialog}

Anstatt Ihre Verbindung zu Google Speech-to-Text durch Bearbeitung Ihres Sprachagenten zu konfigurieren, können Sie Ihre {{site.data.keyword.conversationshort}}-Instanz so programmieren, dass die STT-Einstellungen mit dem Befehl `"vgwActSetSTTConfig"` konfiguriert werden. Weitere Informationen finden Sie in [JSON in der Dialogantwort bearbeiten](api.html#json-editor).

1. Fügen Sie im JSON-Editor für den {{site.data.keyword.conversationshort}}-Dialog den Befehl `"vgwActSetSTTConfig"` zu Ihrem Dialogknoten hinzu.

1. Fügen Sie Ihre Parameter, Berechtigungsnachweise anderer Anbieter und Berechtigungsnachweise (`parameters`, `thirdPartyCredentials` und `credentials`) hinzu.

  * Stellen Sie sicher, dass Sie `"https://stt-adapter"` als Wert für den Berechtigungsnachweis `"url"` verwenden.
  * Verwenden Sie `\\`, um Sonderzeichen mit Escapezeichen zu versehen; z. B. `@` in Ihrer Client-E-Mail (`client_email`).
  {: tip}

  Das folgende Beispiel zeigt Beispielberechtigungsnachweise und eine STT-Konfiguration, die {{site.data.keyword.conversationshort}} an {{site.data.keyword.iva_short}} sendet.

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


## Verbindung zu Google Text-to-Speech über einen {{site.data.keyword.conversationshort}}-Dialogknoten herstellen
{: #tts_dialog}

Anstatt Ihre Verbindung zu Google Text-to-Speech durch Bearbeitung Ihres Sprachagenten zu konfigurieren, können Sie Ihre {{site.data.keyword.conversationshort}}-Instanz so programmieren, dass die TTS-Einstellungen mit dem Befehl `"vgwActSetTTSConfig"` konfiguriert werden. Weitere Informationen finden Sie in [JSON in der Dialogantwort bearbeiten](api.html#json-editor).

1. Fügen Sie im JSON-Editor für den {{site.data.keyword.conversationshort}}-Dialog den Befehl `"vgwActSetTTSConfig"` zu Ihrem Dialogknoten hinzu.

1. Fügen Sie Ihre Parameter, Berechtigungsnachweise anderer Anbieter und Berechtigungsnachweise (`parameters`, `thirdPartyCredentials` und `credentials`) hinzu.

  * Stellen Sie sicher, dass Sie `"https://tts-adapter"` als Wert für den Berechtigungsnachweis `"url"` verwenden.
  * Verwenden Sie `\\`, um Sonderzeichen mit Escapezeichen zu versehen; z. B. `@` in Ihrer Client-E-Mail (`client_email`).
  {: tip}

  Das folgende Beispiel zeigt Beispielberechtigungsnachweise und eine TTS-Konfiguration, die {{site.data.keyword.conversationshort}} an {{site.data.keyword.iva_short}} sendet.

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
