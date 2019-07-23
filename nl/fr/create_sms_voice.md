---

copyright:
  years: 2019
lastupdated: "2019-06-24"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Création d'un agent vocal activé SMS
{: #sms_voice_config_instance}

Après avoir créé votre service {{site.data.keyword.iva_full}}, vous pouvez créer des agents vocaux individuels avec fonction SMS, ou des agents vocaux avec uniquement des possibilités de SMS, à partir du tableau de bord _Gérer_. Vous pouvez configurer {{site.data.keyword.iva_full}} de manière à recevoir des appels vocaux entrants et répondre avec des messages SMS sortants, selon la fonction vocale reçue par l'utilisateur. Pour configurer, ajouter un noeud et une intention dans votre service {{site.data.keyword.conversationshort}}, procédez comme suit :
{: shortdesc}


1. Accédez à l'onglet _Agents vocaux_ sur le tableau de bord _Gestion_, puis cliquez sur **Créer un agent vocal**.

1. Pour **Type d'agent**, sélectionnez _Voix + SMS_.

1. Suivez les instructions fournies dans [Création d'un agent vocal](/docs/services/voice-agent?topic=voice-agent-config_instance).

1. Cochez la case **Démarrer une conversion à partir des messages entrants** pour autoriser les utilisateurs à commencer une session SMS avec votre agent SMS.

1. Cochez la case **Notifier lors d'un délai d'attente de session** pour que votre agent SMS envoie un message SMS à l'utilisateur afin de lui signaler que l'agent n'a pas reçu de réponse dans un certain délai et qu'il va dépasser le délai d'attente. 

   - Voir [Options avancées](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) pour plus d'informations sur les **Options avancées** disponibles pour votre agent SMS, par exemple, définir un délai d'attente personnalisé pour la session.

1. Suivez les instructions fournies dans [Création d'un agent SMS](/docs/services/voice-agent?topic=voice-agent-sms_config_instance) pour créer un agent SMS.

1. _**Remarque :**_ pour qu'un agent dispose à la fois de l'intégration Voix et SMS, par exemple, réception de message entrant vocal et envoi en retour d'un message SMS sortant en réponse, vous **devez** utiliser l'un de vos numéros d'appel **vocal** pour l'agent **SMS**.

### Configuration de l'assistant Watson pour l'intégration Voix et SMS
{: #sms_outbound}

1. Dans votre tableau de bord {{site.data.keyword.Bluemix_notm}}, sélectionnez l'instance {{site.data.keyword.conversationshort}} qui est utilisée par votre agent vocal.

1. Créez **outbound SMS intent** depuis le tableau de bord.

1. Ajoutez **outbound SMS node** depuis le tableau de bord.

1. Dans la section _If assistant recognizes:_, sélectionnez l'attribut **outbound SMS intent** précédemment créé.

1. Ajoutez la réponse au noeud. Copiez et collez le fragment de code suivant pour remplacer le code qui figure dans la zone :

    ```json
        {
            "output": {
                "text": {
                "values": [
                    "Okay. I will send you a text message now."
                ],
     "selection_policy": "sequential"
                },
                "vgwActionSequence": [
                {
                    "command": "vgwActSendSMS",
                    "parameters": {
                    "message": "This is a test message from Watson Assistant"
                    }
                },
                {
                    "command": "vgwActPlayText"
                }
                ]
            }
        }
    ```
    {: codeblock}


1. Appelez votre agent et déclenchez le noeud pour recevoir un message texte sur le téléphone à partir duquel vous appelez. 

Pour en apprendre davantage sur l'utilisation du service {{site.data.keyword.conversationshort}}, voir [A propos de {{site.data.keyword.conversationshort}}](/docs/services/assistant?topic=assistant-index#indext).
