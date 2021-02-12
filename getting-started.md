---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-06-24"

keywords: getting started, voice agent, creating a SIP trunk, creating and connecting your voice agent, voice agent with watson, tutorial, phone number, IBM Cloud

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

# Getting started with Voice Agent with Watson
{: #getting-started}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances. Existing instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

{{site.data.keyword.iva_full}} helps you integrate a set of orchestrated Watson services with the telephone network by using the Session Initiation Protocol (SIP). This tutorial describes how to set up a cognitive agent that you can call from any phone.
{: shortdesc}

A new SMS feature is available for {{site.data.keyword.iva_full_notm}}. Not all of the procedures that are described on this page are necessary to configure SMS functionality. See the [Voice Agent Getting started tutorial](/docs/voice-agent?topic=voice-agent-connect-sms) for instructions on how to connect SMS with {{site.data.keyword.iva_full_notm}}
{: tip}

Watch a demonstration of how to create your first agent in this [{{site.data.keyword.iva_full_notm}} tutorial ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/).
{: tip}

If you require any assistance, find us on Slack in the [IBM Cloud Technology ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) team under the `#ibmvoicegateway` channel
{: tip}

## Before you begin
{: #prereqs}

Create an account or log in to your existing account on [{{site.data.keyword.Bluemix_short}}](https://cloud.ibm.com/).

## Step 1: Creating a {{site.data.keyword.iva_short}} service instance on {{site.data.keyword.Bluemix_notm}}
{: #step1}

From the [{{site.data.keyword.iva_short}} catalog page](https://cloud.ibm.com/catalog/voice-agent-with-watson), review the service information, and then click **Create**.

After you create the service, make note of the agent endpoint on the _Getting started_ dashboard. You need the endpoint SIP URI to configure your SIP trunk.

## Step 2: Creating a SIP trunk to forward calls to {{site.data.keyword.iva_short}}
{: #step2}

1. Create a SIP trunk from any of the following supported providers. Then, associate a phone number with your SIP trunk.

  * [NetFoundry](/docs/voice-agent?topic=voice-agent-connect#NetFoundry-setup)
  * [Twilio](/docs/voice-agent?topic=voice-agent-connect#twilio-setup)
  * [AT&T and other SIP Trunking providers](/docs/voice-agent?topic=voice-agent-connect#att-other)
  * [Peering with {{site.data.keyword.iva_short}}](/docs/voice-agent?topic=voice-agent-connect#peering)

## Step 3: Creating and connecting your agent
{: #step3}

1. Go to the _Manage_ dashboard on the {{site.data.keyword.iva_short}} dashboard, and click **Create an Agent**.

2. Enter the basic settings for your agent:
  * **Name:** A unique name for your agent, such as `Customer Support`
  * **Phone number:** The full phone number that you associated with your SIP trunk, including the country and area codes. For example, for a United States 800 number, specify the phone number as 18883334444. The phone number can have spaces and + ( ) - characters.
  * **Description:** An optional description of its use
  * **Default transfer target:** An optional termination URI that calls can be transferred to.

3. Create the {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, and {{site.data.keyword.texttospeechshort}} service instances for your agent. You can choose to create an agent with either of the following methods:
  * Click **Create an agent** to create all of the services and an agent with the default configuration in a single step.
  * Or, click each of the service names to create the services yourself. Then, return to {{site.data.keyword.iva_short}} and create an agent separately.

   If you manually created a {{site.data.keyword.conversationshort}} service instance, add a dialogue so that you can test your agent.  To quickly get started, clone the [sample conversation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) from GitHub and then [import the sample](/docs/assistant?topic=assistant-skill-dialog-add) as a skill:

   1. On the sample conversation GitHub page, click the `1` line number and select **... > Copy line**. Paste the copied text into a file, and save it as a JSON file such as `voice-gateway-conversation-en.json`.
   2. Launch the {{site.data.keyword.conversationshort}} tool. On the _Skills_ page, click the ![Import workspace](../conversation/images/workspace_import.png) icon and import the JSON file.

  Alternatively, you can [build your own dialog](/docs/assistant?topic=assistant-getting-started#getting-started-build-dialog) to simulate your production environment. At minimum, your dialog must contain a node with the `conversation_start` condition and a node with a default response.


## Next steps
{: #next-steps}

Test your agent by calling its associated phone number. If you hear a response, your agent is active!

If you do not hear a response, you can examine your call logs and agent usage on the _Usage_ dashboard. See [Viewing usage and call logs](/docs/voice-agent?topic=voice-agent-logging).

You can edit the settings for your agent, create or remove agents, and add multiple Watson service locations to your agent from the _Manage_ dashboard. For more information, see [Managing agents](/docs/voice-agent?topic=voice-agent-managing).

You can also configure advanced settings, such as securing your SIP connection from your Twilio account. See [Securing connections](/docs/voice-agent?topic=voice-agent-securing).
