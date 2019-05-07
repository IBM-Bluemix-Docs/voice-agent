---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configuration de plusieurs emplacements de service
{: #disaster-recovery}

Vous pouvez connecter votre agent vocal à plusieurs services dans différents emplacements pour permettre une redondance des services. Votre second emplacement n'est pas un second agent vocal, il agit uniquement en tant que remplaçant.
{: shortdesc}

Si vous utilisez un plan _Lite_ pour votre instance d'agent vocal, vous pouvez connecter votre liaison SIP à un seul noeud final, où votre instance d'agent vocal est créée. Etant donné que le plan _Lite_ permet des connexions vers un seul emplacement, vous pouvez fournir des redondances pour vos services connectés, mais pas pour votre agent vocal. Si une panne se produit au niveau du service dans l'emplacement de votre agent vocal, les appels ne peuvent pas être dirigés vers un emplacement secondaire.
{: tip}

## Ajout de services redondants
{: #add_redundant}

Vous pouvez à tout moment ajouter un emplacement de service tiers ou Watson à la configuration de votre agent de service, en éditant votre agent vocal.

1. Pour ajouter un service redondant à un agent vocal existant, accédez à l'onglet _Agents vocaux_ de votre tableau de bord _Gestion_. Cliquez sur **Editer un agent** pour l'agent vocal que vous souhaitez configurer.

1. Sélectionnez **Emplacement 1** ou **Emplacement 2** pour le service {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} ou {{site.data.keyword.speechtotextshort}} que vous souhaitez connecter, puis ajoutez vos informations de configuration. Vous pouvez utiliser des services tiers ou des instances de service Watson dans votre espace de travail ou dans d'autres espaces de travail. Voir [Utilisation d'instances de service dans d'autres espaces de travail {{site.data.keyword.Bluemix_notm}}](/docs/services/voice-agent?topic=voice-agent-other_service).

**Remarque** : la redondance de service nécessite que vous utilisiez des instances de service Watson dans différentes régions de service pour différents emplacements.

Vous pouvez activer ou désactiver un emplacement en utilisant la zone **Activer l'emplacement**. **Emplacement 1** est activé par défaut et **Emplacement 2** est désactivé par défaut. Au moins un emplacement doit être activé pour chaque service Watson.

## Ajout de plusieurs emplacements de service Watson
{: #add_location}

Votre agent vocal utilise les instances de service Watson par ordre de distance géographique. Par exemple, vous pouvez créer un agent vocal dans la région de Washington DC et vos services {{site.data.keyword.conversationshort}} dans les régions de Dallas et Sydney (Australie). Votre agent vocal utilise la région de Dallas pour {{site.data.keyword.conversationshort}} car elle est géographiquement plus proche de Washington DC que Sydney. Lorsque vous établissez des connexions à des services Watson situés dans plusieurs régions, si un service Watson est hors service à un emplacement, votre agent vocal peut utiliser le service redondant.
