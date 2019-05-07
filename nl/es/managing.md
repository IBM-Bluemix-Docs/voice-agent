---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Gestión de instancias de servicio y de agentes de voz
{: #managing}

Puede utilizar el panel de control _Gestionar_ para cambiar las configuraciones de instancias de servicio y para crear, editar, clonar, configurar o eliminar agentes de voz individuales. Puede tener varios agentes de voz en su instancia de servicio, y cada uno de ellos puede tener hasta 1000 números y descripciones exclusivos. No obstante, cada agente de voz debe tener un nombre exclusivo y al menos un número de teléfono.

* **NOTA**: Una instancia de servicio única de {{site.data.keyword.iva_full}} puede tener hasta 150 agentes de voz.
{: shortdesc}

## Navegación por el panel de control del servicio Voice Agent
{: #navigate_manage}

Encontrará el panel de control _Gestionar_ en el panel de control del servicio de {{site.data.keyword.iva_short}}.

1. Vaya a la [lista de recursos de su cuenta de {{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/resources).

1. En la lista de **Servicios**, seleccione su instancia del servicio **Voice Agent** para abrir el panel de control de servicio en el separador _Gestionar_.

## Resumen de agente de voz
{: #agent_summary}

Si ya tiene un agente de voz, puede ver un resumen de todos los números, descripciones y valores de configuración del agente. Para ver el resumen, pulse en el botón de flecha desplegable que está a la izquierda del **Nombre** del agente de voz. Se desplegará el resumen.

Aunque el agente de voz puede tener varios números, en el resumen solo se muestra el **Número principal**. De forma predeterminada, es el primer número añadido al agente de voz, y solo por motivos de visualización; no tiene valor práctico funcional. Si quiere mostrar otro número del agente de voz, consulte [Gestión de varios números](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

Puede ver todos los números del agente de voz en el resumen del agente. Tras desplegar el resumen de la configuración, haga clic en el botón **Ver números**, y aparecerá una lista de números en un nuevo recuadro de diálogo **Gestionar**. Consulte la página [Gestionar varios números](/docs/services/voice-agent?topic=voice-agent-multi_num) para obtener más información sobre cómo trabajar con el recuadro de diálogo **Gestionar**.

## Edición del número máximo de conexiones simultáneas para la instancia de servicio
{: #edit_service}

En todos los planes, puede recibir 2 conexiones simultáneas de forma gratuita. Si utiliza los planes _Estándar_ o _Premium_, puede [cambiar el número máximo de conexiones simultáneas](/docs/services/voice-agent?topic=voice-agent-edit_concurrency) en los valores predeterminados del separador _Instancias_.

## Creación de un agente de voz
{: #create_va}

[Cree un nuevo agente de voz](/docs/services/voice-agent?topic=voice-agent-config_instance) en el separador _Agentes de voz_ del panel de control _Gestionar_.

## Edición de un agente de voz
{: #edit_va}

Puede cambiar los agentes de voz existentes editándolos en el separador _Agentes de voz_ en el panel de control _Gestionar_. Para editar un agente de voz, pulse **Editar agente** en la lista de opciones del agente de voz. Cambie la configuración y guarde los cambios.

## Clonación de un agente de voz
{: #clone_va}

Cuando clona un agente de voz, se copian todas las configuraciones de los servicios de Watson en un nuevo agente. Para clonar un agente de voz, pulse **Clonar agente** en la lista de opciones para el agente de voz. Proporcione al agente de voz un nombre y un número de teléfono exclusivos, cambie las opciones de configuración como sea necesario y guarde los cambios.

## Supresión de un agente de voz
{: #delete_va}

Puede que desee suprimir un agente de voz para liberar el número de teléfono. Solo puede tener un agente de voz por número de teléfono. Para utilizar un número de teléfono para un agente de voz diferente, primero debe suprimir cualquier agente de voz que utilice el número de teléfono.

Para suprimir un agente de voz, vaya al separador _Agentes de voz_, pulse **Suprimir agente** en la lista de opciones del agente de voz y guarde los cambios. El agente de voz se elimina de la lista de agentes de voz.

## Buscar un agente de voz por Número o por Descripción
{: #search}

Puede buscar agentes de voz en los números o descripciones guardados en el agente.

En la barra _Buscar_, puede escribir un número o descripción. A medida que escriba, los resultados de búsqueda se actualizan automáticamente.  

## Configuración de un agente de voz
{: #configure_va}

Cuando cree, clone o edite un agente de voz, puede realizar cambios en los valores de configuración del agente de voz y en las conexiones con los servicios relacionados.

* **[Configuración de varios números de teléfono](/docs/services/voice-agent?topic=voice-agent-multi_num):** Puede configurar su agente de voz para que incluya varios números de teléfono.
* **[Configuración de varias ubicaciones de servicio](/docs/services/voice-agent?topic=voice-agent-disaster-recovery):** Incluya varias ubicaciones de servicios para que sus servicios conectados den soporte a la redundancia del servicio.
* **[Conexión con servicios de habla y de texto de terceros](/docs/services/voice-agent?topic=voice-agent-third-party):** En lugar de utilizar {{site.data.keyword.texttospeechshort}} o {{site.data.keyword.speechtotextshort}}, puede conectar su agente de voz a API de terceros, como por ejemplo Google Cloud Speech-to-Text.
* **[Utilización de servicios de otros espacios de trabajo de {{site.data.keyword.Bluemix_notm}}](/docs/services/voice-agent?topic=voice-agent-other_service):** puede configurar el agente de voz para que utilice instancias de servicio de {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.speechtotextshort}} que pertenecen a espacios de trabajo de otras cuentas de {{site.data.keyword.Bluemix_short}}.
* **[Configuración de Watson Assistant con un motor de orquestación de servicios](/docs/services/voice-agent?topic=voice-agent-conversation_va):** puede conectar con una habilidad de {{site.data.keyword.conversationshort}} a través de un motor de orquestación de servicios (SOE). Los SOE interceptan mensajes entrantes y salientes del servicio, de modo que pueda modificarlos mediante las API de terceros.
* **[Habilitación del reenvío de sucesos para agentes de voz](/docs/services/voice-agent?topic=voice-agent-event_forwarding):** puede que desee recopilar y analizar los datos de llamada de {{site.data.keyword.iva_short}} para que la conversación resulte más natural para el interlocutor. Cada agente de voz que cree puede reenviar informes de sucesos a una {{site.data.keyword.cloudant_short_notm}} especificada que usted gestione.

## Configuración de opciones avanzadas de agente de voz
{: #config-advanced}

Al crear o clonar un agente de voz, puede pulsar **Mostrar avanzadas** para ver las siguientes opciones de configuración avanzadas.

* **Tiempo excedido de lectura de conversación (opcional)**: Esta opción establece el tiempo, en segundos, que el agente de voz espera para la respuesta de Watson Assistant. Si se sobrepasa el tiempo, el agente de voz vuelve a intentar ponerse en contacto con Watson Assistant. Si aun así no consigue ponerse en contacto con el servicio, la llamada falla. De forma predeterminada, se establece en 5 segundos.
* **Mensaje de respuesta de error de {{site.data.keyword.conversationshort}} (opcional)**: El mensaje de respuesta predeterminado que se envía al receptor del mensaje si la llamada no puede conectarse a {{site.data.keyword.conversationshort}}. Puede especificar hasta 1024 caracteres.
* **Mensaje de respuesta de error de transferencia (opcional)**: El mensaje de respuesta predeterminado que se transmite al interlocutor si falla la transferencia de la llamada. Puede especificar hasta 1024 caracteres.
* **Cabecera SIP INVITE personalizada (opcional)**: especifica una cabecera SIP personalizada para extraer de las solicitudes SIP INVITE entrantes. Puede especificar hasta 1024 caracteres.
* **Enviar respuesta de tono de llamada provisional desde {{site.data.keyword.iva_short}}**: Envía una respuesta `180 llamando` mientras {{site.data.keyword.iva_short}} procesa una llamada entrante. Está habilitado de forma predeterminada.
* **Poner el interlocutor en espera durante la transferencia**: Pone el interlocutor en espera durante la transferencia. Está habilitado de forma predeterminada.
* **Desconectar la llamada si falla la transferencia**: Determina si se desconecta o no la llamada cuando falla la transferencia de una llamada.  Está habilitado de forma predeterminada. Si el valor está inhabilitado y falla la transferencia de una llamada, {{site.data.keyword.iva_short}} inicia un turno de conversación. A continuación, {{site.data.keyword.conversationshort}} puede desconectar la llamada o enviarla a otro destino, tal como esté configurado en el diálogo.
* **Notificar a {{site.data.keyword.conversationshort}} los sucesos de red**: Si habilita y se detecta un error de red, {{site.data.keyword.iva_short}} inicia un turno en el servicio {{site.data.keyword.conversationshort}} con el texto "vgwNetworkWarningMessage". La variable de estado `vgwNetworkWarnings` contiene una lista de los sucesos de red que se han producido durante el turno actual. Si se inhabilita, se envía una lista de los sucesos de red que han producido durante el turno actual en el siguiente suceso de turno en la variable de estado `vgwNetworkWarnings`. Está habilitado de forma predeterminada.
