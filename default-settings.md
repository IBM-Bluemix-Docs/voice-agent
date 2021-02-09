---

copyright:
  years: 2018
lastupdated: "2018-10-31"
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


# Default settings
{: #default-settings}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances, and access to free instances will be removed. Existing paid instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

{{site.data.keyword.iva_full}} uses the following default settings.

| Setting Name | Default |
|------|---------------|
| {{site.data.keyword.conversationshort}} token authentication| Enabled |
| Service Orchestration Engine (SOE) token authentication| Disabled |
| {{site.data.keyword.speechtotextshort}} token authentication| Enabled |
| Profanity filter | Enabled |
| Smart formatting | Enabled |
| Confidence score threshold | `0.2` |
| Barge-in playback resume | Enabled |
| Echo suppression | Enabled |
| Cache time to live | 336 hours |
| Send SIP CALL ID to {{site.data.keyword.conversationshort}} | Enabled |
| Send SIP REQUEST URI to {{site.data.keyword.conversationshort}} | Enabled |
| Send SIP TO URI to {{site.data.keyword.conversationshort}} | Enabled |
| Send SIP FROM URI to {{site.data.keyword.conversationshort}} | Enabled |
| Custom SIP invite header | user-to-user |
{: caption="Table 1. {{site.data.keyword.iva_short}} default settings." caption-side="top"}
