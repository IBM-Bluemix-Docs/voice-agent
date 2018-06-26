---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"

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

{{site.data.keyword.iva_full}} étant basé sur IBM Voice Gateway, l'API fonctionne de la même façon. Si vous connaissez bien Voice Gateway, vous pouvez utiliser les mêmes actions et variables d'état dans vos dialogues {{site.data.keyword.conversationshort}} avec {{site.data.keyword.iva_short}}. Voir [Balises d'action et variables d'état dans l'API Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html).
{: tip}

## Edition du code JSON dans la réponse de dialogue
{: #json-editor}

Les actions et les états sont définis dans une réponse de noeud de dialogue au format JSON. Pour éditer le code JSON, ouvrez l'éditeur JSON.

1. Dans le tableau de bord {{site.data.keyword.Bluemix_short}}, sélectionnez votre instance de service {{site.data.keyword.conversationshort}}.
1. Lancez l'outil {{site.data.keyword.conversationshort}}.
1. Cliquez sur l'espace de travail contenant le dialogue que vous souhaitez éditer.
1. Accédez à l'onglet **Dialog** et sélectionnez le noeud où vous souhaitez définir une action ou un état.
1. Dans la réponse, cliquez sur l'icône de ![réponse avanceé](../conversation/images/kabob.png), puis sélectionnez **Open JSON editor**.

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


### Commandes d'action et attributs
{: #actions-and-attributes}

Le tableau suivant affiche une liste des actions que vous pouvez spécifier dans le dialogue {{site.data.keyword.conversationshort}} ainsi que les attributs que vous pouvez définir pour chaque action.

| Commande d'action | Description | Attributs |
| ----- | ----- | ----- |
| `vgwActPlayText`| Lit un énoncé qui est converti en parole par le service {{site.data.keyword.texttospeechshort}}. | <ul><li>`text` : Liste des énoncés à lire. Facultatif. <p>Exemple :<br/><code>"text": [<br/>&nbsp;&nbsp;&nbsp;"Bonjour. Comment puis-je vous être utile ?"<br/>&nbsp;&nbsp;&nbsp;]</code><p> Par défaut, l'action lit une liste d'énoncés qui sont configurés dans la zone `output.text`. </li><li>`errAudioURL` : URL pointant vers un fichier audio qui est lu si l'agent vocal ne peut pas contacter le service {{site.data.keyword.texttospeechshort}} pour exécuter l'action. Le fichier audio doit être au format WAV.</li></ul>|
| `vgwActPlayUrl` | Lit un fichier audio dès que le texte inclus est lu, par exemple pour lire la musique en attente (MOH) ou des énoncés à usage unique communs. Si aucun texte n'est inclus, le fichier audio est lu immédiatement. Il doit s'agir d'un fichier mono-canal codé MIC (modulation par impulsion et codage), ayant une fréquence d'échantillonnage de 8 000 Hz avec 16 bits par échantillon. | <ul><li>`url` : URL à lire. Obligatoire.</li><li> `playURLInLoop` : Peut être défini sur `Yes` ou `No` pour indiquer si l'URL doit être lue en boucle. La valeur par défaut est `No`.</li></ul> |
| `vgwActHangup` | Termine l'appel. | Aucun attribut. |
| `vgwActSetSTTConfig` | Applique une série de paramètres que l'agent vocal transmet au service Watson {{site.data.keyword.speechtotextshort}}. Le service {{site.data.keyword.conversationshort}} définit dynamiquement les paramètres en fonction de l'appel. | Les attributs sont transmis de façon transparente en tant que propriétés JSON au service {{site.data.keyword.speechtotextshort}}. |
| `vgwActSetTTSConfig` | Applique une série de paramètres que l'agent vocal transmet au service Watson {{site.data.keyword.texttospeechshort}}. Le service {{site.data.keyword.conversationshort}} définit dynamiquement les paramètres en fonction de l'appel. |  Les attributs sont transmis de façon transparente en tant que propriétés JSON au service {{site.data.keyword.texttospeechshort}}.  |
| `vgwActSetConversationConfig` | Applique une série de paramètres pour que l'agent vocal définisse un espace de travail {{site.data.keyword.conversationshort}}. Le service {{site.data.keyword.conversationshort}} définit dynamiquement les paramètres en fonction de l'appel. | <ul><li>`url` : Données d'identification `url` de l'API de service {{site.data.keyword.conversationshort}}.</li><li>`workspaceID` : ID de l'espace de travail {{site.data.keyword.conversationshort}}</li><li>`username` : Données d'identification `username` du service {{site.data.keyword.conversationshort}}.</li><li>`password` : Données d'identification `password` du service {{site.data.keyword.conversationshort}}.</li></ul> |
| `vgwActCollectDtmf` | Indique à l'agent vocal de collecter une entrée de signal de fréquence vocale (DTMF). | L'un des attributs suivants doit être défini. <ul><li> `dtmfTermKey` : Clé de résiliation DTMF qui signale la fin d'une entrée DTMF. Par exemple, "`#`". </li><li> `dtmfCount`: Nombre de caractères DTMF à collecter.</li></ul> Lorsque l'une de ces conditions est remplie, l'agent vocal arrête de collecter l'entrée DTMF. |
| `vgwActPauseDTMF` | Désactive l'entrée DTMF. Toute l'entrée DTMF est ignorée jusqu'à ce qu'elle soit réactivée par l'action `vgwActUnPauseDTMF`. | Aucun attribut. |
| `vgwActUnPauseDTMF` | Active l'entrée DTMF qui a été désactivée par l'action `vgwActPauseDTMF`. | Aucun attribut. |
| `vgwActExcludeFromTTSCache` | Indique à l'agent vocal de ne pas mettre en cache la réponse du service {{site.data.keyword.texttospeechshort}}. Par exemple, les réponses contenant des informations PHI, PII, et PCI DSS sensibles ou des informations dynamiques telles que des noms de client ou des dates de naissance devraient être exclues. <br/>Cette balise d'action doit être définie sur le noeud de dialogue {{site.data.keyword.conversationshort}} pour chaque énoncé que vous ne souhaitez pas mettre en cache. | Aucun attribut. |
| `vgwActPauseSTT` | Met en pause le traitement parole-texte jusqu'à sa réactivation par l'action `vgwActUnPauseSTT`. Si l'enregistrement est activé et le traitement parole-texte mis en pause, l'audio de l'appelant n'est pas capturé. | Aucun attribut. |
| `vgwActUnPauseSTT` | Reprend le traitement parole-texte qui avait été mis en pause auparavant par l'action `vgwActPauseSTT`. | Aucun attribut. |
| `vgwActEnableSpeechBargeIn` | Permet une interruption de parole de façon à ce que les appelants puissent interrompre la lecture depuis l'agent vocal en prenant la parole. | Aucun attribut. |
| `vgwActDisableSpeechBargeIn` | Désactive l'interruption de parole de façon à ce que cette lecture depuis l'agent vocal ne soit pas interrompue quand les appelants parlent. | Aucun attribut. |
| `vgwActEnableDTMFBargeIn`| Permet une interruption DTMF de façon à ce que les appelants puissent interrompre la lecture depuis l'agent vocal en appuyant sur une touche. | Aucun attribut. |
| `vgwActDisableDTMFBargeIn` | Désactive l'interruption DTMF de façon à ce que cette lecture depuis l'agent vocal ne soit pas interrompue quand les appelants appuient sur des touches. | Aucun attribut. |
| `vgwActForceNoInputTurn` | Force un nouvel échange dans la conversation sans attendre l'entrée de l'appelant. | Aucun attribut. |
{: caption="Tableau 1. Actions que vous pouvez initier à partir du service {{site.data.keyword.conversationshort}}" caption-side="top"}

## Définition d'états
{: #setting-states}

Pour indiquer un changement d'état qui reste entre les échanges de conversation, l'agent vocal échange les variables d'état avec le service {{site.data.keyword.conversationfull}} configuré. Ces variables d'état sont définies sur un noeud de dialogue {{site.data.keyword.conversationshort}} en tant que [variables contextuelles](https://console.bluemix.net/docs/services/conversation/dialog-build.html#context) au format JSON.

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

### Variables d'état définies dans le dialogue {{site.data.keyword.conversationshort}}
{: #state-variables-conv}

Vous pouvez définir les variables d'état suivantes dans le dialogue {{site.data.keyword.conversationshort}} pour modifier le comportement de votre agent vocal.

| Nom de la variable d'état | Valeur attendue | Description |
| -------------- | ------ | ----------- |
| `vgwByeCustomHeader` | Défini par l'utilisateur | Définit un en-tête personnalisé dans un message SIP BYE sortant. La valeur de l'en-tête personnalisé est définie par les variables d'état `vgwByeCustomHeaderVal`.  |
| `vgwByeCustomHeaderVal` | Défini par l'utilisateur | Définit la valeur d'un en-tête personnalisé dans un message SIP BYE sortant. L'en-tête personnalisé est défini par les variables d'état `vgwByeCustomHeader`. |
| `vgwPostResponseTimeoutCount` | Temps en millisecondes | Durée d'attente d'un nouvel énoncé après la lecture d'une réponse à l'appelant. Si cette valeur est dépassée, {{site.data.keyword.conversationshort}} reçoit une mise à jour textuelle avec le mot "vgwPostResponseTimeout" afin d'indiquer un dépassement de délai.|
| `vgwConversationFailedMessage` | Chaîne de texte | Message transmis à l'appelant en cas d'échec du service {{site.data.keyword.conversationshort}}. Configurez {{site.data.keyword.conversationshort}} de façon à définir cette variable sur le premier échange. |
| `vgwSessionInactivityTimeout` | Temps en minutes <br/><br/>Valeur par défaut : `2` | Intervalle de délai d'attente d'inactivité. La valeur de l'intervalle de délai d'attente spécifie la durée, en minutes, pendant laquelle l'agent vocal autorise l'inactivité d'une session. Une fois ce délai écoulé, l'agent vocal met fin à la session. |
| `vgwErrAudioURL` | Défini par l'utilisateur | URL pointant vers un fichier audio qui est lu si le service {{site.data.keyword.texttospeechshort}} ne peut pas être contacté lorsque l'agent vocal tente de lire une réponse. Le fichier audio doit être au format WAV. |
{: caption="Tableau 2. Variables définies par le service {{site.data.keyword.conversationshort}}" caption-side="top"}

### Variables d'état définies par l'agent vocal
{: #state-variables-iva}

| Nom de la variable d'état | Valeur attendue | Description |
| -------------- | ----- | ----------- |
| `vgwSessionID`   | Défini par l'utilisateur <br/><br/> Valeur par défaut : `Call-ID` | En-tête d'ID session personnalisé qui est extrait de la demande SIP INVITE. La valeur représente l'ID de session global qui est utilisé dans tous les journaux d'audit de l'agent vocal relatifs à la session. |
| `vgwSIPCallID` | SIP `Call-ID` | ID d'appel SIP associé à l'appel. |
| `vgwSIPRequestURI` | SIP `Request-URI` | URI de demande SIP ayant démarré l'appel. |
| `vgwSIPToURI` | SIP `To` URI | SIP `To` associé à l'appel. |
| `vgwSIPFromURI` | SIP `From` URI | SIP `From` associé à l'appel. |
| `vgwBargeInOccurred` | `Yes` / `No` | Indique si une interruption s'est ou non produite. |
| `vgwHangUp` | `Yes` / `No` | Indique si la conversation a été ou non terminée. |
| `vgwHangupReason` | Chaîne | Lorsqu'il est mis fin à l'appel, que ce soit du fait de l'appelant ou à cause d'une erreur, cette variable est envoyée au service {{site.data.keyword.conversationshort}} afin d'indiquer la raison pour laquelle l'appel a été clôturé. Le texte dans la demande de message envoyée au service {{site.data.keyword.conversationshort}} inclut également "vgwHangUp". |
| `vgwConversationResponseTimeout` | Temps en secondes<br/><br/>Valeur par défaut : `5`  | Durée en secondes durant laquelle l'agent vocal attend une réponse du service {{site.data.keyword.conversationshort}}. Lorsque cette durée est dépassée, l'agent vocal tente à nouveau de contacter le service {{site.data.keyword.conversationshort}}. Si le service n'est toujours pas joignable, l'appel échoue. |
| `vgwSTTResponse` | Objet JSON | Réponse finale du service {{site.data.keyword.speechtotextshort}} au format JSON, y compris la transcription et la cote de confiance de l'hypothèse préférée et toute alternative. <p>Par exemple, le format suivant correspond précisément à celui reçu du service {{site.data.keyword.speechtotextshort}} : </p><p><code>{<br/>&nbsp;&nbsp;"result_index": 0,<br/>&nbsp;&nbsp;"warnings": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;"Unknown arguments: continuous."<br/>&nbsp;&nbsp;],<br/>&nbsp;&nbsp;"results": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"final": true,<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"alternatives": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello world",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.758<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello wooled",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.358<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;]<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}.</code></p> |
| `vgwIsDTMF` | `Yes` / `No` | Indique si l'entrée dans le service {{site.data.keyword.conversationshort}} est du type signal de fréquence vocale (DTMF). |
{: caption="Tableau 3. Variables définies par l'agent vocal" caption-side="top"}
