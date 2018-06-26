---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 故障诊断与支持
{: #troubleshooting}

在使用 {{site.data.keyword.iva_full}} 时，有遇到问题吗？有关常见问题，请查看故障诊断技巧；有关其他问题，请访问社区以寻求帮助。
{: shortdesc}

## 如何对 {{site.data.keyword.iva_short}} 进行故障诊断
{: #how-to}

要对语音代理程序的问题进行故障诊断，您可以使用日志记录、使用情况和事件转发来查找错误和故障记录。这些记录可帮助您诊断和解决语音代理程序的问题。如果使用 {{site.data.keyword.iva_short}} 时遇到问题，请尝试以下步骤。

1. 在呼叫失败时，最后的 {{site.data.keyword.conversationshort}} 轮次可能说明故障。

1. 使用情况日志向您显示特定呼叫期间可能发生的任何错误。请参阅[查看使用情况和呼叫日志](logging.html)。

1. 请检查服务提供者日志以查找信号错误。例如，Twilio 为其托管的每个 SIP 中继提供日志。

1. 通过[为语音代理程序启用事件转发](event-forwarding.html)，您可以配置语音代理程序以将呼叫详细记录 (CDR) 转发到 Cloudant 数据库，然后确定呼叫失败原因。其他事件（例如，{{site.data.keyword.conversationshort}} 轮次事件）可提供有关呼叫中每轮对话的详细信息。

**重要信息**：CDR、转录和轮次事件包含来自用户的信息，其中可能含有受保护的健康信息 (PHI)、个人可标识信息 (PII) 或 PCI 数据安全标准 (PCI DSS) 数据。为了防止泄露个人信息，您必须确保 {{site.data.keyword.cloudant_short_notm}} 实例能够妥善保护用户在对话中或对话期间共享的机密信息。


## 获取帮助
{: #help}

如果您需要帮助，请将您的问题或意见发布到以下任一位置来加入我们的开发者社区，我们会实时监视这些位置。

* 使用 `voice-agent` 标记，发布到 [dwAnswers 论坛 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/topics/voice-agent/) 上
* 使用 `voice-agent` 标记，发布到 [StackOverflow ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://stackoverflow.com/questions/tagged/voice-agent){: new_window} 上
* 在 Slack `#ibmvoicegateway` 通道下的 [IBM Cloud 技术 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) 团队中找到我们

**请记住**：在发布任何日志或呼叫记录前，请除去呼叫者和用户在对话期间可能共享的所有个人信息。

## 故障诊断技巧
{: #troubleshooting-tips}

### 当我呼叫我的语音代理程序时，电话上为什么没有响应？

您的呼叫可能未连接到服务。如果未正确设置 {{site.data.keyword.iva_short}} 服务实例，那么会发生此问题。请检查以下语音代理程序设置：

* 验证语音代理程序_管理_仪表板上的电话号码是否与来自 SIP 中继提供者的电话号码相同，例如，NetFoundry 或 Twilio。

   **注：**当您在语音代理程序的_管理_仪表板上指定电话号码时，必须加上国家和地区代码。例如，`18884253968`。

* 验证 Watson 服务凭证、URL 和 {{site.data.keyword.conversationshort}} 工作空间标识是否都有效。
* 验证 {{site.data.keyword.conversationshort}} 工作空间中的对话是否已正确创建。
  * 可以从 GitHub 导入预构建工作空间的[样本对话 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json)。有关将样本对话另存为 JSON 文件，然后将该文件作为工作空间导入 {{site.data.keyword.conversationshort}} 工具中的详细信息，请参阅[*入门教程*中的步骤 3](getting-started.html#step3)。
  * 如果您创建了自己的 {{site.data.keyword.conversationshort}} 对话，请验证该对话是否包含具有 `conversation_start` 条件的节点和具有缺省响应的节点。有关详细的指示信息，请参阅 {{site.data.keyword.conversationshort}} 文档中的[构建对话](../conversation/dialog-build.html)。
* 查看您的电话呼叫是否在语音代理程序的_使用情况_仪表板上列出。如果存在您电话呼叫的条目，说明您的语音代理程序已连接到 Watson 服务。

### 我在创建语音代理程序时为什么无法指定电话号码？

请查看一下是否有现有语音代理程序已使用您指定的电话号码。一个电话号码只能用于一个语音代理程序。您可以通过 SIP 中继提供者供应其他电话号码，并使用该号码来创建其他语音代理程序。或者，[在_管理_仪表板上删除现有语音代理程序](managing.html#delete_va)以释放电话号码，然后创建新的语音代理程序。

### 为何我的呼叫频繁失败？

如果呼叫失败，那么语音代理程序可能遇到问题，因为服务编排引擎 (SOE) 启动长事务而且不会及时响应语音代理程序。如果事务超过缺省 {{site.data.keyword.conversationshort}} 超时，那么呼叫失败。为避免呼叫失败，SOE 可使用 `vgwConversationResponseTimeout` 状态变量修改缺省 {{site.data.keyword.conversationshort}} 超时。请参阅[在 {{site.data.keyword.conversationshort}} 对话中设置的状态变量](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html#variables-conv)。
