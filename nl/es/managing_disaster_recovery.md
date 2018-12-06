---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configuración de varias ubicaciones de servicio
{: #disaster-recovery}

Puede conectar el agente de voz a varios servicios en ubicaciones distintas para añadir redundancia al servicio. La segunda ubicación no es un segundo agente de voz, solo actúa como copia de seguridad.
{: shortdesc}

Si utiliza un plan _Lite_ para la instancia del agente de voz, solo puede conectar su conexión troncal SIP a un punto final, en el que se crea la instancia del agente de voz. Puesto que el plan _Lite_ proporciona conexiones solo a una ubicación, puede proporcionar redundancias para los servicios conectados, pero no para el agente de voz. Si cae el servicio en la ubicación del agente de voz, las llamadas no se pueden dirigir a una ubicación secundaria.
{: tip}

## Adición de servicios redundantes
{: #add_redundant}

Puede añadir una ubicación de servicio de Watson o de un tercero a la configuración del agente de voz en cualquier momento editando el agente de voz.

1. Para añadir un servicio redundante a un agente de voz existente, vaya al separador _Agentes de voz_ en el panel de control _Gestionar_. Pulse **Editar agente** para el agente de voz que desea configurar.

1. Elija **Ubicación 1** o **Ubicación 2** para el servicio {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} o {{site.data.keyword.speechtotextshort}} que desea conectar y añada la información de configuración. Puede utilizar instancias de servicio de Watson o de terceros en su espacio de trabajo o en otros espacios de trabajo. Consulte [Utilización de instancias de servicio en otros espacios de trabajo de {{site.data.keyword.Bluemix_notm}}](managing_other.html).

**Recuerde**: Para añadir redundancia al servicio, debe utilizar instancias de servicio de Watson de distintas regiones para las distintas ubicaciones.

Puede habilitar o inhabilitar una ubicación utilizando el recuadro **Habilitar ubicación**. La **Ubicación 1** está habilitada de forma predeterminada y la **Ubicación 2** está inhabilitada de forma predeterminada. Debe estar habilitada al menos una ubicación para cada servicio de Watson.

## Adición de varias ubicaciones de servicio de Watson
{: #add_location}

Su agente de voz utiliza las instancias de servicio de Watson en orden de distancia geográfica. Por ejemplo, puede crear un agente de voz en la región Washington DC y crear sus servicios {{site.data.keyword.conversationshort}} en Dallas y en Sídney, Australia. El agente de voz utiliza la región Dallas de {{site.data.keyword.conversationshort}} porque está físicamente más cerca de Washington DC que Sídney. Al conectarse a servicios de Watson en varias regiones, si un servicio de Watson está fuera de línea en una ubicación, su agente de voz puede utilizar el servicio redundante.
