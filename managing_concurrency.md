---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Editing the maximum concurrent connections
{: #edit_concurrency}

If you use the _Standard_ or _Premium_ plans, you can change the maximum number of concurrent connections from the default settings.
{: shortdesc}

In all plans, you receive 2 concurrent connections at no charge. For more information, see the [Pricing plans](https://cloud.ibm.com/catalog/services/voice-agent-with-watson). On the _Manage_ dashboard, you can see the maximum number of concurrent connections that are allowed in your listed plan in **Maximum concurrent connections**. You can also see the maximum number of concurrent connections that are used by your voice agents during the current month in **Maximum concurrent connections used**.

1. Go to the _Instances_ tab on your _Manage_ dashboard to edit the maximum concurrent connections in your plan.

1. If you want to change the maximum number of concurrent connections in your plan, click the **Edit** icon.

1. In _Edit maximum concurrent connections_, enter the maximum number of concurrent connections, and click **Save**.

The minimum number of concurrent connections that you can set through self-service is 10 and the maximum is 50. If you need more than 50 concurrent connections for your voice agent, see [Requesting assisted network setup](/docs/services/voice-agent?topic=voice-agent-connect#request-setup).

## Concurrent connection pricing information
{: #concurrent-charge}

  * _Lite_ and _Standard_ plans include 2 concurrent connections at no charge.
  * _Premium_ plans are customized by instance.
  * In a _Standard_ plan, you have a minimum capacity of 10 concurrent connections.
  * Concurrent connection use is prorated by the month. If you use more than 2 concurrent connections in a day, you are charged the daily rate. For example, because your plan supports 2 concurrent connections free, and you set a maximum limit of 12 connections. If you use only 5 in a day, you are charged for 3.
  * If you have a _Standard_ or _Premium_ plan, you can purchase a greater concurrent connection capacity.
  * You are charged a daily rate for the maximum concurrent connection capacity that you use in a day.

For more information about plans, rates, and features, see [Pricing plans](https://cloud.ibm.com/catalog/services/voice-agent-with-watson).
