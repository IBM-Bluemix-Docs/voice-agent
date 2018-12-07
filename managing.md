---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Managing service instances and voice agents
{: #managing}

You can use the _Manage_ dashboard to change your service instance configurations and create, edit, clone, configure, or remove individual voice agents. You can have multiple voice agents in your service instance, but each voice agent must have a unique name and phone number.
{: shortdesc}

## Navigating to your Voice Agent service dashboard
{: #navigate_manage}

You can find the _Manage_ dashboard from your {{site.data.keyword.iva_short}} service dashboard.

1. Go to your [{{site.data.keyword.Bluemix_notm}} account resource list](https://cloud.ibm.com/resources).

1. From the list of **Services**, select your **Voice Agent** service instance to open the service dashboard on the _Manage_ tab.

## Editing the maximum concurrent connections for your service instance
{: #edit_service}

In all plans, you receive 2 concurrent connections at no charge. If you use the _Standard_ or _Premium_ plans, you can [change the maximum number of concurrent connections](managing_concurrency.html) from the default settings from the _Instances_ tab.

## Creating a voice agent
{: #create_va}

[Create a new voice agent](managing_create.html) from the _Voice agents_ tab on the _Manage_ dashboard.

## Editing a voice agent
{: #edit_va}

You can change existing voice agents by editing them in the _Voice agents_ tab on the _Manage_ dashboard. To edit a voice agent, click **Edit Agent** from the list of options for the voice agent. Change the configuration, and save the changes.

## Cloning a voice agent
{: #clone_va}

When you clone a voice agent, all of the configurations for the Watson services are copied to a new agent. To clone a voice agent, click **Clone Agent** from the list of options for the voice agent. Give your voice agent a unique name and phone number, change any configuration options as needed, and save the changes.

## Deleting a voice agent
{: #delete_va}

You might want to delete a voice agent to free up the phone number. You can have only one voice agent per phone number. To use a phone number for a different voice agent, you first must delete any voice agent that is using the phone number.

To delete a voice agent, go to the _Voice agents_ tab, click **Delete Agent** from the list of options for the voice agent, and save the changes. The voice agent is removed from the list of voice agents.

## Configuring a voice agent
{: #configure_va}

When you create, clone, or edit a voice agent, you can make changes to the configuration settings for your voice agent and connections to related services.

* **[Configuring multiple service locations](managing_disaster_recovery.html):** Include multiple service locations for your connected services to support service redundancy.
* **[Connecting with third-party speech and text services](managing_third_party.html):** Instead of using {{site.data.keyword.texttospeechshort}} or {{site.data.keyword.speechtotextshort}}, you can connect your voice agent to third party APIs, like Google Cloud Speech-to-Text.
* **[Using services in other {{site.data.keyword.Bluemix_notm}} workspaces](managing_other.html):** You can configure your voice agent to use {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, or {{site.data.keyword.speechtotextshort}} service instances that belong to workspaces in other {{site.data.keyword.Bluemix_short}} accounts.
* **[Configuring Watson Assistant with a Service Orchestration Engine](managing_SOE.html):** You can connect to a {{site.data.keyword.conversationshort}} workspace through a service orchestration engine (SOE). An SOE intercepts messages to and from the service so that you can modify them by using third-party APIs.
* **[Enabling event forwarding for voice agents](event-forwarding.html):** You might want to collect and analyze call data from {{site.data.keyword.iva_short}} to improve how natural the conversation feels to the caller. Each voice agent that you create can forward event reports to a specified {{site.data.keyword.cloudant_short_notm}} that you manage.

## Configuring advanced voice agent options
{: #config-advanced}

When you create or clone a voice agent, you can click **Show advanced** to view the following advanced configuration options.

* **{{site.data.keyword.conversationshort}} failure reply message (optional)**: The default response message that is sent to the message receiver if the call cannot connect to {{site.data.keyword.conversationshort}}.
* **Transfer failure reply message (optional)**: The default response message that is streamed to the caller if the call transfer fails.
* **Custom SIP INVITE Header (optional)**: Specifies custom SIP header to extract from incoming SIP INVITE requests
* **Send provisional ringing response from {{site.data.keyword.iva_short}}**: Sends a `180 ringing` response while {{site.data.keyword.iva_short}} processes an incoming call. Enabled by default.
* **Put caller on hold on transfer**: Puts the caller on hold during transfer. Enabled by default.
* **Disconnect call on transfer failure**: Determines whether or not to disconnect the call if a call transfer fails.  Enabled by default. If the setting is disabled and a call transfer fails, {{site.data.keyword.iva_short}} initiates a conversation turn. Then, {{site.data.keyword.conversationshort}} can either disconnect the call or transfer it to a different destination as configured in the dialog.
* **Notify {{site.data.keyword.conversationshort}} on network events**: When enabled, and a network error is detected, {{site.data.keyword.iva_short}} initiates a turn to the {{site.data.keyword.conversationshort}} service with the text "vgwNetworkWarningMessage". The `vgwNetworkWarnings` state variable contains a list of the network events that happened during the current turn. If disabled, a list of the network events that happened during the current turn is sent in the next turn event in the `vgwNetworkWarning`s state variable. Enabled by default.
