---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Creación del servicio

{: shortdesc}
Puede crear una instancia de servicio de {{site.data.keyword.iva_full}} mediante el catálogo de {{site.data.keyword.Bluemix_short}} o un mandato `ibmcloud` de {{site.data.keyword.Bluemix_notm}}.

## Creación del servicio desde el catálogo
{: #catalog_create}

1. Vaya a la [página de catálogo de {{site.data.keyword.iva_short}}](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

   La página de catálogo tiene información sobre el servicio y sus planes de precios. Puede cambiar el valor de **Nombre de servicio**.

2. Pulse **Crear**.

## Creación del servicio desde la línea de mandatos
{: #command_create}

1. [Instale la CLI de {{site.data.keyword.Bluemix_notm}}](../../cli/reference/bluemix_cli/get_started.html).

2. Ejecute el [mandato `ibmcloud`](../../cli/reference/bluemix_cli/bx_cli.html#bluemix_cli) que crea la instancia de servicio de VoiceAgent con el plan _Trial_:

   ```
   ibmcloud service create VoiceAgent _Trial_ "My Voice Agent Service"
   ```
   {: codeblock}

## Pasos siguientes
{: #next}

Cree el agente de voz desde el panel de control _Gestionar_. Consulte [Gestión de agentes de voz](managing.html).
