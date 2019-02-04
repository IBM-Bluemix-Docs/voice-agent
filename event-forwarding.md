---

copyright:
  years: 2019
lastupdated: "2019-01-30"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Enabling event forwarding for voice agents
{: #event_forwarding}

You can enable event forwarding to collect information about calls that are handled by your voice agents in {{site.data.keyword.iva_full}} by using a {{site.data.keyword.cloudantfull}} database service.
{: shortdesc}

You might want to collect and analyze call data from {{site.data.keyword.iva_short}} to improve how natural the conversation feels to the caller. Each voice agent that you create can forward event reports to a specified {{site.data.keyword.cloudant_short_notm}} that you manage. Reported events include the call detail record (CDR) events, transcription events, and turn events reports. You can learn more about the types of events that you can forward in [Reporting events](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}.

Analyzing data from these events can help you adjust dialogs, refine intents, and improve overall caller experience.

When you create or edit voice agents, you can also choose to enable event forwarding. For more detail about creating and editing voice agents, see [Managing voice agents](managing.html). You need to provide {{site.data.keyword.cloudant_short_notm}} account information, including the account name and password, to enable event forwarding.

**Important:** The CDR, transcription, and turn events include information from your users that might potentially contain Protected Health Information (PHI), personally identifiable information (PII), or PCI Data Security Standard (PCI DSS) data. To prevent exposure of personal information, you must ensure that your {{site.data.keyword.cloudant_short_notm}} instance properly protects the confidential information that your users share in or during conversation. See [Information security and data privacy: Event forwarding](infosec.html#event_forwarding) and [{{site.data.keyword.cloudant_short_notm}}: Security](../Cloudant/offerings/security.html#security).


## Enabling event forwarding
{: #enable-event-forwarding}

You can enable event forwarding when you are creating or editing your voice agents in the _Manage_ dashboard on {{site.data.keyword.Bluemix_short}}.

1. In the **Event forwarding** section, after the configuration section for {{site.data.keyword.texttospeechshort}}, select **Enable event forwarding**.

1. Select either **My {{site.data.keyword.cloudant_short_notm}} service instance** or **Other {{site.data.keyword.cloudant_short_notm}} service instance**.
  * If you are using **My {{site.data.keyword.cloudant_short_notm}} service instance**, select the **{{site.data.keyword.cloudant_short_notm}} account** name and username from the lists.
  * If you are creating a voice agent in the Dallas or Washington DC region and you do not have a {{site.data.keyword.cloudant_short_notm}} service instance, you can create one from the **Cloudant account** menu.
  * If you are using **Other {{site.data.keyword.cloudant_short_notm}} service instance**, enter either the {{site.data.keyword.cloudant_short_notm}} user name and password or the API key for the account.

1. Select **Enable** for each type of event that you want to forward, and then choose the database where you want to forward the events.
  * Call detail record (CDR) events
  * Transcription events
  * Turn events

1. View your database to ensure that event reports forward correctly.

## Related links
* [IBM Voice Gateway: Reporting events](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
* [Information security and data privacy](infosec.html)
* [{{site.data.keyword.cloudant_short_notm}}: Security](../Cloudant/offerings/security.html#security)
