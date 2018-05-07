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

# Getting started tutorial
{{site.data.keyword.iva_full}} helps you integrate a set of orchestrated Watson services with the telephone network by using the Session Initiation Protocol (SIP). This tutorial describes how to set up a cognitive voice agent that you call from any phone.
{: shortdesc}

Watch a demonstration of how to create your first voice agent in this [{{site.data.keyword.iva_full_notm}} tutorial ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/).
{: tip}

## Before you begin
{: #prereqs}

Create an [{{site.data.keyword.Bluemix_short}} account](https://console.bluemix.net/), or log in to an existing one.

## Step 1: Create a {{site.data.keyword.iva_short}} service instance on {{site.data.keyword.Bluemix_notm}}
{: #step1}

From the [{{site.data.keyword.iva_short}} catalog page](https://console.bluemix.net/catalog/services/voice-agent-with-watson), review the service information, and then click **Create**.

After you create the service, make note of the voice agent endpoint on the _Getting started_ dashboard. You need the endpoint SIP URI to configure your SIP trunk.

## Step 2: Set up a SIP trunk to forward calls to {{site.data.keyword.iva_short}}
{: #step2}

This release was tested with a [Twilio&reg; ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.twilio.com/){: new_window} SIP trunk.

  **Note:** Creating a [Twilio account  ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.twilio.com/try-twilio){: new_window} requires a credit card, which is periodically charged based on your usage of the SIP trunk that you configure. If you already have a Twilio account, you can use the existing account.

1. Create a SIP trunk from a supported provider.
    1. Create a Twilio account on the [Twilio website  ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.twilio.com/try-twilio){: new_window}

    1. Create a SIP trunk with your Twilio account.

    2. From the Twilio website, go to the Elastic SIP Trunking dashboard.

    3. Select **Trunks** from the navigation bar and create a SIP trunk. If you already have a SIP trunk, click the **+** icon. In the resulting dialog box, enter a name for your SIP trunk and click **Create**.

1. In your SIP trunk, configure your voice agent's SIP URI.
    4. From the Elastic SIP Trunks page, select your SIP trunk.

    5. Select **Origination** from the navigation bar for your SIP trunk and configure the origination SIP URI. You can include multiple host names to prevent service failures by selecting  the **+** icon.

    The IP address or the host name is the value that you noted on the _Getting Started_ dashboard of your {{site.data.keyword.iva_short}} service instance. When you configure the origination URI, it must be in SIP URI format, such as `sip:http://us-south.voiceagent.cloud.ibm.com/`. By including multiple host names or IP addresses, if the first host endpoint fails or is out of service, your SIP trunk provider directs calls to the next host name on the list.

1. Create a phone number from your SIP provider, and assign it to your SIP trunk.
     1. Select **Numbers** from the navigation bar for your SIP trunk. Then, create a phone number and assign it to your SIP trunk.

     On the Numbers page, click **Buy a Number** or, if you already have a number, click the **+** icon. A panel displays where you can provision a new phone number in your region. Assign the number to the SIP trunk you created by going back to the SIP trunk and clicking the Number icon.


## Step 3: Create and connect your voice agent
{: #step3}

1. Go to the _Manage_ dashboard on the {{site.data.keyword.iva_short}} dashboard, and click **Create a Voice Agent**.
2. Enter the basic settings for your voice agent:
  * **Name:** A unique name for your voice agent, such as `Customer Support`
  * **Phone number:** The full phone number that you associated with your SIP trunk, including the country and area codes
  * **Description:** An optional description of its use

3. Create the {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, and {{site.data.keyword.texttospeechshort}} service instances for your voice agent. You can choose to create a voice agent with either of the following methods:
  * Click **Create a voice agent** to create all of the services and a voice agent with the default configuration in a single step.
  * Or, click each of the service names to create the services yourself, and then return to {{site.data.keyword.iva_short}} and create a voice agent separately.

   If you manually created a {{site.data.keyword.conversationshort}} service instance, add a dialog so that you can test your voice agent.  To quickly get started, clone the [sample conversation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) from GitHub and then [import the sample](../conversation/configure-workspace.html#creating-workspaces) as a workspace:

   1. On the sample conversation GitHub page, click the `1` line number and select **... > Copy line**. Paste the copied text into a file, and save it as a JSON file such as `voice-gateway-conversation-en.json`.
   2. Launch the {{site.data.keyword.conversationshort}} tool. On the Workspaces page, click the ![Import workspace](../conversation/images/workspace_import.png) icon and import the JSON file.

  Alternatively, you can [build your own dialog](https://console.bluemix.net/docs/services/conversation/dialog-build.html) to simulate your production environment. At minimum, your dialog must contain a node with the `conversation_start` condition and node with a default response.

## Next steps
{: #next}

Test your voice agent by calling its associated phone number. If you hear a response, your voice agent is active!

If you do not hear a response, you can examine your call logs and voice agent usage on the _Usage_ dashboard. See [Viewing usage and call logs](logging.md).

You can edit the settings for your voice agent and create or remove voice agents from the _Manage_ dashboard. For more information, see [Managing voice agents](managing.html).
