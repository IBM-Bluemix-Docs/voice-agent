---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-01"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Programmation d'agents vocaux à l'aide de l'API
{: #api}

Vous pouvez contrôler le comportement de votre agent vocal en définissant des balises d'action et des variables d'état depuis l'intérieur du service {{site.data.keyword.conversationfull}}. Les balises d'action initient des actions que votre agent vocal effectue durant une session de conversation, et les variables d'état définissent les caractéristiques d'agent vocal qui sont conservées durant toute la conversation, à moins qu'elles ne soient modifiées.
{: shortdesc}

{{site.data.keyword.iva_full}} étant basé sur IBM Voice Gateway, l'API fonctionne de la même façon. Si vous connaissez bien Voice Gateway et SMS Gateway, vous pouvez utiliser les mêmes actions et variables d'état dans vos dialogues {{site.data.keyword.conversationshort}} avec {{site.data.keyword.iva_short}}. Voir [Balises d'action et variables d'état dans l'API Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html) et [API pour SMS Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/sms_api.html), respectivement.
{: tip}

## Edition du code JSON dans la réponse de dialogue
{: #json-editor}

Les actions et les états sont définis dans une réponse de noeud de dialogue au format JSON. Pour éditer le code JSON, ouvrez l'éditeur JSON.

1. Dans le tableau de bord {{site.data.keyword.Bluemix_short}}, sélectionnez votre instance de service {{site.data.keyword.conversationshort}}.
1. Lancez l'outil {{site.data.keyword.conversationshort}}.
1. Cliquez sur la compétence contenant le dialogue que vous voulez éditer.
1. Accédez à l'onglet **Dialog** et sélectionnez le noeud où vous souhaitez définir une action ou un état.
1. Dans la réponse, cliquez sur l'icône de ![réponse avancée](../conversation/images/kabob.png), puis sélectionnez **Open JSON editor**.

Dans l'éditeur JSON, vous pouvez définir des actions sur la propriété `output` et des états sur la propriété `context` comme décrit dans les sections suivantes.

## Initiation d'actions
{: #defining-actions}

Pour initier des actions dans l'agent vocal durant un appel, vous pouvez définir des balises d'action sur un noeud de dialogue {{site.data.keyword.conversationshort}} au format JSON sur la propriété `output`. Vous pouvez définir une action unique sur la balise `vgwAction` ou une séquence d'actions sur la balise `vgwActionSequence`. Chaque action se compose d'une propriété `command` suivie d'une propriété facultative `parameter` pour définir des attributs pour les commandes qui les nécessitent.

### Actions uniques
{: #single-actions}

Pour réaliser une action unique, définissez l'action dans la balise `vgwAction` avec les attributs de paramètre nécessaires. Dans le bloc `text` dans la propriété `output`, vous pouvez également inclure un énoncé qui est lu par l'agent vocal une fois que l'action est exécutée.

L'action unique suivante sur la balise `vgwAction` demande à l'agent vocal de terminer l'appel lorsque la réponse de noeud est déclenchée. La commande `vgwActHangup` n'ayant pas de paramètre, aucun n'est défini.
```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActHangup"
    }
  }
}
```
{: codeblock}

L'action suivante demande à l'agent vocal de collecter l'entrée de signal de fréquence vocale (DTMF) et de lire le texte défini à l'appelant :

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActCollectDtmf",
      "parameters": {
        "dtmfTermKey": "#"
        }
    },
    "text": {
      "values": [
        "Enter your phone number."
      ]
    }
  }
}
```
{: codeblock}

### Séquences d'actions
{: #action-sequences}

Pour exécuter une ou plusieurs actions sur un échange de conversation unique, vous pouvez définir une séquence d'actions dans la balise `vgwActionSequence` en tant que liste JSON. Les actions sont réalisées dans l'ordre dans lequel vous les définissez.

Contrairement aux actions uniques, pour que l'agent vocal puisse lire un énoncé lorsqu'il utilise la balise `vgwActionSequence`, la liste des actions doit contenir l'action `vgwActPlayText`. Contrairement à la balise `vgwAction`, un énoncé dans la zone `output.text` n'est pas automatiquement lu.
{: tip}

Dans l'exemple suivant, plus complexe, les actions définies sur la balise `vgwActionSequence` demandent à l'agent vocal de désactiver le traitement speech-to-text et de collecter l'entrée de signal de fréquence vocale (DTMF) lorsqu'il lit un énoncé.

```json
{
  "output": {
    "vgwActionSequence": [
      {
        "command": "vgwActPauseSTT"
      },
      {
        "command": "vgwActCollectDtmf",
        "parameters": {
          "dtmfTermKey": "#"
        }
      },
      {
        "command": "vgwActPlayText",
        "parameters": {
          "text": [
            "Enter your social security number."
          ]
        }
      }
    ]
  }
}

```
{: codeblock}

## Définition d'états
{: #setting-states}

Pour indiquer un changement d'état qui reste entre les échanges de conversation, l'agent vocal échange les variables d'état avec le service {{site.data.keyword.conversationfull}} configuré. Ces variables d'état sont définies sur un noeud de dialogue {{site.data.keyword.conversationshort}} en tant que [variables contextuelles](/docs/services/assistant?topic=assistant-dialog-build#dialog-build) au format JSON.

Par exemple, vous pouvez définir la variable d'état suivante pour définir le message qui est diffusé pour l'appelant si la connexion au service {{site.data.keyword.conversationshort}} échoue.

```json
{
  "context": {
    "vgwConversationFailedMessage": "Sorry, we're unable to connect you to our help line. Please try again later."
  }
}
```
{: codeblock}

L'agent vocal considère que le service {{site.data.keyword.conversationshort}} est sans état et que tous les états sont conservés au niveau de l'agent vocal entre les échanges avec le service {{site.data.keyword.conversationshort}}. Pour chaque échange de conversation à l'intérieur d'un appel, l'état est transmis au service {{site.data.keyword.conversationshort}}, puis reçu en retour du service dans la section de `contexte` des messages REST.
