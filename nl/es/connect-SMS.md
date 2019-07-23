---

copyright:
  years: 2019
lastupdated: "2019-06-21"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Conexión con proveedores de SMS
{: #connect-sms}

Puede elegir el proveedor de SMS que utilizará para integrarlo con {{site.data.keyword.iva_full}} en la lista siguiente.
{: #shortdesc}

* [Twilio](#twilio-setup)

## Generación de una clave de API y configuración de credenciales
{: #sms_access}

Solo puede crear credenciales para los roles que ya están activos en la cuenta. Para los agentes de SMS y de Voz + SMS, debe tener asignado el rol de *Escritor* o de *Gestor*. Consulte el [Paso 9 de la sección Invitar a los usuarios y asignar acceso inicial](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. En el *Panel de control* de la instancia de {{site.data.keyword.iva_short}}, pulse **Nueva credencial (+)**. 
2. En el nuevo recuadro de diálogo que aparece, especifique un **Nombre** y, en el menú desplegable **Rol**, seleccione *Escritor* o *Gestor*. 
    - **NOTA:** para cualquier funcionalidad relacionada con SMS, **_debe_** seleccionar el rol de *Escritor* o de *Gestor*. 
3. Pulse **Añadir**.
4. Junto a las credenciales recién creadas, pulse **Ver credenciales**. Anote el valor de `APIKEY` en el script JSON para utilizarlo en [Configuración de Twilio para SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

## Configuración de Twilio para SMS
{: #twilio-setup}

1. Acceda a los números de teléfono de Twilio, se encontrará [aquí](https://www.twilio.com/console/phone-numbers/), y seleccione el número de teléfono que se asigna a su agente de _SMS_ o de _Voz + SMS_. 

1. Desplácese hacia abajo hasta la sección **Mensajería**. En el campo _CONFIGURAR CON_, seleccione **Webhooks, TwiML Bins, Functions, Studio o Proxy** en el menú desplegable.

1. En el campo _UN MENSAJE DE ENTRADA_, seleccione **Webhook** en el menú desplegable.

1. En el campo de URL vacío situado junto a **Webhook**, siga las instrucciones en función de la región del agente. 

    - Si el agente que ha creado se basa en la región de Washington, escriba `https://apikey:YOUR_API_KEY@sms-east.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` en el campo.
    - Si el agente que ha creado se basa en la región de Dallas, escriba `https://apikey:YOUR_API_KEY@sms-south.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` en el campo.
    - Sustituya `YOUR_API_KEY` en el URL anterior por el valor de `APIKEY` de la credencial que ha creado anteriormente. Consulte [Generación de una clave de API y configuración de credenciales](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_access). 

1. Pulse **Guardar**. 
