---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-01"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Programación de agentes de voz mediante la API
{: #api}

Puede controlar el comportamiento del agente de voz definiendo etiquetas de acción y variables de estado desde el servicio {{site.data.keyword.conversationfull}}. Las etiquetas de acción inician acciones que el agente de voz realiza durante una sesión de conversación y las variables de estado definen características del agente de voz que se mantienen durante la conversación a no ser que se modifiquen.
{: shortdesc}

Puesto que {{site.data.keyword.iva_full}} se basa en IBM Voice Gateway, la API funciona del mismo modo. Si está familiarizado con Voice Gateway, puede utilizar las mismas acciones y variables de estado en los diálogos de {{site.data.keyword.conversationshort}} con {{site.data.keyword.iva_short}}. Consulte [Etiquetas de acción y variables de estado en la API de Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html).
{: tip}

## Edición de JSON en la respuesta del diálogo
{: #json-editor}

Las acciones y los estados se definen en una respuesta de nodo de diálogo en formato JSON. Para editar el código JSON, abra el editor JSON.

1. En el panel de control de {{site.data.keyword.Bluemix_short}}, seleccione la instancia de servicio de {{site.data.keyword.conversationshort}}.
1. Inicie la herramienta {{site.data.keyword.conversationshort}}.
1. Pulse la habilidad que contiene el diálogo que desea editar.
1. Vaya al separador **Diálogo** y seleccione el nodo donde desea establecer una acción o estado.
1. En la respuesta, pulse el icono ![Respuesta avanzada](../conversation/images/kabob.png) y seleccione **Abrir editor JSON**.

En el editor JSON, puede definir acciones en la propiedad `output` y estados en la propiedad `context`, tal como se describe en las secciones siguientes.

## Inicio de acciones
{: #defining-actions}

Para iniciar acciones en el agente de voz durante una llamada, puede definir etiquetas de acción en un nodo de diálogo de {{site.data.keyword.conversationshort}} en formato JSON en la propiedad `output`. Puede definir una acción única en la etiqueta `vgwAction` o una secuencia de acciones en la etiqueta `vgwActionSequence`. Cada acción consta de una propiedad `command`, seguida por una propiedad opcional `parameter` para definir atributos para los mandatos que los necesitan.

### Acciones únicas
{: #single-actions}

Para realizar una acción única, defina la acción en la etiqueta `vgwAction` con cualquier atributo de parámetro necesario. En el bloque `text` en la propiedad `output`, puede incluir de forma opcional una expresión que el agente de voz reproduce una vez que se realiza la acción.

La acción única siguiente en la etiqueta `vgwAction` indica al agente de voz que cuelgue la llamada cuando se activa la respuesta del nodo. Puesto que el mandato `vgwActHangup` no tiene parámetros, no se define ninguno.
```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActHangup"
    }
  }
}
```
{: codeblock}

La acción siguiente indica al agente de voz que recopile la entrada de señalización de multifrecuencia de tono dual (DTMF) y que reproduzca el texto definido para el interlocutor.

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActCollectDtmf",
      "parameters": {
        "dtmfTermKey": "#"
      }
    },
    "text": {
      "values": [
        "Enter your phone number."
      ]
    }
  }
}
```
{: codeblock}

### Secuencias de acciones
{: #action-sequences}

Para realizar una o varias acciones en un solo turno de la conversación, puede definir una secuencia de acciones en la etiqueta `vgwActionSequence` como una lista JSON. Las acciones se realizan en el orden en el que las define.

A diferencia de las acciones únicas, para que el agente de voz reproduzca una expresión al utilizar la etiqueta `vgwActionSequence`, la lista de acciones debe contener la acción `vgwActPlayText`. Al contrario que en la etiqueta `vgwAction`, las expresiones del campo `output.text` no se reproduce automáticamente.
{: tip}

En el ejemplo siguiente, más complejo, las acciones definidas en la etiqueta `vgwActionSequence` indican al agente de voz que inhabilite el procesamiento de habla a texto y recopile la entrada DTMF mientras reproduce una expresión.

```json
{
  "output": {
    "vgwActionSequence": [
      {
        "command": "vgwActPauseSTT"
      },
      {
        "command": "vgwActCollectDtmf",
        "parameters": {
          "dtmfTermKey": "#"
        }
      },
      {
        "command": "vgwActPlayText",
        "parameters": {
          "text": [
            "Enter your social security number."
          ]
        }
      }
    ]
  }
}

```
{: codeblock}

## Definición de estados
{: #setting-states}

Para indicar un cambio de estado que se mantiene entre turnos de conversación, el agente de voz intercambia variables de estado con el servicio {{site.data.keyword.conversationfull}} configurado. Estas variables de estado están definidas en un nodo de diálogo de {{site.data.keyword.conversationshort}} como [variables de contexto](/docs/services/assistant?topic=assistant-dialog-build#dialog-build) en formato JSON.

Por ejemplo, puede definir la variable de estado siguiente para establecer el mensaje que se transmite al interlocutor si la conexión con el servicio {{site.data.keyword.conversationshort}} falla.

```json
{
  "context": {
    "vgwConversationFailedMessage": "Sorry, we're unable to connect you to our help line. Please try again later."
  }
}
```
{: codeblock}

El agente de voz presupone que el servicio {{site.data.keyword.conversationshort}} no tiene estado y que todo el estado se mantiene en el agente de voz entre intercambios con el servicio {{site.data.keyword.conversationshort}}. Para cada turno de conversación de una llamada, el estado se transfiere al servicio {{site.data.keyword.conversationshort}} y se recibe de nuevo desde el servicio en la sección `context` de los mensajes REST.
