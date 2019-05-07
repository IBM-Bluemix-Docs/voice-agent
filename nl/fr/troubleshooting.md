---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Traitement des incidents et support
{: #troubleshooting}

Vous rencontrez des problèmes avec {{site.data.keyword.iva_full}} ? Passez en revue les astuces relatives au traitement des incidents courants et contactez la communauté si vous des questions.
{: shortdesc}

## Traitement des problèmes liés à {{site.data.keyword.iva_short}}
{: #how-to}

Pour traiter les problèmes liés à vos agents vocaux, vous pouvez utiliser la consignation, l'utilisation et la transmission d'événements afin de trouver des enregistrements d'erreurs et d'incidents. Ces enregistrements peuvent vous aider à diagnostiquer et résoudre des problèmes liés à vos agents vocaux. Si vous rencontrez des difficultés liées à {{site.data.keyword.iva_short}}, exécutez les étapes décrites ci-après.

1. En cas d'échec d'un appel, l'échange de {{site.data.keyword.conversationshort}} final peut être à l'origine de cette défaillance.

1. Les journaux d'utilisation contiennent les erreurs qui peuvent s'être produites durant un appel en particulier. Voir [Affichage des informations d'utilisation et des journaux d'appels](/docs/services/voice-agent?topic=voice-agent-logging).

1. Recherchez d'éventuelles erreurs dans vos journaux de fournisseur de services. Par exemple, Twilio fournit des journaux pour chaque liaison SIP qu'il héberge.

1. En [activant la transmission d'événements pour les agents vocaux](/docs/services/voice-agent?topic=voice-agent-event_forwarding), vous pouvez configurer votre agent vocal pour la transmission d'enregistrements CDR à une base de données Cloudant, puis déterminer la raison pour laquelle un appel a échoué. D'autres événements, tels que des événements d'échange {{site.data.keyword.conversationshort}}, peuvent fournir des détails sur chaque échange de conversation dans un appel.

**Important :** Les événements d'enregistrement des détails d'appel, de transcription et d'échange incluent des informations fournies par vos utilisateurs pouvant potentiellement contenir des renseignements médicaux protégés (PHI), des informations personnelles identifiables (PII) ou des données PCI DSS (norme de sécurité de l'industrie des cartes de paiement). Pour empêcher que les informations personnelles ne soient exposées, vous devez faire en sorte que votre instance {{site.data.keyword.cloudant_short_notm}} protège correctement les informations confidentielles partagées par vos utilisateurs ou divulguées durant une conversation.


## Accès à l'aide
{: #help}

Si vous avez besoin d'aide, joignez notre communauté de développeurs en publiant des questions ou des commentaires aux emplacements suivants, tous activement surveillés.

* Publiez votre question sur le [forum dwAnswers ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/topics/voice-agent/) en y ajoutant la balise `voice-agent`.
* Publiez votre question sur [StackOverflow ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://stackoverflow.com/questions/tagged/voice-agent){: new_window} en y ajoutant la balise `voice-agent`.
* Rejoignez-nous sur Slack, dans l'équipe [IBM Cloud Technology ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) sous le canal `#ibmvoicegateway`.

**N'oubliez pas** : avant de publier des journaux ou des enregistrements d'appels, retirez toutes les informations personnelles que vos appelants et utilisateurs ont pu partager durant la conversation.

## Astuces relatives au traitement des incidents
{: #troubleshooting-tips}

### Je n'obtiens pas de réponse lorsque j'appelle mon agent vocal. Pour quelle raison ?

Votre appel ne s'est probablement pas connecté aux services. Ce problème se produit lorsque l'instance de service {{site.data.keyword.iva_short}} n'est pas correctement configurée. Vérifiez les paramètres d'agent vocal suivants :

* Vérifiez que le numéro de téléphone indiqué sur le tableau de bord _Gestion_ de l'agent vocal est le même que celui fourni par votre fournisseur de liaison SIP, par exemple, NetFoundry ou Twilio.

   **Remarque :** vous devez inclure le code pays et l'indicatif régional lorsque vous spécifiez le numéro de téléphone sur le tableau de bord _Gestion_ de l'agent vocal. Par exemple, `18884253968`.

* Vérifiez que les données d'identification et les URL du service Watson, ainsi que l'ID d'espace de travail {{site.data.keyword.conversationshort}} sont tous valides.
* Vérifiez que le dialogue dans votre compétence {{site.data.keyword.conversationshort}} a été correctement créé.
  * Vous pouvez importer l'[exemple de conversation ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) à partir de GitHub pour une compétence préconfigurée. Pour plus d'informations sur l'enregistrement de l'exemple de conversation en tant que fichier JSON et l'importation de ce fichier en tant que compétence dans l'outil {{site.data.keyword.conversationshort}}, voir l'[étape 3 dans le *tutoriel d'initiation*](/docs/services/voice-agent?topic=voice-agent-getting-started-tutorial#step3).
  * Si vous avez créé votre propre dialogue {{site.data.keyword.conversationshort}}, vérifiez qu'il contient un noeud avec la condition `conversation_start` et un noeud avec une réponse par défaut. Pour obtenir des instructions détaillées, voir [Création d'un dialogue](/docs/services/assistant?topic=assistant-getting-started#getting-started-build-dialog) dans la documentation {{site.data.keyword.conversationshort}}.
* Vérifiez si votre numéro de téléphone est répertorié sur le tableau de bord _Utilisation_ de l'agent vocal. Si un élément est visible pour votre appel téléphonique, cela signifie que votre agent vocal est connecté au service Watson.

### Je ne parviens pas à spécifier un numéro de téléphone lorsque je crée un agent vocal. Pour quelle raison ?

Vérifiez si le numéro de téléphone que vous avez spécifié est utilisé par un agent vocal existant. Un seul agent vocal peut être associé à un numéro de téléphone. Vous pouvez mettre à disposition un autre numéro de téléphone fourni par votre fournisseur de liaison SIP et l'utiliser pour créer un autre agent vocal. Ou alors, vous pouvez [supprimer l'agent vocal existant sur le tableau de bord _Gestion_](/docs/services/voice-agent?topic=voice-agent-managing#delete_va) afin de libérer le numéro de téléphone, puis créer un nouvel agent vocal.

### Pourquoi mes appels échouent-ils fréquemment ?

Les agents vocaux peuvent avoir des problèmes lorsque les appels échouent car un moteur d'orchestration de service initie une longue transaction et il ne répond pas à votre agent vocal en temps voulu. Si une transaction dépasse le délai d'attente {{site.data.keyword.conversationshort}} défini par défaut, l'appel échoue. Pour éviter les échecs d'appel, le moteur d'orchestration de service peut modifier le délai d'attente {{site.data.keyword.conversationshort}} défini par défaut à l'aide de la variable d'état `vgwConversationResponseTimeout`. Voir [Variables définies dans le dialogue {{site.data.keyword.conversationshort}}](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html#variables-conv).
