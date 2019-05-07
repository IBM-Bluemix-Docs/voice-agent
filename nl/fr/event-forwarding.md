---

copyright:
  years: 2019
lastupdated: "2019-01-30"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Activation de la transmission d'événements pour les agents vocaux
{: #event_forwarding}

Vous pouvez activer la transmission d'événements pour collecter des informations sur les appels qui sont gérés par vos agents vocaux dans {{site.data.keyword.iva_full}} à l'aide d'un service de base de données {{site.data.keyword.cloudantfull}}.
{: shortdesc}

Vous souhaiterez peut-être collecter et analyser des données d'appel à partir de {{site.data.keyword.iva_short}} afin d'améliorer la fluidité de la conversation pour l'appelant. Chaque agent vocal que vous créez peut transmettre des rapports d'événements à une base de données {{site.data.keyword.cloudant_short_notm}} que vous gérez. Les événements contenues dans les rapports sont notamment des événements d'enregistrement de détail d'appel (CDR), des événements de transcription et des événements d'échange. Pour en savoir plus sur les types d'événements que vous pouvez transmettre, voir [Evénements de génération de rapports](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}.

L'analyse des données de ces événements peut vous aider à ajuster les dialogues, à affiner les intentions et à améliorer l'expérience globale de l'appelant.

Lorsque vous créez ou éditez des agents vocaux, vous pouvez également choisir d'activer la transmission d'événements. Pour en savoir plus sur la création et l'édition d'agents vocaux, voir [Gestion des agents vocaux](/docs/services/voice-agent?topic=voice-agent-managing). Vous devez fournir des informations sur le compte {{site.data.keyword.cloudant_short_notm}}, y compris le nom du compte et le mot de passe qui lui est associé, pour activer la transmission d'événements.

**Important :** Les événements d'enregistrement des détails d'appel, de transcription et d'échange incluent des informations fournies par vos utilisateurs pouvant potentiellement contenir des renseignements médicaux protégés (PHI), des informations personnelles identifiables (PII) ou des données PCI DSS (norme de sécurité de l'industrie des cartes de paiement). Pour empêcher que les informations personnelles ne soient exposées, vous devez faire en sorte que votre instance {{site.data.keyword.cloudant_short_notm}} protège correctement les informations confidentielles partagées par vos utilisateurs ou divulguées durant une conversation. Voir [Sécurité des informations et confidentialité des données : Transmission d'événements](/docs/services/voice-agent?topic=voice-agent-infosec#event_forwarding) et [{{site.data.keyword.cloudant_short_notm}}: Security](/docs/services/Cloudant/offerings?topic=cloudant-security#security).


## Activation de la transmission d'événements
{: #enable-event-forwarding}

Vous pouvez activer la transmission d'événements lorsque vous créez ou éditez vos agents vocaux dans le tableau de bord _Gestion_ sur {{site.data.keyword.Bluemix_short}}.

1. Dans la section **Transmission d'événements**, située après la section Configuration pour {{site.data.keyword.texttospeechshort}}, sélectionnez **Activer la transmission d'événements**.

1. Sélectionnez **Mon instance de service {{site.data.keyword.cloudant_short_notm}}** ou **Autre instance de service {{site.data.keyword.cloudant_short_notm}}**.
  * Si vous utilisez **Mon instance de service {{site.data.keyword.cloudant_short_notm}}**, sélectionnez le nom et le nom d'utilisateur du **compte {{site.data.keyword.cloudant_short_notm}}** dans les listes.
  * Si vous créez un agent vocal dans la région de Dallas ou de Washington DC et n'avez pas d'instance de service {{site.data.keyword.cloudant_short_notm}}, vous pouvez en créer une à partir du menu **Compte Cloudant**.
  * Si vous utilisez **Autre instance de service {{site.data.keyword.cloudant_short_notm}}**, entrez le nom d'utilisateur et le mot de passe {{site.data.keyword.cloudant_short_notm}} (jusqu'à 128 et 256 caractères, respectivement) ou la clé d'API du compte (jusqu'à 64 caractères).

1. Sélectionnez **Activer** pour chaque type d'événement que vous souhaitez transmettre, puis choisissez la base de données dans laquelle vous souhaitez transmettre les événements.
  * Evénement d'enregistrement des détails d'appel (CDR)
  * Evénements de transcription
  * Evénements d'échange

1. Affichez votre base de données pour vérifier que les rapports d'événements sont correctement transmis.

## Liens connexes
{: #related-links-forwarding}
* [IBM Voice Gateway : Evénements de génération de rapports](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
* [Sécurité des informations et confidentialité des données](/docs/services/voice-agent?topic=voice-agent-infosec)
* [{{site.data.keyword.cloudant_short_notm}}: Security](/docs/services/Cloudant/offerings?topic=cloudant-security#security)
