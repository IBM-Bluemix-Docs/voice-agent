---

copyright:
  years: 2019
lastupdated: "2019-06-24"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Creación de un agente de SMS
{: #sms_config_instance}

Después de crear su servicio {{site.data.keyword.iva_full}}, puede crear agentes de sms individuales desde el panel de control _Gestionar_.
{: shortdesc}

1. Vaya al separador _Agentes de voz_ del panel de control _Gestionar_ y pulse **Crear un agente de voz**.

1. Para **Tipo de agente**, seleccione _SMS_.

1. Para **Nombre**, especifique un nombre exclusivo para el agente de voz. Por ejemplo, `Soporte al cliente - América del Norte`. El nombre puede tener hasta 64 caracteres.

1. Para Número de teléfono, añada el número de su conexión troncal SIP, incluidos los códigos de país y de área. Por ejemplo, para un número 800 de Estados Unidos, especifique el número de teléfono como 18883334444. El número de teléfono puede tener un máximo de 30 caracteres, incluidos los espacios y los caracteres + ( ). SMS solo da soporte a un número por usuario.

1. En **Proveedor de SMS**, escriba el nombre de usuario, la contraseña y el URL de API de su proveedor de SMS. Por ejemplo, si se utiliza _Twilio_, el nombre de usuario es su **SID de cuenta**, la contraseña es su **señal de autenticación** y el proveedor de SMS es `https://api.twilio.com`

1. En **Conversación**, configure la conexión con su instancia de servicio de {{site.data.keyword.conversationshort}}. Puede utilizar instancias de servicio {{site.data.keyword.conversationshort}} en cuentas de {{site.data.keyword.Bluemix_notm}} que posea usted u otra persona. También puede conectarse a cualquiera de estas opciones mediante un motor de orquestación de servicio (SOE).

   * Si está creando un agente de SMS en las regiones de Dallas o de Washington DC y no tiene una instancia de servicio de {{site.data.keyword.conversationshort}}, puede crear una desde el menú **Instancia de servicio**.
   * Como alternativa, puede conectarse a otros orígenes de un diálogo de {{site.data.keyword.conversationshort}} o conectar con un SOE cambiando el [**Tipo de servicio**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service).
   * Si desea configurar varias ubicaciones de servicio, pulse la opción de la otra ubicación y seleccione **Habilitar ubicación** para configurar la conexión a su otra instancia de {{site.data.keyword.conversationshort}}. Para obtener más información, consulte [Adición de varias ubicaciones de servicio Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).

1. Marque el recuadro **Iniciar conversación desde mensajes de entrada** para permitir que los usuarios inicien una sesión de SMS con el agente de SMS.

1. Marque el recuadro **Notificar el tiempo de espera de la sesión** para que el agente de SMS envíe un mensaje SMS al usuario que le avise de que el agente no ha recibido una respuesta en un tiempo y que se excederá el tiempo de espera. 

    - Consulte [Opciones avanzadas](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) para obtener más información acerca de las **Opciones avanzadas** disponibles para el agente de SMS, como por ejemplo el establecimiento de un periodo de tiempo personalizado tras el que la sesión excederá el tiempo de espera.
    - Marque el recuadro únicamente si desea que se le notifique cuando se excede el tiempo de espera de una sesión.

1. También puede optar por habilitar el reenvío de sucesos para recopilar información sobre las llamadas gestionadas por los agentes de voz en una {{site.data.keyword.cloudantfull}}. Para obtener más información, consulte [Habilitación del reenvío de sucesos para agentes de voz](/docs/services/voice-agent?topic=voice-agent-event_forwarding). Para ver más opciones de configuración, consulte [Configuración de un agente de voz](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1.  Pulse **Crear agente de voz** para crear el agente de SMS y los servicios nuevos.

1. Siga [las instrucciones](/docs/services/voice-agent?topic=voice-agent-connect-sms) para conectarse a un proveedor de SMS.

Después de crear el agente de SMS, pruebe el agente de SMS mediante el envío de mensajes de texto a su número de teléfono. Puede ver detalles sobre la interacción en el panel de control _Uso_. Consulte [Visualización de uso y de registros](/docs/services/voice-agent?topic=voice-agent-logging).

Para habilitar la mensajería de SMS entre los clientes y un agente de voz durante una llamada de voz, el número de SMS debe coincidir con el número de voz.
{: tip}

Antes de crear un agente de SMS o de añadir funcionalidad SMS a su agente de voz, **debe** tener configuradas las credenciales adecuadas y generar una clave de API para programar su número de SMS. Para obtener más información, consulte [Generación de una clave de API y configuración de credenciales](/docs/services/voice-agent?topic=voice-agent-connect-sms#sms_access).

También **debe** configurar la conexión troncal SIP para la funcionalidad de SMS. Consulte las instrucciones de su proveedor, por ejemplo Twilio. Si no tiene un número de teléfono de Twilio, consulte [Creación de una conexión troncal SIP de Twilio](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup).

Una vez que tenga un número de Twilio, tendrá que configurarlo para la funcionalidad de SMS. Para obtener más información, consulte [Configuración de Twilio for SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

Si tiene problemas para crear credenciales, póngase en contacto con el administrador de la instancia de servicio para que le otorgue el acceso de *Gestor* o de *Escritor*.
{: tip}

## Opciones avanzadas para agentes de SMS
{: #sms_advanced}

Pulse **Mostrar opciones avanzadas** después del campo **Número de teléfono**.

1. Establezca un valor de **Tiempo de espera de lectura de conversación** opcional. Es el tiempo, en segundos, que SMS Gateway espera una respuesta de Watson Assistant. Si se excede el tiempo, SMS Gateway vuelve a intentar ponerse en contacto con Watson Assistant. Si aun así no consigue acceder al servicio, el mensaje SMS/MMS falla. De forma predeterminada, el tiempo está establecido en 30 segundos.

1. Establezca un **Tiempo de espera de sesión** opcional. Es el tiempo, en segundos, después del cual la sesión caduca si SMS Gateway no recibe una respuesta del usuario.

1. Establezca un **Mensaje de respuesta de anomalía de conversación**. Es el mensaje de respuesta predeterminado que se envía si no se puede acceder a Watson Assistant. El valor predeterminado es `We're sorry, but we can't respond to your message.`.

### Configuración del agente de SMS para la terminación de la sesión
{: #sms_terminate}

El agente de SMS de {{site.data.keyword.iva_full}} termina una sesión en función del valor del tiempo de espera de la sesión, que se puede configurar y cuyo valor predeterminado es 30 segundos. 

También puede añadir un nodo al servicio {{site.data.keyword.conversationshort}} para que responda a un mandato de finalización de sesión del usuario. 

1. En el panel de control de {{site.data.keyword.Bluemix_notm}}, seleccione la instancia de {{site.data.keyword.conversationshort}} que utiliza el agente de voz.

1. Cree una **intención de terminar SMS** desde el panel de control. De forma alternativa, puede modificar una intención existente que ya utilice para el agente de voz, como por ejemplo _Finalizar la llamada_.

1. Añada un **nodo Terminar SMS** desde el panel de control.

1. En la sección _Si el asistente reconoce:_, añada la **intención Terminar SMS** que ha creado previamente.

1. Añada la respuesta al nodo. Copie y pegue el siguiente fragmento de código para sustituir el código que se muestra en el campo.

    ```json
        {
            "output": {
                 "text": {
                    "values": [
                        "Thank you for using the service. Goodbye!"
                    ],
                    "selection_policy”: “sequential"
                },
                "smsAction": {
                    "command": "terminateSession"
                }
            }
        }
    ```
    {: codeblock}

Después de crear el agente de voz, pruebe el agente de voz llamando o enviando un mensaje de texto a su número de teléfono en función de su tipo. Puede ver detalles sobre la interacción en el panel de control _Uso_. Consulte [Visualización de uso y de registros](/docs/services/voice-agent?topic=voice-agent-logging).
