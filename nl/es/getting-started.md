---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

keywords: voice agent, creating a SIP trunk, creating and connecting your voice agent,

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Guía de aprendizaje de iniciación
{: #getting-started}
{{site.data.keyword.iva_full}} le permite integrar una serie de servicios orquestados de Watson con la red telefónica mediante el protocolo de iniciación de sesiones (SIP). Esta guía de aprendizaje describe cómo configurar un agente de voz cognitivo al que poder llamar desde cualquier teléfono.
{: shortdesc}

Vea una demostración de cómo crear su primer agente de voz en esta [guía de aprendizaje de {{site.data.keyword.iva_full_notm}}![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/).
{: tip}

Si necesita ayuda, póngase en contacto con nosotros en Slack en el equipo [IBM Cloud Technology ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) en el canal `#ibmvoicegateway`
{: tip}

## Antes de empezar
{: #prereqs}

Cree una nueva cuenta o inicie la sesión en una cuenta existente en [{{site.data.keyword.Bluemix_short}}](https://cloud.ibm.com/).

## Paso 1: Creación de una instancia de servicio de {{site.data.keyword.iva_short}} en {{site.data.keyword.Bluemix_notm}}
{: #step1}

Desde la [página del catálogo de {{site.data.keyword.iva_short}}](https://cloud.ibm.com/catalog/services/voice-agent-with-watson), revise la información de servicio y pulse **Crear**.

Después de crear el servicio, anote el punto final del agente de voz en el panel de control _Iniciación_. Necesita el URI SIP del punto final para configurar la conexión troncal SIP.

## Paso 2: Creación de una conexión troncal SIP para reenviar llamadas a {{site.data.keyword.iva_short}}
{: #step2}

1. Cree una conexión troncal SIP de cualquiera de los siguientes proveedores admitidos. A continuación, asocie un número de teléfono a su conexión troncal SIP.

  * [NetFoundry](/docs/services/voice-agent?topic=voice-agent-connect#NetFoundry-setup)
  * [Twilio](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup)
  * [AT&T y otros proveedores de conexión troncal SIP](/docs/services/voice-agent?topic=voice-agent-connect#att-other)
  * [Interconexión con {{site.data.keyword.iva_short}}](/docs/services/voice-agent?topic=voice-agent-connect#peering)

## Paso 3: Creación y conexión del agente de voz
{: #step3}

1. Vaya al panel de control _Gestionar_ en el panel de control de {{site.data.keyword.iva_short}} y pulse **Crear un agente de voz**.

2. Especifique los valores básicos del agente de voz:
  * **Nombre:** Un nombre exclusivo para el agente de voz, como `Soporte al cliente`
  * **Número de teléfono:** El número de teléfono completo que ha asociado con la conexión troncal SIP, incluidos los códigos de país y área. Por ejemplo, para un número 800 de Estados Unidos, especifique el número de teléfono como 18883334444. El número de teléfono puede tener espacios y caracteres + ( ) -.
  * **Descripción:** Una descripción opcional del uso
  * **Destino predeterminado de la transferencia:** Un URI de terminación opcional al que se pueden transferir las llamadas.

3. Cree las instancias de servicio de {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} y {{site.data.keyword.texttospeechshort}} para el agente de voz. Puede elegir crear un agente de voz con cualquiera de los siguientes métodos:
  * Pulse **Crear un agente de voz** para crear todos los servicios y un agente de voz con la configuración predeterminada en un solo paso.
  * O bien, pulse cada uno de los nombres de servicio para crear los servicios usted mismo. A continuación, vuelva a {{site.data.keyword.iva_short}} y cree un agente de voz por separado.

   Si ha creado manualmente una instancia de servicio de {{site.data.keyword.conversationshort}}, añada un diálogo para probar el agente de voz.  Para empezar rápidamente, clone la [conversación de ejemplo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) desde GitHub y luego [importe el ejemplo](/docs/conversation?topic=services/conversation-configuring-a-watson-assistant-workspace#creating-workspaces) como una habilidad:

   1. En la página de GitHub de la conversación de ejemplo, pulse el número de línea `1` y seleccione **... > Copiar línea**. Pegue el texto copiado en un archivo y guárdelo como archivo JSON, por ejemplo `voice-gateway-conversation-en.json`.
   2. Inicie la herramienta {{site.data.keyword.conversationshort}}. En la página _Habilidades_, pulse el icono ![Importar espacio de trabajo](../conversation/images/workspace_import.png) e importe el archivo JSON.

  De forma alternativa, puede [crear su propio diálogo](/docs/services/assistant?topic=assistant-getting-started#getting-started-build-dialog) para simular el entorno de producción. Como mínimo, el diálogo debe contener un nodo con la condición `conversation_start` y un nodo con una respuesta predeterminada.


## Pasos siguientes
{: #next-steps}

Pruebe el agente de voz llamando a su número de teléfono asociado. Si escucha una respuesta, significa que el agente de voz está activo.

Si no escucha una respuesta, puede examinar los registros de llamadas y el uso del agente de voz en el panel de control _Uso_. Consulte [Visualización de registros de uso y llamadas](/docs/services/voice-agent?topic=voice-agent-logging).

Puede editar los valores del agente de voz, crear o eliminar agentes de voz, y añadir varias ubicaciones de servicio de Watson al agente de voz desde el panel de control _Gestionar_. Para obtener más información, consulte [Gestión de agentes de voz](/docs/services/voice-agent?topic=voice-agent-managing).

También puede configurar los valores avanzados, como la protección de la conexión SIP desde su cuenta de Twilio. Consulte [Protección de las conexiones](/docs/services/voice-agent?topic=voice-agent-securing).
