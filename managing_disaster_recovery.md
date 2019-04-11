---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configuring multiple service locations
{: #disaster-recovery}

You can connect your voice agent to multiple services in different locations for service redundancy. Your second location is not a second voice agent, it acts only as a backup.
{: shortdesc}

If you use a _Lite_ plan for your voice agent instance, you can connect your SIP trunk to only one endpoint, where your voice agent instance is created. Because _Lite_ plan provides connections to only one location, you can provide redundancies for your connected services, but not your voice agent. If a service outage occurs at your voice agent location, calls cannot be directed to a secondary location.
{: tip}

## Adding redundant services
{: #add_redundant}

You can add a Watson or third-party service location to your voice agent configuration at any time by editing your voice agent.

1. To add a redundant service to an existing voice agent, navigate to the _Voice agents_ tab on your _Manage_ dashboard. Click **Edit agent** for the voice agent you want to configure.

1. Choose either **Location 1** or **Location 2** for the {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}}, or {{site.data.keyword.speechtotextshort}} service that you want to connect, and add your configuration information. You can use third-party services or Watson service instances in your workspace or in other workspaces. See [Using service instances in other {{site.data.keyword.Bluemix_notm}} workspaces](/docs/services/voice-agent?topic=voice-agent-other_service).

**Remember**: For service redundancy, you must use Watson service instances in different service regions for different locations.

You can enable or disable a location by using the **Enable location** box. **Location 1** is enabled by default and **Location 2** is disabled by default. At least one location must be enabled for each Watson service.

## Adding multiple Watson service locations
{: #add_location}

Your voice agent uses the Watson service instances in order of geographical distance. For example, you can create a voice agent in the Washington DC region, and your {{site.data.keyword.conversationshort}} services in Dallas and Sydney, Australia. Your voice agent uses the {{site.data.keyword.conversationshort}} Dallas region because Dallas is geographically nearer to Washington DC than Sydney. By connecting to Watson services in multiple regions, if a Watson service is offline at one location, your voice agent can use the redundant service.
