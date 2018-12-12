---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Gestión de instancias de servicio y de agentes de voz
{: #managing}

Puede utilizar el panel de control _Gestionar_ para cambiar las configuraciones de instancias de servicio y para crear, editar, clonar, configurar o eliminar agentes de voz individuales. Puede tener varios agentes de voz en su instancia de servicio, pero cada agente de voz debe tener un nombre y un número de teléfono exclusivos.
{: shortdesc}

## Navegación por el panel de control del servicio Voice Agent
{: #navigate_manage}

Encontrará el panel de control _Gestionar_ en el panel de control de la cuenta de {{site.data.keyword.Bluemix_notm}}.

1. Vaya al [panel de control de su cuenta de {{site.data.keyword.Bluemix_notm}}](https://console.bluemix.net/dashboard/apps).

1. En la lista de **Servicios**, seleccione su instancia del servicio **Voice Agent** para abrir el panel de control de servicio en el separador _Gestionar_.

## Edición del número máximo de conexiones simultáneas para la instancia de servicio
{: #edit_service}

En todos los planes, puede recibir 2 conexiones simultáneas de forma gratuita. Si utiliza los planes _Estándar_ o _Premium_, puede [cambiar el número máximo de conexiones simultáneas](managing_concurrency.html) en los valores predeterminados del separador _Instancias_.

## Creación de un agente de voz
{: #create_va}

[Cree un nuevo agente de voz](managing_create.html) en el separador _Agentes de voz_ del panel de control _Gestionar_.

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

## Configuración de un agente de voz
{: #configure_va}

Cuando cree, clone o edite un agente de voz, puede realizar cambios en los valores de configuración del agente de voz y en las conexiones con los servicios relacionados.

* **[Configuración de varias ubicaciones de servicio](managing_disaster_recovery.html):** Incluya varias ubicaciones de servicios para que sus servicios conectados den soporte a la redundancia del servicio.
* **[Conexión con servicios de habla y de texto de terceros](managing_third_party.html):** En lugar de utilizar {{site.data.keyword.texttospeechshort}} o {{site.data.keyword.speechtotextshort}}, puede conectar su agente de voz a API de terceros, como por ejemplo Google Cloud Speech-to-Text.
* **[Utilización de servicios de otros espacios de trabajo de {{site.data.keyword.Bluemix_notm}}](managing_other.html):** puede configurar el agente de voz para que utilice instancias de servicio de {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.speechtotextshort}} que pertenecen a espacios de trabajo de otras cuentas de {{site.data.keyword.Bluemix_short}}.
* **[Configuración de Watson Assistant con un motor de orquestación de servicios](managing_SOE.html):** puede conectar con un espacio de trabajo de {{site.data.keyword.conversationshort}} a través de un motor de orquestación de servicios (SOE). Los SOE interceptan mensajes entrantes y salientes del servicio, de modo que pueda modificarlos mediante las API de terceros.
* **[Habilitación del reenvío de sucesos para agentes de voz](event-forwarding.html):** puede que desee recopilar y analizar los datos de llamada de {{site.data.keyword.iva_short}} para que la conversación resulte más natural para el interlocutor. Cada agente de voz que cree puede reenviar informes de sucesos a una {{site.data.keyword.cloudant_short_notm}} especificada que usted gestione.

## Configuración de opciones avanzadas de agente de voz
{: #config-advanced}

Al crear o clonar un agente de voz, puede pulsar **Mostrar avanzadas** para ver las siguientes opciones de configuración avanzadas.

* **Mensaje de respuesta de error de {{site.data.keyword.conversationshort}} (opcional)**: El mensaje de respuesta predeterminado que se envía al receptor del mensaje si la llamada no puede conectarse a {{site.data.keyword.conversationshort}}.
* **Mensaje de respuesta de error de transferencia (opcional)**: El mensaje de respuesta predeterminado que se transmite al interlocutor si falla la transferencia de la llamada.
* **Cabecera SIP INVITE personalizada (opcional)**: especifica una cabecera SIP personalizada para extraer de las solicitudes SIP INVITE entrantes
* **Enviar respuesta de tono de llamada provisional desde {{site.data.keyword.iva_short}}**: Envía una respuesta `180 llamando` mientras {{site.data.keyword.iva_short}} procesa una llamada entrante. Está habilitado de forma predeterminada.
* **Poner el interlocutor en espera durante la transferencia**: Pone el interlocutor en espera durante la transferencia. Está habilitado de forma predeterminada.
* **Desconectar la llamada si falla la transferencia**: Determina si se desconecta o no la llamada cuando falla la transferencia de una llamada.  Está habilitado de forma predeterminada. Si el valor está inhabilitado y falla la transferencia de una llamada, {{site.data.keyword.iva_short}} inicia un turno de conversación. A continuación, {{site.data.keyword.conversationshort}} puede desconectar la llamada o enviarla a otro destino, tal como esté configurado en el diálogo.
* **Notificar a {{site.data.keyword.conversationshort}} los sucesos de red**: Si habilita y se detecta un error de red, {{site.data.keyword.iva_short}} inicia un turno en el servicio {{site.data.keyword.conversationshort}} con el texto "vgwNetworkWarningMessage". La variable de estado `vgwNetworkWarnings` contiene una lista de los sucesos de red que se han producido durante el turno actual. Si se inhabilita, se envía una lista de los sucesos de red que han producido durante el turno actual en el siguiente suceso de turno en la variable de estado `vgwNetworkWarnings`. Está habilitado de forma predeterminada.
