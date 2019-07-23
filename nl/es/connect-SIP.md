---

copyright:
  years: 2019
lastupdated: "2019-02-15"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Conexión a una conexión troncal SIP
{: #connect}

Puede elegir de la siguiente lista el proveedor de la conexión troncal SIP que utiliza para la integración con {{site.data.keyword.iva_full}}.
{: #shortdesc}

* [Nexmo](#nexmo-setup)
* [NetFoundry](#NetFoundry-setup)
* [Twilio](#twilio-setup)
* [Voximplant](#voximplant-setup)
* [Interconexión con {{site.data.keyword.iva_short}}](#peering)
* [AT&T y otros proveedores](#att-other)
* [Solicitud de configuración asistida](#request-setup)

## Creación de una aplicación de voz Nexmo
{: #nexmo-setup}

  **Nota:** Para crear una [cuenta de Nexmo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://dashboard.nexmo.com/sign-up){: new_window}, es necesaria una tarjeta de crédito, a la que se facturará periódicamente en función del uso de la conexión troncal SIP que configure. Si ya tiene una cuenta de Nexmo, puede utilizar la cuenta existente.

  1. Cree una cuenta de Nexmo en el [sitio web de Nexmo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://dashboard.nexmo.com/sign-up){: new_window}.

  1. Siga las instrucciones del README en el repositorio github de Nexmo [ ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/nexmo-community/watson-voice-agent){: new_window}. El repositorio github contiene una muestra de iniciación.

  1. Una vez que su número de teléfono Nexmo esté aprovisionado y su aplicación se esté ejecutando, configure su Agente de Voz con el número de teléfono Nexmo.

  1. Pruebe su configuración llamando a su número de teléfono Nexmo.


## Creación de una conexión troncal SIP de NetFoundry y número de teléfono
{: #NetFoundry-setup}

**Nota:** Para crear una cuenta es necesaria una tarjeta de crédito, a la que se facturará periódicamente en función de su uso. Si ya tiene una cuenta de NetFoundry, puede utilizar la cuenta existente.

1. Cree una cuenta en el sitio web de [NetFoundry![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson.netfoundry.io/watson-login){: new_window}.

1. Vaya a la página principal de la _cuenta de Watson_.

1. Seleccione la región de donde desea que sea el número.

  **Nota:** Consulte el sitio web de Netfoundry para ver las regiones disponibles. Continuamente se están añadiendo nuevas regiones.

1. Pulse **Adquirir** y siga las instrucciones en pantalla para completar la compra.

1. Una vez que el pago se haya procesado correctamente, su número de teléfono de conexión troncal SIP se muestra en la cuenta.

Necesita este número de teléfono para configurar el agente de voz y la transferencia de llamada, incluidos los códigos de área y país. Consulte [Creación y conexión del agente de voz](/docs/services/voice-agent?topic=voice-agent-getting-started#step3).


## Creación de una conexión troncal SIP de Twilio
{: #twilio-setup}

**Nota:** Para crear una [cuenta de Twilio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.twilio.com/try-twilio){: new_window}, es necesaria una tarjeta de crédito, a la que se facturará periódicamente en función del uso de la conexión troncal SIP que configure. Si ya tiene una cuenta de Twilio, puede utilizar la cuenta existente.

  1. Cree una cuenta de Twilio en el [sitio web de Twilio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.twilio.com/try-twilio){: new_window}.

  1. Cree una conexión troncal SIP con la cuenta de Twilio.

  1. En el sitio web de Twilio, vaya al panel de control Conexiones troncales Elastic SIP.

  1. Seleccione **Conexiones troncales** desde la barra de navegación y cree una conexión troncal SIP. Si ya tiene una conexión troncal SIP, pulse el icono **+**. En el recuadro de diálogo resultante, especifique un nombre para la conexión troncal SIP y pulse **Crear**.

  1. En la página Conexiones troncales Elastic SIP, seleccione la conexión troncal SIP.

  1. Seleccione **Origen** desde la barra de navegación para la conexión troncal SIP y configure el URI SIP de origen. Puede incluir varios nombres de host para evitar anomalías de servicio seleccionando el icono **+**.

  La dirección IP o el nombre de host es el valor que ha anotado en el panel de control _Iniciación_ de la instancia de servicio de {{site.data.keyword.iva_short}}. Cuando configure el URI de origen, debe estar en formato URI SIP, como `sip:us-south.voiceagent.cloud.ibm.com/`. Al incluir varios nombres de host o direcciones IP, si el punto final del primer host falla o está fuera de servicio, el proveedor de conexiones troncales SIP dirige las llamadas al siguiente nombre de host de la lista.

  1. Seleccione **Números** desde la barra de navegación de la conexión troncal SIP. A continuación, cree un número de teléfono y asígnelo a la conexión troncal SIP.

  En la página Números, pulse **Comprar un número** o, si ya tiene uno, pulse el icono **+**. Un panel muestra dónde puede suministrar un número de teléfono nuevo en su región. Asigne el número a la conexión troncal SIP que ha creado yendo a la conexión troncal SIP y pulsando el icono de número.

  Necesita este número de teléfono para configurar el agente de voz, incluidos los códigos de área y país. Consulte [Creación y conexión del agente de voz](/docs/services/voice-agent?topic=voice-agent-getting-started#step3).

  **NOTA**: Si utiliza una cuenta Lite/Trial Twilio para probar las transferencias en {{site.data.keyword.iva_short}},
deberá asegurarse de _verificar_ el destino de la transferencia. En el [sitio oficial de Twilio](https://support.twilio.com/hc/en-us/articles/223136107-How-does-Twilio-s-Free-Trial-work-) hallará más información.

## Conexión con Voximplant
{: #voximplant-setup}

1. Cree [una cuenta de desarrollador de Voximplant](https://voximplant.com/sign-up/).

1. Vaya al [panel de control de Voximplant](https://manage.voximplant.com/numbers/my_numbers). En el menú, seleccione **Números** y pulse **Comprar nuevo número de teléfono**. Puede marcar **Real** o **Números de prueba** y, a continuación, seleccionar un número en la lista y pulsar **Comprar seleccionado** para comprar un número de teléfono.

1. Especifique este número en los valores del agente de voz.

1. Vaya a [la sección Aplicaciones](https://manage.voximplant.com/applications) del _panel de control de Voximplant_ para crear una aplicación llamada **Watson**.

1. Dentro de la aplicación, vaya al separador **Escenarios** y cree un **watson-scenario** con el siguiente código:
    ```javascript
      VoxEngine.addEventListener(AppEvents.CallAlerting, (e) => {
        let call2 = VoxEngine.callSIP("sip:12025550186@us-south.voiceagent.cloud.ibm.com");
        VoxEngine.easyProcess(e.call, call2);
      })
    ```
    {: codeblock}

    Preste atención a la llamada de función **callSIP**:
      * Sustituya `12025550186` por el número de Voximplant que ha comprado en el paso 2. 
      * Sustituya `us-south.voiceagent.cloud.ibm.com` por el punto final de SIP del agente de voz. El punto final se especifica en la página _Iniciación_ de la documentación de {{site.data.keyword.iva_full}}. Consulte la [*guía de aprendizaje de iniciación*](/docs/services/voice-agent?topic=voice-agent-getting-started#step1).
    
1. Vaya al separador **Direccionamiento** para crear una **watson-rule**. Especifique **watson-scenario** como un escenario asignado.

1. Abra el separador **Números** con las secciones **Conectado** (ya vacío) y **Disponible**. Vaya a **Seleccionado**, seleccione su número y pulse **Conectar**. En la ventana que se abre, especifique **watson-rule** y luego pulse **Conectar**.

## Interconexión con {{site.data.keyword.iva_short}}
{: #peering}

{{site.data.keyword.iva_short}} soporta conexiones de pares con las PBX del cliente, como Asterisk. Para la interconexión con {{site.data.keyword.iva_short}}, puede añadir a la lista blanca las direcciones IP de sus servidores.

1. Vaya al panel de control _Gestionar_ y seleccione el separador _Instancia_.

1. Pulse el icono **Añadir una nueva IP** para añadir una nueva dirección IP a la lista blanca.

1. Añada un **Apodo de IP** y la **Dirección IP**.

## Conexión con AT&T y otros proveedores
{: #att-other}

{{site.data.keyword.iva_short}} da soporte a conexiones con AT&T&reg; y otros proveedores de conexión troncal SIP. Sin embargo, la configuración de estas conexiones no es de tipo autoservicio, por lo que requieren asistencia adicional. Consulte [Solicitud de configuración asistida](#request-setup).

## Solicitud de configuración asistida
{: #request-setup}

Puede solicitar la configuración de red asistida para conectarse con AT&T u otros proveedores de conexiones troncales SIP, para la interconexión con {{site.data.keyword.iva_short}} o para solicitar más de 50 conexiones simultáneas utilizando el siguiente proceso.

Puede incluir una PBX como Asterisk en su instancia de {{site.data.keyword.iva_short}}. Abra una incidencia de soporte sólo si la lista blanca de Internet pública no es una solución aceptable. Consulte [Direcciones IP a la lista blanca](/docs/services/voice-agent?topic=voice-agent-whitelist_IP#whitelist_IP).

1. Abra una nueva [incidencia de soporte de {{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/unifiedsupport/tickets/add)

1. En **Tipo de incidencia**, seleccione **Técnico**.

1. En **Seleccione un contexto de recurso**, elija **Cloud Foundry**.

1. En **Área técnica de soporte**, elija **Servicios de aplicación**.

1. Elija la **Región**, **Organización** y **Espacio** para su instancia de {{site.data.keyword.iva_short}}.

1. Seleccione su instancia de servicio de {{site.data.keyword.iva_short}} en **Recurso asociado**.

1. En **Gravedad**, elija **Gravedad 4 - Impacto mínimo**.

1. En **Asunto**, escriba `Configuración de red asistida de {{site.data.keyword.iva_short}}`.

1. En la sección **Descripción breve**, describa cómo piensa conectarse al servicio {{site.data.keyword.iva_short}} o solicitar más de 50 conexiones simultáneas para su agente de voz. La conexión entre iguales está disponible para usuarios con planes _Estándar_ o _Premium_. Si cambia la instancia de un plan _Estándar_ o _Premium_ a un plan _Lite_, o si suprime la instancia, se inhabilita la conexión entre iguales.

  Puede conectarse utilizando un proveedor de conexión troncal SIP o una conexión entre iguales, como un túnel IPSec. En la incidencia, puede adjuntar un diagrama de red que describa su topología de red en formato PDF o de imagen. También puede adjuntar documentos técnicos que describan en detalle las capacidades de servicio que desea.

  Incluya la información siguiente en la **Descripción breve**:
  * Nombre de la empresa
  * ID de cuenta de {{site.data.keyword.Bluemix_notm}}
  * URL del panel de control del servicio {{site.data.keyword.iva_short}}
  * Caso de uso
  * Diagrama de red con la información de proveedor de conexión troncal SIP o dirección IP
