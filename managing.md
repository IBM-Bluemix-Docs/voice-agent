---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-15"

keywords: call transfer, service instance
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


# Managing service instances and agents
{: #managing}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances, and access to free instances will be removed. Existing paid instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

You can use the _Manage_ dashboard to change your service instance configurations and create, edit, clone, configure, or remove individual agents. You can have multiple agents in your service instance, and each agent can have up to 1000 unique numbers and descriptions. However, each agent must have a unique name and at least one phone number.

* **NOTE**: A single {{site.data.keyword.iva_full}} service instance can have up to 150 agents.
{: shortdesc}

## Navigating to your Agent service dashboard
{: #navigate_manage}

You can find the _Manage_ dashboard from your {{site.data.keyword.iva_short}} service dashboard.

1. Go to your [{{site.data.keyword.Bluemix_notm}} account resource list](https://cloud.ibm.com/resources).

1. From the list of **Services**, select your **Agent** service instance to open the service dashboard on the _Manage_ tab.

## Agent Summary
{: #agent_summary}

If you already have an existing agent, you can see a summary of all the numbers, descriptions, and configuration settings for the agent. To see the summary, click the dropdown arrow to the left of the agent **Name**. The summary then expands.

While the agent can contain multiple numbers, on the agent summary only the **Primary Number** is selected to be shown. By default, it is the first number added to the agent, and is only for display, and has no functional purpose. If you want to display a different number from the agent, see [Managing Multiple Numbers](/docs/voice-agent?topic=voice-agent-multi_num#primary_num).

You can view all the numbers in the agent from the agent summary. After the summary of the configuration is expanded, click the **View Numbers** button, and a list of all the numbers will appear in a new **Manage** dialog box. See the [Managing Multiple Numbers](/docs/voice-agent?topic=voice-agent-multi_num) page for more information on working with the **Manage** dialog box.

## Editing the maximum concurrent connections for your service instance
{: #edit_service}

In all plans, you receive 2 concurrent connections at no charge. If you use the _Standard_ or _Premium_ plans, you can [change the maximum number of concurrent connections](/docs/voice-agent?topic=voice-agent-edit_concurrency) from the default settings from the _Instances_ tab.

## Creating a voice agent
{: #create_va}

[Create a new voice agent](/docs/voice-agent?topic=voice-agent-config_instance) from the _Agents_ tab on the _Manage_ dashboard.

## Editing an agent
{: #edit_va}

You can change existing agents by editing them in the  _Agents_ tab on the _Manage_ dashboard. To edit an agent, click **Edit Agent** from the list of options for the agent. Change the configuration, and save the changes.

## Cloning an agent
{: #clone_va}

When you clone an agent, all of the configurations for the Watson services are copied to a new agent. To clone an agent, click **Clone Agent** from the list of options for the agent. Give your agent a unique name and phone number, change any configuration options as needed, and save the changes.

## Deleting an agent
{: #delete_va}

You might want to delete an agent to free up the phone number. You can have only one agent per phone number. To use a phone number for a different agent, you first must delete any agent that is using the phone number.

To delete an agent, go to the _Agents_ tab, click **Delete Agent** from the list of options for the agent, and save the changes. The agent is removed from the list of agents.

## Searching an agent by Number or Description
{: #search}

You can search for agents based on the numbers or descriptions that are saved in the agent.

In the _Search_ bar, you can type a number or description. As you type, the search results are updated automatically.  

## Configuring an agent
{: #configure_va}

When you create, clone, or edit an agent, you can make changes to the configuration settings for your agent and connections to related services.

* **[Configuring multiple phone numbers](/docs/voice-agent?topic=voice-agent-multi_num):** You can configure your Agent to include multiple phone numbers.
* **[Configuring multiple service locations](/docs/voice-agent?topic=voice-agent-disaster-recovery):** Include multiple service locations for your connected services to support service redundancy.
* **[Connecting with third-party speech and text services](/docs/voice-agent?topic=voice-agent-third-party):** Instead of using {{site.data.keyword.texttospeechshort}} or {{site.data.keyword.speechtotextshort}}, you can connect your agent to third-party APIs, like Google Cloud Speech-to-Text.
* **[Using services in other {{site.data.keyword.Bluemix_notm}} workspaces](/docs/voice-agent?topic=voice-agent-other_service):** You can configure your agent to use {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, or {{site.data.keyword.speechtotextshort}} service instances that belong to workspaces in other {{site.data.keyword.Bluemix_short}} accounts.
* **[Configuring Watson Assistant with a Service Orchestration Engine](/docs/voice-agent?topic=voice-agent-conversation_va):** You can connect to a {{site.data.keyword.conversationshort}} skill through a service orchestration engine (SOE). An SOE intercepts messages to and from the service so that you can modify them by using third-party APIs.
* **[Enabling event forwarding for agents](/docs/voice-agent?topic=voice-agent-event_forwarding):** You might want to collect and analyze call data from {{site.data.keyword.iva_short}} to improve how natural the conversation feels to the caller. Each agent that you create can forward event reports to a specified {{site.data.keyword.cloudant_short_notm}} that you manage.

## Configuring advanced agent options
{: #config-advanced}

When you create or clone an agent, you can click **Show advanced** to view the following advanced configuration options.

* **Conversation read timeout (optional)**: This option sets the time, in seconds, that the Agent waits for a response from Watson Assistant. If the time is exceeded, the Agent reattempts to contact Watson Assistant. If the service still cannot be reached, the call fails. Set to 5 seconds by default.
* **{{site.data.keyword.conversationshort}} failure reply message (optional)**: The default response message that is sent to the message receiver if the call cannot connect to {{site.data.keyword.conversationshort}}. You can enter up to 1024 characters.
* **Transfer failure reply message (optional)**: The default response message that is streamed to the caller if the call transfer fails. You can enter up to 1024 characters.
* **Custom SIP INVITE Header (optional)**: Specifies custom SIP header to extract from incoming SIP INVITE requests. You can enter up to 1024 characters.
* **Send provisional ringing response from {{site.data.keyword.iva_short}}**: Sends a `180 ringing` response while {{site.data.keyword.iva_short}} processes an incoming call. Enabled by default.
* **Put caller on hold on transfer**: Puts the caller on hold during transfer. Enabled by default.
* **Disconnect call on transfer failure**: Determines whether to disconnect the call if a call transfer fails.  Enabled by default. If the setting is unavailable and a call transfer fails, {{site.data.keyword.iva_short}} initiates a conversation turn. Then, {{site.data.keyword.conversationshort}} can either disconnect the call or transfer it to a different destination as configured in the dialog.
* **Notify {{site.data.keyword.conversationshort}} on network events**: When enabled, and a network error is detected, {{site.data.keyword.iva_short}} initiates a turn to the {{site.data.keyword.conversationshort}} service with the text "vgwNetworkWarningMessage". The `vgwNetworkWarnings` state variable contains a list of the network events that happened during the current turn. If unavailable, a list of the network events that happened during the current turn is sent in the next turn event in the `vgwNetworkWarning`s state variable. Enabled by default.
