---

copyright:
  years: 2019
lastupdated: "2019-06-24"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Creating an sms agent
{: #config_sms_instance}

After you have created your {{site.data.keyword.iva_full}} service, you can create individual sms agents from the _Manage_ dashboard.
{: shortdesc}

1. Go to the _Voice agents_ tab on the _Manage_ dashboard, and click **Create a Voice Agent**.

1. For **Agent Type**, select _SMS_.

1. Follow steps 3 through 6 in [creating a voice agent](https://test.cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-config_instance).

1. Under **SMS Provider**, enter the user name, password and API URL for your SMS provider. For example, if using _Twilio_, the username is your **Account SID**, the password is your **Auth Token** and your SMS provider is `https://api.twilio.com`

1. Under **Conversation**, configure the connection to your {{site.data.keyword.conversationshort}} service instance. You can use {{site.data.keyword.conversationshort}} service instances in {{site.data.keyword.Bluemix_notm}} accounts that you or someone else owns. You can also connect to any of these options through a service orchestration engine (SOE).

   * If you are creating an SMS agent in either the Dallas or Washington DC region and do not have a {{site.data.keyword.conversationshort}} service instance, you can create one in the **Service instance** menu.
   * Alternatively, you can connect to other sources of a {{site.data.keyword.conversationshort}} dialog or to connect with a SOE by changing the [**Service type**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service).
   * If you want to configure multiple service locations, click the other location option and select **Enable location** to configure the connection to your other {{site.data.keyword.conversationshort}} instance. For more information, see [Adding multiple Watson service locations](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).

1. You can also choose to enable event forwarding to collect information about calls that are handled by your voice agents in a {{site.data.keyword.cloudantfull}}. For more information, see [Enabling event forwarding for voice agents](/docs/services/voice-agent?topic=voice-agent-event_forwarding). For more configuration options, see [Configuring a voice agent](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1.  Click **Create voice agent** to create your SMS agent and any new services.

After you create the SMS agent, test your SMS agent by texting its phone number. You can view details about your interaction on the _Usage_ dashboard. See [Viewing Usage and Logs](/docs/services/voice-agent?topic=voice-agent-logging).   
