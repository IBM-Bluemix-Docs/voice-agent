---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Configuration de {{site.data.keyword.conversationshort}} avec un moteur d'orchestration de service
{: #conversation_va}

Comme alternative à la configuration d'une instance de service {{site.data.keyword.conversationshort}}, vous pouvez vous connecter à un moteur d'orchestration de service.
{: shortdesc}

Vous pouvez vous connecter à un espace de travail {{site.data.keyword.conversationshort}} via un [moteur d'orchestration de service](about.html#arch-soe). Un moteur d'orchestration de service intercepte les messages émis vers et depuis le service de manière à vous permettre de les modifier à l'aide d'API tierces.

## Configuration d'une connexion à un moteur d'orchestration de service
{: #how-to}

1. Dans l'onglet _Agent vocal_ de la page _Gérer_ de votre agent vocal, accédez à la section de configuration de {{site.data.keyword.conversationshort}}.

1. Choisissez **Moteur d'orchestration de service** comme votre **Type de service**.

1. Sélectionnez la **Région** de votre **Type de service**.

1. Dans la zone **URL**, entrez l'adresse URL complète de l'espace de travail de votre moteur d'orchestration de service, par exemple, `https://iva-soesample.myorg.net/SOE/myWorkspace`.

  **Important** : pour la sécurité des données, veillez à utiliser une URL sécurisée pour votre espace de travail de moteur d'orchestration de service, en utilisant `https:` au lieu de `http:`, et exigez une authentification. Voir [Sécurité des informations et confidentialité des données](infosec.html) pour en savoir plus sur les éléments à prendre en compte en matière de sécurité.

1. **Facultatif **: si votre moteur d'orchestration de service nécessite une authentification (recommandé), entrez le nom d'utilisateur et le mot de passe dans les zones correspondantes.
