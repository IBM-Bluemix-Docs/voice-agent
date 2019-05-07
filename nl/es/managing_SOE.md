---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Configuración de {{site.data.keyword.conversationshort}} con un motor de orquestación de servicios
{: #conversation_va}

Como alternativa a configurar una instancia de servicio de {{site.data.keyword.conversationshort}}, puede conectarse a un motor de orquestación de servicios (SOE).
{: shortdesc}

Puede conectar con un espacio de trabajo de {{site.data.keyword.conversationshort}} mediante un [motor de orquestación de servicios (SOE)](/docs/services/voice-agent?topic=voice-agent-about#arch-soe). Los SOE interceptan mensajes entrantes y salientes del servicio, de modo que pueda modificarlos mediante las API de terceros.

## Configuración de una conexión con un SOE
{: #how-to-SEO}

1. En el separador _Agente de voz_ de la página _Gestionar_ del agente de voz, vaya a la sección de configuración de {{site.data.keyword.conversationshort}}.

1. Seleccione **Motor de orquestación de servicios** como **Tipo de servicio**.

1. Seleccione la **Región** correspondiente a su **Tipo de servicio**.

1. En el campo **URL**, especifique el URL completo del espacio de trabajo del SOE, por ejemplo `https://iva-soesample.myorg.net/SOE/myWorkspace`. Para el URL se pueden especificar hasta 256 caracteres.

  **Importante**: Para la seguridad de datos, asegúrese de utilizar un URL seguro para el espacio de trabajo de SOE, utilizando `https:` en lugar de `http:`, y solicite autenticación. Consulte [Seguridad de información y privacidad de datos](/docs/services/voice-agent?topic=voice-agent-infosec) para obtener más información sobre las consideraciones de seguridad.

1. **Opcional** Si el SOE requiere autenticación (recomendado), especifique el nombre de usuario y la contraseña en los campos correspondientes, hasta 64 y 256 caracteres cada uno.
