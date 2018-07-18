---

copyright:
  years: 2018
lastupdated: "2018-06-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configuración de transferencia de llamada
{: #call-transfer}

Puede configurar la transferencia de llamada de forma que si un interlocutor solicita hablar con un agente en directo durante una conversación, el agente de voz transfiera la llamada automáticamente.
{: shortdesc}

## Acerca de la transferencia de llamada
{: #about-ct}

Al habilitar la transferencia de llamada, si un interlocutor solicita hablar con un agente en directo durante una conversación, el agente de voz redirigirá la llamada. Puede habilitar la transferencia de llamada definiendo un URI de terminación en la configuración del proveedor SIP. A continuación, defina el destino de transferencia en una acción de API en un nodo de diálogo de la instancia de {{site.data.keyword.conversationshort}}. Su destino de transferencia es un URI SIP que contiene el URI de terminación y el número de teléfono. Para obtener más información sobre las acciones admitidas y personalizar los agentes de voz, consulte [Programación de agentes de voz mediante la API](api.html).

## Paso 1: Configuración del URI de terminación
{: #termination-setup}

### Configuración de un URI de terminación en NetFoundry
{: #termination-netfoundry}

Anote el número de teléfono de su [cuenta de NetFoundry ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson.netfoundry.io/watson-login){: new_window} que desea transferir. Posteriormente, puede especificar este número de teléfono y el URI de terminación como destino de transferencia en el diálogo de {{site.data.keyword.conversationshort}}. No utilice un número de teléfono personal.

Puede copiar el siguiente URI de terminación de NetFoundry para utilizarlo en el destino de transferencia.

```
dal.watson-va.netfoundry.net
```
{: codeblock}

No es necesario configurar manualmente el URI de terminación en su cuenta de NetFoundry si realiza la [Configuración de {{site.data.keyword.conversationshort}} para la transferencia de llamada](#conversation-setup).

### Configuración de un URI de terminación en Twilio
{: #termination-Twilio}

1. En la cuenta de Twilio, vaya al panel de control _Conexiones troncales Elastic SIP_ y seleccione **Conexiones troncales**.

1. Elija la conexión troncal a la que desea añadir la transferencia de llamada seleccionando una conexión troncal existente o creando una nueva pulsando el icono **+**.

  * Si crea una nueva conexión troncal, debe configurar el _URI de conexión troncal SIP_ en el panel de control **Origen**.  Para obtener más información, consulte [Conexión a una conexión troncal SIP](connect-SIP.html).

1. Seleccione **Terminación** en la barra de navegación y especifique un nombre para el URI de terminación.

  * Los nombres de URI de terminación deben ser exclusivos. Twilio comprueba automáticamente la disponibilidad del nombre que elige. Consulte [Valores de terminación de conexión troncal SIP ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window} para obtener más detalles sobre los servicios de Twilio.

1. En la sección _Autenticación_, pulse el icono **+** para añadir una dirección IP de agente de voz a la lista de IP de control de acceso.

  Añada las dos siguientes direcciones IP:
   * 169.60.154.134 (región de servicio EE. UU. Sur)
   * 169.61.86.179 (región de servicio EE. UU. Este)

1. Pulse **Guardar** para acabar de configurar el URI de terminación.

Anote el número de teléfono y el URI de terminación que desea transferir. Asegúrese de que el número de teléfono no sea un número de teléfono personal. Puede utilizar el número de teléfono y el URI de terminación para especificar el destino de transferencia en el diálogo de {{site.data.keyword.conversationshort}}.


## Paso 2: Configuración de {{site.data.keyword.conversationshort}} para la transferencia de llamada
{: #conversation-setup}

Para obtener más información sobre cómo trabajar en el servicio {{site.data.keyword.conversationshort}}, consulte [Acerca de {{site.data.keyword.conversationshort}}](../conversation/index.html#about).

1. En el panel de control de {{site.data.keyword.Bluemix_notm}}, seleccione la instancia de {{site.data.keyword.conversationshort}} que utiliza el agente de voz.

1. En el panel de control _Iniciación_, pulse el botón **Iniciar herramienta**.

1. Pulse **Iniciación** en el espacio de trabajo que desea editar.

1. Pulse **Añadir intención** y especifique un nombre para la intención, como _Transferencia_.

  Puede especificar información más detallada, o volver a editar más adelante y refinar la intención.

1. Después de crear la intención de transferencia de llamada, seleccione el separador _Diálogo_.

1. Pulse **Añadir nodo** y especifique un nombre para el nodo, como _Transferencia de llamada_.

1. En la sección _Si el bot reconoce:_, escriba **Intención de transferencia de llamada** para encontrar la intención que ha creado.

1. En la sección _Entonces, responder con:_, pulse el icono **&vellip;** y seleccione **Abrir editor JSON**. Copie y pegue el siguiente fragmento de código para sustituir el código que se muestra en el campo.

```json
{
    "output": {
        "text": {
            "values": [ "Please hold on while I connect you with a live agent." ],
     "selection_policy": "sequential"
        },
   "vgwAction": {
            "command": "vgwActTransfer",
     "parameters": {
                "transferTarget": "sip:18889990000\\@dal.watson-va.netfoundry.net"
            }
        }
    }
}
```
{: codeblock}

**Recuerde**: El URI SIP del destino de transferencia incluye un número de teléfono y el URI de terminación que ha creado. No utilice un número de teléfono personal como destino de transferencia. Por ejemplo, si el número de teléfono es `18889990000` y el URI de terminación es `mysiptrunk.pstn.twilio.com`, el URI SIP completo es `sip:18889990000\\@mysiptrunk.pstn.twilio.com`. Si utiliza Netfoundry y tiene el número de teléfono `18889990000`, el URI SIP completo es `sip:18889990000\\@dal.watson-va.netfoundry.net`.

## Pasos siguientes
{: #Next}

Pruebe el agente de voz llamando a su número de teléfono asociado y utilice los términos clave que ha identificado en su intención. Si el agente de voz le redirige a usted, la transferencia se ha realizado correctamente.

Ahora puede refinar y configurar la intención de **Transferencia** y el diálogo para responder a los términos y frases clave que elija.
