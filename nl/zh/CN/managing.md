---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 管理服务实例和语音代理程序
{: #managing}

您可以使用_管理_仪表板来更改服务实例配置，还可以创建、编辑、克隆、配置或除去单个语音代理程序。您的服务实例中可以有多个语音代理程序，但每个语音代理程序最多可以包含 1000 个唯一号码和描述。
但是，每个语音代理程序必须具有一个唯一名称和至少一个电话号码。

* **注释**：单个 {{site.data.keyword.iva_full}} 服务实例可以最多包含 150 个语音代理程序。
{: shortdesc}

## 导航到语音代理程序服务仪表板
{: #navigate_manage}

您可以从 {{site.data.keyword.iva_short}} 服务仪表板中找到_管理_仪表板。

1. 转至 [{{site.data.keyword.Bluemix_notm}} 帐户资源列表](https://cloud.ibm.com/resources)。

1. 从**服务**列表中，选择您的**语音代理程序**服务实例，以在_管理_选项卡上打开服务仪表板。

## 语音代理程序摘要
{: #agent_summary}

如果您现在已经具有语音代理程序，那么您可以看到该代理程序的所有号码、描述和配置设置的摘要。要查看摘要，请单击语音代理程序**名称**左侧的下拉箭头按钮。然后将展开摘要。

语音代理程序可能包含多个号码，在语音代理程序摘要上将仅显示所选的**主号码**。缺省情况下，主号码为添加到语音代理程序的第一个号码，主号码仅用于展示，没有其他功能性用途。如果您希望语音代理程序展示其他号码，请参阅
[管理多个号码](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num)。

您可以从代理程序摘要中查看语音代理程序中的所有号码。展开配置的摘要后，单击**查看号码**按钮，新的**管理**对话框中将显示所有号码的列表。请参阅[管理多个号码](/docs/services/voice-agent?topic=voice-agent-multi_num)页面以获取使用**管理**对话框的更多信息。

## 编辑服务实例的最大并发连接数
{: #edit_service}

所有套餐都可以免费获取 2 个并发连接。如果使用_标准_或_高端_套餐，那么可以在_实例_选项卡上[更改最大并发连接数](/docs/services/voice-agent?topic=voice-agent-edit_concurrency)的缺省设置。

## 创建语音代理程序
{: #create_va}

使用_管理_仪表板上的_语音代理程序_选项卡来[创建新的语音代理程序](/docs/services/voice-agent?topic=voice-agent-config_instance)。

## 编辑语音代理程序
{: #edit_va}

您可以通过使用_管理_仪表板上的_语音代理程序_选项卡编辑现有语音代理程序来对其进行更改。要编辑语音代理程序，请单击语音代理程序的选项列表中的**编辑代理程序**。更改配置，然后保存更改。

## 克隆语音代理程序
{: #clone_va}

克隆语音代理程序时，Watson 服务的所有配置都会复制到新代理程序中。要克隆语音代理程序，请单击语音代理程序的选项列表中的**克隆代理程序**。为语音代理程序提供唯一名称和电话号码，根据需要更改任何配置选项，然后保存更改。

## 删除语音代理程序
{: #delete_va}

您可能想要删除语音代理程序以释放电话号码。一个电话号码只能有一个语音代理程序。要将电话号码用于其他语音代理程序，必须先将使用该电话号码的语音代理程序删除。

要删除语音代理程序，请转至_语音代理程序_选项卡，单击语音代理程序选项列表中的**删除代理程序**，然后保存更改。这将从语音代理程序列表中除去该语音代理程序。

## 按号码或描述搜索语音代理程序
{: #search}

您可以根据代理程序中保存的号码或描述搜索语音代理程序。

在_搜索_栏中，您可以输入号码或描述。输入时，搜索结果将自动更新。  

## 配置语音代理程序
{: #configure_va}

在创建、克隆或编辑语音代理程序时，可以更改语音代理程序的配置设置以及与相关服务的连接。

* **[配置多个电话号码](/docs/services/voice-agent?topic=voice-agent-multi_num)：**您可以将语音代理程序配置为包含多个电话号码。
* **[配置多个服务位置](/docs/services/voice-agent?topic=voice-agent-disaster-recovery)：**将所连接服务的多个服务位置都包含在内，以实现服务冗余。
* **[与第三方语音和文字服务连接](/docs/services/voice-agent?topic=voice-agent-third-party)：**不使用 {{site.data.keyword.texttospeechshort}} 或 {{site.data.keyword.speechtotextshort}}，而是将语音代理程序连接到第三方 API，例如 Google Cloud Speech-to-Text。
* **[使用其他 {{site.data.keyword.Bluemix_notm}} 工作空间中的服务](/docs/services/voice-agent?topic=voice-agent-other_service)：**可以将语音代理程序配置为使用属于其他 {{site.data.keyword.Bluemix_short}} 帐户中工作空间的 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.speechtotextshort}} 服务实例。
* **[使用服务编排引擎配置 Watson Assistant](/docs/services/voice-agent?topic=voice-agent-conversation_va)：**可以通过服务编排引擎 (SOE) 连接到 {{site.data.keyword.conversationshort}} 技能。SOE 可拦截传入和传出服务的消息，以便您使用第三方 API 对这些消息进行修改。
* **[为语音代理程序启用事件转发](/docs/services/voice-agent?topic=voice-agent-event_forwarding)：**您可能想要从 {{site.data.keyword.iva_short}} 收集呼叫数据并加以分析，以便让对话给呼叫者一种更自然的感觉。您创建的每个语音代理程序都可以将事件报告转发给您管理的指定 {{site.data.keyword.cloudant_short_notm}}。

## 配置高级语音代理程序选项
{: #config-advanced}

在创建或克隆语音代理程序时，可以单击**显示高级**以查看以下高级配置选项。

* **对话读取超时（可选）**：此选项设置语音代理程序等待 Watson Assistant 响应的时间（以秒为单位）。如果超过此时间，语音代理程序会再次尝试联系 Watson Assistant。如果仍无法联系服务，那么呼叫失败。缺省情况下设置为 5 秒。
* **{{site.data.keyword.conversationshort}} 失败回复消息（可选）**：在呼叫无法连接到 {{site.data.keyword.conversationshort}} 时发送给消息接收方的缺省响应消息。您可以输入最多 1024 个字符。
* **转移失败回复消息（可选）**：在呼叫转移失败时向呼叫者传送的缺省响应消息。您可以输入最多 1024 个字符。
* **定制 SIP INVITE 标题（可选）**：指定要从入局 SIP INVITE 请求中抽取的定制 SIP 标题。您可以输入最多 1024 个字符。
* **从 {{site.data.keyword.iva_short}} 发送临时响铃响应**：在 {{site.data.keyword.iva_short}} 处理入局呼叫时，发送 `180 ringing` 响应。缺省情况下，会启用此设置。
* **转移时让呼叫者等待**：在转移期间让呼叫者等待。缺省情况下，会启用此设置。
* **转移失败时断开呼叫**：用于确定在呼叫转移失败时是否断开呼叫。缺省情况下，会启用此设置。如果禁用此设置，那么当呼叫转移失败时，{{site.data.keyword.iva_short}} 会启动一轮对话。然后，{{site.data.keyword.conversationshort}} 可以断开呼叫或将其转移到对话中配置的其他目标。
* **发生网络事件时通知 {{site.data.keyword.conversationshort}}**：启用此设置后，如果检测到网络错误，那么 {{site.data.keyword.iva_short}} 会使用文本“vgwNetworkWarningMessage”向 {{site.data.keyword.conversationshort}} 服务启动一轮对话。`vgwNetworkWarnings` 状态变量包含在当前轮次中发生的网络事件的列表。如果禁用此设置，那么会在 `vgwNetworkWarnings` 状态变量中的下一个轮次事件中发送当前轮次期间发生的网络事件的列表。缺省情况下，会启用此设置。
