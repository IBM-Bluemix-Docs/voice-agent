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


# Conectando-se com serviços de fala e texto de terceiro
{: #third-party}

É possível conectar serviços de fala e texto de terceiro ao criar, clonar ou editar o agente de voz no painel _Gerenciar_.
{: shortdesc}

Como alternativa, para configurar as conexões de serviço de fala e texto rapidamente, é possível [usar a configuração dinâmica com o {{site.data.keyword.conversationshort}}](/docs/services/voice-agent?topic=voice-agent-dynamic-donfig). Isso permite mudar a configuração do agente de voz com as tags de ação e as variáveis de estado.

## Conectando-se ao Google Speech-to-Text por meio do {{site.data.keyword.iva_short}}
{: #stt_va}

Em vez de usar uma instância do {{site.data.keyword.speechtotextfull}}, é possível escolher conectar seu agente de voz a um serviço de fala para texto de terceiro, como o [Google Cloud Speech-to-Text ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.google.com/speech-to-text/).

1. Navegue para a guia _Agentes de voz_ no painel _Gerenciar_ e selecione **Editar** um agente de voz existente ou **Criar novo agente de voz**.

1. Na configuração do serviço _Fala para texto_, escolha a **instância de serviço do Google Speech to Text**.

1. Escolha o **Idioma** para a instância de serviço.

1. Insira suas credenciais de serviço Google Cloud Speech-to-Text, com um limite de até 3.072 caracteres.
  * É possível gerar suas credenciais de serviço no Google Cloud Platform como uma chave JSON ao [configurar uma conta de serviço ![ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). O exemplo de código a seguir contém os campos de credencial de amostra que você gera no Google Cloud Platform.

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

1. **Opcional** Selecione **Mostrar avançado** para inserir definições de configuração especiais definidas pelo Google em um formato JSON válido.
  O exemplo a seguir mostra as definições de configuração do Google para ativar um filtro de profanidade para uma instância em inglês dos EUA.
  ```json
  {
    "languageCode": "en-US",
    "profanityFilter": false
  }
  ```
  {: codeblock}

  Se você selecionar um idioma na configuração de serviço diferente do idioma definido em `languageCode`, o {{site.data.keyword.iva_short}} sobrescreverá a sua seleção com o idioma definido pela configuração `languageCode` do JSON.
  {: tip}

## Conectando-se ao Google Text-to-Speech por meio do {{site.data.keyword.iva_short}}
{: #tts_va}

Em vez de usar uma instância do {{site.data.keyword.texttospeechfull}}, é possível optar por conectar o agente de voz a um serviço de fala para texto de terceiro, como o [Google Cloud Text-to-Speech ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.google.com/text-to-speech/).

1. Navegue para a guia _Agentes de voz_ no painel _Gerenciar_ e selecione **Editar** um agente de voz existente ou **Criar novo agente de voz**.

1. Na configuração de serviço _Texto para fala_, escolha **Instância de serviço do Google Text-to-Speech**.

1. Escolha o **Idioma** e a **Voz** para a instância de serviço.

1. Insira suas credenciais de serviço Google Cloud Text-to-Speech, com um limite de até 3.072 caracteres.
  * É possível gerar suas credenciais de serviço no Google Cloud Platform como uma chave JSON ao [configurar uma conta de serviço ![ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). O exemplo de código a seguir contém os campos de credencial de amostra que você gera no Google Cloud Platform.

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

1. **Opcional** Selecione **Mostrar avançado** para inserir definições de configuração especiais definidas pelo Google em um formato JSON válido.
  O exemplo a seguir mostra as definições de configuração do Google para uma voz feminina falando alemão.

  Se você selecionar um idioma na configuração de serviço diferente do idioma definido em `languageCode`, o {{site.data.keyword.iva_short}} sobrescreverá a sua seleção com o idioma definido pela configuração `languageCode` do JSON.
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
