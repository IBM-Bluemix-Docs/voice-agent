---

copyright:
  years: 2018
lastupdated: "2018-11-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Sécurité des informations et confidentialité des données
{: #infosec}

IBM s'est engagée à fournir à ses clients et partenaires des solutions de confidentialité des données ainsi que de sécurité et de gouvernance.
{: shortdesc}

## Gestion des informations et options de configuration
{: #configure_infosec}

{{site.data.keyword.iva_short}} ne stocke ni ne collecte ou traite les données reçues des clients. Ces données sont acheminées vers différents services pour traitement. Lors d'une conversation, les utilisateurs peuvent partager des informations qui contiennent des renseignements médicaux protégés (PHI), des informations personnelles identifiables (PII) ou des données PCI DSS (norme de sécurité de l'industrie des cartes de paiement). Pour en savoir plus sur les flux de conversion et l'architecture de {{site.data.keyword.iva_short}}, voir [Architecture](about.html#architecture){: new_window}.

Prenez en compte les fonctions suivantes lorsque vous configurez votre instance d'agent vocal pour la prise en charge de la gestion de la sécurisé et de la confidentialité de données.

### Transfert d'appel
{:  #calltransfer_infosec}

Lors de l'ajout de fonctionnalités de transfert d'appel à votre agent vocal, vous fournissez un numéro de téléphone lorsque vous configurez l'URI SIP de la cible de transfert. Les utilisateurs ne doivent pas fournir un numéro de téléphone personnel pour cette cible de transfert.

Pour en savoir plus sur la configuration de votre liaison SIP et de votre URI SIP pour le transfert d'appel, voir [Configuration du transfert d'appel](call-transfer.html).

### Transmission d'événements
{: #event_forwarding}

Vous pouvez configurer votre agent vocal de manière à transmettre les événements de génération de rapports à une instance de base de données {{site.data.keyword.cloudantfull}}. Ces événements de génération de rapports peuvent inclure des données PII, PHI et PCI DSS concernant vos appelants sous forme de transcriptions, événements d'échange de conversation et événements d'enregistrements de détail d'appel (CDR, Call Detail Record). Les données d'appel et événements de génération de rapports ne sont pas stockés, traités ou collectés dans {{site.data.keyword.iva_short}} et les utilisateurs doivent configurer leurs services {{site.data.keyword.cloudant_short_notm}} de manière appropriée. **Par défaut, la transmission d'événements est désactivée.**

Voir [Activation de la transmission d'événements](event-forwarding.html) pour configurer vos agents vocaux de manière à transmettre des événements de génération de rapports.

Voir [**{{site.data.keyword.cloudant_short_notm}} : Sécurité**](../Cloudant/offerings/security.html#security){: new_window} pour plus d'informations sur la confidentialité des données et la sécurité des informations pour {{site.data.keyword.cloudant_short_notm}}.

### Mise en cache Text to Speech
{: #tts_caching}

Pour dialoguer avec les clients, {{site.data.keyword.conversationshort}} élabore des réponses sous forme de texte qui sont transmises au service {{site.data.keyword.texttospeechshort}} et prononcées à haute voix dans {{site.data.keyword.iva_short}}. Les réponses que crée {{site.data.keyword.conversationshort}} peuvent contenir des informations sensibles. Pour éviter que {{site.data.keyword.iva_short}} ne mette en cache les réponses reçues du service {{site.data.keyword.texttospeechshort}} qui contiennent des renseignements personnels, vous pouvez activer la commande d'action `vgwActExcludeFromTTSCache` afin d'exclure de la mise en cache les énoncés contenant certains types d'informations. Voir [Programmation d'agents vocaux à l'aide de l'API](api.html#action-sequences).

### Connexions sécurisées
{: #secure_trunking}

{{site.data.keyword.iva_short}} est basé dans {{site.data.keyword.Bluemix_notm}} et s'intègre aux liaisons SIP que les utilisateurs configurent. Etant donné que les liaisons SIP sont des éléments externes qui se connectent à {{site.data.keyword.iva_short}}, vous pouvez activer des connexions sécurisées entre vos liaisons SIP et {{site.data.keyword.iva_short}} à l'aide du protocole SRTP (Secure Real Time Transport Protocol) et le chiffrement à l'aide de secure sip (sips), qui s'appuie sur TLS (Transport Layer Security). Voir [Sécurisation des connexions](secure-trunking.html).

### Configuration du moteur d'orchestration de service
{: #SOE_config}

Vous pouvez utiliser un moteur d'orchestration de service pour traiter la transmission des informations entre {{site.data.keyword.iva_short}} et {{site.data.keyword.conversationshort}} afin de personnaliser la conversation avec les appelants. Pour préserver la sécurité de la connexion, veillez à configurer votre moteur d'orchestration de service avec une URL sécurisée, `https`, et une authentification d'utilisateur.

Voir [Configuration de {{site.data.keyword.conversationshort}} pour votre agent vocal](managing_SOE.html#conversation_va) et [Architecture avec un moteur d'orchestration de service](about.html#arch-soe).

## Services liés à {{site.data.keyword.iva_short}}
{: #related_services}

{{site.data.keyword.iva_short}} orchestre différents services {{site.data.keyword.Bluemix_notm}} afin de coordonner la communication entre les utilisateurs finaux et les services cognitifs basés sur le Cloud. {{site.data.keyword.iva_short}} ne stocke ni ne collecte ou traite les données d'une manière susceptible d'enfreindre les droits des utilisateurs finaux. Cependant, selon la configuration des services associés, ces services intégrés peuvent collecter des renseignements médicaux protégés (PHI), des informations personnelles identifiables (PII) ou des données PCI DSS (norme de sécurité de l'industrie des cartes de paiement) que fournissent les utilisateurs au cours d'une conversation. Pour plus d'information sur le flux de conversation et l'architecture {{site.data.keyword.iva_short}}, voir [Architecture](about.html#architecture){: new_window}.

Voir les ressources suivantes pour des considérations relatives à chaque service et à {{site.data.keyword.Bluemix_notm}}.

  * [**{{site.data.keyword.Bluemix_short}}: Security compliance**](../security/compliance.html)
  * [**{{site.data.keyword.conversationfull}}: Information security**](../conversation/information-security.html){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}: Information security**](../text-to-speech/information-security.html){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}: Information security**](../speech-to-text/information-security.html){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: Security**](../Cloudant/offerings/security.html#security){: new_window}
