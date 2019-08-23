---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: SOE, service orchestration engine, SOE workspace
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Configuring {{site.data.keyword.conversationshort}} with a Service Orchestration Engine
{: #conversation_va}

As an alternative to configuring a {{site.data.keyword.conversationshort}} service instance, you can connect to a service orchestration engine (SOE).
{: shortdesc}

You can connect to a {{site.data.keyword.conversationshort}} workspace through a [service orchestration engine (SOE)](/docs/services/voice-agent?topic=voice-agent-about#arch-soe). An SOE intercepts messages to and from the service so that you can modify them by using third-party APIs.

## Configuring a connection to an SOE
{: #how-to-SEO}

1. In the _Voice agent_ tab on the _Manage_ page for your voice agent, go to the {{site.data.keyword.conversationshort}} configuration section.

1. Choose **Service orchestration engine** as your **Service type**.

1. Select the **Region** for your **Service type**.

1. In the **URL** field, enter the full URL to your SOE workspace, such as `https://iva-soesample.myorg.net/SOE/myWorkspace`. Up to 256 characters can be entered for the URL.

  **Important**: For data security, make sure that you use a secure URL for your SOE workspace, by using `https:` instead of `http:`, and require authentication. See [Information security and data privacy](/docs/services/voice-agent?topic=voice-agent-infosec) to learn more about security considerations.

1. **Optional** If your SOE requires authentication (recommended), enter the user name and password in the respective fields, up to 64 and 256 characters each.
