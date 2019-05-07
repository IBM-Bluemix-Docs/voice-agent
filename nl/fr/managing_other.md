---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Utilisation d'instances de service dans d'autres espaces de travail {{site.data.keyword.Bluemix_notm}}
{: #other_service}

Vous pouvez configurer votre agent vocal pour qu'il utilise des instances de service {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.speechtotextshort}} appartenant à des espaces de travail situés dans d'autres comptes {{site.data.keyword.Bluemix_short}}.
{: shortdesc}

Pour connecter votre agent vocal à d'autres instances de service, vous pouvez utiliser les données d'identification par nom d'utilisateur et mot de passe ou une clé d'API pour vos instances de service. Le nom d'utilisateur et le mot de passe ne doivent pas dépasser 64 et 256 caractères, respectivement. La clé d'API est quant à elle limitée à 64 caractères.

1. Dans l'onglet _Agents vocaux_ du tableau de bord _Gestion_, cliquez sur **Créer un agent vocal** ou sélectionnez un agent vocal que vous souhaitez éditer.

1. Dans {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.speechtotextshort}}, **Sélectionnez une autre instance de service** pour votre **type de service**, puis sélectionnez la **région**.

1. Choisissez **Nom d'utilisateur et mot de passe** ou **Clé d'API** et entrez vos données d'identification de service.
  Pour trouver ces valeurs, accédez à l'instance de service que vous souhaitez configurer et sélectionnez **Données d'identification de service**, puis **Afficher les données d'identification**.

  * **Nom d'utilisateur et mot de passe** : dans les zones **URL**, **Nom d'utilisateur** et **Mot de passe**, configurez les données d'identification pour vos instances de service {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.texttospeechshort}}.
  * **Clé d'API** : dans les zones **URL** et **Clé d'API**, configurez les données d'identification pour vos instances de service {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.texttospeechshort}}.

  Les données d'identification ne sont pas votre nom d'utilisateur et votre mot de passe {{site.data.keyword.Bluemix_notm}}, mais des données d'identification chiffrées pour l'instance de service spécifique.
  {:tip}

1. Entrez les informations relatives à votre instance de service.

  * **{{site.data.keyword.conversationshort}} :** Dans la zone **ID d'espace de travail**, entrez l'ID de l'espace de travail que vous souhaitez utiliser avec votre agent vocal, sans dépasser 128 caractères. Pour trouver l'ID d'espace de travail, lancez l'outil, et sur l'espace de travail que vous souhaitez intégrer, cliquez sur l'icône Actions(**&vellip;**) et sélectionnez **Afficher les détails**.
  * **{{site.data.keyword.speechtotextshort}} :** dans la zone **Sélectionner un type de modèle**, choisissez **Bande étroite**, **Bande large** ou **Bande étroite et bande large**, puis sélectionnez le **modèle** de langue.
  * **{{site.data.keyword.texttospeechshort}} :** dans la zone **Voix**, sélectionnez la langue et la voix qui seront utilisées par votre service. Vous devez spécifier une voix pour votre service.

**Important :** pour que votre agent vocal fonctionne, vous devez configurer vos instances de service {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} et {{site.data.keyword.texttospeechshort}} pour la même langue. Voir [Langues prises en charge](/docs/services/voice-agent?topic=voice-agent-about#supported-languages).
