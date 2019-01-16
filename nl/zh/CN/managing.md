---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 管理服务实例和语音代理程序
{: #managing}

您可以使用_管理_仪表板来更改服务实例配置，还可以创建、编辑、克隆、配置或除去单个语音代理程序。您的服务实例中可以有多个语音代理程序，但每个语音代理程序的名称和电话号码都必须唯一。
{: shortdesc}

## 导航到语音代理程序服务仪表板
{: #navigate_manage}

您可以从 {{site.data.keyword.iva_short}} 服务仪表板中找到_管理_仪表板。

1. 转至 [{{site.data.keyword.Bluemix_notm}} 帐户资源列表](https://cloud.ibm.com/resources)。

1. 从**服务**列表中，选择您的**语音代理程序**服务实例，以在_管理_选项卡上打开服务仪表板。

## 编辑服务实例的最大并发连接数
{: #edit_service}

所有套餐都可以免费获取 2 个并发连接。如果使用_标准_或_高端_套餐，那么可以在_实例_选项卡上[更改最大并发连接数](managing_concurrency.html)的缺省设置。

## 创建语音代理程序
{: #create_va}

使用_管理_仪表板上的_语音代理程序_选项卡来[创建新的语音代理程序](managing_create.html)。

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

## 配置语音代理程序
{: #configure_va}

在创建、克隆或编辑语音代理程序时，可以更改语音代理程序的配置设置以及与相关服务的连接。

* **[配置多个服务位置](managing_disaster_recovery.html)：**将所连接服务的多个服务位置都包含在内，以实现服务冗余。
* **[与第三方语音和文字服务连接](managing_third_party.html)：**不使用 {{site.data.keyword.texttospeechshort}} 或 {{site.data.keyword.speechtotextshort}}，而是将语音代理程序连接到第三方 API，例如 Google Cloud Speech-to-Text。
* **[使用其他 {{site.data.keyword.Bluemix_notm}} 工作空间中的服务](managing_other.html)：**可以将语音代理程序配置为使用属于其他 {{site.data.keyword.Bluemix_short}} 帐户中工作空间的 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.speechtotextshort}} 服务实例。
* **[使用服务编排引擎配置 Watson Assistant](managing_SOE.html)：**可以通过服务编排引擎 (SOE) 连接到 {{site.data.keyword.conversationshort}} 工作空间。SOE 可拦截传入和传出服务的消息，以便您使用第三方 API 对这些消息进行修改。
* **[为语音代理程序启用事件转发](event-forwarding.html)：**您可能想要从 {{site.data.keyword.iva_short}} 收集呼叫数据并加以分析，以便让对话给呼叫者一种更自然的感觉。您创建的每个语音代理程序都可以将事件报告转发给您管理的指定 {{site.data.keyword.cloudant_short_notm}}。

## 配置高级语音代理程序选项
{: #config-advanced}

在创建或克隆语音代理程序时，可以单击**显示高级**以查看以下高级配置选项。

* **{{site.data.keyword.conversationshort}} 失败回复消息（可选）**：在呼叫无法连接到 {{site.data.keyword.conversationshort}} 时发送给消息接收方的缺省响应消息。
* **转移失败回复消息（可选）**：在呼叫转移失败时向呼叫者传送的缺省响应消息。
* **定制 SIP INVITE 标题（可选）**：指定要从入局 SIP INVITE 请求中抽取的定制 SIP 标题
* **从 {{site.data.keyword.iva_short}} 发送临时响铃响应**：在 {{site.data.keyword.iva_short}} 处理入局呼叫时，发送 `180 ringing` 响应。缺省情况下，会启用此设置。
* **转移时让呼叫者等待**：在转移期间让呼叫者等待。缺省情况下，会启用此设置。
* **转移失败时断开呼叫**：用于确定在呼叫转移失败时是否断开呼叫。缺省情况下，会启用此设置。如果禁用此设置，那么当呼叫转移失败时，{{site.data.keyword.iva_short}} 会启动一轮对话。然后，{{site.data.keyword.conversationshort}} 可以断开呼叫或将其转移到对话中配置的其他目标。
* **发生网络事件时通知 {{site.data.keyword.conversationshort}}**：启用此设置后，如果检测到网络错误，那么 {{site.data.keyword.iva_short}} 会使用文本“vgwNetworkWarningMessage”向 {{site.data.keyword.conversationshort}} 服务启动一轮对话。`vgwNetworkWarnings` 状态变量包含在当前轮次中发生的网络事件的列表。如果禁用此设置，那么会在 `vgwNetworkWarnings` 状态变量中的下一个轮次事件中发送当前轮次期间发生的网络事件的列表。缺省情况下，会启用此设置。
