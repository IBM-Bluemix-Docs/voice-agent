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

# Creación de un agente de voz habilitado para SMS
{: #sms_voice_config_instance}

Después de haber creado el servicio {{site.data.keyword.iva_full}}, puede crear agentes de voz individuales con funciones de SMS, o agentes de voz solo con funciones de SMS, desde el panel de control _Gestionar_. Puede configurar {{site.data.keyword.iva_full}} para que reciba llamadas de voz de entrada y responda con mensajes de salida de SMS, en función del mandato de voz recibido por el usuario. Para configurarlo, añada un nodo y una intención en el servicio {{site.data.keyword.conversationshort}}.
{: shortdesc}


1. Vaya al separador _Agentes de voz_ del panel de control _Gestionar_ y pulse **Crear un agente de voz**.

1. Para **Tipo de agente**, seleccione _Voz + SMS_.

1. Siga las instrucciones de la sección [creación de un agente de voz](/docs/services/voice-agent?topic=voice-agent-config_instance).

1. Marque el recuadro **Iniciar conversación desde mensajes de entrada** para permitir que los usuarios inicien una sesión de SMS con el agente de SMS.

1. Marque **Notificar el tiempo de espera de la sesión** para que el agente de SMS envíe un mensaje SMS al usuario que le avise de que el agente no ha recibido una respuesta en un tiempo y que se excederá el tiempo de espera. 

   - Consulte [Opciones avanzadas](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) para obtener más información acerca de las **Opciones avanzadas** disponibles para el agente de SMS, como por ejemplo el establecimiento de un periodo de tiempo personalizado tras el que la sesión excederá el tiempo de espera.

1. Siga las instrucciones de la sección sobre [creación de un agente de SMS](/docs/services/voice-agent?topic=voice-agent-sms_config_instance) para crear un agente de SMS.

1. _**NOTA:**_ para que un agente tenga la integración tanto de voz como de SMS, como en el caso de recepción de entrada de voz y envío de un mensaje de salida de SMS para responder, **debe** utilizar uno de los números de **voz** para el agente de **SMS**.

### Configuración de Watson Assistant para la integración de voz y SMS
{: #sms_outbound}

1. En el panel de control de {{site.data.keyword.Bluemix_notm}}, seleccione la instancia de {{site.data.keyword.conversationshort}} que utiliza el agente de voz.

1. Cree una **intención de SMS de salida** en el panel de control.

1. Añada un **nodo de SMS de salida** en el panel de control.

1. En la sección _Si el asistente reconoce:_, seleccione el atributo **intención de SMS de salida** que ha creado anteriormente.

1. Añada la respuesta al nodo. Copie y pegue el siguiente fragmento de código para sustituir el código que se muestra en el campo.

    ```json
        {
            "output": {
                "text": {
                "values": [
                    "Okay. I will send you a text message now."
                ],
              "selection_policy": "sequential"
                },
                "vgwActionSequence": [
                {
                    "command": "vgwActSendSMS",
                    "parameters": {
                    "message": "This is a test message from Watson Assistant"
                    }
                },
                {
                    "command": "vgwActPlayText"
                }
                ]
            }
        }
    ```
    {: codeblock}


1. Llame a su agente y active el nodo para recibir un mensaje de texto en el teléfono desde el que llama. 

Para obtener más información sobre cómo trabajar en el servicio {{site.data.keyword.conversationshort}}, consulte [Acerca de {{site.data.keyword.conversationshort}}](/docs/services/assistant?topic=assistant-index#indext).
