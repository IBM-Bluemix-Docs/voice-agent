---

copyright:
  years: 2018
lastupdated: "2018-08-24"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Habilitación del reenvío de sucesos para agentes de voz
{: #event_forwarding}

Puede habilitar el reenvío de sucesos para recopilar información sobre las llamadas gestionadas por los agentes de voz en {{site.data.keyword.iva_full}} mediante un servicio de base de datos de {{site.data.keyword.cloudantfull}}.
{: shortdesc}

Puede que desee recopilar y analizar los datos de llamada de {{site.data.keyword.iva_short}} para que la conversación resulte más natural para el interlocutor. Cada agente de voz que cree puede reenviar informes de sucesos a una {{site.data.keyword.cloudant_short_notm}} especificada que usted gestione. Entre los sucesos comprendidos en los informes se incluyen los sucesos de registro de detalles de llamadas (CDR), los sucesos de transcripción y los informes de sucesos de turno. Puede obtener más información sobre los tipos de sucesos que puede reenviar en [Informes de sucesos](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}.

Analizar los datos de estos sucesos le permite ajustar diálogos, refinar intenciones y mejorar la experiencia general del interlocutor.

Cuando cree o edite agentes de voz, también puede optar por habilitar el reenvío de sucesos. Para obtener más detalles sobre la creación y la edición de agentes de voz, consulte [Gestión de agentes de voz](managing.html). Para habilitar el reenvío de sucesos, debe indicar la información de cuenta de {{site.data.keyword.cloudant_short_notm}}, incluido el nombre de cuenta y la contraseña.

**Importante:** Los sucesos de turno, transcripción y CDR incluyen información de los usuarios que puede contener PHI (información sanitaria personal), PII (información de identificación personal) o datos PCI DSS (PCI Data Security Standard). Para evitar la exposición de información personal, debe asegurarse de que la instancia de {{site.data.keyword.cloudant_short_notm}} protege correctamente la información confidencial que los usuarios comparten en o durante la conversación. Consulte [Seguridad de información y privacidad de datos: Reenvío de sucesos](infosec.html#event_forwarding) y [{{site.data.keyword.cloudant_short_notm}}: Seguridad](../Cloudant/offerings/security.html#security).


## Habilitación del reenvío de sucesos
{: #enable-event-forwarding}

Puede habilitar el reenvío de sucesos cuando crea o edita los agentes de voz en el panel de control _Gestionar_ en {{site.data.keyword.Bluemix_short}}.

1. En la sección **Reenvío de sucesos**, después de la sección de configuración de {{site.data.keyword.texttospeechshort}}, seleccione **Habilitar el reenvío de sucesos**.

1. Seleccione **Mi instancia de servicio de {{site.data.keyword.cloudant_short_notm}}** u **Otra instancia de servicio de {{site.data.keyword.cloudant_short_notm}}**.
  * Si va a utilizar **Mi instancia de servicio de {{site.data.keyword.cloudant_short_notm}}**, seleccione el nombre de usuario y el nombre de la **cuenta de {{site.data.keyword.cloudant_short_notm}}** en las listas.
  * Si va a utilizar **Otra instancia de servicio de {{site.data.keyword.cloudant_short_notm}}**, especifique el nombre de usuario y la contraseña de {{site.data.keyword.cloudant_short_notm}} o la clave de API de la cuenta.

1. Seleccione **Habilitar** para cada tipo de suceso que desea reenviar y, a continuación, elija la base de datos a la que desea reenviar los sucesos.
  * Sucesos de registro de detalles de llamadas (CDR)
  * Sucesos de transcripción
  * Sucesos de turno

1. Consulte la base de datos para asegurarse de que los informes de sucesos se reenvían correctamente.

## Enlaces relacionados
* [IBM Voice Gateway: Informes de sucesos](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
* [Seguridad de información y privacidad de datos](infosec.html)
* [{{site.data.keyword.cloudant_short_notm}}: Seguridad](../Cloudant/offerings/security.html#security)
