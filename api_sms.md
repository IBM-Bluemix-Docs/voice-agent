---

copyright:
  years: 2020
lastupdated: "2020-04-20"
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


# API for Managing SMS Sessions
{: #api-sms}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances, and access to free instances will be removed. Existing paid instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

You can perform REST API operations to create and delete SMS sessions and trigger Watson Assistant to send outbound SMS requests.

To initiate a SMS operation, make an HTTP POST request to the SMS service endpoint. The service endpoint for your service instance can be found in the Getting Started page of your {{site.data.keyword.iva_full}} dashboard.

For instance:

`US South: https://sms-south.voiceagent.cloud.ibm.com`

`US East: https://sms-east.voiceagent.cloud.ibm.com`

`Frankfurt: https://sms-fra04.voiceagent.cloud.ibm.com or https://sms-fra05.voiceagent.cloud.ibm.com`

## More information

For the API documentation on SMS, see [IBM Voice Agent API Documentation](https://cloud.ibm.com/apidocs/voice-agent/sms-api).
