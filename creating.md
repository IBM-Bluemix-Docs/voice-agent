---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

keywords: service instance, creating, Lite plan

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:deprecated: .deprecated}
{:external: target="_blank" .external}


# Creating the service

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances, and access to free instances will be removed. Existing paid instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

You can create an {{site.data.keyword.iva_full}} service instance by using the {{site.data.keyword.Bluemix_short}} catalog or with an {{site.data.keyword.Bluemix_notm}} `ibmcloud` command.
{: shortdesc}


## Creating the service from the catalog
{: #catalog_create}

1. Go to the [{{site.data.keyword.iva_short}} catalog page](https://cloud.ibm.com/catalog/voice-agent-with-watson).

   The catalog page has information about the service and its pricing plans. You can change the **Service name** value.

2. Click **Create** to [create an agent from the _Manage_ dashboard](/docs/voice-agent?topic=voice-agent-config_instance#config_instance).

## Creating the service from the command line
{: #command_create}

1. [Install the {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli?topic=cloud-cli-install-ibmcloud-cli).

2. Run the [`ibmcloud` command](/docs/cli/idt?topic=cloud-cli-idt-cli#idt-cli) that creates your Voice Agent service instance with the _Lite_ plan:

   ```
   ibmcloud service create VoiceAgent _Lite_ "My Voice Agent Service"
   ```
   {: codeblock}
