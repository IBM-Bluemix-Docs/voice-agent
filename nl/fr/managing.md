---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Gestion des instances de service et des agents vocaux
{: #managing}

Vous pouvez utiliser le tableau de bord _Gestion_ pour changer la configuration de vos instances de service et créer, éditer, cloner, configurer ou supprimer les agents vocaux individuels. Vous pouvez avoir plusieurs agents vocaux dans votre instance de service, et chaque agent vocal peut avoir jusqu'à 1 000 numéros et descriptions uniques. Toutefois, chaque agent vocal doit avoir un nom unique et au moins un numéro de téléphone.

* **Remarque** : Une seule instance de service {{site.data.keyword.iva_full}} peut comporter jusqu'à 150 agents vocaux.
{: shortdesc}

## Accès au tableau de bord du service Agent vocal
{: #navigate_manage}

Le tableau de bord _Gestion_ est accessible à partir du tableau de bord de votre service {{site.data.keyword.iva_short}}.

1. Accédez à la [liste de ressources de votre compte {{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/resources).

1. Dans la liste des **Services**, sélectionnez votre instance de service **Agent vocal** pour ouvrir le tableau de bord du service sur l'onglet _Gérer_.

## Récapitulatif de l'agent vocal
{: #agent_summary}

Si vous possédez déjà un agent vocal, vous pouvez afficher un récapitulatif de tous les numéros, descriptions et paramètres de configuration de cet agent. Pour cela, cliquez sur le bouton flèche à gauche du **Nom** de l'agent vocal. Le récapitulatif se développe.

Bien que l'agent vocal puisse comporter plusieurs numéros, seul le **Numéro principal** s'affiche dans le récapitulatif. Par défaut, il s'agit du premier numéro ayant été ajouté à l'agent vocal. Ce numéro est utilisé uniquement à des fins d'affichage, et n'a aucun rôle fonctionnel. Si vous préférez afficher un autre numéro de l'agent vocal, consultez la rubrique [Managing Multiple Numbers](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

Vous avez la possibilité d'afficher tous les numéros d'un agent vocal à partir du récapitulatif. Lorsque le récapitulatif a été développé, cliquez sur le bouton **Afficher les numéros** pour faire apparaître la liste de tous les numéros dans une nouvelle boîte de dialogue **Gestion**. Voir la page [Managing Multiple Numbers](/docs/services/voice-agent?topic=voice-agent-multi_num) pour en savoir plus sur l'utilisation de la boîte de dialogue **Gestion**.

## Modification du maximum de connexions simultanées pour votre instance de service
{: #edit_service}

Dans tous les plans, vous recevez gratuitement 2 connexions simultanées. Si vous utilisez le plan _Standard_ ou le plan _Premium_, vous pouvez [modifier le nombre maximal de connexions simultanées](/docs/services/voice-agent?topic=voice-agent-edit_concurrency) défini dans les paramètres par défaut à partir de l'onglet _Instances_.

## Création d'un agent vocal
{: #create_va}

La [création d'un agent vocal](/docs/services/voice-agent?topic=voice-agent-config_instance) s'effectue dans l'onglet _Agents vocaux_, sur le tableau de bord _Gestion_.

## Edition d'un agent vocal
{: #edit_va}

Vous pouvez changer les agents vocaux existants en les éditant dans l'onglet _Agents vocaux_ sur le tableau de bord _Gestion_. Pour éditer un agent vocal, cliquez sur **Editer un agent** dans la liste d'options de l'agent vocal. Modifiez la configuration, puis sauvegardez les modifications.

## Clonage d'un agent vocal
{: #clone_va}

Lorsque vous clonez un agent vocal, toutes les configurations des services Watson sont copiées vers un nouvel agent. Pour cloner un agent vocal, cliquez sur **Cloner un agent** dans la liste d'options pour l'agent vocal. Affectez un nom et un numéro de téléphonique uniques à votre agent vocal, modifiez certaines options de configuration, le cas échéant, et sauvegardez les modifications.

## Suppression d'un agent vocal
{: #delete_va}

Il est possible que vous souhaitiez supprimer un agent vocal afin de libérer son numéro de téléphone. Il ne peut exister qu'un seul agent vocal par numéro de téléphone. Afin d'utiliser un numéro de téléphone pour un autre agent vocal, vous devez d'abord supprimer l'agent vocal qui utilise le numéro de téléphone.

Pour supprimer un agent vocal, accédez à l'onglet _Agents vocaux_, cliquez sur **Supprimer l'agent** dans la liste d'options de l'agent vocal concerné, puis enregistrez vos modifications. L'agent vocal est retiré de la liste des agents vocaux.

## Recherche d'un agent vocal à l'aide d'un numéro ou d'une description
{: #search}

Vous pouvez rechercher des agents vocaux en fonction des numéros ou des descriptions enregistrées sous l'agent.

Dans la barre de _recherche_, tapez un numéro ou une description. Lorsque vous tapez, les résultats de la recherche sont mis à jour automatiquement.  

## Configuration d'un agent vocal
{: #configure_va}

Lorsque vous créez, clonez ou éditez un agent vocal, vous pouvez modifier les paramètres de configuration de votre agent vocal et les connexions aux services associés.

* **[Configuration de plusieurs numéros de téléphone](/docs/services/voice-agent?topic=voice-agent-multi_num) :** Vous pouvez configurer votre agent vocal de manière à utiliser plusieurs numéros de téléphone.
* **[Configuration de plusieurs emplacements de service](/docs/services/voice-agent?topic=voice-agent-disaster-recovery) :** Incluez plusieurs emplacements de service pour vos services connectés afin de permettre la prise en charge de la redondance des services.
* **[Connexion à des services voix et texte tiers](/docs/services/voice-agent?topic=voice-agent-third-party) :** Au lieu d'utiliser {{site.data.keyword.texttospeechshort}} ou {{site.data.keyword.speechtotextshort}}, vous pouvez connecter votre agent vocal à des API tiers, tels que Google Cloud Speech-to-Text.
* **[Utilisation des services dans d'autres espaces de travail {{site.data.keyword.Bluemix_notm}}](/docs/services/voice-agent?topic=voice-agent-other_service) :** Vous pouvez configurer votre agent vocal pour utiliser des instances de service {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.speechtotextshort}} qui appartiennent à des espaces de travail situés dans d'autres comptes {{site.data.keyword.Bluemix_short}}.
* **[Configuration de Watson Assistant avec un moteur d'orchestration de service](/docs/services/voice-agent?topic=voice-agent-conversation_va) :** Vous pouvez vous connecter à une compétence {{site.data.keyword.conversationshort}} via un moteur d'orchestration de service. Un moteur d'orchestration de service intercepte les messages émis vers et depuis le service de manière à vous permettre de les modifier à l'aide d'API tierces.
* **[Activation du transfert d'événement pour les agents vocaux](/docs/services/voice-agent?topic=voice-agent-event_forwarding) :** Vous pouvez collecter et analyser des données d'appel à partir de {{site.data.keyword.iva_short}} afin d'améliorer la fluidité de la conversation avec l'appelant. Chaque agent vocal que vous créez peut transmettre des rapports d'événements à une base de données {{site.data.keyword.cloudant_short_notm}} que vous gérez.

## Configuration des options avancées pour les agents vocaux
{: #config-advanced}

Lorsque vous créez ou clonez un agent vocal, vous pouvez cliquer sur **Afficher les paramètres avancés** pour afficher les options de configuration avancées présentées ci-après.

* **Délai de lecture de conversation (facultatif)** : Cette option définit la durée, en secondes, pendant laquelle l'agent vocal attend une réponse de Watson Assistant. Si la durée est dépassée, l'agent vocal tente à nouveau de contacter Watson Assistant. Si le service n'est toujours pas joignable, l'appel échoue. La valeur par défaut est 5 secondes.
* **Message de réponse en cas d'échec de {{site.data.keyword.conversationshort}} (facultatif)** : message de réponse par défaut qui est envoyé au récepteur de messagerie si l'appel ne peut pas se connecter à {{site.data.keyword.conversationshort}}. Vous pouvez entrer jusqu'à 1024 caractères.
* **Message de réponse en cas d'échec du transfert (facultatif)** : message de réponse par défaut qui est diffusé à l'appelant si le transfert d'appel échoue. Vous pouvez entrer jusqu'à 1024 caractères.
* **En-tête SIP INVITE (facultatif)** : Indique l'en-tête SIP personnalisé à extraire des requêtes SIP INVITE entrantes. Vous pouvez entrer jusqu'à 1024 caractères.
* **Envoyer une réponse provisoire par téléphone depuis {{site.data.keyword.iva_short}}** : envoie une réponse `180 ringing` durant le traitement d'un appel entrant par {{site.data.keyword.iva_short}}. Activée par défaut.
* **Placer l'appelant en attente lors du transfert** : l'appelant est placé en attente durant le transfert. Activée par défaut.
* **Déconnecter l'appel en cas d'échec du transfert** : détermine s'il convient ou non de déconnecter l'appel en cas d'échec du transfert d'appel.  Activée par défaut. Si le paramètre est désactivé et qu'un transfert d'appel échoue, {{site.data.keyword.iva_short}} initie un échange de conversation. Ensuite, {{site.data.keyword.conversationshort}} peut déconnecter l'appel ou le transférer vers une autre destination, selon la configuration dans le dialogue.
* **Notifier {{site.data.keyword.conversationshort}} lors d'événements de réseau** : lorsque cette option est activée et qu'une erreur réseau est détectée, {{site.data.keyword.iva_short}} initie un échange avec le service {{site.data.keyword.conversationshort}} avec le texte "vgwNetworkWarningMessage". La variable d'état `vgwNetworkWarnings` contient une liste d'événements de réseau qui se sont produits durant l'échange en cours. Si cette option est désactivée, une liste des événements de réseau qui se sont produits durant l'échange en cours est envoyée à l'événement d'échange suivant dans la variable d'état `vgwNetworkWarning`. Activée par défaut.
