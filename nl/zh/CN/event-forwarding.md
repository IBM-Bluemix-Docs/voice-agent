---

copyright:
  years: 2019
lastupdated: "2019-01-30"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 为语音代理程序启用事件转发
{: #event_forwarding}

要启用事件转发来收集 {{site.data.keyword.iva_full}} 中语音代理程序所处理的呼叫的相关信息，可以使用 {{site.data.keyword.cloudantfull}} 数据库服务。
{: shortdesc}

您可能想要从 {{site.data.keyword.iva_short}} 中收集呼叫数据并加以分析，让对话给呼叫者一种更自然的感觉。您创建的每个语音代理程序都可以将事件报告转发给您管理的指定 {{site.data.keyword.cloudant_short_notm}}。事件报告包括呼叫详细记录 (CDR) 事件、转录事件和轮次事件报告。有关可转发的事件类型的更多信息，请参阅[报告事件](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}。

分析来自这些事件的数据可帮助您调整对话，优化意向以及改善呼叫者的总体体验。

此外，还可以在创建或编辑语音代理程序时选择启用事件转发。有关创建和编辑语音代理程序的更多详细信息，请参阅[管理语音代理程序](/docs/services/voice-agent?topic=voice-agent-managing)。您需要提供 {{site.data.keyword.cloudant_short_notm}} 帐户信息（包括帐户名称和密码）才能启用事件转发。

**重要信息**：CDR、转录和轮次事件包含来自用户的信息，其中可能含有受保护的健康信息 (PHI)、个人可标识信息 (PII) 或 PCI 数据安全标准 (PCI DSS) 数据。为了防止泄露个人信息，您必须确保 {{site.data.keyword.cloudant_short_notm}} 实例能够妥善保护用户在对话中或对话期间共享的机密信息。请参阅[信息安全和数据隐私：事件转发](/docs/services/voice-agent?topic=voice-agent-infosec#event_forwarding)以及 [{{site.data.keyword.cloudant_short_notm}}：安全性](/docs/services/Cloudant/offerings?topic=cloudant-security#security)。


## 启用事件转发
{: #enable-event-forwarding}

在 {{site.data.keyword.Bluemix_short}} 上的_管理_仪表板中创建或编辑语音代理程序时，可以启用事件转发。

1. 在**事件转发**部分中，完成 {{site.data.keyword.texttospeechshort}} 的“配置”部分后，选择**启用事件转发**。

1. 选择**我的 {{site.data.keyword.cloudant_short_notm}} 服务实例**或**其他 {{site.data.keyword.cloudant_short_notm}} 服务实例**。
  * 如果使用**我的 {{site.data.keyword.cloudant_short_notm}} 服务实例**，请从列表中选择 **{{site.data.keyword.cloudant_short_notm}} 帐户**名称和用户名。
  * 如果要在达拉斯或华盛顿区域创建语音代理程序，但没有 {{site.data.keyword.cloudant_short_notm}} 服务实例，那么可以使用 **Cloudant 帐户**菜单创建一个服务实例。
  * 如果您使用**其他 {{site.data.keyword.cloudant_short_notm}} 服务实例**，那么请输入 {{site.data.keyword.cloudant_short_notm}} 用户名和密码（最多分别为 128 和 256 个字符）或者帐户的 API 密钥（最多 64 个字符）。

1. 针对要转发的每种类型的事件选择**启用**，然后选择要将事件转发给哪个数据库。
  * 呼叫详细记录 (CDR) 事件
  * 转录事件
  * 轮次事件

1. 查看数据库以确保事件报告转发正确无误。

## 相关链接
{: #related-links-forwarding}
* [IBM Voice Gateway：报告事件](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
* [信息安全和数据隐私](/docs/services/voice-agent?topic=voice-agent-infosec)
* [{{site.data.keyword.cloudant_short_notm}}：安全性](/docs/services/Cloudant/offerings?topic=cloudant-security#security)
