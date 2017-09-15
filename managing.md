---

copyright:
  years: 2017
lastupdated: "2017-09-08"

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
## Adding a {{site.data.keyword.iva_short}} service instance
{: #config_instance}

1. Click **Add a Voice Agent**.

3. Optionally, for **Name**, specify a unique name for your voice agent. For example, `Customer Support - North America`.

4. For **Phone number**, add the number from your SIP trunk. For example, a United States 800 number uses the `18883334444` format. The phone number can have spaces and `+ ( ) -` characters.

5. Optionally, describe your voice agent.

6. Under **{{site.data.keyword.conversationshort}}**, configure the connection to the {{site.data.keyword.conversationshort}} service.
   * To use an SOE, select **Connect to service orchestration engine (SOE)** and provide a URL, user name, and password. An SOE intercepts messages to and from the {{site.data.keyword.conversationshort}} service so that you can modify them by using third-party APIs. For more information, see [Architecture with a service orchestration engine](about.html#arch-soe).
   * To use Watson {{site.data.keyword.conversationshort}}, select your Watson {{site.data.keyword.conversationshort}} service instance, the service credentials, and a workspace. For the workspace, [create new intents and entries](../conversation/configure-workspace.html#configuring-a-conversation-workspace) with the {{site.data.keyword.conversationshort}} tool or by uploading a JSON or text file. Or, to quickly get a workspace, [import our sample conversation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json){: new_window}.

7. Under **{{site.data.keyword.speechtotextshort}}**, select your Watson {{site.data.keyword.speechtotextshort}} service instance, the service credentials, and a model.

6. Under **{{site.data.keyword.texttospeechshort}}**, select your Watson {{site.data.keyword.texttospeechshort}} service instance, the service credentials, and a voice.

7. Click **Save changes**.

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
