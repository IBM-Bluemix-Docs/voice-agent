---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-06-24"

keywords: voice agent, creating a SIP trunk, creating and connecting your voice agent,

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 入门教程
{: #getting-started}
{{site.data.keyword.iva_full}} 使用会话启动协议 (SIP)，帮助您将一组精心编排的 Watson 服务与电话网络进行集成。本教程介绍了如何设置可从任何电话进行呼叫的认知语音代理程序。
{: shortdesc}

新的 SMS 功能已添加到 {{site.data.keyword.iva_full_notm}}。配置 SMS 功能并不需要本页面上描述的所有过程。请参阅[语音代理程序入门教程](/docs/services/voice-agent?topic=voice-agent-connect-sms)，以获取有关如何将 SMS 与 {{site.data.keyword.iva_full_notm}} 连接的指示信息
{: tip}

观看本 [{{site.data.keyword.iva_full_notm}} 教程 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/) 中有关如何创建第一个语音代理程序的演示。
{: tip}

如果您需要任何协助，请通过 Slack `#ibmvoicegateway` 通道下的 [IBM Cloud 技术 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) 团队联络我们。
{: tip}

## 开始之前
{: #prereqs}

在 [{{site.data.keyword.Bluemix_short}}](https://cloud.ibm.com/) 上创建新帐户或登录到现有帐户。

## 步骤 1：在 {{site.data.keyword.Bluemix_notm}} 上创建 {{site.data.keyword.iva_short}} 服务实例
{: #step1}

在 [{{site.data.keyword.iva_short}} 目录页面](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)上，查看服务信息，然后单击**创建**。

创建服务后，请记下_开始使用_仪表板上的语音代理程序端点。您需要该端点 SIP URI 来配置 SIP 中继。

## 步骤 2：创建 SIP 中继以将呼叫转移到 {{site.data.keyword.iva_short}}
{: #step2}

1. 通过以下任一受支持提供者创建 SIP 中继。然后，将电话号码关联到 SIP 中继。

  * [NetFoundry](/docs/services/voice-agent?topic=voice-agent-connect#NetFoundry-setup)
  * [Twilio](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup)
  * [AT&T 以及其他 SIP 中继提供者](/docs/services/voice-agent?topic=voice-agent-connect#att-other)
  * [与 {{site.data.keyword.iva_short}}](/docs/services/voice-agent?topic=voice-agent-connect#peering) 对等 

## 步骤 3：创建和连接语音代理程序
{: #step3}

1. 转至 {{site.data.keyword.iva_short}} 仪表板上的_管理_仪表板，然后单击**创建语音代理程序**。

2. 输入语音代理程序的基本设置：
  * **名称**：语音代理程序的唯一名称，例如 `Customer Support`
  * **电话号码**：与 SIP 中继相关联的完整电话号码，包括国家和地区代码。例如，对于美国 800 号码，请将电话号码指定为 18883334444。电话号码可以包含空格和 + ( ) - 字符。
  * **描述**：用途的相关描述（非必填）
  * **缺省转移目标：**可将呼叫转移到的终止 URI（非必填）。

3. 为语音代理程序创建 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 和 {{site.data.keyword.texttospeechshort}} 服务实例。您可以选择使用以下任一方法来创建语音代理程序：
  * 单击**创建语音代理程序**，以使用缺省配置一步创建语音代理程序和所有服务。
  * 或者，分别单击每个服务名称来自行创建服务。然后，返回到 {{site.data.keyword.iva_short}} 并单独创建语音代理程序。

   如果手动创建了 {{site.data.keyword.conversationshort}} 服务实例，请添加对话来测试语音代理程序。要快速开始测试，请从 GitHub 克隆[样本对话 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json)，然后将该[样本作为技能导入](/docs/services/assistant?topic=assistant-skill-dialog-add)：

   1. 在样本对话 GitHub 页面上，单击行号 `1`，然后选择 **... > 复制行**。将复制的文本粘贴到一个文件中，然后将其另存为 JSON 文件，例如 `voice-gateway-conversation-en.json`。
   2. 启动 {{site.data.keyword.conversationshort}} 工具。在_技能_页面上，单击 ![导入工作空间](../conversation/images/workspace_import.png) 图标，并导入 JSON 文件。

  或者，可以[构建自己的对话](/docs/services/assistant?topic=assistant-getting-started#getting-started-build-dialog)来模拟生产环境。对话必须至少包含具有 `conversation_start` 条件的节点和具有缺省响应的节点。


## 后续步骤
{: #next-steps}

通过呼叫与语音代理程序相关联的电话号码来测试语音代理程序。如果听到响应，说明语音代理程序处于活动状态！

如果未听到响应，可以在_使用情况_仪表板上检查呼叫日志和语音代理程序使用情况。请参阅[查看使用情况和呼叫日志](/docs/services/voice-agent?topic=voice-agent-logging)。

您可以在_管理_仪表板上，编辑语音代理程序的设置，创建或除去语音代理程序，以及将多个 Watson 服务位置添加到语音代理程序。有关更多信息，请参阅[管理语音代理程序](/docs/services/voice-agent?topic=voice-agent-managing)。

您还可以配置高级设置，例如从 Twilio 帐户保护 SIP 连接的安全。请参阅[保护连接](/docs/services/voice-agent?topic=voice-agent-securing)。
