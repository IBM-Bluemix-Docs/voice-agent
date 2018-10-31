---

copyright:
  years: 2017, 2018
lastupdated: "2018-10-11"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Gestion des agents vocaux
{: #managing}

Vous pouvez créer, éditer, cloner, configurer et retirer des agents vocaux sur le tableau de bord _Gestion_. Vous pouvez posséder plusieurs agents vocaux, mais chacun d'eux doit être associé à un nom et à un numéro de téléphone uniques.
{: shortdesc}

<!-- Title should be task oriented and descriptive-->

## Création d'un agent vocal
{: #config_instance}

Lorsque vous créez un agent vocal, {{site.data.keyword.iva_short}} recherche automatiquement les instances de service Watson disponibles que vous pouvez utiliser. Si les services ne sont pas disponibles, vous pouvez choisir de les créer en même temps que l'agent vocal ou de vous connecter aux services figurant dans un autre espace de compte {{site.data.keyword.Bluemix_short}}.

1. Cliquez sur **Créer un agent vocal**.

1. Dans la zone **Nom**, spécifiez un nom unique pour votre agent vocal. Par exemple, `Customer Support - North America`.

1. Dans la zone **Numéro de téléphone**, ajoutez le numéro depuis votre liaison SIP, en incluant le code pays et l'indicatif régional. Par exemple, pour un numéro 800 aux Etats-Unis, spécifiez le numéro de téléphone sous la forme suivante : `18883334444`. Le numéro de téléphone peut comporter des espaces et les caractères `+ ( ) -`.

1. Décrivez éventuellement votre agent vocal.

1. Si vous souhaitez activer le transfert d'appel, vous pouvez configurer un URI d'arrêt pour votre **cible de transfert**. Voir [Configuration du transfert d'appel](call-transfer.html). N'utilisez pas de numéro de téléphone personnel pour votre cible de transfert.

1. Configurez les connexions à vos instances de service Watson. Vous pouvez établir des connexions à plusieurs instances de service Watson en configurant des connexions pour **Emplacement 1** et pour **Emplacement 2**. Lorsque des connexions sont établies avec plusieurs instances de service, votre agent vocal peut passer à une autre instance de service si une indisponibilité se produit. Voir [Ajout de plusieurs emplacements de service Watson](#add_location).

    **Important** : les instances _Trial_ et _Lite_ peuvent uniquement se connecter à l'emplacement où votre instance de service {{site.data.keyword.iva_short}} est créée. Votre second emplacement n'est pas un second agent vocal. Il agit uniquement comme sauvegarde pour la reprise après incident.

1. Sous **{{site.data.keyword.conversationshort}}**, configurez la connexion à votre instance de service {{site.data.keyword.conversationshort}} en cliquant sur **Activer l'emplacement 1** ou **Activer l'emplacement 2**. Vous pouvez utiliser des instances {{site.data.keyword.conversationshort}} ou des instances {{site.data.keyword.virtualagentfull}} dans des comptes {{site.data.keyword.Bluemix_notm}} que vous possédez ou qui sont la propriété de quelqu'un d'autre. Vous pouvez également vous connecter à l'une de ces options via un moteur d'orchestration de service.

    * Si vous créez un agent vocal dans la région Sud des Etats-Unis ou Est des Etats-Unis alors que vous ne disposez d'aucune instance de service {{site.data.keyword.conversationshort}}, vous pouvez en créer une dans le menu **Instance de service**.
    * Sinon, vous pouvez vous connecter à d'autres sources d'un dialogue {{site.data.keyword.conversationshort}} en modifiant le [**type de service**](#other_service).
    * Si vous souhaitez configurer plusieurs emplacements de service, cliquez sur l'autre option d'emplacement et sélectionnez **Activer l'emplacement** afin de configurer la connexion à votre autre instance {{site.data.keyword.conversationshort}}. Voir [Ajout de plusieurs emplacements de service Watson](#add_location).

1. Sous **{{site.data.keyword.speechtotextshort}}**, revoyez la configuration par défaut de votre instance de service {{site.data.keyword.speechtotextshort}} en cliquant sur **Activer l'emplacement 1** ou sur **Activer l'emplacement 2**. Vous pouvez personnaliser votre configuration comme indiqué ci-après.
    * Si vous créez un agent vocal dans la région Sud des Etats-Unis ou Est des Etats-Unis alors que vous ne disposez d'aucune instance de service {{site.data.keyword.speechtotextshort}}, vous pouvez en créer une dans le menu **Instance de service**.
    * Sélectionnez le [**Type de service**](#other_service) pour connecter votre agent vocal à une instance {{site.data.keyword.speechtotextshort}} dans un autre service {{site.data.keyword.Bluemix_notm}} ou dans un [service parole-texte tiers](#third-party), comme Google Cloud Speech-to-Text.
    * Si vous souhaitez configurer plusieurs emplacements de service, cliquez sur l'autre option d'emplacement et sélectionnez **Activer l'emplacement** afin de configurer la connexion à votre autre instance {{site.data.keyword.speechtotextshort}}. Voir [Ajout de plusieurs emplacements de service Watson](#add_location).
    * **Rappel :** {{site.data.keyword.iva_short}} ne prend en charge que les modèles à bande étroite.

1. Sous **{{site.data.keyword.texttospeechshort}}**, revoyez la configuration par défaut de votre instance de service {{site.data.keyword.texttospeechshort}} en cliquant sur **Activer l'emplacement 1** ou sur **Activer l'emplacement 2**.
    * Si vous créez un agent vocal dans la région Sud des Etats-Unis ou Est des Etats-Unis alors que vous ne disposez d'aucune instance de service {{site.data.keyword.texttospeechshort}}, vous pouvez en créer une dans le menu **Instance de service**.
    * Vous pouvez également connecter votre agent vocal à une instance {{site.data.keyword.texttospeechshort}} dans un autre espace de compte {{site.data.keyword.Bluemix_notm}} en modifiant le [**Type de service**](#other_service).
    * Si vous souhaitez configurer plusieurs emplacements de service, cliquez sur l'autre option d'emplacement et sélectionnez **Activer l'emplacement** afin de configurer la connexion à votre autre instance {{site.data.keyword.texttospeechshort}}. Voir [Ajout de plusieurs emplacements de service Watson](#add_location).

1. Vous pouvez également choisir d'activer la transmission d'événements afin de collecter des informations sur les appels qui sont gérés par vos agents vocaux dans une instance {{site.data.keyword.cloudantfull}}. Voir [Activation de la transmission d'événements pour les agents vocaux](event-forwarding.html). Pour connaître d'autres options de configuration, voir [Configuration d'un agent vocal](#configure_va).

1. Cliquez sur **Créer un agent vocal** pour créer votre agent vocal et de nouveaux services.

Une fois l'agent vocal créé, testez-le en appelant le numéro de téléphone qui lui est associé. Vous pouvez afficher des informations détaillées concernant votre appel téléphonique sur le tableau d bord _Utilisation_.  

## Edition du nombre maximal de connexions simultanées
{: #edit_concurrency}

Si vous utilisez le plan _Standard_, vous pouvez modifier le nombre maximal de connexions simultanées défini par défaut. Dans tous les plans, vous recevez gratuitement 2 connexions simultanées. Pour plus d'informations, voir [Plans de tarification](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

Sur le tableau de bord _Gestion_, le nombre maximal de connexions simultanées autorisées dans votre plan figure dans la zone **Nombre maximal de connexions simultanées**. En outre, le nombre maximal de connexions simultanées qui sont utilisées par vos agents vocaux durant le mois en cours figure dans la zone **Nombre maximal de connexions simultanées utilisées**.

Si vous souhaitez modifier le nombre maximal de connexions simultanées de votre plan, cliquez sur l'icône **Editer**. Dans la fenêtre _Editer le nombre maximal de connexions simultanées_, choisissez le nombre maximal de connexions simultanées, puis cliquez sur **Sauvegarder**. Vous pouvez définir entre 10 et 50 connexions simultanées en libre-service. Si vous avez besoin de plus de 50 connexions simultanées pour votre agent vocal, voir [Demande de configuration réseau assistée](connect-SIP.html#request-setup).

### Informations de tarification relatives aux connexions simultanées
{: #concurrent-charge}

  * Les plans _Lite_, _Trial_ et _Standard_ incluent 2 connexions simultanées gratuites.
  * Les plans _Premium_ sont personnalisés par instance.
  * Dans un plan _Standard_, vous disposez d'une capacité minimale de 10 connexions simultanées.
  * L'utilisation des connexions simultanées est répartie au prorata mois par mois. Si vous utilisez plus de 2 connexions simultanées dans une même journée, un tarif quotidien vous est facturé.
  * Si vous disposez d'un plan _Standard_ ou _Premium_, vous pouvez acheter une capacité de connexions simultanées supérieure.
  * Un tarif quotidien vous est facturé pour la capacité maximale de connexions simultanées que vous utilisez dans une journée. Par exemple, votre plan prend en charge 2 connexions simultanées gratuites et vous définissez une limite maximale de 12 connexions. Si vous utilisez uniquement 5 connexions simultanées dans une journée, 3 connexions simultanées vous sont facturées.

Pour plus d'informations sur les plans, les tarifs et les fonctions, voir [Plans de tarification](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

## Edition d'un agent vocal
{: #edit_va}

Vous pouvez modifier des agents vocaux existants en les éditant. Pour éditer un agent vocal, cliquez sur **Editer un agent** dans la liste d'options pour l'agent vocal. Modifiez la configuration, puis sauvegardez les modifications.

## Clonage d'un agent vocal
{: #clone_va}

Lorsque vous clonez un agent vocal, toutes les configurations des services Watson sont copiées vers un nouvel agent. Pour cloner un agent vocal, cliquez sur **Cloner un agent** dans la liste d'options pour l'agent vocal. Affectez un nom et un numéro de téléphonique uniques à votre agent vocal, modifiez certaines options de configuration, le cas échéant, et sauvegardez les modifications.

## Suppression d'un agent vocal
{: #delete_va}

Vous souhaiterez peut-être supprimer un agent vocal afin de libérer le numéro de téléphone. Vous pouvez avoir un seul agent vocal par numéro de téléphone. Afin d'utiliser un numéro de téléphone pour un autre agent vocal, vous devez d'abord supprimer l'agent vocal qui utilise le numéro de téléphone.

Pour supprimer un agent vocal, cliquez sur **Supprimer un agent** dans la liste d'options pour l'agent vocal et sauvegardez les modifications. L'agent vocal est retiré de la liste d'agents vocaux.

## Configuration d'un agent vocal
{: #configure_va}

### Configuration des options avancées
{: #config-advanced}

Lorsque vous créez ou clonez un agent vocal, vous pouvez cliquer sur **Afficher les paramètres avancés** pour afficher les options de configuration avancées présentées ci-après.

* **Message de réponse en cas d'échec de {{site.data.keyword.conversationshort}} (facultatif)** : message de réponse par défaut qui est envoyé au récepteur de messagerie si l'appel ne peut pas se connecter à {{site.data.keyword.conversationshort}}.
* **Message de réponse en cas d'échec du transfert (facultatif)** : message de réponse par défaut qui est diffusé à l'appelant si le transfert d'appel échoue.
* **En-tête SIP INVITE personnalisé (facultatif)** : indique l'en-tête SIP personnalisé à extraire des requêtes SIP INVITE entrantes.
* **Envoyer une réponse provisoire par téléphone depuis {{site.data.keyword.iva_short}}** : envoie une réponse `180 ringing` durant le traitement d'un appel entrant par {{site.data.keyword.iva_short}}. Activée par défaut.
* **Placer l'appelant en attente lors du transfert** : l'appelant est placé en attente durant le transfert. Activée par défaut.
* **Déconnecter l'appel en cas d'échec du transfert** : détermine s'il convient ou non de déconnecter l'appel en cas d'échec du transfert d'appel.  Activée par défaut. Si le paramètre est désactivé et qu'un transfert d'appel échoue, {{site.data.keyword.iva_short}} initie un échange de conversation. Ensuite, {{site.data.keyword.conversationshort}} peut déconnecter l'appel ou le transférer vers une autre destination, selon la configuration dans le dialogue.
* **Notifier {{site.data.keyword.conversationshort}} lors d'événements de réseau** : lorsque cette option est activée et qu'une erreur réseau est détectée, {{site.data.keyword.iva_short}} initie un échange avec le service {{site.data.keyword.conversationshort}} avec le texte "vgwNetworkWarningMessage". La variable d'état `vgwNetworkWarnings` contient une liste d'événements de réseau qui se sont produits durant l'échange en cours. Si cette option est désactivée, une liste des événements de réseau qui se sont produits durant l'échange en cours est envoyée à l'événement d'échange suivant dans la variable d'état `vgwNetworkWarning`. Activée par défaut.

### Ajout de plusieurs emplacements de service Watson
{: #add_location}

Si vous disposez d'un plan _Standard_ ou _Premium_, vous pouvez connecter votre agent vocal à plusieurs services Watson dans différents emplacements pour la redondance de service. Les plans _Trial_ et _Lite_ peuvent uniquement se connecter à l'emplacement où votre instance de service {{site.data.keyword.iva_short}} est créée. Votre second emplacement n'est pas un second agent vocal. Il agit uniquement comme sauvegarde pour la reprise après incident.

Votre agent vocal utilise les instances de service Watson par ordre de distance géographique. Par exemple, vous pouvez créer un agent vocal dans la région Est des Etats-Unis alors que vos service {{site.data.keyword.conversationshort}} se trouvent dans la région Sud des Etats-Unis et à Sydney, en Australie. Votre agent vocal utilise la région {{site.data.keyword.conversationshort}} Sud des Etats-Unis, car cette dernière est plus proche géographiquement de la région Est des Etats-Unis que Sydney. Lorsque vous établissez des connexions à des services Watson situés dans plusieurs régions, si un service Watson est hors service à un emplacement, votre agent vocal peut utiliser le service redondant.

Vous pouvez à tout moment ajouter un emplacement de service Watson à votre configuration d'agent vocal. Pour savoir comment connecter plusieurs instances d'emplacement de service lors de la création de votre agent vocal, voir [Création d'un agent vocal](#creating).

Afin d'ajouter un emplacement de service Watson à un agent vocal existant, cliquez sur **Editer un agent** pour l'agent vocal que vous souhaitez configurer. Choisissez**Emplacement 1** ou **Emplacement 2** pour l'instance {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} ou {{site.data.keyword.speechtotextshort}} que vous souhaitez connecter, puis ajoutez vos informations de configuration. Vous pouvez utiliser des instances de service Watson dans votre espace de travail ou dans d'autres espaces de travail. Voir [Utilisation d'instances de service dans d'autres espaces de travail {{site.data.keyword.Bluemix_notm}}](#other_services).

**Remarque** : la redondance de service nécessite que vous utilisiez des instances de service Watson dans différentes régions de service pour différents emplacements.

Vous pouvez activer ou désactiver un emplacement en utilisant la zone **Activer l'emplacement**. **Emplacement 1** est activé par défaut et **Emplacement 2** est désactivé par défaut. Au moins un emplacement doit être activé pour chaque service Watson.

### Utilisation d'instances de service dans d'autres espaces de travail {{site.data.keyword.Bluemix_notm}}
{: #other_service}

Vous pouvez configurer votre agent vocal pour qu'il utilise des instances de service {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.speechtotextshort}} appartenant à des espaces de travail situés dans d'autres comptes {{site.data.keyword.Bluemix_short}}. Pour connecter votre agent vocal à d'autres instances de service, vous pouvez utiliser les données d'identification par nom d'utilisateur et mot de passe ou une clé d'API pour vos instances de service.

1. Sélectionnez une valeur pour **Type de service** et **Région**.

1. Choisissez **Nom d'utilisateur et mot de passe** ou **Clé d'API** et entrez vos données d'identification de service.
  Pour trouver ces valeurs, accédez à l'instance de service que vous souhaitez configurer et sélectionnez **Données d'identification de service**, puis **Afficher les données d'identification**.

  * **Nom d'utilisateur et mot de passe** : dans les zones **URL**, **Nom d'utilisateur** et **Mot de passe**, configurez les données d'identification pour vos instances de service {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.texttospeechshort}}.
  * **Clé d'API** : dans les zones **URL** et **Clé d'API**, configurez les données d'identification pour vos instances de service {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.texttospeechshort}}.

  Les données d'identification ne sont pas votre nom d'utilisateur et votre mot de passe {{site.data.keyword.Bluemix_notm}}, mais des données d'identification chiffrées pour l'instance de service spécifique.
  {:tip}

1. Entrez les informations relatives à votre instance de service.

  * **{{site.data.keyword.conversationshort}} :** dans la zone **ID d'espace de travail**, entrez l'ID de l'espace de travail que vous souhaitez utiliser avec votre agent vocal. Pour trouver l'ID d'espace de travail, lancez l'outil, et sur l'espace de travail que vous souhaitez intégrer, cliquez sur l'icône Actions(**&vellip;**) et sélectionnez **Afficher les détails**.
  * **{{site.data.keyword.speechtotextshort}} :** dans la zone **Modèle**, sélectionnez une langue et un format pour votre service. {{site.data.keyword.iva_short}} ne prend en charge que les modèles à bande étroite.
  * **{{site.data.keyword.texttospeechshort}} :** dans la zone **Voix**, sélectionnez la langue et la voix qui seront utilisées par votre service. Vous devez spécifier une voix pour votre service.

**Important :** pour que votre agent vocal fonctionne, vous devez configurer vos instances de service {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} et {{site.data.keyword.texttospeechshort}} pour la même langue. Voir [Langues prises en charge](about.html#supported-languages).

### Connexion à des services tiers
{: #third-party}

Au lieu d'utiliser une instance {{site.data.keyword.speechtotextshort}}, vous pouvez choisir de connecter votre agent vocal à un service de parole-texte tiers, tel que [Google Cloud Speech-to-Text ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.google.com/speech-to-text/).

1. Dans votre configuration de service _Speech to Text_, choisissez **Instance de service Google Speech to Text**.

1. Entrez vos données d'identification au service Google Cloud Speech-to-Text.
  * Vous pouvez générer vos données d'identification au service dans la plateforme Google Cloud sous la forme d'une clé JSON lorsque vous [définissez un compte de service ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account).

### Configuration de {{site.data.keyword.conversationshort}} pour votre agent vocal
{: #conversation_va}

Au lieu de configurer une instance de service {{site.data.keyword.conversationshort}}, vous pouvez vous connecter à un moteur d'orchestration ou à Watson {{site.data.keyword.virtualagentshort}}.

* **Moteur d'orchestration de service** : connectez-vous à un espace de travail {{site.data.keyword.conversationshort}} ou à{{site.data.keyword.virtualagentshort}} via un [moteur d'orchestration de service](about.html#arch-soe). Un moteur d'orchestration de service intercepte des messages émis vers et depuis le service de manière à vous permettre de les modifier à l'aide d'API tierces.

  Dans la zone **URL**, entrez l'adresse URL complète de votre espace de travail de moteur d'orchestration de service, par exemple, `https://iva-soesample.myorg.net/SOE/myWorkspace`. Si votre moteur d'orchestration de service nécessite une authentification (recommandé), entrez le nom d'utilisateur et le mot de passe dans les zones prévues à cet effet.

  **Important** : pour la sécurité des données, veillez à utiliser une URL sécurisée pour votre espace de travail de moteur d'orchestration de service, en utilisant `https:` au lieu de `http:`, et exigez une authentification. Voir [Sécurité des informations et confidentialité des données](infosec.html) pour en savoir plus sur les éléments à prendre en compte en matière de sécurité.

* **Watson {{site.data.keyword.virtualagentshort}}** : connectez-vous à un agent conversationnel {{site.data.keyword.virtualagentshort}} à la place d'un espace de travail {{site.data.keyword.conversationshort}}. [{{site.data.keyword.virtualagentshort}}](../virtual-agent/getting-started.html#getting-started) est construit sur le service {{site.data.keyword.conversationshort}}, mais il fournit des fonctions pré-entraînées de manière à vous permettre de vous lancer même si vous n'avez aucune expérience en matière d'apprentissage automatique.

  Dans la zone **URL**, entrez les données d'identification d'URL de {{site.data.keyword.virtualagentshort}}, par exemple, `https://api.ibm.com/virtualagent/run/api`. Pour les zones **ID de client** et **Valeur confidentielle du client**, entrez les clés d'authentification, ce qui établit une correspondance avec les zones d'en-tête `X-IBM-Client-Id` et `X-IBM-Client-Secret` pour les appels d'API. Dans la zone **ID de bot**, entrez l'ID du bot qui doit être utilisé pour cet agent vocal. Pour savoir comment trouver ces valeurs, voir [Publication de l'agent](../virtual-agent/publish.html) dans la documentation {{site.data.keyword.virtualagentshort}}.
