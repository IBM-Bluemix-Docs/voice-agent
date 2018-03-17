---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Creating the service

{: shortdesc}
You can create an {{site.data.keyword.iva_full}} service instance by using the {{site.data.keyword.Bluemix_short}} catalog or a {{site.data.keyword.Bluemix_notm}} `bx` command.

<!-- Title should be task oriented and descriptive-->
## Creating the service from the catalog
{: #catalog_create}

1. Go to the [{{site.data.keyword.iva_short}} catalog page](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

   The catalog page has information about the service and its pricing plans. You can change the **Service name** value. For this release, the Trial plan is no charge.

2. Click **Create**.

## Creating the service from the command line
{: #command_create}

1. [Install the {{site.data.keyword.Bluemix_notm}} CLI](../../cli/reference/bluemix_cli/get_started.html).

2. Run the [`bx` command](../../cli/reference/bluemix_cli/bx_cli.html#bluemix_cli) that creates your VoiceAgent service instance with the Trial plan:

   ```
   bx service create VoiceAgent Trial "My Voice Agent Service"
   ```
   {: codeblock}

## Next steps
{: #next}

Create the voice agent from the _Manage_ dashboard. See [Managing voice agents](managing.html).
