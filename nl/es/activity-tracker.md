---

copyright:
  years: 2018
lastupdated: "2018-10-30"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Sucesos de Activity Tracker
{: #activity-tracker}

Utilice el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar un seguimiento de cómo interactúan los usuarios y las aplicaciones con el servicio {{site.data.keyword.iva_full}} en {{site.data.keyword.Bluemix}}.
{: shortdesc}

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.Bluemix_notm}}. Para obtener más información, consulte [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started#getting-started).

## Lista de sucesos
{: #event-List}

En la tabla siguiente se muestran las acciones que generan un suceso.

|Acción| descripción |
| --- | ---- |
| `crear agente: POST /config/submitconfig` | Crear un nuevo agente de voz |
| `actualizar agente: POST /config/submitconfig` | Actualizar un agente de voz |
| `Actualizar simultaneidad: POST /config/updatemax` | Actualizar el máximo de llamadas simultáneas |
| `suprimir agente: POST /config/submitconfig` | Suprimir un agente de voz |
{: caption="Tabla 1. Acciones que generan sucesos" caption-side="top"}

## Dónde ver los sucesos de actividad
{: #view-event}

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el dominio de la cuenta de {{site.data.keyword.cloudaccesstrailshort}} que está disponible en la región de {{site.data.keyword.Bluemix_notm}} donde se generan los sucesos.

## Filtrado de sucesos
{: #filter_events}

### Filtrado por ID de agente de voz
{: #filter_id}

Puede filtrar la lista de sucesos de actividad de un agente de voz específico por su ID de instancia.

1. Vaya a la página **Gestionar** de {{site.data.keyword.cloudaccesstrailshort}}.
2. Escriba `target.name_str` en el **Campo de búsqueda** y el ID de instancia del agente de voz en el campo **Buscar** como una serie. Compruebe que el ID de instancia del agente de voz está codificado con porcentajes y que utiliza una búsqueda con caracteres comodín, _*_.

Por ejemplo, para buscar el ID de instancia del agente de voz, `serviceInstanceId=crn%3A...`.

  * **Campo de búsqueda**: `target.name_str`
  * **Buscar**: `"*crn%3A...*"`

### Filtrado por suceso de acción
{: #filter_action}

También puede filtrar sucesos de acción específicos en la lista de sucesos de actividad

1. Vaya a la página **Gestionar** de {{site.data.keyword.cloudaccesstrailshort}} y escriba el siguiente valor de configuración en cada uno de los campos.

  * **Ver registros**: `Registros de espacio`
  * **Campo de búsqueda**: `action_str`
  * **Buscar**: `"action string"`

## Creación de filtros avanzados
{: #advanced_filters}

También puede crear filtros avanzados utilizando `AND` u `OR` para combinar términos de búsqueda en el campo **Buscar**.

Por ejemplo, puede filtrar por un ID de instancia del agente de voz específico y una acción específica.

* **Ver registros**: `Registros de espacio`
* **Campo de búsqueda**: `target.name_str`
* **Buscar**: `"*crn%3A...*" AND action_str:"action string"`

**Recuerde**: Compruebe que el id de instancia del agente de voz está codificado con porcentajes y que utiliza una búsqueda con caracteres comodín, _*_.
