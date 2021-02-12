---

copyright:
  years: 2019
lastupdated: "2019-10-30"

keywords: SIP trunk authentication, SIP authentication, trunk group password

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
{:note: .note}

# SIP Authentication
{: #sip_auth}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances. Existing instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

You can enable **SIP authentication** at the agent level in the _Manage_ dashboard. When **SIP authentication** is enabled, you can choose a **service credential** to use for authentication.
{: shortdesc}

## Enabling/Disabling SIP trunk group authentication
{: #enable_disable_sip_auth}

1. Go to the _Agent_ tab in the _Manage_ dashboard and select a Voice or Voice+SMS agent that you want to edit. 
1. Toggle the checkbox next to _Enable SIP authentication_ under the agent's name and description to enable or disable SIP authentication.
1. When enabled, a drop-down list of **service credential** key names from the _Service credentials_ tab appears. Select the **service credential** that is associated with the _API key_ to use for authentication.

**Digest Authentication** is the default authentication method used when **SIP authentication** is enabled. When the user initiates a call by using **Digest Authentication**, the token that is used is an `MD5` hash in the format `username:realm:password` with the following values:
- `username`: `apikey`
- `realm`: `vgw`
- `password`: The **service credential** _API key_ selected above.

## Retrieving the trunk group password
{: #get_sip_auth_pwd}
1. Go to the _Service Credentials_ tab in the dashboard.
1. Click on the _View credentials_ action for the **service credential** that is selected for SIP trunk authentication.
1. The listed _API key_ is the password that is used for **SIP trunk group authentication**.

In order to view the **service credential** _API key_, the user must be assigned the required IAM roles.
{: note}
