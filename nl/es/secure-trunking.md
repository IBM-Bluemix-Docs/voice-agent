---

copyright:
  years: 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Protección de las conexiones
{: #securing}

Puede habilitar SRTP (Secure Real Time Transport Protocol, protocolo de transporte en tiempo real seguro) y el cifrado utilizando TLS (Transport Layer Security, seguridad de la capa de transporte) para sus conexiones troncales SIP para proteger las conexiones realizadas con {{site.data.keyword.iva_full}}.

## Configuración de SRTP en Twilio
{: #SRTP}

**Nota:** Si habilita SRTP, los mensajes SIP también se cifran. No es necesario habilitar SRTP y el cifrado de mensajes SIP de forma separada.

1. En la cuenta de Twilio, vaya al panel de control _Conexiones troncales Elastic SIP_ y seleccione **Conexiones troncales**.

1. Elija la conexión troncal que desea proteger con SRTP seleccionando una conexión troncal existente o creando una nueva pulsando el icono **+**.

  * Si crea una nueva conexión troncal, debe configurar el _URI de conexión troncal SIP_ en el panel de control **Origen**.  Para obtener más información, consulte [Conexión a una conexión troncal SIP](connect-SIP.html).

1. En el panel de control _General_, busque la sección _Conexión troncal segura_. Pulse **Inhabilitada** para cambiar el valor de conexión troncal segura a **Habilitada** y guarde los cambios.

## Habilitación del cifrado solo para los mensajes SIP utilizando TLS en Twilio
{: #TLS}

Si desea cifrar solo los mensajes SIP en {{site.agent.keyword.iva_short}} sin SRTP, puede seleccionar un punto final URI que utilice TLS en Twilio.

1. En la cuenta de Twilio, vaya al panel de control _Conexiones troncales Elastic SIP_ y seleccione **Conexiones troncales**.

1. Elija la conexión troncal a la que desea añadir la transferencia de llamada seleccionando una conexión troncal existente o creando una nueva pulsando el icono **+**.

1. Seleccione **Origen** en el menú y escriba los siguientes URI de origen seguros, uno por uno. Al incluir varios nombres de host o direcciones IP, si el punto final del primer host falla o está fuera de servicio, el proveedor de conexiones troncales SIP dirige las llamadas al siguiente nombre de host de la lista.

```
sip:us-south.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}

O bien

```
sip:us-east.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}
