---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Connessione ai servizi di discorso e testo di terze parti
{: #third-party}

Puoi collegare i servizi di discorso e testo di terze parti quando crei, cloni o modifichi il tuo Voice Agent nel dashboard _Manage_.
{: shortdesc}

In alternativa, per configurare le tue connessioni di discorso e testo sul momento, puoi [utilizzare la configurazione dinamica con {{site.data.keyword.conversationshort}}](/docs/services/voice-agent?topic=voice-agent-dynamic-donfig). Questo ti consente di modificare la tua configurazione del Voice Agent con tag di azione e variabili di stato.

## Collegamento a Google Speech-to-Text da {{site.data.keyword.iva_short}}
{: #stt_va}

Invece di utilizzare un'istanza {{site.data.keyword.speechtotextfull}}, puoi scegliere di connettere il tuo Voice Agent a un servizio da voce a testo di terze parti come [Google Cloud Speech-to-Text ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.google.com/speech-to-text/).

1. Passa alla scheda _Voice agents_ nel tuo dashboard _Manage_ e seleziona **Edit** per un Voice Agent esistente o **Create new voice agent**.

1. Nella tua configurazione del servizio _Speech to Text_, scegli **Google Speech to Text service instance**.

1. Scegli la lingua (**Language**) della tua istanza del servizio.

1. Immetti le tue credenziali del servizio Google Cloud Speech-to-Text, con un limite fino a 3072 caratteri.
  * Puoi generare le tue credenziali del servizio nella Google Cloud Platform come una chiave JSON quando [configuri un account del servizio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). Il seguente esempio di codice contiene i campi delle credenziali di esempio generati su Google Cloud Platform.

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

1. **Facoltativo** seleziona **Show Advanced** per immettere le impostazioni di configurazione speciali definite da Google in un formato JSON valido.
  Il seguente esempio mostra le impostazioni di configurazione Google per abilitare un filtro volgarità per un'istanza di lingua inglese (US).
  ```json
  {
    "languageCode": "en-US",
    "profanityFilter": false
  }
  ```
  {: codeblock}

  Se selezioni una lingua nella configurazione del servizio differente dalla lingua che hai definito in `languageCode`, {{site.data.keyword.iva_short}} sovrascrive la tua selezione con la lingua definita dalla configurazione JSON `languageCode`.
  {: tip}

## Collegamento a Google Text-to-Speech da {{site.data.keyword.iva_short}}
{: #tts_va}

Invece di utilizzare un'istanza {{site.data.keyword.texttospeechfull}}, puoi scegliere di collegare il tuo Voice Agent a un servizio speech to text di terze parti, come ad esempio [Google Cloud Text-to-Speech ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.google.com/text-to-speech/).

1. Passa alla scheda _Voice agents_ nel tuo dashboard _Manage_ e seleziona **Edit** per un Voice Agent esistente o **Create new voice agent**.

1. Nella tua configurazione del servizio _Text to Speech_, scegli **Google Text to Speech service instance**.

1. Scegli la lingua (**Language**) e la voce (**Voice**) della tua istanza del servizio.

1. Immetti le tue credenziali del servizio Google Cloud Text-to-Speech, con un limite fino a 3072 caratteri.
  * Puoi generare le tue credenziali del servizio nella Google Cloud Platform come una chiave JSON quando [configuri un account del servizio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). Il seguente esempio di codice contiene i campi delle credenziali di esempio generati su Google Cloud Platform.

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

1. **Facoltativo** seleziona **Show Advanced** per immettere le impostazioni di configurazione speciali definite da Google in un formato JSON valido.
  Il seguente esempio mostra le impostazioni di configurazione Google per una voce femminile in tedesco.

  Se selezioni una lingua nella configurazione del servizio differente dalla lingua che hai definito in `languageCode`, {{site.data.keyword.iva_short}} sovrascrive la tua selezione con la lingua definita dalla configurazione JSON `languageCode`.
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
