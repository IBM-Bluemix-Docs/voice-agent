---

copyright:
  years: 2017, 2018
lastupdated: "2018-10-31"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Tutoriel d'initiation
{{site.data.keyword.iva_full}} vous permet d'intégrer un ensemble de services Watson orchestrés avec le réseau téléphonique via le protocole SIP (Session Initiation Protocol). Ce tutoriel décrit comment configurer un agent vocal cognitif que vous appelez depuis n'importe quel téléphone.
{: shortdesc}

Regardez une démonstration expliquant comment créer votre premier agent vocal dans ce[tutoriel {{site.data.keyword.iva_full_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/).
{: tip}

## Avant de commencer
{: #prereqs}

Créez un nouveau compte ou connectez-vous à un compte existant sur [{{site.data.keyword.Bluemix_short}}](https://console.bluemix.net/).

## Etape 1 : Création d'une instance de service {{site.data.keyword.iva_short}} sur {{site.data.keyword.Bluemix_notm}}
{: #step1}

A partir de la [page de catalogue {{site.data.keyword.iva_short}}](https://console.bluemix.net/catalog/services/voice-agent-with-watson), passez en revue les informations de service, puis cliquez sur **Créer**.

Une fois que vous avez créé le service, notez le noeud final d'agent vocal sur le tableau de bord _Initiation_. Vous avez besoin de l'URI SIP de noeud final pour configurer votre liaison SIP.

## Etape 2 : Création d'une liaison SIP pour réacheminer des appels vers {{site.data.keyword.iva_short}}
{: #step2}

1. Créez une liaison SIP à partir de l'un quelconque des fournisseurs pris en charge présentés ci-après. Ensuite, associez un numéro de téléphone à votre liaison SIP.

  * [NetFoundry](connect-SIP.html#NetFoundry-setup)
  * [Twilio](connect-SIP.html#twilio-setup)
  * [AT&T et autres fournisseurs de liaisons SIP](connect-SIP.html#att-other)
  * [Appairage avec {{site.data.keyword.iva_short}}](connect-SIP.html#peering)

## Etape 3 : Création et connexion de votre agent vocal
{: #step3}

1. Accédez au tableau de bord _Gestion_ sur le tableau de bord {{site.data.keyword.iva_short}} et cliquez sur **Créer un agent vocal**.

2. Entrez les paramètres de base pour votre agent vocal :
  * **Nom :** Nom unique pour votre agent vocal, par exemple, `Customer Support`
  * **Numéro de téléphone :** Numéro de téléphone complet que vous avez associé à votre liaison SIP, y compris le code pays et l'indicatif régional. Par exemple, pour un numéro 800 aux Etats-Unis, spécifiez le numéro de téléphone sous la forme suivante : 18883334444. Le numéro de téléphone peut comporter des espaces et les caractères + ( ) -.
  * **Description :** Description facultative de son utilisation
  * **Cible par défaut du transfert :** URI de terminaison facultatif vers lequel les appels peuvent être transférés. 

3. Créez les instances de service {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} et {{site.data.keyword.texttospeechshort}} pour votre agent vocal. Vous pouvez choisir de créer un agent vocal avec l'une ou l'autre des méthodes suivantes :
  * Cliquez sur **Créer un agent vocal** pour créer en une seule étape tous les services et un agent vocal avec la configuration par défaut.
  * Ou, cliquez sur chacun des noms de service pour créer vous-même les services. Revenez ensuite à {{site.data.keyword.iva_short}} et créez un agent vocal séparément.

   Si vous avez créé manuellement une instance de service {{site.data.keyword.conversationshort}}, ajoutez un dialogue afin de pouvoir tester votre agent vocal.  Pour commencer rapidement, clonez l'[exemple de conversation ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) à partir de GitHub, puis [importez l'exemple](../conversation/configure-workspace.html#creating-workspaces) en tant qu'espace de travail :

   1. Sur la page GitHub contenant l'exemple de conversation, cliquez sur le numéro de ligne `1` et sélectionnez **... > Copy line**. Collez le texte copié dans un fichier, puis enregistrez-le en tant que fichier JSON, par exemple, `voice-gateway-conversation-en.json`.
   2. Lancez l'outil {{site.data.keyword.conversationshort}}. Sur la page _Espaces de travail_, cliquez sur l'icône ![Importer un espace de travail](../conversation/images/workspace_import.png) et importez le fichier JSON.

  Vous pouvez aussi [générer votre propre dialogue](../conversation/dialog-build.html) afin de simuler votre environnement de production. Votre dialogue doit au moins contenir un noeud avec la condition `conversation_start` et un noeud avec une réponse par défaut.


## Etapes suivantes
{: #next}

Testez votre agent vocal en appelant le numéro de téléphone qui lui est associé. Si vous entendez une réponse, cela signifie que votre agent vocal est actif !

Si vous n'entendez pas de réponse, vous pouvez afficher vos journaux d'appels et les informations relatives à l'utilisation de votre agent vocal sur le tableau de bord _Utilisation_. Voir [Affichage des informations d'utilisation et des journaux d'appels](logging.html).

Vous pouvez éditer les paramètres de votre agent vocal, créer ou retirer des agents vocaux et ajouter plusieurs emplacements de service Watson à votre agent vocal à partir du tableau de bord _Gestion_. Pour plus d'informations, voir [Gestion des agents vocaux](managing.html).

Vous pouvez également configurer des paramètres avancés, tels que la sécurisation de votre connexion SIP à partir de votre compte Twilio. Voir [Sécurisation des connexions](secure-trunking.html).
