---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-29"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Managing voice agents
{: #managing}

You can create, edit, clone, configure, and remove voice agents on the _Manage_ dashboard. You can have multiple voice agents, but each voice agent must have a unique name and phone number.
{: shortdesc}

<!-- Title should be task oriented and descriptive-->

## Creating a voice agent
{: #config_instance}

When you create a voice agent, {{site.data.keyword.iva_short}} automatically searches for any available Watson service instances that you can use. If a service is not available, you can select to create them along with the voice agent or connect to services in a different {{site.data.keyword.Bluemix_short}} account space.

1. Click **Create a Voice Agent**.

1. For **Name**, specify a unique name for your voice agent. For example, `Customer Support - North America`.

1. For **Phone number**, add the number from your SIP trunk, including the country and area codes. For example, for a United States 800 number, specify the phone number as `18883334444`. The phone number can have spaces and `+ ( ) -` characters.

1. Optionally describe your voice agent.

1. If you want to enable call transfer, you can configure a termination URI for your **Transfer Target**. See [Setting up call transfer](call-transfer.html). Do not use a personal phone number for your transfer target.

1. Configure the connections to your Watson service instances. You can connect to multiple Watson service instances by configuring connections for both **Location 1** and **Location 2**. Having connections to multiple service instances enables your voice agent to switch to an alternate service instance if an outage occurs. See [Adding multiple Watson service locations](#add_location).

    **Important**: _Trial_ and _Lite_ instances can connect only to the location where your {{site.data.keyword.iva_short}} service instance is created. Your second location is not a second voice agent. It acts only as a backup for disaster recovery.

1. Under **{{site.data.keyword.conversationshort}}**, configure the connection to your {{site.data.keyword.conversationshort}} service instance by clicking **Enable location 1** or **Enable location 2**. You can use {{site.data.keyword.conversationshort}} instances or {{site.data.keyword.virtualagentfull}} instances in {{site.data.keyword.Bluemix_notm}} accounts that you or someone else owns. You can also connect to any of these options through a service orchestration engine.

    * If you are creating a voice agent in either the US South or US East region and do not have a {{site.data.keyword.conversationshort}} service instance, you can create one in the **Service instance** menu.
    * Alternatively, you can connect to other sources of a {{site.data.keyword.conversationshort}} dialog by changing the [**Service type**](#other_service).
    * If you want to configure multiple service locations, click the other location option and select **Enable location** to configure the connection to your other {{site.data.keyword.conversationshort}} instance. See [Adding multiple Watson service locations](#add_location).

1. Under **{{site.data.keyword.speechtotextshort}}**, review the default configuration for your {{site.data.keyword.speechtotextshort}} service instance by clicking **Enable location 1** or **Enable location 2**. You can customize your configuration with the following.
    * If you are creating a voice agent in the US South or US East region and do not have a {{site.data.keyword.speechtotextshort}} service instance, you can create one from the **Service instance** menu.
    * Choose the [**Service type**](#other_service) to connect your voice agent to a {{site.data.keyword.speechtotextshort}} instance in a different {{site.data.keyword.Bluemix_notm}}.
    * If you want to configure multiple service locations, click the other location option and select **Enable location** to configure the connection to your other {{site.data.keyword.speechtotextshort}} instance. See [Adding multiple Watson service locations](#add_location).
    * **Remember:** {{site.data.keyword.iva_short}} supports only narrowband models.

1. Under **{{site.data.keyword.texttospeechshort}}**, review the default configuration for your {{site.data.keyword.texttospeechshort}} service instance by clicking **Enable location 1** or **Enable location 2**. 
    * If you are creating a voice agent in the US South or US East region and you do not have a {{site.data.keyword.texttospeechshort}} service instance, you can create one from the **Service instance** menu. 
    * You can also connect your voice agent to a {{site.data.keyword.texttospeechshort}} instance in a different {{site.data.keyword.Bluemix_notm}} account space by changing the [**Service type**](#other_service).
    * If you want to configure multiple service locations, click the other location option and select **Enable location** to configure the connection to your other {{site.data.keyword.texttospeechshort}} instance. See [Adding multiple Watson service locations](#add_location).

1. You can also choose to enable event forwarding to collect information about calls that are handled by your voice agents in a {{site.data.keyword.cloudantfull}}. See [Enabling event forwarding for voice agents](event-forwarding.html). For more configuration options, see [Configuring a voice agent](#configure_va).

1. Click **Create voice agent** to create your voice agent and any new services.

After you create the voice agent, test your voice agent by calling its phone number. You can view details about your phone call on the _Usage_ dashboard.  

## Editing the maximum concurrent connections
{: #edit_concurrency}

If you use the _Standard_ plan, you can change the maximum number of concurrent connections from the default settings. In all plans, you receive 2 concurrent connections at no charge. For more information, see the [Pricing plans](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

On the _Manage_ dashboard, you can see the maximum number of concurrent connections that are allowed in your listed plan in **Maximum concurrent connections**. You can also see the maximum number of concurrent connections that are used by your voice agents during the current month in **Maximum concurrent connections used**.

If you want to change the maximum number of concurrent connections in your plan, click the **Edit** icon. In the _Edit maximum concurrent connections_ window, choose the maximum number of concurrent connections, and click **Save**. The minimum number of concurrent connections that you can set through self-service is 10 and the maximum is 50. If you need more than 50 concurrent connections for your voice agent, see [Requesting assisted network setup](connect-SIP.html#request-setup).

### Concurrent connection pricing information
{: #concurrent-charge}

  * _Lite_, _Trial_, and _Standard_ plans include 2 concurrent connections at no charge.
  * _Premium_ plans are customized by instance.
  * In a _Standard_ plan, you have a minimum capacity of 10 concurrent connections.
  * Concurrent connection use is prorated by the month. If you use more than 2 concurrent connections in a day, you are charged a daily rate.
  * If you have a _Standard_ or _Premium_ plan, you can purchase a greater concurrent connection capacity.
  * You are charged a daily rate for the maximum concurrent connection capacity that you use in a day. For example, because your plan supports 2 concurrent connections free, and you set a maximum limit of 12 connections. If you use only 5 in a day, you are charged for 3.

For more information about plans, rates, and features, see [Pricing plans](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

## Editing a voice agent
{: #edit_va}

You can change existing voice agents by editing them. To edit a voice agent, click **Edit Agent** from the list of options for the voice agent. Change the configuration, and save the changes.

## Cloning a voice agent
{: #clone_va}

When you clone a voice agent, all of the configurations for the Watson services are copied to a new agent. To clone a voice agent, click **Clone Agent** from the list of options for the voice agent. Give your voice agent a unique name and phone number, change any configuration options as needed, and save the changes.

## Deleting a voice agent
{: #delete_va}

You might want to delete a voice agent to free up the phone number. You can have only one voice agent per phone number. To use a phone number for a different voice agent, you first must delete any voice agent that is using the phone number.

To delete a voice agent, click **Delete Agent** from the list of options for the voice agent, and save the changes. The voice agent is removed from the list of voice agents.

## Configuring a voice agent
{: #configure_va}

### Configuring advanced options
{: #config-advanced}

When you create or clone a voice agent, you can click **Show advanced** to view the following advanced configuration options.

* **{{site.data.keyword.conversationshort}} failure reply message (optional)**: The default response message that is sent to the message receiver if the call cannot connect to {{site.data.keyword.conversationshort}}.
* **Transfer failure reply message (optional)**: The default response message that is streamed to the caller if the call transfer fails.
* **Custom SIP INVITE Header (optional)**: Specifies custom SIP header to extract from incoming SIP INVITE requests
* **Send provisional ringing response from {{site.data.keyword.iva_short}}**: Sends a `180 ringing` response while {{site.data.keyword.iva_short}} processes an incoming call. Enabled by default.
* **Put caller on hold on transfer**: Puts the caller on hold during transfer. Enabled by default.
* **Disconnect call on transfer failure**: Determines whether or not to disconnect the call if a call transfer fails.  Enabled by default. If the setting is disabled and a call transfer fails, {{site.data.keyword.iva_short}} initiates a conversation turn. Then, {{site.data.keyword.conversationshort}} can either disconnect the call or transfer it to a different destination as configured in the dialog.
* **Notify {{site.data.keyword.conversationshort}} on network events**: When enabled, and a network error is detected, {{site.data.keyword.iva_short}} initiates a turn to the {{site.data.keyword.conversationshort}} service with the text "vgwNetworkWarningMessage". The `vgwNetworkWarnings` state variable contains a list of the network events that happened during the current turn. If disabled, a list of the network events that happened during the current turn is sent in the next turn event in the `vgwNetworkWarning`s state variable. Enabled by default.

### Adding multiple Watson service locations
{: #add_location}

If you have a _Standard_ or _Premium_ instance, you can connect your voice agent to multiple Watson services in different locations for service redundancy. _Trial_ and _Lite_ instances can connect only to the location where your {{site.data.keyword.iva_short}} service instance is created. Your second location is not a second voice agent. It acts only as a backup for disaster recovery.

Your voice agent uses the Watson service instances in order of geographical distance. For example, you can create a voice agent in the US East region, and your {{site.data.keyword.conversationshort}} services in US South and Sydney, Australia. Your voice agent uses the {{site.data.keyword.conversationshort}} US South region because US South is geographically nearer to US East than Sydney. By connecting to Watson services in multiple regions, if a Watson service is offline at one location, your voice agent can use the redundant service.

You can add a Watson service location to your voice agent configuration at any time. For information about connecting multiple service location instances when you create your voice agent, see [Creating a voice agent](#creating).

To add a Watson service location to an existing voice agent, click **Edit agent** for the voice agent you want to configure. Choose either **Location 1** or **Location 2** for the {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}}, or {{site.data.keyword.speechtotextshort}} instance that you want to connect, and add your configuration information. You can use Watson service instances in your workspace or in other workspaces. See [Using service instances in other {{site.data.keyword.Bluemix_notm}} workspaces](#other_services).

**Remember**: For service redundancy, you must use Watson service instances in different service regions for different locations.

You can enable or disable a location by using the **Enable location** box. **Location 1** is enabled by default and **Location 2** is disabled by default. At least one location must be enabled for each Watson service.

### Using service instances in other {{site.data.keyword.Bluemix_notm}} workspaces
{: #other_service}

You can configure your voice agent to use {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, or {{site.data.keyword.speechtotextshort}} service instances that belong to workspaces in other {{site.data.keyword.Bluemix_short}} accounts. To connect your voice agent to other service instances, you can use either the user name and password credentials or an API key for your service instances.

1. Select your **Service type** and **Region**.

1. Choose either **User name and password** or **API key**, and enter your service credentials.
  To find these values, go to the service instance that you want to configure, and select **Service credentials** and then **View credentials**.

  * **User name and password**: In the **URL**, **User name**, and **Password** fields, configure the credentials for your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}},  or {{site.data.keyword.texttospeechshort}} service instances.
  * **API key**: In the **URL** and **API key** fields, configure the credentials for your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}},  or {{site.data.keyword.texttospeechshort}} service instances.

  The credentials are not your {{site.data.keyword.Bluemix_notm}} user name and password, but rather encrypted credentials for the specific service instance.
  {:tip}

1. Enter your service instance information.

  * **{{site.data.keyword.conversationshort}}:** In the **Workspace ID** field, enter the ID of the workspace that you want to use with your voice agent. To find the workspace ID, launch the tool, and on the workspace that you want to integrate, click the Actions icon (**&vellip;**) and select **View details**.
  * **{{site.data.keyword.speechtotextshort}}:** In the **Model** field, select the speech language and format for your service. {{site.data.keyword.iva_short}} supports only narrowband models.
  * **{{site.data.keyword.texttospeechshort}}:** In the **Voice** field, select the language and voice that your service uses. You must specify a voice for your service.

**Remember:** For your voice agent to work, you must configure your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, and {{site.data.keyword.texttospeechshort}} for the same language. See [Supported languages](about.html#supported-languages).

### Configuring {{site.data.keyword.conversationshort}} for your voice agent
{: #conversation_va}

As an alternative to configuring a {{site.data.keyword.conversationshort}} service instance, you can connect to a service orchestration engine (SOE) or Watson {{site.data.keyword.virtualagentshort}}.

* **Service orchestration engine**: Connect to a {{site.data.keyword.conversationshort}} workspace or {{site.data.keyword.virtualagentshort}} through a [service orchestration engine (SOE)](about.html#arch-soe). An SOE intercepts messages to and from the service so that you can modify them by using third-party APIs.

  In the **URL** field, enter the full URL to your SOE workspace, such as `https://iva-soesample.myorg.net/SOE/myWorkspace`. If your SOE requires authentication (recommended), enter the user name and password in the respective fields.

  **Important**: For data security, make sure that you use a secure URL for your SOE workspace, by using `https:` instead of `http:`, and require authentication. See [Information security and data privacy](infosec.html) to learn more about security considerations.

* **Watson {{site.data.keyword.virtualagentshort}}**: Connect to a {{site.data.keyword.virtualagentshort}} chatbot instead of a {{site.data.keyword.conversationshort}} workspace. [{{site.data.keyword.virtualagentshort}}](../virtual-agent/getting-started.html#getting-started) is built on the {{site.data.keyword.conversationshort}} service, but it provides pre-trained capabilities so you can get started with zero machine-learning experience.

  In the **URL** field, enter the URL credential for {{site.data.keyword.virtualagentshort}}, such as `https://api.ibm.com/virtualagent/run/api`. For the **Client ID** and **Client secret** fields, enter the authentication keys, which map to the `X-IBM-Client-Id` and `X-IBM-Client-Secret` header fields for API calls. In the **Bot ID** field, enter the ID for the bot to use for this voice agent. For more information about how to find these values, see [Publishing the agent](../virtual-agent/publish.html) in the {{site.data.keyword.virtualagentshort}} documentation.
