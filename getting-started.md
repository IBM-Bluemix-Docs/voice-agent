---

copyright:
  years: 2017
lastupdated: "2017-11-07"

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

## Before you begin
{: #prereqs}

Create an [{{site.data.keyword.Bluemix_short}} account](https://console.bluemix.net/), or log in to an existing one.

## Step 1: Create a {{site.data.keyword.iva_short}} service instance on {{site.data.keyword.Bluemix_notm}}
{: #step1}

From the [{{site.data.keyword.iva_short}} catalog page](https://console.bluemix.net/catalog/services/voice-agent-with-watson), review the service information, and then click **Create**.

After you create the service, make note of the voice agent endpoint on the _Getting started_ page. You need the endpoint SIP URI to configure your SIP trunk.

## Step 2: Set up a SIP trunk to forward calls to {{site.data.keyword.iva_short}}
{: #step2}

This experimental release was tested with a [Twilio&reg; ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.twilio.com/){: new_window} SIP trunk.

1. Create an account on the [Twilio website ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.twilio.com/try-twilio){: new_window}.

   **Note:** Creating an account requires a credit card, which is periodically charged based on your usage of the SIP trunk that you configure. If you already have a Twilio account, you can use the existing account.

2. From the Twilio website, go to the Elastic SIP Trunking dashboard.

3. Select **Trunks** from the navigation bar and create a SIP trunk. If you already have a SIP trunk, click the **+** icon. In the resulting dialog box, enter a name for your SIP trunk and click **Create**.

4. From the Elastic SIP Trunks page, select your SIP trunk.

5. Select **Origination** from the navigation bar for your SIP trunk and configure the origination SIP URI.

   The IP address or the host name is the value that you noted on the _Getting Started_ page of your {{site.data.keyword.iva_short}} service instance. When you configure the origination URI, it must be in SIP URI format, such as `sip:23.246.192.240`.

6. Select **Numbers** from the navigation bar for your SIP trunk. Then, create a phone number and assign it to your SIP trunk.

   On the Numbers page, click **Buy a Number** or, if you already have a number, click the **+** icon. A panel displays where you can provision a new phone number in your region. Assign the number to the SIP trunk you created by going back to the SIP trunk and clicking the Number icon.


## Step 3: Create and configure your voice agent
{: #step3}

1. Go to the _Manage_ page on the {{site.data.keyword.iva_short}} dashboard, and click **Add a Voice Agent**.
2. Enter the basic settings for your voice agent:
  * **Name:** A unique name for your voice agent, such as `Customer Support`
  * **Phone number:** The full phone number that you associated with your SIP trunk, including the country and area codes
  * **Description:** An optional description of its use
3. Create the Watson {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, and {{site.data.keyword.texttospeechshort}} service instances for your voice agent.
  * Click **Create for me** to create all of the services and a voice agent with the default configuration.
  * Click **Go to catalog** to create the services yourself, and then return to {{site.data.keyword.iva_short}} and add a voice agent separately.

   If you manually created a {{site.data.keyword.conversationshort}} service instance, add a dialog so that you can test your voice agent.  To quickly get started, clone the [sample conversation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) from GitHub and then [import the sample](../conversation/configure-workspace.html#creating-workspaces) as a workspace:

   1. On the sample conversation GitHub page, click the `1` line number and select **... > Copy line**. Paste the copied text into a file, and save it as a JSON file such as `voice-gateway-conversation-en.json`.
   2. Launch the {{site.data.keyword.conversationshort}} tool. On the Workspaces page, click the ![Import workspace](../conversation/images/workspace_import.png) icon and import the JSON file.

  Alternatively, you can [build your own dialog](https://console.bluemix.net/docs/services/conversation/dialog-build.html) to simulate your production environment. At minimum, your dialog must contain a node with the `conversation_start` condition and node with a default response.

## Next steps
{: #next}

Test your voice agent by calling its associated phone number. If you hear a response, your voice agent is active!

You can edit the settings for your voice agent and add or remove voice agents from the _Manage_ page. For more information, see [Managing voice agents](managing.html).
