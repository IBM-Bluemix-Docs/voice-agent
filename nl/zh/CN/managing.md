---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-29"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 管理语音代理程序
{: #managing}

在_管理_仪表板上，可以创建、编辑、克隆、配置和除去语音代理程序。您可以有多个语音代理程序，但每个语音代理程序的名称和电话号码都必须唯一。
{: shortdesc}

<!-- Title should be task oriented and descriptive-->

## 创建语音代理程序
{: #config_instance}

创建语音代理程序时，{{site.data.keyword.iva_short}} 会自动搜索您可以使用的任何可用 Watson 服务实例。如果服务不可用，可以选择在创建语音代理程序时创建服务，或者连接到其他 {{site.data.keyword.Bluemix_short}} 帐户空间中的服务。

1. 单击**创建语音代理程序**。

1. 对于**名称**，请为语音代理程序指定唯一名称。例如，`Customer Support - North America`。

1. 对于**电话号码**，请从 SIP 中继添加号码，包括国家和地区代码。例如，对于美国 800 号码，请将电话号码指定为 `18883334444`。电话号码可以包含空格和 `+ ( ) -` 字符。

1. （可选）对语音代理程序进行描述。

1. 如果要启用呼叫转移，您可以为**转移目标**配置终止 URI。请参阅[设置呼叫转移](call-transfer.html)。不要对转移目标使用个人电话号码。

1. 配置 Watson 服务实例的连接。您可以通过配置**位置 1** 和**位置 2** 的连接来连接到多个 Watson 服务实例。连接到多个服务实例之后，您的语音代理程序可以在发生宕机时切换到其他服务实例。请参阅[添加多个 Watson 服务位置](#add_location)。

    **重要信息**：_试用_和_轻量_实例只能连接到创建 {{site.data.keyword.iva_short}} 服务实例的位置。第二个位置不是第二个语音代理程序。该位置仅充当灾难恢复的备份。

1. 在 **{{site.data.keyword.conversationshort}}** 下，通过单击**启用位置 1** 或**启用位置 2** 配置 {{site.data.keyword.conversationshort}} 服务实例的连接。您可以在您或其他人的 {{site.data.keyword.Bluemix_notm}} 帐户下使用 {{site.data.keyword.conversationshort}} 实例或 {{site.data.keyword.virtualagentfull}} 实例。还可以通过服务编排引擎连接到其中任一实例。

    * 如果要在美国南部或美国东部区域创建语音代理程序，但没有 {{site.data.keyword.conversationshort}} 服务实例，那么可以在**服务实例**菜单中创建一个服务实例。
    * 或者，可以通过更改[**服务类型**](#other_service)来连接到 {{site.data.keyword.conversationshort}} 对话的其他源。
    * 如果您想要配置多个服务位置，请单击其他位置选项，并选择**启用位置**以配置到其他 {{site.data.keyword.conversationshort}} 实例的连接。请参阅[添加多个 Watson 服务位置](#add_location)。

1. 在 **{{site.data.keyword.speechtotextshort}}** 下，通过单击**启用位置 1** 或**启用位置 2** 来查看 {{site.data.keyword.speechtotextshort}} 服务实例的缺省配置。
    * 如果要在美国南部或美国东部区域创建语音代理程序，但没有 {{site.data.keyword.speechtotextshort}} 服务实例，那么可以在**服务实例**菜单中创建一个服务实例。
    * 选择[**服务类型**](#other_service)以将语音代理程序连接到位于不同 {{site.data.keyword.Bluemix_notm}} 中的 {{site.data.keyword.speechtotextshort}} 实例。
    * 如果您想要配置多个服务位置，请单击其他位置选项，并选择**启用位置**以配置到其他 {{site.data.keyword.speechtotextshort}} 实例的连接。请参阅[添加多个 Watson 服务位置](#add_location)。
    * **请记住：**{{site.data.keyword.iva_short}} 仅支持窄带模型。

1. 在 **{{site.data.keyword.texttospeechshort}}** 下，通过单击**启用位置 1** 或**启用位置 2** 来查看 {{site.data.keyword.texttospeechshort}} 服务的缺省配置。 
    * 如果要在美国南部或美国东部区域创建语音代理程序，但没有 {{site.data.keyword.texttospeechshort}} 服务实例，那么可以在**服务实例**菜单中创建一个服务实例。 
    * 也可以通过更改[**服务类型**](#other_service)，将语音代理程序连接到其他 {{site.data.keyword.Bluemix_notm}} 帐户空间中的 {{site.data.keyword.texttospeechshort}} 实例。
    * 如果您想要配置多个服务位置，请单击其他位置选项，并选择**启用位置**以配置到其他 {{site.data.keyword.texttospeechshort}} 实例的连接。请参阅[添加多个 Watson 服务位置](#add_location)。

1. 也可以选择启用事件转发，以收集 {{site.data.keyword.cloudantfull}} 中语音代理程序所处理的呼叫的相关信息。请参阅[为语音代理程序启用事件转发](event-forwarding.html)。有关更多配置选项，请参阅[配置语音代理程序](#configure_va)。

1. 单击**创建语音代理程序**以创建语音代理程序和任何新服务。

创建语音代理程序后，通过呼叫其电话号码来进行测试。在_使用情况_仪表板上，可以查看有关电话呼叫的详细信息。  

## 编辑最大并发连接数
{: #edit_concurrency}

如果使用_标准_套餐，那么可以通过缺省设置更改最大并发连接数。所有套餐都可以免费获取 2 个并发连接。有关更多信息，请参阅[价格套餐](https://console.bluemix.net/catalog/services/voice-agent-with-watson)。

在_管理_仪表板上，可以在**最大并发连接数**中查看您的所列套餐中允许的最大并发连接数。还可以在**已使用的最大并发连接数**中查看您的语音代理程序当月使用的最大并发连接数。

如果想要更改套餐中的最大并发连接数，请单击**编辑**图标。在_编辑最大并发连接数_窗口中，选择最大并发连接数，然后单击**保存**。可通过自助服务设置的最小并发连接数为 10，最大并发连接数为 50。如果语音代理程序需要 50 个以上的并发连接，请参阅[请求网络设置协助](connect-SIP.html#request-setup)。

### 并发连接定价信息
{: #concurrent-charge}

  * _轻量_、_试用_和_标准_套餐都包含 2 个免费的并行连接。
  * _高端_套餐可按实例进行定制。
  * 在_标准_套餐中，最小容量为 10 个并发连接。
  * 并发连接的使用量是按月分派的。如果某一天的使用量超过 2 个并发连接，那么将按每日费率进行收费。
  * 如果使用_标准_或_高端_套餐，那么可以购买更大的并发连接容量。
  * 系统会按每日费率对您在一天内使用的最大并发连接容量进行收费。例如，您的套餐免费支持 2 个并发连接，而您设置的最大限制为 12 个连接。如果某一天只使用 5 个，那么将收取 3 个的费用。

有关套餐、费率和特色服务的更多信息，请参阅[价格套餐](https://console.bluemix.net/catalog/services/voice-agent-with-watson)。

## 编辑语音代理程序
{: #edit_va}

可以通过编辑现有语音代理程序来对其进行更改。要编辑语音代理程序，请单击语音代理程序的选项列表中的**编辑代理程序**。更改配置，然后保存更改。

## 克隆语音代理程序
{: #clone_va}

克隆语音代理程序时，Watson 服务的所有配置都会复制到新代理程序中。要克隆语音代理程序，请单击语音代理程序的选项列表中的**克隆代理程序**。为语音代理程序提供唯一名称和电话号码，根据需要更改任何配置选项，然后保存更改。

## 删除语音代理程序
{: #delete_va}

您可能想要删除语音代理程序以释放电话号码。一个电话号码只能有一个语音代理程序。要将电话号码用于其他语音代理程序，必须先将使用该电话号码的语音代理程序删除。

要删除语音代理程序，请单击语音代理程序的选项列表中的**删除代理程序**，然后保存更改。这将从语音代理程序列表中除去该语音代理程序。

## 配置语音代理程序
{: #configure_va}

### 配置高级选项
{: #config-advanced}

在创建或克隆语音代理程序时，可以单击**显示高级**以查看以下高级配置选项。

* **{{site.data.keyword.conversationshort}} 失败回复消息（可选）**：在呼叫无法连接到 {{site.data.keyword.conversationshort}} 时发送给消息接收方的缺省响应消息。
* **转移失败回复消息（可选）**：在呼叫转移失败时向呼叫者传送的缺省响应消息。
* **定制 SIP INVITE 标题（可选）**：指定要从入局 SIP INVITE 请求中抽取的定制 SIP 标题
* **从 {{site.data.keyword.iva_short}} 发送临时响铃响应**：在 {{site.data.keyword.iva_short}} 处理入局呼叫时，发送 `180 ringing` 响应。缺省情况下，会启用此设置。
* **转移时让呼叫者等待**：在转移期间让呼叫者等待。缺省情况下，会启用此设置。
* **转移失败时断开呼叫**：用于确定在呼叫转移失败时是否断开呼叫。缺省情况下，会启用此设置。如果禁用此设置，那么当呼叫转移失败时，{{site.data.keyword.iva_short}} 会启动一轮对话。然后，{{site.data.keyword.conversationshort}} 可以断开呼叫或将其转移到对话中配置的其他目标。
* **发生网络事件时通知 {{site.data.keyword.conversationshort}}**：启用此设置后，如果检测到网络错误，那么 {{site.data.keyword.iva_short}} 会使用文本“vgwNetworkWarningMessage”向 {{site.data.keyword.conversationshort}} 服务启动一轮对话。`vgwNetworkWarnings` 状态变量包含在当前轮次中发生的网络事件的列表。如果禁用此设置，那么会在 `vgwNetworkWarnings` 状态变量中的下一个轮次事件中发送当前轮次期间发生的网络事件的列表。缺省情况下，会启用此设置。

### 添加多个 Watson 服务位置
{: #add_location}

如果使用_标准_或_高端_实例，那么可以将语音代理程序连接到不同位置的多个 Watson 服务来实现服务冗余。_试用_和_轻量_实例只能连接到创建 {{site.data.keyword.iva_short}} 服务实例的位置。第二个位置不是第二个语音代理程序。该位置仅充当灾难恢复的备份。

语音代理程序按地理位置的远近使用 Watson 服务实例。例如，您可以在美国东部区域创建语音代理程序，而在美国南部和澳大利亚的悉尼创建 {{site.data.keyword.conversationshort}} 服务。 语音代理程序会使用 {{site.data.keyword.conversationshort}} 美国南部区域，因为美国南部在地理上比悉尼更靠近美国东部。在多个地区连接 Watson 服务时，如果一个位置的 Watson 服务脱机，您的语音代理程序可以使用冗余服务。

您可以随时将 Watson 服务位置添加到语音代理程序配置中。有关在创建语音代理程序时连接多个服务位置实例的信息，请参阅[创建语音代理程序](#creating)。

要将 Watson 服务位置添加到现有语音代理程序，对于您要配置的语音代理程序，单击**编辑代理程序**。对您想要连接的 {{site.data.keyword.conversationshort}}、
{{site.data.keyword.texttospeechshort}} 或 {{site.data.keyword.speechtotextshort}} 实例，选择**位置 1** 或**位置 2**，并添加配置信息。您可以使用您的工作空间或其他工作空间中的 Watson 服务实例。请参阅[使用其他 {{site.data.keyword.Bluemix_notm}} 工作空间中的服务实例](#other_services)。

**请记住**：对于服务冗余，您必须在不同服务地区的不同位置使用 Watson 服务实例。

您可以通过使用**启用位置**框启用或禁用位置。**位置 1** 在缺省情况下已启用，**位置 2** 在缺省情况下已禁用。对于每个 Watson 服务必须启用至少一个位置。

### 使用其他 {{site.data.keyword.Bluemix_notm}} 工作空间中的服务实例
{: #other_service}

可以将语音代理程序配置为使用属于其他 {{site.data.keyword.Bluemix_short}} 帐户中工作空间的 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.speechtotextshort}} 服务实例。要将语音代理程序连接到其他服务实例，您可以对服务实例使用用户名和密码凭证，或者 API 密钥。

1. 选择您的**服务类型**和**区域**。

1. 选择**用户名和密码**或者 **API 密钥**，并输入您的服务凭证。要找到这些值，请转至要配置的服务实例，选择**服务凭证**，然后选择**查看凭证**。

  * **用户名和密码**：在 **URL**、**用户名**和**密码**字段中，配置 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.texttospeechshort}} 服务实例的凭证。
  * **API 密钥**：在 **URL** 和 **API 密钥**字段中，配置 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.texttospeechshort}} 服务实例的凭证。

  凭证不是您的 {{site.data.keyword.Bluemix_notm}} 用户名和密码，而是特定服务实例的加密凭证。
{:tip}

1. 输入服务实例信息。

  * **{{site.data.keyword.conversationshort}}**：在**工作空间标识**字段中，输入要用于语音代理程序的工作空间的标识。要找到工作空间标识，请启动工具，然后在要集成的工作空间上，单击“操作”图标 (**&vellip;**)，并选择**查看详细信息**。
  * **{{site.data.keyword.speechtotextshort}}**：在**模型**字段中，选择服务的语音语言和格式。{{site.data.keyword.iva_short}} 仅支持窄带模型。
  * **{{site.data.keyword.texttospeechshort}}**：在**语音**字段中，选择服务使用的语言和语音。您必须指定服务的语音。

**请记住：**为确保语音代理程序能够正常运行，必须将 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 和 {{site.data.keyword.texttospeechshort}} 配置为使用同一语言。请参阅[支持的语言](about.html#supported-languages)。

### 为语音代理程序配置 {{site.data.keyword.conversationshort}}
{: #conversation_va}

作为配置 {{site.data.keyword.conversationshort}} 服务实例的替代方法，您可以连接到服务编排引擎 (SOE) 或 Watson {{site.data.keyword.virtualagentshort}}。

* **服务编排引擎**：通过[服务编排引擎 (SOE)](about.html#arch-soe) 连接到 {{site.data.keyword.conversationshort}} 工作空间或 {{site.data.keyword.virtualagentshort}}。SOE 可拦截传入和传出服务的消息，以便您使用第三方 API 对这些消息进行修改。

  在 **URL** 字段中，输入 SOE 工作空间的完整 URL，例如 `https://iva-soesample.myorg.net/SOE/myWorkspace`。如果 SOE 需要认证（建议），请在相应的字段中输入用户名和密码。

  **重要信息**：为了实现数据安全，请确保对 SOE 工作空间使用安全 URL（即，使用 `https:` 而不是 `http:`），并要求认证。请参阅[信息安全和数据隐私](infosec.html)以了解更多安全性注意事项。

* **Watson {{site.data.keyword.virtualagentshort}}**：连接到 {{site.data.keyword.virtualagentshort}} 聊天机器人，而不是 {{site.data.keyword.conversationshort}} 工作空间。[{{site.data.keyword.virtualagentshort}}](../virtual-agent/getting-started.html#getting-started) 基于 {{site.data.keyword.conversationshort}} 服务而构建，但它提供了预先训练的功能，即使您没有机器学习经验，也可以轻松上手。

  在 **URL** 字段中，输入 {{site.data.keyword.virtualagentshort}} 的 URL 凭证，例如 `https://api.ibm.com/virtualagent/run/api`。对于**客户机标识**和**客户机私钥**字段，请输入认证密钥，这些密钥会映射到 API 调用的 `X-IBM-Client-Id` 和 `X-IBM-Client-Secret` 头字段。在**机器人标识**字段中，输入要用于此语音代理程序的机器人的标识。有关如何找到这些值的更多信息，请参阅 {{site.data.keyword.virtualagentshort}} 文档中的[发布代理程序](../virtual-agent/publish.html)。
