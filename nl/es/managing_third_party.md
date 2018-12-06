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


# Conexión con servicios de habla y texto de terceros
{: #third-party}

Puede conectar servicios de habla y texto de terceros cuando cree, clone o edite su agente de voz en el panel de control _Gestionar_.
{: shortdesc}

Como alternativa, para configurar las conexiones del servicio de habla y texto al momento, puede [utilizar una configuración dinámica con {{site.data.keyword.conversationshort}}](api_dynamic_config.html). Esto le permite cambiar la configuración del agente de voz con etiquetas de acción y variables de estado.

## Conexión de Google Speech-to-Text desde {{site.data.keyword.iva_short}}
{: #stt_va}

En lugar de utilizar una instancia de {{site.data.keyword.speechtotextfull}}, puede conectar el agente de voz a un servicio de habla a texto de terceros, como [Google Cloud Speech-to-Text ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.google.com/speech-to-text/).

1. Vaya al separador _Agentes de voz_ del panel de control _Gestionar_ y seleccione **Editar** un agente de voz existente o **Crear nuevo agente de voz**.

1. En la configuración del servicio _Speech to Text_, elija **Instancia de servicio Google Speech to Text**.

1. Elija el **Idioma** de la instancia del servicio.

1. Escriba sus credenciales del servicio Google Cloud Speech-to-Text.
  * Puede generar sus credenciales de servicio en la plataforma Google Cloud Platform como una clave JSON al [configurar una cuenta de servicio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). El siguiente ejemplo de código contiene los campos de credenciales de ejemplo que se generan en Google Cloud Platform.

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

1. **Opcional** seleccione **Mostrar opciones avanzadas** para especificar valores especiales de configuración definidos por Google en un formato JSON válido.
  En el siguiente ejemplo se muestran los valores de configuración de Google para habilitar un filtro de lenguaje obsceno para una instancia en inglés de EE.UU.
  ```json
  {
    "languageCode": "en-US",
    "profanityFilter": false
  }
  ```
  {: codeblock}

  Si selecciona un idioma en la configuración del servicio distinto del idioma que ha definido en `languageCode`, {{site.data.keyword.iva_short}} sobrescribe su selección con el idioma definido en la configuración JSON `languageCode`.
  {: tip}

## Conexión de Google Text-to-Speech desde {{site.data.keyword.iva_short}}
{: #tts_va}

En lugar de utilizar una instancia de {{site.data.keyword.texttospeechfull}}, puede conectar el agente de voz a un servicio de habla a texto de terceros, como [Google Cloud Text-to-Speech ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.google.com/text-to-speech/).

1. Vaya al separador _Agentes de voz_ del panel de control _Gestionar_ y seleccione **Editar** un agente de voz existente o **Crear nuevo agente de voz**.

1. En la configuración del servicio _Texto a habla_, seleccione **Instancia de servicio de Google Text to Speech**.

1. Elija el **Idioma** y la **Voz** para la instancia de servicio.

1. Especifique sus credenciales del servicio Google Cloud Text-to-Speech.
  * Puede generar sus credenciales de servicio en la plataforma Google Cloud Platform como una clave JSON al [configurar una cuenta de servicio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account). El siguiente ejemplo de código contiene los campos de credenciales de ejemplo que se generan en Google Cloud Platform.

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

1. **Opcional** seleccione **Mostrar opciones avanzadas** para especificar valores especiales de configuración definidos por Google en un formato JSON válido.
  En el siguiente ejemplo se muestran los valores de configuración de Google para una voz femenina que habla en alemán.

  Si selecciona un idioma en la configuración del servicio distinto del idioma que ha definido en `languageCode`, {{site.data.keyword.iva_short}} sobrescribe su selección con el idioma definido en la configuración JSON `languageCode`.
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
