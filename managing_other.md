---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: service instance, workspaces, user name, API key

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


# Using service instances in other {{site.data.keyword.Bluemix_notm}} workspaces
{: #other_service}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances, and access to free instances will be removed. Existing paid instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

You can configure your agent to use {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, or {{site.data.keyword.speechtotextshort}} service instances that belong to workspaces in other {{site.data.keyword.Bluemix_short}} accounts.
{: shortdesc}

To connect your agent to other service instances, you can use either the user name and password credentials or an API key for your service instances. The user name and password are limited to 64 and 256 characters, respectively. The API key is limited to 64 characters.

1. In the _Agents_ tab on the _Manage_ dashboard, select either **Create a new agent** or an agent that you want to edit.

1. In  {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, or {{site.data.keyword.speechtotextshort}} Select **Other service instance** for your **Service type** and then select the **Region**.

1. Choose either **user name and password** or **API key**, and enter your service credentials.
  To find these values, go to the service instance that you want to configure, and select **Service credentials** and then **View credentials**.

  * **User name and password**: In the **URL**, **user name**, and **Password** fields, configure the credentials for your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, or {{site.data.keyword.texttospeechshort}} service instances.
  * **API key**: In the **URL** and **API key** fields, configure the credentials for your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, or {{site.data.keyword.texttospeechshort}} service instances.

  The credentials are not your {{site.data.keyword.Bluemix_notm}} user name and password, but rather encrypted credentials for the specific service instance.
  {:tip}

1. Enter your service instance information.

  * **{{site.data.keyword.conversationshort}}:** In the **Workspace ID** field, enter the ID of the workspace that you want to use with your agent, up to 128 characters. To find the workspace ID, launch the tool, and on the workspace that you want to integrate, click the Actions icon (**&vellip;**) and select **View details**.
  * **{{site.data.keyword.speechtotextshort}}:** For **Select model type**, choose **Narrowband**, **Broadband**, or **Both narrowband and broadband**, then select the language **Model**.
  * **{{site.data.keyword.texttospeechshort}}:** In the **Voice** field, select the language and voice that your service uses. You must specify a voice for your service.

**Remember:** For your agent to work, you must configure your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, and {{site.data.keyword.texttospeechshort}} for the same language. See [Supported languages](/docs/voice-agent?topic=voice-agent-about#supported-languages).
