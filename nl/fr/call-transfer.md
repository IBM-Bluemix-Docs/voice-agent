---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configuration du transfert d'appel
{: #call-transfer}

Vous pouvez configurer le transfert d'appel de sorte que si un appelant demande à parler à un agent humain durant une conversation, l'appel est transféré automatiquement par l'agent vocal.
{: shortdesc}

## A propos du transfert d'appel
{: #about-ct}

Lorsque le transfert d'appel est configuré, si un appelant demande à parler à un agent humain durant une conversation, l'appel est transféré automatiquement par l'agent vocal. {{site.data.keyword.iva_short}} utilise un protocole SIP REFER pour diriger l'appel vers votre fournisseur de liaison SIP pour gestion, et n'ancre pas les appels téléphoniques transférés.

Vous pouvez activer le transfert d'appel en définissant un URI ou un URI tél de terminaison dans la configuration de votre fournisseur SIP. Vous configurez ensuite la cible de transfert ou définissez une action d'API dans un noeud de dialogue de votre instance {{site.data.keyword.conversationshort}}. Votre cible de transfert est un URI SIP qui contient l'URI de terminaison et le numéro de téléphone ou un URI tél avec numéro de téléphone. Pour plus d'informations sur les actions prises en charge et la personnalisation de vos agents vocaux, voir [Programmation des agents vocaux à l'aide de l'API](/docs/services/voice-agent?topic=voice-agent-api).

## Etape 1 : Configuration de l'URI de terminaison
{: #termination-setup}

Si vous utilisez un URI de téléphone à la place d'un URI de terminaison pour la configuration de votre URI SIP, vous pouvez utiliser l'URI de téléphone, par exemple `tel:+18889990000`, pour votre cible de transfert (`transferTarget`). Lorsque vous utilisez un URI SIP, vous avez besoin d'un URI de terminaison pour votre `transferTarget`.
{: tip}

### Configuration d'un URI de terminaison dans NetFoundry
{: #termination-netfoundry}

Notez le numéro de téléphone dans votre [compte NetFoundry![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson.netfoundry.io/watson-login){: new_window} vers lequel le transfert doit s'effectuer. Vous pouvez ensuite spécifier ce numéro de téléphone et l'URI de terminaison comme cible de transfert dans votre dialogue {{site.data.keyword.conversationshort}}. N'utilisez pas un numéro de téléphone personnel.

Copiez l'URI de terminaison NetFoundry suivant à utiliser dans la cible de transfert.

```
dal.watson-va.netfoundry.net
```
{: codeblock}

Vous n'avez pas besoin de configurer manuellement l'URI de terminaison dans votre compte NetFoundry lors de l'étape [Configuration de {{site.data.keyword.conversationshort}} pour le transfert d'appel](#conversation-setup).

### Configuration d'un URI de terminaison dans Twilio
{: #termination-Twilio}

1. Dans votre compte Twilio, accédez au tableau de bord _Elastic SIP Trunking_ et sélectionnez **Trunks**.

1. Choisissez la liaison à laquelle vous souhaitez ajouter le transfert d'appel en sélectionnant une liaison existante ou en créant une nouvelle liaison en cliquant sur l'icône **+**.

  * Si vous créez une nouvelle liaison, vous devez configurer l'_URI de liaison SIP_ dans le tableau de bord **Origination**.  Pour plus d'informations, voir [Connexion d'une liaison SIP](/docs/services/voice-agent?topic=voice-agent-connect).

1. Sélectionnez **Termination** sur votre barre de navigation et entrez un nom pour votre URI de terminaison.

  * Les noms d'URI de terminaison doivent être uniques. Twilio vérifie automatiquement si le nom que vous avez choisi est disponible. Pour plus de détails sur les services Twilio, voir [Paramètres d'arrêt de liaison SIP![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window}.

1. Sélectionnez **General** dans votre barre de navigation pour afficher les _paramètres généraux_. Sous l'en-tête **Call Transfer (SIP REFER)**, basculez le paramètre sur **Enabled** et sélectionnez **Allow Call Transfers to the PSTN via your Trunk**.

1. Cliquez sur **Save** pour finaliser la configuration de votre URI de terminaison et activer le transfert d'appel.

1. Notez le numéro de téléphone et l'URI de terminaison vers lesquels le transfert doit s'effectuer. Assurez-vous que le numéro de téléphone n'est pas un numéro personnel. Vous pouvez utiliser le numéro de téléphone et l'URI de terminaison pour indiquer la cible de transfert dans votre dialogue {{site.data.keyword.conversationshort}}.


## Etape 2 : Configuration de {{site.data.keyword.conversationshort}} pour le transfert d'appel
{: #conversation-setup}

Pour en apprendre davantage sur l'utilisation du service {{site.data.keyword.conversationshort}}, voir [A propos de {{site.data.keyword.conversationshort}}](/docs/services/assistant?topic=assistant-index#indext).

1. Dans votre tableau de bord {{site.data.keyword.Bluemix_notm}}, sélectionnez l'instance {{site.data.keyword.conversationshort}} qui est utilisée par votre agent vocal.

1. A partir du tableau de bord d'_initiation_, cliquez sur le bouton **Launch tool**.

1. Cliquez sur **Getting Started** dans la compétence que vous souhaitez éditer.

1. Cliquez sur **Add intent** et entrez un nom pour l'intention, par exemple, _Transfer_.

  Vous pouvez entrer des informations plus détaillées ou revenir ultérieurement pour éditer et affiner l'intention.

1. Une fois votre intention de transfert d'appel créée, sélectionnez l'onglet _Dialog_.

1. Cliquez sur **Add node** et entrez un nom pour le noeud, par exemple, _Call Transfer_.

1. Dans la section _If the bot recognizes:_, tapez **Call transfer intent** pour retrouver l'intention que vous avez créée.

1. Pour la section _Then respond with:_, cliquez sur l'icône **&vellip;** et sélectionnez **Open JSON editor**. Copiez et collez le fragment de code suivant pour remplacer le code qui figure dans la zone :

  * Si vous utilisez un URI tél, replacez l'URI SIP dans `transferTarget` avec votre URI tél. Par exemple,  `"transferTarget":"tel:+18889990000"`.

  * **Remarque** : Assurez-vous que l'URI `transferTarget` commence par `+`.

  ```json
  {
      "output": {
          "text": {
              "values": [ "Please hold on while I connect you with a live agent." ],
     "selection_policy": "sequential"
          },
    "vgwAction": {
              "command": "vgwActTransfer",
      "parameters": {
                  "transferTarget": "sip:+18889990000\\@dal.watson-va.netfoundry.net"
              }
          }
      }
  }
  ```
  {: codeblock}

1. Vérifiez que le numéro de téléphone indiqué dans votre URI de terminaison ou URI tél dans `transferTarget` correspond bien au numéro de téléphone dans votre liaison SIP.

**Rappel** : l'URI SIP de la cible de transfert inclut un numéro de téléphone et l'URI de terminaison que vous avez créé. N'utilisez pas de numéro de téléphone personnel dans votre cible de transfert. Par exemple, si le numéro de téléphone est `18889990000` et que votre URI de terminaison est `mysiptrunk.pstn.twilio.com`, l'URI SIP complet est `sip:+18889990000\\@mysiptrunk.pstn.twilio.com`. Si vous utilisez NetFoundry et que votre numéro de téléphone est `18889990000`, l'URI SIP complet est `sip:+18889990000\\@dal.watson-va.netfoundry.net`.

**Remarque** : Assurez-vous que l'URI `transferTarget` commence par `+` et comprend jusqu'à 256 caractères.

## Etapes suivantes
{: #Next}

Testez votre agent vocal en appelant le numéro de téléphone qui lui est associé et utilisez les termes clés que vous avez identifiés dans votre intention. Si votre agent vocal vous redirige, cela a fonctionné !

A présent, vous avez affiner et configurer l'intention **Transfer** et le dialogue pour répondre aux termes et aux phrases clés de votre choix.
