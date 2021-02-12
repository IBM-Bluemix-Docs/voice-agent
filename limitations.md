---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-09"
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

# Limitations
{: #limitations}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances. Existing instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

This release of {{site.data.keyword.iva_full}} has the following limitations.
{: shortdesc}

* You can create new Watson service instances directly from the _Create a voice agent_ dashboard for either the **Dallas** or **Washington DC** regions. To connect your voice agent to Watson services in other regions, create your Watson services before you create a voice agent on the _Manage_ dashboard.
* Only connections to the public switched telephone network (PSTN) are supported.
* All voice agent configuration must be specified in the {{site.data.keyword.conversationshort}} service that uses the API.
