---

copyright:
  years: 2017
lastupdated: "2017-10-23"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Managing voice agents
{: #managing}

You can add, edit, and remove voice agents on the _Manage_ page.
{: shortdesc}

<!-- Title should be task oriented and descriptive-->
## Adding a voice agent
{: #config_instance}

When you add a voice agent, {{site.data.keyword.iva_short}} automatically searches for any available Watson service instances that you can use.

1. Click **Add a Voice Agent**.

1. For **Name**, specify a unique name for your voice agent. For example, `Customer Support - North America`.

1. For **Phone number**, add the number from your SIP trunk, including the country and area codes. For example, for a United States 800 number, specify the phone number as `18883334444`. The phone number can have spaces and `+ ( ) -` characters.

1. Optionally describe your voice agent.

1. Under **{{site.data.keyword.conversationshort}}**, configure the connection to your {{site.data.keyword.conversationshort}} service instance. You can use {{site.data.keyword.conversationshort}} instances under your or others' {{site.data.keyword.Bluemix_short}} accounts, {{site.data.keyword.virtualagentfull}}, or connect to any of these through a service orchestration engine.

  If you already have a {{site.data.keyword.conversationshort}} workspace on your {{site.data.keyword.Bluemix_short}} account, the {{site.data.keyword.conversationshort}} service credentials and workspace ID are selected by default. You can change the selections to a different service instance or workspace.

  If you do not have a {{site.data.keyword.conversationshort}} service instance, you can create one from the catalog. Be sure to add a workspace with a dialog so you can test your voice agent. To quickly get started, copy and save the [sample conversation JSON file ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) and then [import it as a workspace](https://console.bluemix.net/docs/services/conversation/configure-workspace.html#creating-workspaces).

  Alternatively, you can connect to other sources of a {{site.data.keyword.conversationshort}} dialog by changing the **Service type**:
   * **Other {{site.data.keyword.conversationshort}} service instance**: Connect to a {{site.data.keyword.conversationshort}} workspace that is not under your {{site.data.keyword.Bluemix_short}} account.

     In the **URL**, **User name**, and **Password** fields, configure the credentials for the {{site.data.keyword.conversationshort}} service instance. To find these values, go to the  {{site.data.keyword.conversationshort}} service instance that you want to configure, and select **Service credentials** and then **View credentials**. In the **Workspace ID** field, enter the ID of the workspace with the dialog to use for this voice agent. To find the workspace ID, launch the {{site.data.keyword.conversationshort}} tool, and on the workspace that you want to integrate, click the Actions icon (**&vellip;**) and select **View details**.

     The credentials are not your {{site.data.keyword.Bluemix_short}} user name and password, but rather encrypted credentials for the specific service instance.
     {:tip}
   * **Service orchestration engine**: Connect to a {{site.data.keyword.conversationshort}} workspace or {{site.data.keyword.virtualagentshort}} through a [service orchestration engine (SOE)](about.html#arch-soe). An SOE intercepts messages to and from the service so that you can modify them by using third-party APIs.

     In the **URL** field, enter the full URL to your SOE workspace, such as `https://iva-soesample.myorg.net/SOE/myWorkspace`. If your SOE requires authentication (recommended), enter the user name and password in the respective fields.
   * **Watson {{site.data.keyword.virtualagentshort}}**: Connect to a {{site.data.keyword.virtualagentshort}} chatbot instead of a {{site.data.keyword.conversationshort}} workspace. [{{site.data.keyword.virtualagentshort}}](https://console.bluemix.net/docs/services/virtual-agent/getting-started.html#getting-started) is built on the {{site.data.keyword.conversationshort}} service, but it provides pre-trained capabilities so you can get started with zero machine-learning experience.

     In the **URL** field, enter the URL credential for {{site.data.keyword.virtualagentshort}}, such as `https://api.ibm.com/virtualagent/run/api`. For the **Client ID** and **Client secret** fields, enter the authentication keys, which map to the `X-IBM-Client-Id` and `X-IBM-Client-Secret` header fields for API calls. In the **Bot ID** field, enter the ID for the bot to use for this voice agent. For information about how to find these values, see [Publishing the agent](../virtual-agent/publish.html) in the {{site.data.keyword.virtualagentshort}} documentation.

  For **Service connection error response**, you can optionally change the default message that is streamed to callers if the configured service encounters an error during a call.

1. Under **{{site.data.keyword.speechtotextshort}}**, review the default configuration for your {{site.data.keyword.speechtotextshort}} service instance. If you do not have a {{site.data.keyword.speechtotextshort}} service instance, create one from the catalog.

1. Under **{{site.data.keyword.speechtotextshort}}**, review the default configuration for your {{site.data.keyword.texttospeechshort}} service instance. If you do not have a {{site.data.keyword.texttospeechshort}} service instance, create one from the catalog.

1. Click **Save changes** to add your voice agent.

### Next steps
{: #next}

Test your voice agent by calling its phone number. You can view details about your phone call on the _Usage_ page.  

If you have more SIP trunk phone numbers, you can click **Add a Voice Agent** and create more voice agents.

## Editing a voice agent
{: #edit_instance}

To edit a voice agent, click **Edit Agent** from the list of options for the voice agent. Change the configuration and save the changes.

## Deleting a voice agent
{: #delete_instance}

To delete a voice agent, click **Delete Agent** from the list of options for the voice agent, and save the changes. The voice agent is removed from the list of voice agents.

You might want to delete a voice agent to free up the phone number. You can have only one voice agent for a phone number. To use a phone number for a different voice agent, you first must delete any voice agent that is using the phone number.
