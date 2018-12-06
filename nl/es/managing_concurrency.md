---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Edición del número máximo de conexiones simultáneas
{: #edit_concurrency}

Si utiliza los planes _Estándar_ o _Premium_, puede cambiar el número máximo de conexiones simultáneas en los valores predeterminados.
{: shortdesc}

En todos los planes, puede recibir 2 conexiones simultáneas de forma gratuita. Para obtener más información, consulte [Planes de tarifas](https://console.bluemix.net/catalog/services/voice-agent-with-watson). En el panel de control _Gestionar_, puede ver el número máximo de conexiones simultáneas permitidas en el plan listado en **Número máximo de conexiones simultáneas**. También puede ver el número máximo de conexiones simultáneas utilizado por los agentes de voz en el mes actual en **Número máximo de conexiones simultáneas utilizado**.

1. Vaya al separador _Instancias_ en el panel de control _Gestionar_ para editar el número máximo de conexiones simultáneas en el plan. 
1. Si desea cambiar el número máximo de conexiones simultáneas de su plan, pulse el icono **Editar**.
1. En la ventana _Editar número máximo de conexiones simultáneas_, elija el número máximo de conexiones simultáneas y pulse **Guardar**.

El número mínimo de conexiones simultáneas que puede establecer mediante autoservicio es 10 y el máximo es 50. Si necesita más de 50 conexiones simultáneas para su agente de voz, consulte [Solicitud de configuración de red asistida](connect-SIP.html#request-setup).

## Información sobre precios de conexiones simultáneas
{: #concurrent-charge}

  * Los planes _Lite_ y _Estándar_ incluyen 2 conexiones simultáneas de forma gratuita.
  * Los planes _Premium_ están personalizados por instancia.
  * En un plan _Estándar_, tiene una capacidad mínima de 10 conexiones simultáneas.
  * El uso de conexiones simultáneas se prorratea por mes. Si utiliza más de 2 conexiones simultáneas en un día, se le facturará la tarifa diaria. Por ejemplo, su plan admite 2 conexiones simultáneas gratuitas y ha establecido un límite máximo de 12 conexiones. Si solo utiliza 5 conexiones en un día, se le facturarán 3.
  * Si tiene un plan _Estándar_ o _Premium_, puede adquirir una mayor capacidad de conexiones simultáneas.
  * Se le facturará una tarifa diaria para la capacidad de conexiones simultáneas máxima que utilice en un día.

Para obtener más información sobre planes, tarifas y características, consulte [Planes de tarifas](https://console.bluemix.net/catalog/services/voice-agent-with-watson).
