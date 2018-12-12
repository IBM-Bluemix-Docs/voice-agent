---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Creación de un agente de voz desde el panel de control _Gestionar_
{: #config_instance}

Después de crear su servicio {{site.data.keyword.iva_full}}, puede crear agentes de voz individuales desde el panel de control _Gestionar_.
{: shortdesc}


## Creación de un agente de voz
{: #create_instance}

Cuando crea un agente de voz, {{site.data.keyword.iva_short}} busca automáticamente las instancias de servicio de Watson disponibles que puede utilizar. Si un servicio no está disponible, puede crearlo junto con el agente de voz o conectarse a los servicios en otro espacio de cuenta de {{site.data.keyword.Bluemix_short}}. También puede conectar su agente de voz con una instancia de un motor de orquestación de servicios, Google Speech to Text o Google Text to Speech.

1. Vaya al separador _Agentes de voz_ del panel de control _Gestionar_ y pulse **Crear un agente de voz**.

1. Para **Nombre**, especifique un nombre exclusivo para el agente de voz. Por ejemplo, `Soporte al cliente - América del Norte`.

1. Para **Número de teléfono**, añada el número de su conexión troncal SIP, incluidos los códigos de país y de área. Por ejemplo, para un número 800 de Estados Unidos, especifique el número de teléfono como `18883334444`. El número de teléfono puede tener espacios y caracteres `+ ( ) -`.

1. Describa opcionalmente el agente de voz.

1. Si desea habilitar la transferencia de llamada, escriba el URI de terminación para su **Destino predeterminado de transferencia**. Consulte [Configuración de transferencia de llamada](call-transfer.html) para obtener información sobre cómo configurar un URI de terminación. No utilice un número de teléfono personal como destino de transferencia.

1. Configure las conexiones a sus instancias de servicio de Watson. Puede conectarse a varias instancias de servicio de Watson configurando las conexiones tanto para la **Ubicación 1** como para la **Ubicación 2**. Disponer de conexiones a varias instancias de servicio permite al agente de voz conmutar a una instancia de servicio alternativa si se produce una interrupción del servicio. Consulte [Adición de varias ubicaciones de servicio de Watson](managing_disaster_recovery.html#add_location).

1. En **{{site.data.keyword.conversationshort}}**, configure la conexión con su instancia de servicio de {{site.data.keyword.conversationshort}} pulsando **Ubicación 1** o **Ubicación 2** y habilitando la ubicación seleccionada. Puede utilizar instancias de {{site.data.keyword.conversationshort}} en cuentas de {{site.data.keyword.Bluemix_notm}} que posea usted u otra persona. También puede conectarse a cualquiera de estas opciones mediante un motor de orquestación de servicio.

   * Si está creando un agente de voz en las regiones de Dallas o de Washington DC y no tiene una instancia de servicio de {{site.data.keyword.conversationshort}}, puede crear una desde el menú **Instancia de servicio**.
   * Como alternativa, puede conectarse a otros orígenes de un diálogo de {{site.data.keyword.conversationshort}} o conectar con un SOE cambiando el [**Tipo de servicio**](managing_other.html#other_service).
   * Si desea configurar varias ubicaciones de servicio, pulse la opción de la otra ubicación y seleccione **Habilitar ubicación** para configurar la conexión a su otra instancia de {{site.data.keyword.conversationshort}}. Consulte [Adición de varias ubicaciones de servicio de Watson](managing_disaster_recovery.html#add_location).

1. En **{{site.data.keyword.speechtotextshort}}**, revise la configuración predeterminada de la instancia de servicio {{site.data.keyword.speechtotextshort}} seleccionando **Ubicación 1** o **Ubicación 2** y habilitando la ubicación. Puede personalizar la configuración con lo siguiente.
   * Para conectar el agente de voz a una instancia existente como **Tipo de servicio**, seleccione **Mi instancia de habla a texto**. Luego, para **Seleccionar tipo de modelo**, seleccione **Banda estrecha**, **Banda ancha** o **Banda estrecha y banda ancha** y luego seleccione el **Modelo** de idioma.
   * Si está creando un agente de voz en las regiones de Dallas o de Washington DC y no tiene una instancia de servicio de {{site.data.keyword.speechtotextshort}}, puede crear una desde el menú **Instancia de servicio**.
   * Para el **Tipo de servicio**, puede elegir [una instancia de {{site.data.keyword.speechtotextshort}} de otro espacio de trabajo de {{site.data.keyword.Bluemix_notm}}](managing_other.html) o un [servicio de habla a texto de terceros](managing_third_party.html), como Google Cloud Speech-to-Text.
   * Si desea configurar varias ubicaciones de servicio, pulse la opción de la otra ubicación y seleccione **Habilitar ubicación** para configurar la conexión a su otra instancia de {{site.data.keyword.speechtotextshort}}. Consulte [Adición de varias ubicaciones de servicio de Watson](managing_disaster_recovery.html).

1. En **{{site.data.keyword.texttospeechshort}}**, revise la configuración predeterminada de la instancia de servicio {{site.data.keyword.texttospeechshort}} pulsando **Ubicación 1** o **Ubicación 2** y habilitando la ubicación. Puede personalizar la configuración con lo siguiente.
   * Si está creando un agente de voz en las regiones de Dallas o de Washington DC y no tiene una instancia de servicio de {{site.data.keyword.texttospeechshort}}, puede crear una desde el menú **Instancia de servicio**.
   * Para el **Tipo de servicio**, puede seleccionar una [instancia de {{site.data.keyword.texttospeechshort}} de otro espacio de trabajo de {{site.data.keyword.Bluemix_notm}}](managing_other.html) o un [servicio de texto a habla de terceros](managing_third_party.html), como Google Cloud Text-to-Speech.
   * Si desea configurar varias ubicaciones de servicio, pulse la opción de la otra ubicación y seleccione **Habilitar ubicación** para configurar la conexión a su otra instancia de {{site.data.keyword.texttospeechshort}}. Consulte [Adición de varias ubicaciones de servicio de Watson](managing_disaster_recovery.html).

1. También puede optar por habilitar el reenvío de sucesos para recopilar información sobre las llamadas gestionadas por los agentes de voz en una {{site.data.keyword.cloudantfull}}. Consulte [Habilitación del reenvío de sucesos para agentes de voz](event-forwarding.html). Para ver más opciones de configuración, consulte [Configuración de un agente de voz](managing.html#configure_va).

1. Pulse **Crear agente de voz** para crear el agente de voz y los servicios nuevos.

Después de crear el agente de voz, pruebe su agente de voz llamando a su número de teléfono. Puede ver detalles sobre la llamada telefónica en el panel de control _Uso_.  
