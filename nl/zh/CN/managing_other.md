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


# 使用其他 {{site.data.keyword.Bluemix_notm}} 工作空间中的服务实例
{: #other_service}

可以将语音代理程序配置为使用属于其他 {{site.data.keyword.Bluemix_short}} 帐户中工作空间的 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.speechtotextshort}} 服务实例。
{: shortdesc}

要将语音代理程序连接到其他服务实例，您可以对服务实例使用用户名和密码凭证，或者 API 密钥。

1. 在_管理_仪表板上的_语音代理程序_选项卡中，选择**创建新的语音代理程序**，或选择要编辑的语音代理程序。

1. 在 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.speechtotextshort}} 中，选择**其他服务实例**作为您的**服务类型**，然后选择**区域**。

1. 选择**用户名和密码**或者 **API 密钥**，并输入您的服务凭证。要找到这些值，请转至要配置的服务实例，选择**服务凭证**，然后选择**查看凭证**。

  * **用户名和密码**：在 **URL**、**用户名**和**密码**字段中，配置 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.texttospeechshort}} 服务实例的凭证。
  * **API 密钥**：在 **URL** 和 **API 密钥**字段中，配置 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.texttospeechshort}} 服务实例的凭证。

  凭证不是您的 {{site.data.keyword.Bluemix_notm}} 用户名和密码，而是特定服务实例的加密凭证。
  {:tip}

1. 输入服务实例信息。

  * **{{site.data.keyword.conversationshort}}**：在**工作空间标识**字段中，输入要用于语音代理程序的工作空间的标识。要找到工作空间标识，请启动工具，然后在要集成的工作空间上，单击“操作”图标 (**&vellip;**)，并选择**查看详细信息**。
  * **{{site.data.keyword.speechtotextshort}}：**对于**选择模型类型**，选择**窄带**、**宽带**或**窄带和宽带**，然后选择语言**模型**。
  * **{{site.data.keyword.texttospeechshort}}**：在**语音**字段中，选择服务使用的语言和语音。您必须指定服务的语音。

**请记住：**为确保语音代理程序能够正常运行，必须将 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 和 {{site.data.keyword.texttospeechshort}} 配置为使用同一语言。请参阅[支持的语言](about.html#supported-languages)。
