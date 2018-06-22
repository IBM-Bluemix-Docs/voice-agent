---

copyright:
  years: 2018
lastupdated: "2018-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Connexion d'une liaison SIP
{: #connect}

Vous pouvez choisir dans la liste présentée ci-après le fournisseur de liaison SIP que vous utilisez pour l'intégration à {{site.data.keyword.iva_full}}.
{: #shortdesc}

* [NetFoundry](#NetFoundry-setup)
* [Twilio](#twilio-setup)
* [AT&T et autres fournisseurs](#att-other)
* [Appairage avec {{site.data.keyword.iva_short}}](#peering)
* [Demande de configuration assistée](#request-setup)

## Création d'une liaison SIP et d'un numéro de téléphone NetFoundry
{: #NetFoundry-setup}

**Remarque :** la création d'un compte nécessite une carte de crédit, périodiquement facturée en fonction de votre utilisation. Si vous disposez déjà d'un compte NetFoundry, vous pouvez l'utiliser.

1. Créez un compte sur le site Web [NetFoundry![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson.netfoundry.io/watson-login){: new_window}. 

1. Accédez à la page principale du _compte Watson_.

1. Sélectionnez une région d'origine du numéro. 

  **Remarque :** consultez le site Web Netfoundry pour connaître les régions disponibles. De nouvelles régions sont continuellement ajoutées. 

1. Cliquez sur **Purchase** et suivez les instructions affichées pour réaliser l'achat. 

1. Une fois le traitement du paiement terminé, votre numéro de téléphone de liaison SIP apparaît dans votre compte.

Vous avez besoin de ce numéro de téléphone pour installer et configurer votre agent vocal et pour configurer le transfert d'appel, y compris le code pays et l'indicatif régional. Voir [Création et connexion de votre agent vocal](getting-started.html#step3).


## Création d'une liaison SIP Twilio
{: #twilio-setup}

**Remarque :** la création d'un [compte Twilio ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.twilio.com/try-twilio){: new_window} nécessite une carte de crédit, périodiquement facturée en fonction de votre utilisation de la liaison SIP que vous configurez. Si vous disposez déjà d'un compte Twilio, vous pouvez l'utiliser.

  1. Créez un compte Twilio sur le [site Web Twilio ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.twilio.com/try-twilio){: new_window}.

  1. Créez une liaison SIP avec votre compte Twilio.

  1. Depuis le site Web Twilio, accédez au tableau de bord Elastic SIP Trunking.

  1. Sélectionnez **Trunks** dans la barre de navigation et créez une liaison SIP. Si vous disposez déjà d'une liaison SIP, cliquez sur l'icône **+**. Dans la boîte de dialogue que vous obtenez, entrez un nom pour votre liaison SIP et cliquez sur **Create**.

  1. Sur la page Elastic SIP Trunks, sélectionne votre liaison SIP.

  1. Sélectionnez **Origination** dans la barre de navigation pour votre liaison SIP et configurez l'URI SIP d'origine. Vous pouvez inclure plusieurs noms d'hôte afin d'empêcher les pannes de service en sélectionnant l'icône **+**.

  L'adresse IP ou le nom d'hôte est la valeur que vous avez notée sur le tableau de bord _Getting Started_ de votre instance de service {{site.data.keyword.iva_short}}. Lorsque vous configurez l'URI d'orifine, il doit être au format d'URI SIP, par exemple, `sip:us-south.voiceagent.cloud.ibm.com/`. Grâce à l'ajout de plusieurs noms d'hôte ou adresses IP, si le premier noeud final d'hôte échoue ou est hors service, votre fournisseur de liaison SIP dirige les appels vers le nom d'hôte suivant dans la liste.

  1. Sélectionnez **Numbers** dans la barre de navigation pour votre liaison SIP. Créez ensuite un numéro de téléphone et affectez-le à votre liaison SIP.

  Sur la page Numbers, cliquez sur **Buy a Number** ou, si vous possédez déjà un numéro, cliquez sur l'icône **+**. Un panneau s'affiche, dans lequel vous pouvez fournir un nouveau numéro de téléphone pour votre région. Affectez le numéro à la liaison SIP que vous avez créée en revenant à la liaison SIP et en cliquant sur l'icône Number.

  Vous avez besoin de ce numéro de téléphone pour configurer votre agent vocal, y compris le code pays et l'indicatif régional. Voir [Création et connexion de votre agent vocal](getting-started.html#step3).


## Connexion avec AT&T et d'autres fournisseurs
{: #att-other}

{{site.data.keyword.iva_short}} prend en charge les connexions à AT&T&reg; et d'autres fournisseurs de liaisons SIP. Toutefois, ces connexions ne sont pas configurées en libre-service et nécessitent une assistance supplémentaire. Voir [Demande de configuration assistée](#request-setup).

## Appairage avec {{site.data.keyword.iva_short}}
{: #peering}

{{site.data.keyword.iva_short}} prend en charge les connexion homologues, par exemple, un tunnel IPSec. Toutefois, ces connexions ne sont pas configurées en libre-service et nécessitent une assistance supplémentaire. Voir [Demande de configuration assistée](#request-setup).

## Demande de configuration assistée
{: #request-setup}

Vous pouvez demander une configuration réseau assistée pour vous connecter à AT&T ou à d'autres fournisseurs de liaison SIP, de pair à pair avec {{site.data.keyword.iva_short}}, ou pour demander plus de 50 connexions simultanées à l'aide du processus ci-après. 

1. Ouvrez un nouveau [ticket de demande de service {{site.data.keyword.Bluemix_notm}}](https://console.bluemix.net/unifiedsupport/tickets/add)

1. Sélectionnez **Technique** pour **Type de ticket**.

1. Choisissez **Cloud Foundry** pour **Sélectionnez un contexte de ressources**.

1. Pour **Zone de support technique**, choisissez **Services d'application**.

1. Renseignez les zones **Région**, **Organisation** et **Espace** pour votre instance {{site.data.keyword.iva_short}}.

1. Sélectionnez votre instance de service {{site.data.keyword.iva_short}} pour **Ressource associée**.

1. Choisissez **Gravité 4 - impact minimal** pour **Gravité**

1. Pour **Objet**, entrez `Configuration réseau assistée par {{site.data.keyword.iva_short}}`.

1. Dans la section **Description brève**, décrivez de quelle façon vous souhaitez vous connecter à votre service {{site.data.keyword.iva_short}} ou demander plu de 50 connexions simultanées pour votre agent vocal. Vous pouvez vous connecter à l'aide d'un fournisseur de liaison SIP ou d'une connexion homologue, telle qu'un tunnel IPSec. Dans votre ticket, vous pouvez joindre un diagramme réseau décrivant votre topologie de réseau au format PDF ou image. Vous pouvez également joindre des livres blancs décrivant de façon détaillée les fonctions de service souhaitées.
