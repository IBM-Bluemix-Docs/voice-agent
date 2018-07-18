---

copyright:
  years: 2018
lastupdated: "2018-06-19"

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

Lorsque le transfert d'appel est configuré, si un appelant demande à parler à un agent humain durant une conversation, l'appel est transféré automatiquement par l'agent vocal. Vous pouvez activer le transfert d'appel en définissant un URI d'arrêt dans la configuration de votre fournisseur SIP. Ensuite, définissez la cible du transfert sur une action API dans un noeud de dialogue de votre instance {{site.data.keyword.conversationshort}}. Votre cible de transfert est un URI SIP qui contient l'URI d'arrêt et le numéro de téléphone. Pour plus d'informations sur les actions prises en charge et la personnalisation de vos agents vocaux, voir [Programmation des agents vocaux à l'aide de l'API](api.html).

## Etape 1 : Configuration de l'URI d'arrêt
{: #termination-setup}

### Configuration d'un URI d'arrêt dans NetFoundry
{: #termination-netfoundry}

Notez le numéro de téléphone dans votre [compte NetFoundry![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien extern")](https://watson.netfoundry.io/watson-login){: new_window} vers lequel le transfert doit s'effectuer. Vous pouvez ensuite spécifier ce numéro de téléphone et l'URI d'arrêt comme cible de transfert dans votre dialogue {{site.data.keyword.conversationshort}}. N'utilisez pas un numéro de téléphone personnel.

Vous pouvez copier l'URI d'arrêt NetFoundry à utiliser dans la cible de transfert.

```
dal.watson-va.netfoundry.net
```
{: codeblock}

Vous n'avez pas besoin de configurer manuellement l'URI d'arrêt dans votre compte NetFoundry lors de l'étape [Configuration de {{site.data.keyword.conversationshort}} pour le transfert d'appel](#conversation-setup).

### Configuration d'un URI d'arrêt dans Twilio
{: #termination-Twilio}

1. Dans votre compte Twilio, accédez au tableau de bord _Elastic SIP Trunking_ et sélectionnez **Trunks**.

1. Choisissez la liaison à laquelle vous souhaitez ajouter le transfert d'appel en sélectionnant une liaison existante ou en créant une nouvelle liaison en cliquant sur l'icône **+**.

  * Si vous créez une nouvelle liaison, vous devez configurer l'_URI de liaison SIP_ dans le tableau de bord **Origination**.  Pour plus d'informations, voir [Connexion d'une liaison SIP](connect-SIP.html).

1. Sélectionnez **Termination** sur votre barre de navigation et entrez un nom pour votre URI d'arrêt.

  * Les noms d'URI d'arrêt doivent être uniques. Twilio vérifie automatiquement si le nom que vous avez choisi est disponible. Pour plus de détails sur les services Twilio, voir [Paramètres d'arrêt de liaison SIP![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window}.

1. Dans la section _Authentication_, cliquez sur l'icône **+** pour ajouter une adresse IP d'agent vocal à la liste d'adresses IP de contrôle d'accès.

  Ajoutez les deux adresses IP suivantes :
   * 169.60.154.134 (région de service du Sud des Etats-Unis)
   * 169.61.86.179 (région de service de l'Est des Etats-Unis)

1. Cliquez sur **Save** pour finaliser la configuration de votre URI d'arrêt.

Notez le numéro de téléphone et l'URI d'arrêt vers lesquels le transfert doit s'effectuer. Assurez-vous que le numéro de téléphone n'est pas un numéro personnel. Vous pouvez utiliser le numéro de téléphone et l'URI d'arrêt pour indiquer la cible du transfert dans votre dialogue {{site.data.keyword.conversationshort}}.


## Etape 2 : Configuration de {{site.data.keyword.conversationshort}} pour le transfert d'appel
{: #conversation-setup}

Pour en apprendre davantage sur l'utilisation du service {{site.data.keyword.conversationshort}}, voir [A propos de {{site.data.keyword.conversationshort}}](../conversation/index.html#about).

1. Dans votre tableau de bord {{site.data.keyword.Bluemix_notm}}, sélectionnez l'instance {{site.data.keyword.conversationshort}} qui est utilisée par votre agent vocal.

1. A partir du tableau de bord _Initiation_, cliquez sur le bouton **Lancer l'outil**.

1. Cliquez sur **Initiation** sur l'espace de travail que vous souhaitez éditer.

1. Cliquez sur **Ajouter une intention** et entrez un nom pour l'intention, par exemple, _Transfer_.

  Vous pouvez entrer des informations plus détaillées ou revenir ultérieurement pour éditer et affiner l'intention.

1. Une fois votre intention de transfert d'appel créée, sélectionnez l'onglet _Dialogue_.

1. Cliquez sur **Ajouter un noeud** et entrez un nom pour le noeud, par exemple, _Call Transfer_.

1. Dans la section _If the bot recognizes:_, tapez **Call transfer intent** pour retrouver l'intention que vous avez créée.

1. Pour la section _Then respond with:_, cliquez sur l'icône **&vellip;** et sélectionnez **Open JSON editor**. Copiez et collez le fragment de code suivant pour remplacer le code qui figure dans la zone :

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
                "transferTarget": "sip:18889990000\\@dal.watson-va.netfoundry.net"
            }
        }
    }
}
```
{: codeblock}

**N'oubliez pas** : L'URI SIP du cible de transfert inclut un numéro de téléphone et l'URI d'arrêt que vous avez créé. N'utilisez pas de numéro de téléphone personnel dans votre cible de transfert. Par exemple, si le numéro de téléphone est `18889990000` et que votre URI d'arrêt est `mysiptrunk.pstn.twilio.com`, l'URI SIP complet est `sip:18889990000\\@mysiptrunk.pstn.twilio.com`. Si vous utilisez NetFoundry et que votre numéro de téléphone est `18889990000`, l'URI SIP complet est `sip:18889990000\\@dal.watson-va.netfoundry.net`.

## Etapes suivantes
{: #Next}

Testez votre agent vocal en appelant le numéro de téléphone qui lui est associé et utilisez les termes clés que vous avez identifiés dans votre intention. Si votre agent vocal vous redirige, cela a fonctionné !

A présent, vous avez affiner et configurer l'intention **Transfer** et le dialogue pour répondre aux termes et aux phrases clés de votre choix.
