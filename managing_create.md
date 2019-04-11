---

copyright:
  years: 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Creating a voice agent from the _Manage_ dashboard
{: #config_instance}

After you have created your {{site.data.keyword.iva_full}} service, you can create individual voice agents from the _Manage_ dashboard.
{: shortdesc}


## Creating a voice agent
{: #create_instance}

When you create a voice agent, {{site.data.keyword.iva_short}} automatically searches for any available Watson service instances that you can use. If a service is not available, you can select to create them along with the voice agent or connect to services in a different {{site.data.keyword.Bluemix_short}} account space. You can also choose to connect your voice agent to a Service Orchestration Engine, Google Speech to Text, or Google Text to Speech instance.

1. Go to the _Voice agents_ tab on the _Manage_ dashboard, and click **Create a Voice Agent**.

1. For **Name**, specify a unique name for your voice agent. For example, `Customer Support - North America`. The name may include up to 64 characters.

1. For **Phone number**, add the number from your SIP trunk, including the country and area codes. For example, for a United States 800 number, specify the phone number as `18883334444`. The phone number can have spaces and `+ ( ) -` characters, and a maximum of 30 characters.

1. By default, this phone number will be set as the **Primary Number** for the service; this is simply the first number shown to you when you have a list of numbers, and is only for display purposes.. See [Setting the Primary Number](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num) for changing the Primary Number.

1. You can also choose to add multiple numbers to one Voice Agent by clicking on **Manage**, next to **Phone Number**. See [Configuring Multiple Phone Numbers in a Voice Agent Instance](/docs/services/voice-agent?topic=voice-agent-multi_num) for information about how to set up and associate multiple numbers. You may also edit the numbers and add descriptions for the individual numbers from the **Manage** dialog box.

1. Alternatively, if you have multiple numbers in the Voice Agent, the **Phone Number** field will be greyed out. If you wish to edit the numbers simply click on the greyed out **Phone Number** field, or click on **Manage**. See [Editing a Number and/or Description for Multiple Numbers](/docs/services/voice-agent?topic=voice-agent-multi_num#edit_num).

1. Optionally describe your voice agent using up to 256 characters.

1. If you want to enable call transfer, enter the termination URI for your **Transfer default target**. See [Setting up call transfer](/docs/services/voice-agent?topic=voice-agent-call-transfer) for information about how to set up a termination URI. Do not use a personal phone number for your transfer target. The **Transfer default target** termination URI may include up to 256 characters.

1. Configure the connections to your Watson service instances. You can connect to multiple Watson service instances by configuring connections for both **Location 1** and **Location 2**. Having connections to multiple service instances enables your voice agent to switch to an alternate service instance if an outage occurs. See [Adding multiple Watson service locations](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).

1. Under **{{site.data.keyword.conversationshort}}**, configure the connection to your {{site.data.keyword.conversationshort}} service instance by clicking **Location 1** or **Location 2** and enabling the location that you selected. You can use {{site.data.keyword.conversationshort}} service instances in {{site.data.keyword.Bluemix_notm}} accounts that you or someone else owns. You can also connect to any of these options through a service orchestration engine.

   * If you are creating a voice agent in either the Dallas or Washington DC region and do not have a {{site.data.keyword.conversationshort}} service instance, you can create one in the **Service instance** menu.
   * Alternatively, you can connect to other sources of a {{site.data.keyword.conversationshort}} dialog or to connect with a SOE by changing the [**Service type**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service).
   * If you want to configure multiple service locations, click the other location option and select **Enable location** to configure the connection to your other {{site.data.keyword.conversationshort}} instance. See [Adding multiple Watson service locations](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).

1. Under **{{site.data.keyword.speechtotextshort}}**, review the default configuration for your {{site.data.keyword.speechtotextshort}} service instance by selecting **Location 1** or **Location 2** and enabling that location. You can customize your configuration with the following.
   * To connect your voice agent to an existing instance as your **Service type**, choose **My speech to text instance**. Next, for **Select model type**, choose **Narrowband**, **Broadband**, or **Both narrowband and broadband**, then select the language **Model**.
   * If you are creating a voice agent in the Dallas or Washington DC region and do not have a {{site.data.keyword.speechtotextshort}} service instance, you can create one from the **Service instance** menu.
   * For your **Service type**, you can choose either [a {{site.data.keyword.speechtotextshort}} instance in a different {{site.data.keyword.Bluemix_notm}} workspace](/docs/services/voice-agent?topic=voice-agent-other_service) or a [third-party speech to text service](managing_third_party.html), like Google Cloud Speech-to-Text.
   * If you want to configure multiple service locations, click the other location option and select **Enable location** to configure the connection to your other {{site.data.keyword.speechtotextshort}} instance. See [Adding multiple Watson service locations](/docs/services/voice-agent?topic=voice-agent-disaster-recovery).

1. Under **{{site.data.keyword.texttospeechshort}}**, review the default configuration for your {{site.data.keyword.texttospeechshort}} service instance by clicking **Location 1** or **Location 2** and enabling that location. You can customize your configuration with the following.
   * If you are creating a voice agent in the Dallas or Washington DC region and you do not have a {{site.data.keyword.texttospeechshort}} service instance, you can create one from the **Service instance** menu.
   * For your **Service type**, you can choose either a [{{site.data.keyword.texttospeechshort}} instance in a different {{site.data.keyword.Bluemix_notm}} workspace](/docs/services/voice-agent?topic=voice-agent-other_service) or a [third-party text to speech service](/docs/services/voice-agent?topic=voice-agent-third-party), like Google Cloud Text-to-Speech.
   * If you want to configure multiple service locations, click the other location option and select **Enable location** to configure the connection to your other {{site.data.keyword.texttospeechshort}} instance. See [Adding multiple Watson service locations](/docs/services/voice-agent?topic=voice-agent-disaster-recovery).

1. You can also choose to enable event forwarding to collect information about calls that are handled by your voice agents in a {{site.data.keyword.cloudantfull}}. See [Enabling event forwarding for voice agents](/docs/services/voice-agent?topic=voice-agent-event_forwarding). For more configuration options, see [Configuring a voice agent](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1. Click **Create voice agent** to create your voice agent and any new services.

After you create the voice agent, test your voice agent by calling its phone number. You can view details about your phone call on the _Usage_ dashboard. See [Viewing Usage and Call Logs](/docs/services/voice-agent?topic=voice-agent-logging).   
