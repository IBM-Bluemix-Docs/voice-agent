---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

keywords: concurrency, concurrent connection, maximum concurrent connection, premium plans, standard plans, rate

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

# Editing the maximum concurrent connections
{: #edit_concurrency}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances. Existing instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

If you use the _Standard_ or _Premium_ plans, you can change the maximum number of concurrent connections from the default settings.
{: shortdesc}

In all plans, you receive 2 concurrent connections at no charge. For more information, see the [Pricing plans](https://cloud.ibm.com/catalog/voice-agent-with-watson). On the _Manage_ dashboard, you can see the maximum number of concurrent connections that are allowed in your listed plan in **Maximum concurrent connections**. You can also see the maximum number of concurrent connections that are used by your agents during the current month in **Maximum concurrent connections used**.

1. Go to the _Instances_ tab on your _Manage_ dashboard to edit the maximum concurrent connections in your plan.

1. If you want to change the maximum number of concurrent connections in your plan, click the **Edit** icon.

1. In _Edit maximum concurrent connections_, enter the maximum number of concurrent connections, and click **Save**.

The minimum number of concurrent connections that you can set through self-service is 10 and the maximum is 50. If you need more than 50 concurrent connections for your agent, see [Requesting assisted network setup](/docs/voice-agent?topic=voice-agent-connect#request-setup).

## Concurrent connection pricing information
{: #concurrent-charge}

  * _Lite_ and _Standard_ plans include 2 concurrent connections at no charge.
  * _Premium_ plans are customized by instance.
  * In a _Standard_ plan, you have a minimum capacity of 10 concurrent connections.
  * Concurrent connection use is prorated by the month. If you use more than 2 concurrent connections in a day, you are charged the daily rate. For example, because your plan supports 2 concurrent connections free, and you set a maximum limit of 12 connections. If you use only 5 in a day, you are charged for 3.
  * If you have a _Standard_ or _Premium_ plan, you can purchase a greater concurrent connection capacity.
  * You are charged a daily rate for the maximum concurrent connection capacity that you use in a day.

For more information about plans, rates, and features, see [Pricing plans](https://cloud.ibm.com/catalog/voice-agent-with-watson).
