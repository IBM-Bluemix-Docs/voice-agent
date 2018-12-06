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


# Utilisation de la configuration dynamique pour la connexion à des services tiers
{: #dynamic-donfig}

Vous pouvez connecter des services voix et texte tiers en définissant Speech-to-Text ou Text-to-Speech depuis un noeud de dialogue {{site.data.keyword.conversationshort}}.
{: shortdesc}

Voir [Programmation des agents vocaux à l'aide de l'API](api.html) pour obtenir des exemples de code et des informations sur la manière dont vous pouvez définir des états et initier des séquences d'action.

## Connexion à Google Speech-to-Text depuis un noeud de dialogue {{site.data.keyword.conversationshort}}
{: #stt_dialog}

Au lieu de configurer votre connexion à Google Speech-to-Text en éditant votre agent vocal, vous pouvez programmer {{site.data.keyword.conversationshort}} pour configurer les paramètres Speech-To-Text avec la commande `"vgwActSetSTTConfig"`. Voir [Edition du code JSON dans la réponse de dialogue](api.html#json-editor).

1. Dans l'éditeur JSON du dialogue {{site.data.keyword.conversationshort}}, ajoutez la commande `"vgwActSetSTTConfig"` à votre noeud de dialogue.

1. Renseignez `parameters`, `thirdPartyCredentials` et `credentials`.

  * Vérifiez que vous utilisez `"https://stt-adapter"` comme valeur pour les données d'identification `"url"`.
  * Utilisez `\\` pour mettre en échappement les caractères spéciaux tels que `@` sous `client_email`.
  {: tip}

  L'exemple suivant montre des exemples de données d'identification et une configuration Speech-To-Text que {{site.data.keyword.conversationshort}} envoie à {{site.data.keyword.iva_short}}.

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


## Connexion à Google Text-to-Speech depuis un noeud de dialogue {{site.data.keyword.conversationshort}}
{: #tts_dialog}

Au lieu de configurer votre connexion à Google Text-to-Speech en éditant votre agent vocal, vous pouvez programmer {{site.data.keyword.conversationshort}} pour configurer les paramètres Text-To-Speech vocaux avec la commande `"vgwActSetTTSConfig"`. Voir [Edition du code JSON dans la réponse de dialogue](api.html#json-editor).

1. Dans l'éditeur JSON du dialogue {{site.data.keyword.conversationshort}}, ajoutez la commande `"vgwActSetTTSConfig"` à votre noeud de dialogue.

1. Renseignez `parameters`, `thirdPartyCredentials` et `credentials`.

  * Vérifiez que vous utilisez `"https://tts-adapter"` comme valeur pour les données d'identification `"url"`.
  * Utilisez `\\` pour mettre en échappement les caractères spéciaux tels que `@` sous `client_email`.
  {: tip}

  L'exemple suivant montre des exemples de données d'identification et une configuration Text-To-Speech que {{site.data.keyword.conversationshort}} envoie à {{site.data.keyword.iva_short}}.

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
