---

copyright:
  years: 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"

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

Pour utiliser le service et optimiser l'expérience utilisateur, {{site.data.keyword.iva_short}} collecte et stocke un ensemble minimal d'informations personnelles qui sont traitées en accord avec notre [autorité de protection des données](https://www.ibm.com/support/customer/csol/terms/){: new_window} et l'[annexe de l'autorité de protection des données](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=00C4CE004FA711E7AA10752A2F494A7C){: new_window}. {{site.data.keyword.iva_short}} ne stocke ni ne collecte ou traite aucune des données reçues dans le cadre de conversations vocales ou par SMS. Ces données sont acheminées vers différents services pour traitement. Lors d'une conversation, les utilisateurs peuvent partager des informations qui contiennent des renseignements médicaux protégés (PHI), des informations personnelles identifiables (PII) ou des données PCI DSS (norme de sécurité de l'industrie des cartes de paiement). Pour en savoir plus sur les flux de conversion et l'architecture de {{site.data.keyword.iva_short}}, voir [Architecture](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}.

Prenez en compte les fonctions suivantes lorsque vous configurez votre instance d'agent vocal pour la prise en charge de la gestion de la sécurisé et de la confidentialité de données.

### Transfert d'appel
{:  #calltransfer_infosec}

Lors de l'ajout de fonctionnalités de transfert d'appel à votre agent vocal, vous fournissez un numéro de téléphone lorsque vous configurez l'URI SIP de la cible de transfert. Les utilisateurs ne doivent pas fournir un numéro de téléphone personnel pour cette cible de transfert.

Pour en savoir plus sur la configuration de votre liaison SIP et de votre URI SIP pour le transfert d'appel, voir [Configuration du transfert d'appel](/docs/services/voice-agent?topic=voice-agent-call-transfer).

### Transmission d'événements
{: #infosec_event_forwarding}

Vous pouvez configurer votre agent vocal de manière à transmettre les événements de génération de rapports à une instance de base de données {{site.data.keyword.cloudantfull}}. Ces événements de génération de rapports peuvent inclure des données PII, PHI et PCI DSS concernant vos appelants sous forme de transcriptions, événements d'échange de conversation et événements d'enregistrements de détail d'appel (CDR, Call Detail Record). Les données d'appel et de SMS ainsi que les événements de génération de rapports ne sont pas stockés, traités ou collectés dans {{site.data.keyword.iva_short}} et les utilisateurs doivent configurer leurs services {{site.data.keyword.cloudant_short_notm}} externes de manière appropriée. **Par défaut, la transmission d'événements est désactivée.**

Voir [Activation de la transmission d'événements](/docs/services/voice-agent?topic=voice-agent-event_forwarding) pour configurer vos agents vocaux de manière à transmettre des événements de génération de rapports.

Voir [**{{site.data.keyword.cloudant_short_notm}} : Sécurité**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window} pour plus d'informations sur la confidentialité des données et la sécurité des informations pour {{site.data.keyword.cloudant_short_notm}}.

### Mise en cache Text to Speech
{: #tts_caching}

Pour dialoguer avec les clients, {{site.data.keyword.conversationshort}} élabore des réponses sous forme de texte qui sont transmises au service {{site.data.keyword.texttospeechshort}} et prononcées à haute voix dans {{site.data.keyword.iva_short}}. Les réponses que crée {{site.data.keyword.conversationshort}} peuvent contenir des informations sensibles. Pour éviter que {{site.data.keyword.iva_short}} ne mette en cache les réponses reçues du service {{site.data.keyword.texttospeechshort}} qui contiennent des renseignements personnels, vous pouvez activer la commande d'action `vgwActExcludeFromTTSCache` afin d'exclure de la mise en cache les énoncés contenant certains types d'informations. Voir [Programmation d'agents vocaux à l'aide de l'API](/docs/services/voice-agent?topic=voice-agent-api#action-sequences).

Une fois votre instance d'agent vocal supprimée, le cache TTS est vidé dans les 24 heures. Cette valeur est appelée `TTS cache timeout value`.

### Connexions sécurisées
{: #secure_trunking}

{{site.data.keyword.iva_short}} est basé dans {{site.data.keyword.Bluemix_notm}} et s'intègre aux liaisons SIP que les utilisateurs configurent. Etant donné que les liaisons SIP sont des éléments externes qui se connectent à {{site.data.keyword.iva_short}}, vous pouvez activer des connexions sécurisées entre vos liaisons SIP et {{site.data.keyword.iva_short}} à l'aide du protocole SRTP (Secure Real Time Transport Protocol) et le chiffrement à l'aide de secure sip (sips), qui s'appuie sur TLS (Transport Layer Security). Voir [Sécurisation des connexions](/docs/services/voice-agent?topic=voice-agent-securing).

Par défaut, les données SMS sont chiffrées avec TLS. Pour plus d'informations, voir [Voice Gateway: Data Processing](https://www.ibm.com/support/knowledgecenter/en/SS4U29/gdpr_considerations.html#GDPR_dataProcessing){: new_window}.

### Configuration du moteur d'orchestration de service
{: #SOE_config}

Vous pouvez utiliser un moteur d'orchestration de service pour traiter la transmission des informations entre {{site.data.keyword.iva_short}} et {{site.data.keyword.conversationshort}} afin de personnaliser la conversation avec les appelants. Pour préserver la sécurité de la connexion, veillez à configurer votre moteur d'orchestration de service avec une URL sécurisée, `https`, et une authentification d'utilisateur.

Voir [Configuration de {{site.data.keyword.conversationshort}} pour votre agent vocal](/docs/services/voice-agent?topic=voice-agent-conversation_va#conversation_va) et [Architecture avec un moteur d'orchestration de service](/docs/services/voice-agent?topic=voice-agent-about#arch-soe).

## Prise en charge des SMS/MMS
{: #SMS_MMS}

### Traitement des données
{: #data_handling}

{{site.data.keyword.iva_short}} ne stocke ni ne collecte ou traite les données SMS. Les images MMS sont stockées en dehors de notre service et sont gérées par le fournisseur de services. Les clients doivent se reporter à l'accord de sécurité/confidentialité de leur fournisseur SMS. {{site.data.keyword.iva_short}} gère uniquement les liens textuels vers les images intégrées aux messages SMS.

Lorsqu'un moteur d'orchestration de service ou {{site.data.keyword.conversationshort}} envoie un message MMS à l'utilisateur (avec ou sans message texte SMS), une ou plusieurs URL de support publiques sont envoyées à Twilio. Twilio ne prend pas en charge les URL non publiques.Les utilisateurs doivent éviter d'envoyer des informations personnelles ou sensibles via MMS.

{{site.data.keyword.iva_short}} masque l'ID de l'appelant dans les journaux des messages pour éviter de collecter ce type d'informations personnelles identifiables.

### Authentification
{: #authentication}

Les messages SMS entrants sont sécurisés avec le fournisseur de services à l'aide de l'[authentification IAM](/docs/services/voice-agent?topic=voice-agent-iam#sms_access){: new_window}.

## Services liés à {{site.data.keyword.iva_short}}
{: #related_services}

{{site.data.keyword.iva_short}} orchestre différents services {{site.data.keyword.Bluemix_notm}} afin de coordonner la communication entre les utilisateurs finaux et les services cognitifs basés sur le Cloud. {{site.data.keyword.iva_short}} ne stocke ni ne collecte ou traite les données d'une manière susceptible d'enfreindre les droits des utilisateurs finaux. Cependant, selon la configuration des services associés, ces services intégrés peuvent collecter des renseignements médicaux protégés (PHI), des informations personnelles identifiables (PII) ou des données PCI DSS (norme de sécurité de l'industrie des cartes de paiement) que fournissent les utilisateurs au cours d'une conversation. Pour plus d'information sur le flux de conversation et l'architecture {{site.data.keyword.iva_short}}, voir [Architecture](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}.

Voir les ressources suivantes pour des considérations relatives à chaque service et à {{site.data.keyword.Bluemix_notm}}.

  * [**{{site.data.keyword.Bluemix_short}}: Security compliance**](/docs/overview?topic=overview-security#security)
  * [**{{site.data.keyword.conversationfull}}: Information security**](/docs/services/assistant?topic=assistant-information-security#information-security){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}: Information security**](/docs/services/text-to-speech?topic=text-to-speech-information-security){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}: Information security**](/docs/services/speech-to-text?topic=speech-to-text-information-security){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: Security**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}
