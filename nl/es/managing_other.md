---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Utilización de instancias de servicio en otros espacios de trabajo de {{site.data.keyword.Bluemix_notm}}
{: #other_service}

Puede configurar el agente de voz para utilizar instancias de servicio de {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.speechtotextshort}} que pertenecen a espacios de trabajo de otras cuentas de {{site.data.keyword.Bluemix_short}}.
{: shortdesc}

Para conectar su agente de voz a otras instancias de servicio, puede utilizar las credenciales de nombre de usuario y contraseña o una clave de API para sus instancias de servicio.

1. En el separador _Agentes de voz_ del panel de control _Gestionar_, seleccione **Crear un agente de voz nuevo** o el agente de voz que desea editar.

1. En  {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.speechtotextshort}}, seleccione **Otra instancia de servicio** para su **Tipo de servicio** y luego seleccione la **Región**.

1. Elija **Nombre de usuario y contraseña** o **Clave de API** y escriba sus credenciales de servicio.
  Para encontrar estos valores, vaya a la instancia de servicio que desea configurar, seleccione **Credenciales de servicio** y luego **Ver credenciales**.

  * **Nombre de usuario y contraseña**: En los campos **URL**, **Nombre de usuario** y **Contraseña**, configure las credenciales para las instancias de servicio de {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.texttospeechshort}}.
  * **Clave de API**: En los campos **URL** y **Clave de API**, configure las credenciales para las instancias de servicio de {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.texttospeechshort}}.

  Las credenciales no son el nombre de usuario y la contraseña de {{site.data.keyword.Bluemix_notm}}, sino las credenciales cifradas para la instancia de servicio específica.
  {:tip}

1. Especifique la información de su instancia de servicio.

  * **{{site.data.keyword.conversationshort}}:** En el campo **ID de espacio de trabajo**, escriba el ID del espacio de trabajo que desea utilizar con el agente de voz. Para encontrar el ID de espacio de trabajo, inicie la herramienta y, en el espacio de trabajo que desea integrar, pulse el icono Acciones (**&vellip;**) y seleccione **Ver detalles**.
  * **{{site.data.keyword.speechtotextshort}}:** para **Seleccionar tipo de modelo**, seleccione **Banda estrecha**, **Banda ancha** o **Banda estrecha y banda ancha** y luego seleccione el **Modelo** de idioma.
  * **{{site.data.keyword.texttospeechshort}}:** En el campo **Voz**, seleccione el idioma y la voz que utiliza el servicio. Debe especificar una voz para el servicio.

**Recuerde:** Para que el agente de voz funcione, debe configurar {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} y {{site.data.keyword.texttospeechshort}} para el mismo idioma. Consulte [Idiomas admitidos](about.html#supported-languages).
