---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Creación del servicio

Puede crear una instancia de servicio de {{site.data.keyword.iva_full}} mediante el catálogo de {{site.data.keyword.Bluemix_short}} o con un mandato `ibmcloud` de {{site.data.keyword.Bluemix_notm}}.
{: shortdesc}


## Creación del servicio desde el catálogo
{: #catalog_create}

1. Vaya a la [página de catálogo de {{site.data.keyword.iva_short}}](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

   La página de catálogo tiene información sobre el servicio y sus planes de precios. Puede cambiar el valor de **Nombre de servicio**.

2. Pulse **Crear** para [crear un agente de voz desde el panel de control _Gestionar_](managing_create.html#config_instance).

## Creación del servicio desde la línea de mandatos
{: #command_create}

1. [Instale la CLI de {{site.data.keyword.Bluemix_notm}}](../cli/index.html#overview).

2. Ejecute el [mandato de `ibmcloud`](../cli/idt/commands.html#idt-cli) que crea el servicio del agente de voz con el plan _Lite_:

   ```
   ibmcloud service create VoiceAgent _Lite_ "My Voice Agent Service"
   ```
   {: codeblock}
