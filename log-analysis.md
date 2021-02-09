---

copyright:
  years: 2019
lastupdated: "2019-09-25"

keywords: log analysis, integration, logdna

subcollection: "voice-agent"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}

# Log Analysis integration
{: #log-analysis-integration}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances, and access to free instances will be removed. Existing paid instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

{{site.data.keyword.iva_full}} is integrated with [{{site.data.keyword.la_full}}](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-about){: new_window}{: external}, so you can view database logs.

Currently, {{site.data.keyword.la_full_notm}} integration is available for {{site.data.keyword.iva_full}} deployments according to the following table:

Deployment Region | LogDNA Region
----------|-----------
`Dallas` | `Dallas`
`Washington DC` | `Dallas`
{: caption="Table 1. Log Analysis regions" caption-side="top"}

## Provisioning {{site.data.keyword.la_full_notm}}
{: #provisioning-logdna}

Log information from your {{site.data.keyword.iva_full}} instances are automatically forwarded to {{site.data.keyword.la_full_notm}}, but to access it you must [provision a Log Analysis service](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-provision){: new_window}{: external} in your {{site.data.keyword.cloud_notm}} account and [configure the service to receive {{site.data.keyword.cloud_notm}} service logs](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-config_svc_logs){: new_window}{: external}.

This setting enables logs from **all** {{site.data.keyword.cloud_notm}} services on your account that have {{site.data.keyword.la_full_notm}} integration to send logs to your {{site.data.keyword.la_full_notm}} service. [A list of the integrated services is available](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-cloud_services#cloud_services){: new_window}{: external}.
{: .tip}

{{site.data.keyword.la_full_notm}} has a lite plan that is free to use, but it offers only streaming events. To take advantage of the tagging, export, retention, and other features, you need to use one of the [paid plans](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-about#overview_pricing_plans){: new_window}{: external}.

### HIPAA 
{: #hipaa_logdna}

{{site.data.keyword.la_full_notm}} does not currently offer a HIPAA-compliant plan for the service. 

Use caution when you configure the platform service logs, since this setting can impact other services that require HIPAA compliance.
{: important}

## Using {{site.data.keyword.la_full_notm}}
{: #using-logdna}

After logs are live streaming, each log can be expanded to a detailed view by clicking the arrow to the left of the timestamp.

The expanded view has some handy, color-coded fields to help you parse your logs. 

Line identifiers | Description
-----------------|------------
`Source` | The region the logs are being sent from.
`App` | The CRN of your database deployment that is sending the logs. 
{: caption="Table 2. Line identifiers" caption-side="top"}

{{site.data.keyword.la_full_notm}} offers [searching](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-view_logs#view_logs_step6){: new_window}{: external} and [filtering](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-view_logs#view_logs_step5){: new_window}{: external} capabilities to help you navigate your logs. [Export](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-export#export){: new_window}{: external} and [archive](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-archiving#archiving){: new_window}{: external} capabilities are available so you can customize retention and cost for your use case.
