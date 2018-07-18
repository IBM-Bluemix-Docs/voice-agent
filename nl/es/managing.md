---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-19"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Gestión de agentes de voz
{: #managing}

Puede crear, editar, clonar, configurar y eliminar agentes voz en el panel de control _Gestionar_. Puede tener varios agentes de voz, pero cada agente de voz debe tener un nombre y un número de teléfono exclusivos.
{: shortdesc}

<!-- Title should be task oriented and descriptive-->

## Creación de un agente de voz
{: #config_instance}

Cuando crea un agente de voz, {{site.data.keyword.iva_short}} busca automáticamente las instancias de servicio de Watson disponibles que puede utilizar. Si un servicio no está disponible, puede crearlo junto con el agente de voz o conectarse a los servicios en otro espacio de cuenta de {{site.data.keyword.Bluemix_short}}.

1. Pulse **Crear un agente de voz**.

1. Para **Nombre**, especifique un nombre exclusivo para el agente de voz. Por ejemplo, `Soporte al cliente - América del Norte`.

1. Para **Número de teléfono**, añada el número de su conexión troncal SIP, incluidos los códigos de país y de área. Por ejemplo, para un número 800 de Estados Unidos, especifique el número de teléfono como `18883334444`. El número de teléfono puede tener espacios y caracteres `+ ( ) -`.

1. Describa opcionalmente el agente de voz.

1. Si desea habilitar la transferencia de llamada, puede configurar un URI de terminación para su **Destino de transferencia**. Consulte [Configuración de transferencia de llamada](call-transfer.html). No utilice un número de teléfono personal como destino de transferencia.

1. Configure las conexiones a sus instancias de servicio de Watson. Puede conectarse a varias instancias de servicio de Watson configurando las conexiones tanto para la **Ubicación 1** como para la **Ubicación 2**. Disponer de conexiones a varias instancias de servicio permite al agente de voz conmutar a una instancia de servicio alternativa si se produce una interrupción del servicio. Consulte [Adición de varias ubicaciones de servicio de Watson](#add_location).

**Importante**: Las cuentas _Prueba_ y _Lite_ solo se pueden conectar a la ubicación donde se ha creado su instancia de servicio de {{site.data.keyword.iva_short}}. La segunda ubicación no es un segundo agente de voz. Solo es una ubicación de respaldo para la recuperación tras desastre.

1. En **{{site.data.keyword.conversationshort}}**, configure la conexión a su instancia de servicio de {{site.data.keyword.conversationshort}} pulsando **Habilitar ubicación 1** o **Habilitar ubicación 2**. Puede utilizar instancias de {{site.data.keyword.conversationshort}} o instancias de {{site.data.keyword.virtualagentfull}} en cuentas de {{site.data.keyword.Bluemix_notm}} que posee usted u otra persona. También puede conectarse a cualquiera de estas opciones mediante un motor de orquestación de servicio.

    * Si está creando un agente de voz en la región EE.UU. sur y no tiene una instancia de servicio de {{site.data.keyword.conversationshort}}, puede crear una desde el menú **Instancia de servicio**.
    * Como alternativa, puede conectarse a otros orígenes de un diálogo de {{site.data.keyword.conversationshort}} cambiando el [**Tipo de servicio**](#other_service).
    * Si desea configurar varias ubicaciones de servicio, pulse la opción de la otra ubicación y seleccione **Habilitar ubicación** para configurar la conexión a su otra instancia de {{site.data.keyword.conversationshort}}. Consulte [Adición de varias ubicaciones de servicio de Watson](#add_location).

1. En **{{site.data.keyword.speechtotextshort}}**, revise la configuración predeterminada para su instancia de servicio de {{site.data.keyword.speechtotextshort}} pulsando **Habilitar ubicación 1** o **Habilitar ubicación 2**. Si está creando un agente de voz en la región EE.UU. sur y no tiene una instancia de servicio de {{site.data.keyword.speechtotextshort}}, puede crear una desde el menú **Instancia de servicio**. O bien, puede conectar su agente de voz a una instancia de {{site.data.keyword.speechtotextshort}} en un espacio de cuenta diferente de {{site.data.keyword.Bluemix_notm}} cambiando el [**Tipo de servicio**](#other_service). {{site.data.keyword.iva_short}} sólo admite modelos de banda estrecha.

    Si desea configurar varias ubicaciones de servicio, pulse la opción de la otra ubicación y seleccione **Habilitar ubicación** para configurar la conexión a su otra instancia de {{site.data.keyword.speechtotextshort}}. Consulte [Adición de varias ubicaciones de servicio de Watson](#add_location).

1. En **{{site.data.keyword.texttospeechshort}}**, revise la configuración predeterminada para su instancia de servicio de {{site.data.keyword.texttospeechshort}} pulsando **Habilitar ubicación 1** o **Habilitar ubicación 2**. Si está creando un agente de voz en la región EE.UU. sur y no tiene una instancia de servicio de {{site.data.keyword.texttospeechshort}}, puede crear una desde el menú **Instancia de servicio**. O bien, puede conectar su agente de voz a una instancia de {{site.data.keyword.texttospeechshort}} en un espacio de cuenta diferente de {{site.data.keyword.Bluemix_notm}} cambiando el [**Tipo de servicio**](#other_service).

    Si desea configurar varias ubicaciones de servicio, pulse la opción de la otra ubicación y seleccione **Habilitar ubicación** para configurar la conexión a su otra instancia de {{site.data.keyword.texttospeechshort}}. Consulte [Adición de varias ubicaciones de servicio de Watson](#add_location).

1. También puede optar por habilitar el reenvío de sucesos para recopilar información sobre las llamadas gestionadas por los agentes de voz en una {{site.data.keyword.cloudantfull}}. Consulte [Habilitación del reenvío de sucesos para agentes de voz](event-forwarding.html). Para ver más opciones de configuración, consulte [Configuración de un agente de voz](#configure_va).

1. Pulse **Crear agente de voz** para crear el agente de voz y los servicios nuevos.

Después de crear el agente de voz, pruebe su agente de voz llamando a su número de teléfono. Puede ver detalles sobre la llamada telefónica en el panel de control _Uso_.  

## Edición del número máximo de conexiones simultáneas
{: #edit_concurrency}

Si utiliza el plan _Estándar_, puede cambiar el número máximo de conexiones simultáneas en los valores predeterminados. En todos los planes, puede recibir 2 conexiones simultáneas de forma gratuita. Para obtener más información, consulte [Planes de tarifas](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

En el panel de control _Gestionar_, puede ver el número máximo de conexiones simultáneas permitidas en el plan listado en **Número máximo de conexiones simultáneas**. También puede ver el número máximo de conexiones simultáneas utilizado por los agentes de voz en el mes actual en **Número máximo de conexiones simultáneas utilizado**.

Si desea cambiar el número máximo de conexiones simultáneas de su plan, pulse el icono **Editar**. En la ventana _Editar número máximo de conexiones simultáneas_, elija el número máximo de conexiones simultáneas y pulse **Guardar**. El número mínimo de conexiones simultáneas que puede establecer mediante autoservicio es 10 y el máximo es 50. Si necesita más de 50 conexiones simultáneas para su agente de voz, consulte [Solicitud de configuración de red asistida](connect-SIP.html#request-setup).

### Información sobre precios de conexiones simultáneas
{: #concurrent-charge}

  * Los planes _Lite_, _Prueba_ y _Estándar_ incluyen 2 conexiones simultáneas de forma gratuita.
  * Los planes _Premium_ están personalizados por instancia.
  * En una cuenta _Estándar_, tiene una capacidad mínima de 10 conexiones simultáneas.
  * El uso de conexiones simultáneas se prorratea por mes. Si utiliza más de 2 conexiones simultáneas en un día, se le facturará una tarifa diaria.
  * Si tiene un plan _Estándar_ o _Premium_, puede adquirir una mayor capacidad de conexiones simultáneas.
  * Se le facturará una tarifa diaria para la capacidad de conexiones simultáneas máxima que utilice en un día. Por ejemplo, su plan admite 2 conexiones simultáneas gratuitas y ha establecido un límite máximo de 12 conexiones. Si solo utiliza 5 conexiones en un día, se le facturarán 3.

Para obtener más información sobre planes, tarifas y características, consulte [Planes de tarifas](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

## Edición de un agente de voz
{: #edit_va}

Puede cambiar los agentes de voz existentes editándolos. Para editar un agente de voz, pulse **Editar agente** en la lista de opciones del agente de voz. Cambie la configuración y guarde los cambios.

## Clonación de un agente de voz
{: #clone_va}

Cuando clona un agente de voz, se copian todas las configuraciones de los servicios de Watson en un nuevo agente. Para clonar un agente de voz, pulse **Clonar agente** en la lista de opciones para el agente de voz. Proporcione al agente de voz un nombre y un número de teléfono exclusivos, cambie las opciones de configuración como sea necesario y guarde los cambios.

## Supresión de un agente de voz
{: #delete_va}

Puede que desee suprimir un agente de voz para liberar el número de teléfono. Sólo puede tener un agente de voz para un número de teléfono. Para utilizar un número de teléfono para un agente de voz diferente, primero debe suprimir cualquier agente de voz que utilice el número de teléfono.

Para suprimir un agente de voz, pulse **Suprimir agente** en la lista de opciones del agente de voz y guarde los cambios. El agente de voz se elimina de la lista de agentes de voz.

## Configuración de un agente de voz
{: #configure_va}

### Configuración de opciones avanzadas
{: #config-advanced}

Al crear o clonar un agente de voz, puede pulsar **Mostrar avanzadas** para ver las siguientes opciones de configuración avanzadas.

* **Mensaje de respuesta de error de {{site.data.keyword.conversationshort}} (opcional)**: El mensaje de respuesta predeterminado que se envía al receptor del mensaje si la llamada no puede conectarse a {{site.data.keyword.conversationshort}}.
* **Mensaje de respuesta de error de transferencia (opcional)**: El mensaje de respuesta predeterminado que se transmite al interlocutor si falla la transferencia de la llamada.
* **Enviar respuesta de tono de llamada provisional desde {{site.data.keyword.iva_short}}**: Envía una respuesta `180 llamando` mientras {{site.data.keyword.iva_short}} procesa una llamada entrante. Está habilitado de forma predeterminada.
* **Poner el interlocutor en espera durante la transferencia**: Pone el interlocutor en espera durante la transferencia. Está habilitado de forma predeterminada.
* **Desconectar la llamada si falla la transferencia**: Determina si se desconecta o no la llamada cuando falla la transferencia de una llamada.  Está habilitado de forma predeterminada. Si el valor está inhabilitado y falla la transferencia de una llamada, {{site.data.keyword.iva_short}} inicia un turno de conversación. A continuación, {{site.data.keyword.conversationshort}} puede desconectar la llamada o enviarla a otro destino, tal como esté configurado en el diálogo.
* **Notificar a {{site.data.keyword.conversationshort}} los sucesos de red**: Si habilita y se detecta un error de red, {{site.data.keyword.iva_short}} inicia un turno en el servicio {{site.data.keyword.conversationshort}} con el texto "vgwNetworkWarningMessage". La variable de estado `vgwNetworkWarnings` contiene una lista de los sucesos de red que se han producido durante el turno actual. Si se inhabilita, se envía una lista de los sucesos de red que han producido durante el turno actual en el siguiente suceso de turno en la variable de estado `vgwNetworkWarnings`. Está habilitado de forma predeterminada.

### Adición de varias ubicaciones de servicio de Watson
{: #add_location}

Si tiene una cuenta _Estándar_ o _Premium_, puede conectar el agente de voz a varios servicios de Watson en ubicaciones distintas para añadir redundancia al servicio. Las cuentas _Prueba_ y _Lite_ solo se pueden conectar a la ubicación donde se ha creado su instancia de servicio de {{site.data.keyword.iva_short}}. La segunda ubicación no es un segundo agente de voz. Solo es una ubicación de respaldo para la recuperación tras desastre.

Su agente de voz utiliza las instancias de servicio de Watson en orden de distancia geográfica. Por ejemplo, puede crear un agente de voz en la región EE.UU. este y crear sus servicios {{site.data.keyword.conversationshort}} en EE.UU. sur y Sídney, Australia. El agente de voz utiliza la región EE.UU. sur de {{site.data.keyword.conversationshort}} porque es geográficamente más cercana a EE.UU. este que a Sídney. Al conectarse a servicios de Watson en varias regiones, si un servicio de Watson está fuera de línea en una ubicación, su agente de voz puede utilizar el servicio redundante.

Puede añadir una ubicación de servicio de Watson a la configuración del agente de voz en cualquier momento. Para obtener información sobre cómo conectarse a varias instancias de ubicación de servicio al crear el agente de voz, consulte [Creación de un agente de voz](#creating).

Para añadir una ubicación de servicio de Watson a un agente de voz existente, pulse **Editar agente** para el agente de voz que desea configurar. Elija **Ubicación 1** o **Ubicación 2** para la instancia de {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} o {{site.data.keyword.speechtotextshort}} que desea conectar y añada la información de configuración. Puede utilizar una instancia de servicio de Watson de su espacio de trabajo o de otros espacios de trabajo. Consulte [Utilización de instancias de servicio en otros espacios de trabajo de {{site.data.keyword.Bluemix_notm}}](#other_services).

**Recuerde**: Para añadir redundancia al servicio, debe utilizar instancias de servicio de Watson de distintas regiones para las distintas ubicaciones.

Puede habilitar o inhabilitar una ubicación utilizando el recuadro **Habilitar ubicación**. La **Ubicación 1** está habilitada de forma predeterminada y la **Ubicación 2** está inhabilitada de forma predeterminada. Debe estar habilitada al menos una ubicación para cada servicio de Watson.

### Utilización de instancias de servicio en otros espacios de trabajo de {{site.data.keyword.Bluemix_notm}}
{: #other_service}

Puede configurar el agente de voz para utilizar instancias de servicio de {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.speechtotextshort}} que pertenecen a espacios de trabajo de otras cuentas de {{site.data.keyword.Bluemix_short}}. Para conectar su agente de voz a otras instancias de servicio, puede utilizar las credenciales de nombre de usuario y contraseña o una clave de API para sus instancias de servicio.

1. Seleccione el **Tipo de servicio** y la **Región**.

1. Elija **Nombre de usuario y contraseña** o **Clave de API** y escriba sus credenciales de servicio.
  Para encontrar estos valores, vaya a la instancia de servicio que desea configurar, seleccione **Credenciales de servicio** y luego **Ver credenciales**.

  * **Nombre de usuario y contraseña**: En los campos **URL**, **Nombre de usuario** y **Contraseña**, configure las credenciales para las instancias de servicio de {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.texttospeechshort}}.
  * **Clave de API**: En los campos **URL** y **Clave de API**, configure las credenciales para las instancias de servicio de {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.texttospeechshort}}.

  Las credenciales no son el nombre de usuario y la contraseña de {{site.data.keyword.Bluemix_notm}}, sino las credenciales cifradas para la instancia de servicio específica.
  {:tip}

1. Especifique la información de su instancia de servicio.

  * **{{site.data.keyword.conversationshort}}:** En el campo **ID de espacio de trabajo**, escriba el ID del espacio de trabajo que desea utilizar con el agente de voz. Para encontrar el ID de espacio de trabajo, inicie la herramienta y, en el espacio de trabajo que desea integrar, pulse el icono Acciones (**&vellip;**) y seleccione **Ver detalles**.

  * **{{site.data.keyword.speechtotextshort}}:** En el campo **Modelo**, seleccione el idioma del habla y el formato del servicio. {{site.data.keyword.iva_short}} sólo admite modelos de banda estrecha.

  * **{{site.data.keyword.texttospeechshort}}:** En el campo **Voz**, seleccione el idioma y la voz que utiliza el servicio. Debe especificar una voz para el servicio.

**Recuerde:** Para que el agente de voz funcione, debe configurar {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} y {{site.data.keyword.texttospeechshort}} para el mismo idioma. Consulte [Idiomas admitidos](about.html#supported-languages).

### Configuración de {{site.data.keyword.conversationshort}} para el agente de voz
{: #conversation_va}

Como alternativa a configurar una instancia de servicio de {{site.data.keyword.conversationshort}}, puede conectarse a un motor de orquestación de servicio (SOE) o Watson {{site.data.keyword.virtualagentshort}}.

* **Motor de orquestación de servicio**: Conéctese a un espacio de trabajo de {{site.data.keyword.conversationshort}} o a {{site.data.keyword.virtualagentshort}} mediante un [motor de orquestación de servicio (SOE)](about.html#arch-soe). Los SOE interceptan mensajes entrantes y salientes del servicio, de modo que pueda modificarlos mediante las API de terceros.

  En el campo **URL**, especifique el URL completo del espacio de trabajo del SOE, por ejemplo `https://iva-soesample.myorg.net/SOE/myWorkspace`. Si el SOE requiere autenticación (recomendado), especifique el nombre de usuario y la contraseña en los campos correspondientes.

* **Watson {{site.data.keyword.virtualagentshort}}**: Conéctese a un chatbot de {{site.data.keyword.virtualagentshort}} en lugar de a un espacio de trabajo de {{site.data.keyword.conversationshort}}. [{{site.data.keyword.virtualagentshort}}](../virtual-agent/getting-started.html#getting-started) se basa en el servicio {{site.data.keyword.conversationshort}} pero ofrece funciones preentrenadas, de forma que pueda empezar a trabajar sin necesidad de tener experiencia en aprendizaje automático.

  En el campo **URL**, especifique la credencial de URL de {{site.data.keyword.virtualagentshort}}, como `https://api.ibm.com/virtualagent/run/api`. Para los campos **ID de cliente** y **Secreto de cliente**, escriba las claves de autenticación, que se correlacionan con los campos de cabecera `X-IBM-Client-Id` y `X-IBM-Client-Secret` para llamadas de API. En el campo **ID de bot**, escriba el ID del bot que desea utilizar para este agente de voz. Para obtener más información sobre cómo encontrar estos valores, consulte [Publicación del agente](../virtual-agent/publish.html) en la documentación de {{site.data.keyword.virtualagentshort}}.
