---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 使用_管理_仪表板创建语音代理程序
{: #config_instance}

创建 {{site.data.keyword.iva_full}} 服务后，可以使用_管理_仪表板来创建单个语音代理程序。
{: shortdesc}


## 创建语音代理程序
{: #create_instance}

创建语音代理程序时，{{site.data.keyword.iva_short}} 会自动搜索您可以使用的任何可用 Watson 服务实例。如果服务不可用，可以选择在创建语音代理程序时创建服务，或者连接到其他 {{site.data.keyword.Bluemix_short}} 帐户空间中的服务。您还可以选择将语音代理程序连接到服务编排引擎、Google Speech to Text 或 Google Text to Speech 实例。

1. 转至_管理_仪表板上的_语音代理程序_选项卡，然后单击**创建语音代理程序**。

1. 对于**名称**，请为语音代理程序指定唯一名称。例如，`Customer Support - North America`。

1. 对于**电话号码**，请从 SIP 中继添加号码，包括国家和地区代码。例如，对于美国 800 号码，请将电话号码指定为 `18883334444`。电话号码可以包含空格和 `+ ( ) -` 字符。

1. （可选）对语音代理程序进行描述。

1. 如果要启用呼叫转移，请输入您的**缺省转移目标**的终止 URI。有关如何设置终止 URI 的信息，请参阅[设置呼叫转移](call-transfer.html)。不要对转移目标使用个人电话号码。

1. 配置 Watson 服务实例的连接。您可以通过配置**位置 1** 和**位置 2** 的连接来连接到多个 Watson 服务实例。连接到多个服务实例之后，您的语音代理程序可以在发生宕机时切换到其他服务实例。请参阅[添加多个 Watson 服务位置](managing_disaster_recovery.html#add_location)。

1. 在 **{{site.data.keyword.conversationshort}}** 下，配置与您的 {{site.data.keyword.conversationshort}} 服务实例的连接，方法是单击**位置 1** 或**位置 2**，然后启用所选位置。您可以使用自己或其他人拥有的 {{site.data.keyword.Bluemix_notm}} 帐户中的 {{site.data.keyword.conversationshort}} 实例。还可以通过服务编排引擎连接到其中任一实例。

   * 如果要在达拉斯或华盛顿区域创建语音代理程序，但没有 {{site.data.keyword.conversationshort}} 服务实例，那么可以使用**服务实例**菜单创建一个服务实例。
   * 或者，可以通过更改[**服务类型**](managing_other.html#other_service)来连接到 {{site.data.keyword.conversationshort}} 对话的其他源或与 SOE 连接。
   * 如果您想要配置多个服务位置，请单击其他位置选项，并选择**启用位置**以配置到其他 {{site.data.keyword.conversationshort}} 实例的连接。请参阅[添加多个 Watson 服务位置](managing_disaster_recovery.html#add_location)。

1. 在 **{{site.data.keyword.speechtotextshort}}** 下，查看您的 {{site.data.keyword.speechtotextshort}} 服务实例的缺省配置，方法是选择**位置 1** 或**位置 2**，然后启用该位置。您可以通过执行以下步骤来定制您的配置。
   * 要将语音代理程序连接到现有实例，请选择**我的语音转文字实例**来作为您的**服务类型**。接下来，对于**选择模型类型**，选择**窄带**、**宽带**或**窄带和宽带**，然后选择语言**模型**。
   * 如果要在达拉斯或华盛顿区域创建语音代理程序，但没有 {{site.data.keyword.speechtotextshort}} 服务实例，那么可以使用**服务实例**菜单创建一个服务实例。
   * 对于**服务类型**，可以选择[其他 {{site.data.keyword.Bluemix_notm}} 工作空间中的 {{site.data.keyword.speechtotextshort}} 实例](managing_other.html)或[第三方语音转文字服务](managing_third_party.html)（例如 Google Cloud Speech-to-Text）。
   * 如果您想要配置多个服务位置，请单击其他位置选项，并选择**启用位置**以配置到其他 {{site.data.keyword.speechtotextshort}} 实例的连接。请参阅[添加多个 Watson 服务位置](managing_disaster_recovery.html)。

1. 在 **{{site.data.keyword.texttospeechshort}}** 下，查看您的 {{site.data.keyword.texttospeechshort}} 服务实例的缺省配置，方法是单击**位置 1** 或**位置 2**，然后启用该位置。您可以通过执行以下步骤来定制您的配置。
   * 如果要在达拉斯或华盛顿区域创建语音代理程序，但没有 {{site.data.keyword.texttospeechshort}} 服务实例，那么可以使用**服务实例**菜单创建一个服务实例。
   * 对于**服务类型**，可以选择[其他 {{site.data.keyword.Bluemix_notm}} 工作空间中的 {{site.data.keyword.texttospeechshort}} 实例](managing_other.html)或[第三方文字转语音服务](managing_third_party.html)，例如 Google Cloud Text-to-Speech。
   * 如果您想要配置多个服务位置，请单击其他位置选项，并选择**启用位置**以配置到其他 {{site.data.keyword.texttospeechshort}} 实例的连接。请参阅[添加多个 Watson 服务位置](managing_disaster_recovery.html)。

1. 也可以选择启用事件转发，以收集 {{site.data.keyword.cloudantfull}} 中语音代理程序所处理的呼叫的相关信息。请参阅[为语音代理程序启用事件转发](event-forwarding.html)。有关更多配置选项，请参阅[配置语音代理程序](managing.html#configure_va)。

1. 单击**创建语音代理程序**以创建语音代理程序和任何新服务。

创建语音代理程序后，通过呼叫其电话号码来进行测试。在_使用情况_仪表板上，可以查看有关电话呼叫的详细信息。  
