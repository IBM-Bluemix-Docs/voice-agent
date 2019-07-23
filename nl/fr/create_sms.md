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


# Création d'un agent SMS
{: #sms_config_instance}

Après avoir créé votre service {{site.data.keyword.iva_full}}, vous pouvez créer des agents SMS individuels à partir du tableau de bord _Gérer_.
{: shortdesc}

1. Accédez à l'onglet _Agents vocaux_ sur le tableau de bord _Gestion_, puis cliquez sur **Créer un agent vocal**.

1. Pour **Type d'agent**, sélectionnez _SMS_.

1. Dans la zone **Nom**, spécifiez un nom unique pour votre agent vocal. Par exemple, `Customer Support - North America`. Le nom peut comporter jusqu'à 64 caractères.

1. Dans la zone Numéro de téléphone, ajoutez le numéro depuis votre liaison SIP, en incluant le code pays et l'indicatif régional. Par exemple, pour un numéro 800 aux Etats-Unis, spécifiez le numéro de téléphone sous la forme suivante : 18883334444. Le numéro de téléphone peut comporter jusqu'à 30 caractères, y compris des espaces et les caractères + ( ) -. SMS ne pend en charge qu'un numéro par utilisateur.

1. Sous **Fournisseur SMS**, entrez le nom d'utilisateur, le mot de passe et l'URL d'API de votre fournisseur SMS. Par exemple, si vous utilisez _Twilio_, le nom d'utilisateur est votre **Identificateur de sécurité**, le mot de passe est votre **Jeton d'authentification** et votre fournisseur SMS est `https://api.twilio.com`

1. Sous **Conversation**, configurez la connexion à votre instance de service {{site.data.keyword.conversationshort}}. Vous pouvez utiliser des instances de service {{site.data.keyword.conversationshort}} dans vos comptes {{site.data.keyword.Bluemix_notm}} ou ceux de quelqu'un d'autre. Vous pouvez également vous connecter à l'une de ces options via un moteur d'orchestration de service.

   * Si vous créez un agent SMS dans la région de Dallas ou de Washington DC et n'avez pas d'instance de service {{site.data.keyword.conversationshort}}, vous pouvez en créer une dans le menu **Instance de service**.
   * Vous pouvez également vous connecter à d'autres sources d'un dialogue {{site.data.keyword.conversationshort}} ou à un moteur d'orchestration de service en changeant le [**Type de service**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service).
   * Si vous souhaitez configurer plusieurs emplacements de service, cliquez sur l'option Autre emplacement et sélectionnez **Activer l'emplacement** afin de configurer la connexion à votre autre instance {{site.data.keyword.conversationshort}}. Pour plus d'informations, voir [Ajout de plusieurs emplacements de service Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).

1. Cochez la case **Démarrer une conversion à partir des messages entrants** pour autoriser les utilisateurs à commencer une session SMS avec votre agent SMS.

1. Cochez la case **Notifier lors d'un délai d'attente de session** pour que votre agent SMS envoie un message SMS à l'utilisateur afin de lui signaler que l'agent n'a pas reçu de réponse dans un certain délai et qu'il va dépasser le délai d'attente. 

    - Voir [Options avancées](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) pour plus d'informations sur les **Options avancées** disponibles pour votre agent SMS, par exemple, définir un délai d'attente personnalisé pour la session.
    - Ne cochez la case que si vous voulez être averti en cas de dépassement de délai d'une session.

1. Vous pouvez également choisir d'activer la transmission d'événements afin de collecter des informations sur les appels qui sont gérés par vos agents vocaux dans une instance {{site.data.keyword.cloudantfull}}. Pour plus d'informations, voir [Activation de la transmission d'événements pour les agents vocaux](/docs/services/voice-agent?topic=voice-agent-event_forwarding). Pour connaître d'autres options de configuration, voir [Configuration d'un agent vocal](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1.  Cliquez sur **Créer un agent vocal** pour créer votre agent SMS et de nouveaux services.

1. Suivez [les instructions](/docs/services/voice-agent?topic=voice-agent-connect-sms) de connexion à un fournisseur SMS.

Une fois l'agent SMS créé, testez-le en envoyant un texto à son numéro de téléphone. Vous pouvez afficher les détails de votre interaction sur le tableau de bord _Utilisation_. Voir [Affichage de l'utilisation et des journaux](/docs/services/voice-agent?topic=voice-agent-logging).

