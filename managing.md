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


# Managing voice agents
{: #managing}

You can create, edit, clone, and remove voice agents on the _Manage_ dashboard. You can have multiple voice agents, but each voice agent must have a unique name and phone number.
{: shortdesc}

<!-- Title should be task oriented and descriptive-->
## Create a new voice agent
{: #config_instance}

When you create a voice agent, {{site.data.keyword.iva_short}} automatically searches for any available Watson service instances that you can use. If a service is not available, you can select to create them along with the voice agent or connect to services in a different {{site.data.keyword.Bluemix_short}} account space.

1. Click **Create a Voice Agent**.

1. For **Name**, specify a unique name for your voice agent. For example, `Customer Support - North America`.

1. For **Phone number**, add the number from your SIP trunk, including the country and area codes. For example, for a United States 800 number, specify the phone number as `18883334444`. The phone number can have spaces and `+ ( ) -` characters.

1. Optionally describe your voice agent.

1. Under **{{site.data.keyword.conversationshort}}**, configure the connection to your {{site.data.keyword.conversationshort}} service instance. You can use {{site.data.keyword.conversationshort}} instances or {{site.data.keyword.virtualagentfull}} instances in {{site.data.keyword.Bluemix_notm}} accounts that you or someone else owns. You can also connect to any of these options through a service orchestration engine.

  If you do not have a {{site.data.keyword.conversationshort}} service instance, you can select to create one from the **Service instance** menu.

  Alternatively, you can connect to other sources of a {{site.data.keyword.conversationshort}} dialog by changing the [**Service type**](#other_service).

  For **Service connection error response**, you can optionally change the default message that is streamed to callers if the configured service encounters an error after the call connects.

1. Under **{{site.data.keyword.speechtotextshort}}**, review the default configuration for your {{site.data.keyword.speechtotextshort}} service instance. If you do not have a {{site.data.keyword.speechtotextshort}} service instance, you can select to create one from the **Service instance** menu. Or, you can connect your voice agent to a {{site.data.keyword.speechtotextshort}} instance in a different {{site.data.keyword.Bluemix_notm}} account space by changing the [**Service type**](#other_service). {{site.data.keyword.iva_short}} supports only narrowband models.

1. Under **{{site.data.keyword.texttospeechshort}}**, review the default configuration for your {{site.data.keyword.texttospeechshort}} service instance. If you do not have a {{site.data.keyword.texttospeechshort}} service instance, you can select to create one from the **Service instance** menu. Or, you can connect your voice agent to a {{site.data.keyword.texttospeechshort}} instance in a different {{site.data.keyword.Bluemix_notm}} account space by changing the [**Service type**](#other_service).

1. You can also choose to enable event forwarding to collect information about calls handled by your voice agents in a {{site.data.keyword.cloudantfull}}. See [Enabling event forwarding for voice agents](event-forwarding.md)

1. Click **Create voice agent** to create your voice agent and any new services.

After you create the voice agent, test your voice agent by calling its phone number. You can view details about your phone call on the _Usage_ dashboard.  

## Editing a voice agent
{: #edit_va}

You can make changes to existing voice agents by editing them. To edit a voice agent, click **Edit Agent** from the list of options for the voice agent. Change the configuration, and save the changes.

## Cloning a voice agent
{: #clone_va}

When you clone a voice agent, all of the configuration for the Watson services are copied to a new agent. To clone a voice agent, click **Clone Agent** from the list of options for the voice agent. Give your voice agent a unique name and phone number, change any configuration options as needed, and save the changes.

## Deleting a voice agent
{: #delete_va}

You might want to delete a voice agent to free up the phone number. You can have only one voice agent for a phone number. To use a phone number for a different voice agent, you first must delete any voice agent that is using the phone number.

To delete a voice agent, click **Delete Agent** from the list of options for the voice agent, and save the changes. The voice agent is removed from the list of voice agents.

## Configuring a voice agent
{: #configure_va}

### Using service instances in other {{site.data.keyword.Bluemix_notm}}  workspaces
{: #other_service}

You can configure your voice agent to use  {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, or {{site.data.keyword.speechtotextshort}} service instances that belong to workspaces in other {{site.data.keyword.Bluemix_short}} accounts.

The credentials are not your {{site.data.keyword.Bluemix_notm}} user name and password, but rather encrypted credentials for the specific service instance.
{:tip}

In the **URL**, **User name**, and **Password** fields, configure the credentials for your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}},  or {{site.data.keyword.texttospeechshort}} service instances. To find these values, go to the  service instance that you want to configure, and select **Service credentials** and then **View credentials**.

* **{{site.data.keyword.conversationshort}}:** In the **Workspace ID** field, enter the ID of the workspace that you want to use with your voice agent. To find the workspace ID, launch the tool, and on the workspace that you want to integrate, click the Actions icon (**&vellip;**) and select **View details**.

* **{{site.data.keyword.speechtotextshort}}:**  In the **Model** field, select the speech language and format for your service.

  **Important**: You must specify a model for your service. {{site.data.keyword.iva_short}} supports only narrowband models.

* **{{site.data.keyword.texttospeechshort}}:** In the **Voice** field, select  the language and voice that your service uses.

  **Important**: You must specify a voice for your service.

**Remember:** For your voice agent to work, you must configure your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, and {{site.data.keyword.texttospeechshort}} for the same language. See [Supported languages](about.html#supported-languages)

### Configuring {{site.data.keyword.conversationshort}} for your voice agent
{: #conversation_va}

As an alternative to configuring a {{site.data.keyword.conversationshort}} service instance, you can connect to a service orchestration engine (SOE) or Watson {{site.data.keyword.virtualagentshort}}.

* **Service orchestration engine**: Connect to a {{site.data.keyword.conversationshort}} workspace or {{site.data.keyword.virtualagentshort}} through a [service orchestration engine (SOE)](about.html#arch-soe). An SOE intercepts messages to and from the service so that you can modify them by using third-party APIs.

  In the **URL** field, enter the full URL to your SOE workspace, such as `https://iva-soesample.myorg.net/SOE/myWorkspace`. If your SOE requires authentication (recommended), enter the user name and password in the respective fields.

* **Watson {{site.data.keyword.virtualagentshort}}**: Connect to a {{site.data.keyword.virtualagentshort}} chatbot instead of a {{site.data.keyword.conversationshort}} workspace. [{{site.data.keyword.virtualagentshort}}](https://console.bluemix.net/docs/services/virtual-agent/getting-started.html#getting-started) is built on the {{site.data.keyword.conversationshort}} service, but it provides pre-trained capabilities so you can get started with zero machine-learning experience.

  In the **URL** field, enter the URL credential for {{site.data.keyword.virtualagentshort}}, such as `https://api.ibm.com/virtualagent/run/api`. For the **Client ID** and **Client secret** fields, enter the authentication keys, which map to the `X-IBM-Client-Id` and `X-IBM-Client-Secret` header fields for API calls. In the **Bot ID** field, enter the ID for the bot to use for this voice agent. For information about how to find these values, see [Publishing the agent](../virtual-agent/publish.html) in the {{site.data.keyword.virtualagentshort}} documentation.
