---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-21"

keywords: Whitelist, IP Address, whitelisting, IP Nickname

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

# Whitelisting IP addresses
{: #whitelist_IP}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances. Existing instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

You can configure peering to {{site.data.keyword.iva_short}} or other providers by whitelisting IP addresses.
{: shortdesc}

Your {{site.data.keyword.iva_short}} instance **must** be on a Standard, Plus or Premium plan to be able to use the whitelisting feature. 
{: tip}

## Adding an IP address to the whitelist
{: #add_IP}

1. Go to the _Manage_ dashboard and select the _Instance_ tab.

1. Click **Add a new IP** icon to whitelist a new IP address.

1. Add an **IP Nickname** and the **IP address**.

## Editing IP addresses
{: #edit_IP}

1. Go to the _Manage_ dashboard and select the _Instance_ tab.

1. Click the IP address entry that you want to edit.

1. Make your changes, and then click **Save**.
