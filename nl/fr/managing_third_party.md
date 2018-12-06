---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-16"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Connexion à des services voix et texte tiers
{: #third-party}

Vous pouvez connecter des services voix et texte tiers lors de la création, du clonage ou de l'édition de votre agent vocal sur le tableau de bord _Gestion_.
{: shortdesc}

Comme alternative, pour configurer vos connexions de services voix et texte à la volée, vous pouvez [utiliser la configuration dynamique avec {{site.data.keyword.conversationshort}}](api_dynamic_config.html). Ceci vous permet de changer la configuration de votre agent vocal avec des balises d'action et des variables d'état.

## Connection à Google Speech-to-Text depuis {{site.data.keyword.iva_short}}
{: #stt_va}

Au lieu d'utiliser une instance {{site.data.keyword.speechtotextfull}}, vous pouvez choisir de connecter votre agent vocal à un service Speech to Text tiers, tel que [Google Cloud Speech-to-Text ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.google.com/speech-to-text/).

1. Accédez à l'onglet _Agents vocaux_ de votre tableau de bord _Gestion_ et choisissez soit d'**éditer** un agent vocal existant ou de **créer un nouvel agent vocal**.

1. Dans votre configuration du service _Speech to Text_, choisissez **Instance de service Google Speech to Text**.

1. Choisissez la **Langue** de votre instance de service.

1. Entrez les données d'identification de votre service Google Cloud Speech-to-Text.
  * Vous pouvez générer les données d'identification de votre service dans la plateforme Google Cloud sous la forme d'une clé JSON lorsque vous [définissez un compte de service ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). L'exemple de code suivant contient des exemples de zones de données d'identification générées sur la plateforme Google Cloud.

    ```json
    {
      "type": "",
      "auth_uri": "",
      "client_id": "",
      "token_uri": "",
      "project_id": "",
      "private_key": "",
      "client_email": "",
      "private_key_id": "",
      "client_x509_cert_url": "",
      "auth_provider_x509_cert_url": ""
    }
    ```
    {: codeblock}

1. **Facultatif :** Sélectionnez **Afficher les paramètres avancés** pour entrer les paramètres de configuration spéciaux définis par Google dans un format JSON valide.
  L'exemple suivant montre les paramètres de configuration Google qui permettent d'activer un filtre anti-grossièretés pour une instance en Anglais US.
  ```json
  {
    "languageCode": "en-US",
    "profanityFilter": false
  }
  ```
  {: codeblock}

  Si vous sélectionnez une langue différente de celle définie dans `languageCode` dans la configuration du service, {{site.data.keyword.iva_short}} remplace votre sélection par la langue définie par la configuration JSON `languageCode`.
  {: tip}

## Connexion à Google Text-to-Speech depuis {{site.data.keyword.iva_short}}
{: #tts_va}

Au lieu d'utiliser une instance {{site.data.keyword.texttospeechfull}}, vous pouvez choisir de connecter votre agent vocal à un service Text to Speech tiers, tel que [Google Cloud Text-to-Speech ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.google.com/text-to-speech/).

1. Accédez à l'onglet _Agents vocaux_ de votre tableau de bord _Gestion_ et choisissez soit d'**éditer** un agent vocal existant ou de **créer un nouvel agent vocal**.

1. Dans la configuration de votre service _Text to Speech_, choisissez **Instance de service Google Text to Speech**.

1. Choisissez la **Langue** et la **Voix** de votre instance de service.

1. Entrez les données d'identification de votre service Google Cloud Text-to-Speech.
  * Vous pouvez générer les données d'identification de votre service dans la plateforme Google Cloud sous la forme d'une clé JSON lorsque vous [définissez un compte de service ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). L'exemple de code suivant contient des exemples de zones de données d'identification générées sur la plateforme Google Cloud.

    ```json
    {
      "type": "",
      "auth_uri": "",
      "client_id": "",
      "token_uri": "",
      "project_id": "",
      "private_key": "",
      "client_email": "",
      "private_key_id": "",
      "client_x509_cert_url": "",
      "auth_provider_x509_cert_url": ""
    }
    ```
    {: codeblock}

1. **Facultatif :** Sélectionnez **Afficher les paramètres avancés** pour entrer les paramètres de configuration spéciaux définis par Google dans un format JSON valide.
  L'exemple suivant montre les paramètres de configuration Google d'une voix féminine parlant l'allemand.

  Si vous sélectionnez une langue différente de celle définie dans `languageCode` dans la configuration du service, {{site.data.keyword.iva_short}} remplace votre sélection par la langue définie par la configuration JSON `languageCode`.
  {: tip}

  ```json
  {
  "config": {
    "audioConfig": {
      "speakingRate": 1.3
    },
    "voiceConfig": {
      "ssmGender": "FEMALE",
      "languageCode": "de-DE"
    }
  }
  }
  ```
  {: codeblock}
