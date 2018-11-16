---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Using service instances in other {{site.data.keyword.Bluemix_notm}} workspaces
{: #other_service}

You can configure your voice agent to use {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, or {{site.data.keyword.speechtotextshort}} service instances that belong to workspaces in other {{site.data.keyword.Bluemix_short}} accounts.
{: shortdesc}

To connect your voice agent to other service instances, you can use either the user name and password credentials or an API key for your service instances.

1. In the _Voice agents_ tab on the _Manage_ dashboard, select either **Create a new voice agent** or a voice agent that you want to edit.

1. In  {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, or {{site.data.keyword.speechtotextshort}} Select **Other service instance** for your **Service type** and then select the **Region**.

1. Choose either **User name and password** or **API key**, and enter your service credentials.
  To find these values, go to the service instance that you want to configure, and select **Service credentials** and then **View credentials**.

  * **User name and password**: In the **URL**, **User name**, and **Password** fields, configure the credentials for your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}},  or {{site.data.keyword.texttospeechshort}} service instances.
  * **API key**: In the **URL** and **API key** fields, configure the credentials for your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}},  or {{site.data.keyword.texttospeechshort}} service instances.

  The credentials are not your {{site.data.keyword.Bluemix_notm}} user name and password, but rather encrypted credentials for the specific service instance.
  {:tip}

1. Enter your service instance information.

  * **{{site.data.keyword.conversationshort}}:** In the **Workspace ID** field, enter the ID of the workspace that you want to use with your voice agent. To find the workspace ID, launch the tool, and on the workspace that you want to integrate, click the Actions icon (**&vellip;**) and select **View details**.
  * **{{site.data.keyword.speechtotextshort}}:** For **Select model type**, choose **Narrowband**, **Broadband**, or **Both narrowband and broadband**, then select the language **Model**.
  * **{{site.data.keyword.texttospeechshort}}:** In the **Voice** field, select the language and voice that your service uses. You must specify a voice for your service.

**Remember:** For your voice agent to work, you must configure your {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}}, and {{site.data.keyword.texttospeechshort}} for the same language. See [Supported languages](about.html#supported-languages).
