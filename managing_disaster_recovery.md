---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"

keywords: disaster, failure, service, Watson, service instance
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


# Configuring multiple service locations
{: #disaster-recovery}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances, and access to free instances will be removed. Existing paid instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

You can connect your agent to multiple services in different locations for service redundancy. Your second location is not a second agent. It acts only as a backup.
{: shortdesc}

If you use a _Lite_ plan for your agent instance, you can connect your SIP trunk to only one endpoint, where your agent instance is created. Because _Lite_ plan provides connections to only one location, you can provide redundancies for your connected services, but not your agent. If a service outage occurs at your agent location, calls cannot be directed to a secondary location.
{: tip}

## Adding redundant services
{: #add_redundant}

You can add a Watson or third-party service location to your agent configuration at any time by editing your agent.

1. To add a redundant service to an existing agent, go to the _Agents_ tab on your _Manage_ dashboard. Click **Edit agent** for the agent you want to configure.

1. Choose either **Location 1** or **Location 2** for the {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}}, or {{site.data.keyword.speechtotextshort}} service that you want to connect, and add your configuration information. You can use third-party services or Watson service instances in your workspace or in other workspaces. See [Using service instances in other {{site.data.keyword.Bluemix_notm}} workspaces](/docs/voice-agent?topic=voice-agent-other_service).

**Remember**: For service redundancy, you must use Watson service instances in different service regions for different locations.

You can enable or disable a location by using the **Enable location** box. **Location 1** is enabled by default and **Location 2** is disabled by default. At least one location must be enabled for each Watson service.

## Adding multiple Watson service locations
{: #add_location}

Your agent uses the Watson service instances in order of geographical distance. For example, you can create an agent in the Washington DC region, and your {{site.data.keyword.conversationshort}} services in Dallas and Sydney, Australia. Your agent uses the {{site.data.keyword.conversationshort}} Dallas region because Dallas is geographically nearer to Washington DC than Sydney. By connecting to Watson services in multiple regions, if a Watson service is offline at one location, your agent can use the redundant service.