Pour activer la messagerie SMS entre des clients et un agent vocal pendant un appel vocal, le numéro SMS doit correspondre au numéro de téléphone.
{: tip}

Avant de créer un agent SMS ou d'ajouter une fonctionnalité SMS à votre agent vocal, vous **devez** disposer des données d'identification appropriées et générer une clé d'API afin de programmer votre numéro SMS. Pour plus d'informations, voir [Génération d'une clé d'API et définition de données d'identification](/docs/services/voice-agent?topic=voice-agent-connect-sms#sms_access).

Vous **devez** également configurer votre liaison SIP pour la fonctionnalité SMS. Reportez-vous aux instructions de votre fournisseur, par exemple, Twilio. Si vous n'avez pas de numéro de téléphone Twilio, voir [Création d'une liaison SIP Twilio](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup).

Une fois en possession d'un numéro Twilio, vous devez le configurer pour la fonctionnalité SMS. Pour plus d'informations, voir [Configuration de Twilio pour SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

En cas de difficulté lors de la création des données d'identification, contactez l'administrateur de votre instance de service pour qu'il vous accorde un accès *Responsable* ou *Auteur*.
{: tip}

## Options avancées pour les agents SMS
{: #sms_advanced}

Cliquez sur **Afficher les options avancées** après la zone **Numéro de téléphone**.

1. Définissez le **Délai d'attente de lecture de conversation** (facultatif). Il s'agit de la durée en secondes durant laquelle la passerelle SMS attend une réponse de l'assistant Watson. Lorsque ce délai est atteint, la passerelle SMS tente à nouveau de contacter l'assistant Watson. Si le service n'est toujours pas joignable, le message SMS/MMS échoue. Par défaut, ce délai est de 30 secondes.

1. Définissez le **Délai d'attente de session** (facultatif). Il s'agit du délai en secondes au-delà duquel la session expire si la passerelle SMS ne reçoit pas de réponse de l'utilisateur.

1. Définissez un **Message de réponse en cas d'échec de la conversation**. Il s'agit du message de réponse par défaut qui est envoyé lorsque l'assistant Watson n'est pas joignable. Par défaut, ce message est le suivant `Nous sommes désolés, mais nous ne pouvons pas répondre à votre message`.

### Configuration de l'agent SMS pour terminer la session
{: #sms_terminate}

L'agent SMS {{site.data.keyword.iva_full}} met fin à une session en se basant sur le délai d'attente de session, configurable et défini par défaut sur 30 secondes. 

Vous pouvez également ajouter un noeud à votre service {{site.data.keyword.conversationshort}} afin de répondre à une commande de fin de session émise par l'utilisateur. 

1. Dans votre tableau de bord {{site.data.keyword.Bluemix_notm}}, sélectionnez l'instance {{site.data.keyword.conversationshort}} qui est utilisée par votre agent vocal.

1. Créez une **Terminate SMS intent** depuis le tableau de bord. Vous pouvez également modifier une intention existante que vous avez déjà utilisée pour l'agent vocal, par exemple, _Fin d'appel_.

1. Ajoutez un **Terminate SMS node** depuis le tableau de bord.

1. Dans la section _If assistant recognizes:_, ajoutez l'attribut **Terminate SMS intent** précédemment créé.

1. Ajoutez la réponse au noeud. Copiez et collez le fragment de code suivant pour remplacer le code qui figure dans la zone :

    ```json
        {
            "output": {
                 "text": {
                    "values": [
                        "Thank you for using the service. Goodbye!"
                    ],
                    "selection_policy”: “sequential"
                },
                "smsAction": {
                    "command": "terminateSession"
                }
            }
        }
    ```
    {: codeblock}

Une fois l'agent vocal créé, testez-le en appelant son numéro de téléphone ou en lui envoyant un texto en fonction de son type. Vous pouvez afficher les détails de votre interaction sur le tableau de bord _Utilisation_. Voir [Affichage de l'utilisation et des journaux](/docs/services/voice-agent?topic=voice-agent-logging).
