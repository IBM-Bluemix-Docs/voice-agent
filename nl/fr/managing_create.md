---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Création d'un agent vocal à partir du tableau de bord _Gestion_
{: #config_instance}

Après avoir créé votre service {{site.data.keyword.iva_full}}, vous pouvez créer des agents vocaux individuels à partir du tableau de bord _Gestion_.
{: shortdesc}


## Création d'un agent vocal
{: #create_instance}

Lorsque vous créez un agent vocal, {{site.data.keyword.iva_short}} recherche automatiquement les instances de service Watson disponibles que vous pouvez utiliser. Si les services ne sont pas disponibles, vous pouvez choisir de les créer en même temps que l'agent vocal ou de vous connecter aux services figurant dans un autre espace de compte {{site.data.keyword.Bluemix_short}}. Vous pouvez également choisir de connecter votre agent vocal à un moteur d'orchestration de service, ou bien à une instance Google Speech to Text ou Google Text to Speech.

1. Accédez à l'onglet _Agents vocaux_ sur le tableau de bord _Gestion_, puis cliquez sur **Créer un agent vocal**.

1. Dans la zone **Nom**, spécifiez un nom unique pour votre agent vocal. Par exemple, `Customer Support - North America`.

1. Dans la zone **Numéro de téléphone**, ajoutez le numéro depuis votre liaison SIP, en incluant le code pays et l'indicatif régional. Par exemple, pour un numéro 800 aux Etats-Unis, spécifiez le numéro de téléphone sous la forme suivante : `18883334444`. Le numéro de téléphone peut comporter des espaces et les caractères `+ ( ) -`.

1. Décrivez votre agent vocal si vous le désirez.

1. Si vous souhaitez activer le transfert d'appel, entrez l'URI de terminaison de votre **Cible par défaut du transfert**. Voir [Configuration du transfert d'appel](call-transfer.html) pour obtenir des informations sur la manière dont vous pouvez configurer un URI de terminaison. N'utilisez pas un numéro de téléphone personnel pour votre cible de transfert.

1. Configurez les connexions à vos instances de service Watson. Vous pouvez établir des connexions à plusieurs instances de service Watson en configurant des connexions pour **Emplacement 1** et pour **Emplacement 2**. Lorsque des connexions sont établies avec plusieurs instances de service, votre agent vocal peut passer à une autre instance de service si une indisponibilité se produit. Voir [Ajout de plusieurs emplacements de service Watson](managing_disaster_recovery.html#add_location).

1. Sous **{{site.data.keyword.conversationshort}}**, configurez la connexion à votre instance de service {{site.data.keyword.conversationshort}} en cliquant sur **Emplacement 1** ou **Emplacement 2** et en activant l'emplacement sélectionné. Vous pouvez utiliser les instances {{site.data.keyword.conversationshort}} dans vos comptes {{site.data.keyword.Bluemix_notm}} ou ceux de quelqu'un d'autre. Vous pouvez également vous connecter à l'une de ces options via un moteur d'orchestration de service.

   * Si vous créez un agent vocal dans la région de Dallas ou de Washington DC et n'avez pas d'instance de service {{site.data.keyword.conversationshort}}, vous pouvez en créer une dans le menu **Instance de service**.
   * Vous pouvez également vous connecter à d'autres sources d'un dialogue {{site.data.keyword.conversationshort}} ou à un moteur d'orchestration de service en changeant le [**Type de service**](managing_other.html#other_service).
   * Si vous souhaitez configurer plusieurs emplacements de service, cliquez sur l'autre option d'emplacement et sélectionnez **Activer l'emplacement** afin de configurer la connexion à votre autre instance {{site.data.keyword.conversationshort}}. Voir [Ajout de plusieurs emplacements de service Watson](managing_disaster_recovery.html#add_location).

1. Sous **{{site.data.keyword.speechtotextshort}}**, passez en revue la configuration par défaut de votre instance de service {{site.data.keyword.speechtotextshort}} en sélectionnant **Emplacement 1** ou **Emplacement 2** et en activant cet emplacement. Vous pouvez personnaliser votre configuration comme suit.
   * Pour connecter votre agent vocal à une instance existante en tant que votre **Type de service**, choisissez **Mon instance de service Speech to Text**. Ensuite, sous **Sélectionner un type de modèle**, sélectionnez **Bande étroite**, **Bande large** ou **Bande étroite et bande large**, puis sélectionnez le **Modèle** de langue.
   * Si vous créez un agent vocal dans la région de Dallas ou de Washington DC et n'avez pas d'instance de service {{site.data.keyword.speechtotextshort}}, vous pouvez en créer une à partir du menu **Instance de service**.
   * Sous **Type de service**, sélectionnez une instance {{site.data.keyword.speechtotextshort}} [ dans un espace de travail {{site.data.keyword.Bluemix_notm}} différent](managing_other.html) ou un [service Speech to Text tiers](managing_third_party.html), tel que Google Cloud Speech-to-Text.
   * Si vous souhaitez configurer plusieurs emplacements de service, cliquez sur l'autre option d'emplacement et sélectionnez **Activer l'emplacement** afin de configurer la connexion à votre autre instance {{site.data.keyword.speechtotextshort}}. Voir [Ajout de plusieurs emplacements de service Watson](managing_disaster_recovery.html).

1. Sous **{{site.data.keyword.texttospeechshort}}**, passez en revue la configuration par défaut de votre instance de service {{site.data.keyword.texttospeechshort}} en cliquant sur **Emplacement 1** ou **Emplacement 2** et en ajoutant cet emplacement. Vous pouvez personnaliser votre configuration comme suit.
   * Si vous créez un agent vocal dans la région de Dallas ou de Washington DC et n'avez pas d'instance de service {{site.data.keyword.texttospeechshort}}, vous pouvez en créer une à partir du menu **Instance de service**.
   * Sous **Type de service**, sélectionnez une instance {{site.data.keyword.texttospeechshort}} [dans un espace de travail {{site.data.keyword.Bluemix_notm}} différent](managing_other.html) ou un [service Text to Speech tiers](managing_third_party.html), tel que Google Cloud Text-to-Speech.
   * Si vous souhaitez configurer plusieurs emplacements de service, cliquez sur l'autre option d'emplacement et sélectionnez **Activer l'emplacement** afin de configurer la connexion à votre autre instance {{site.data.keyword.texttospeechshort}}. Voir [Ajout de plusieurs emplacements de service Watson](managing_disaster_recovery.html).

1. Vous pouvez également choisir d'activer la transmission d'événements afin de collecter des informations sur les appels qui sont gérés par vos agents vocaux dans une instance {{site.data.keyword.cloudantfull}}. Voir [Activation de la transmission d'événements pour les agents vocaux](event-forwarding.html). Pour connaître d'autres options de configuration, voir [Configuration d'un agent vocal](managing.html#configure_va).

1. Cliquez sur **Créer un agent vocal** pour créer votre agent vocal et de nouveaux services.

Une fois l'agent vocal créé, testez-le en appelant le numéro de téléphone qui lui est associé. Vous pouvez afficher des informations détaillées sur votre appel téléphonique sur le tableau de bord _Utilisation_.  
