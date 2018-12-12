---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 使用服务编排引擎配置 {{site.data.keyword.conversationshort}}
{: #conversation_va}

作为配置 {{site.data.keyword.conversationshort}} 服务实例的替代方法，您可以连接到服务编排引擎 (SOE)。
{: shortdesc}

您可以通过[服务编排引擎 (SOE)](about.html#arch-soe) 连接到 {{site.data.keyword.conversationshort}} 工作空间。SOE 可拦截传入和传出服务的消息，以便您使用第三方 API 对这些消息进行修改。

## 配置与 SOE 的连接
{: #how-to}

1. 在语音代理程序_管理_页面上的_语音代理程序_选项卡中，导航到 {{site.data.keyword.conversationshort}} 配置部分。

1. 选择**服务编排引擎**，作为您的**服务类型**。

1. 为您的**服务类型**选择**区域**。

1. 在 **URL** 字段中，输入 SOE 工作空间的完整 URL，例如 `https://iva-soesample.myorg.net/SOE/myWorkspace`。

  **重要信息**：为了实现数据安全，请确保对 SOE 工作空间使用安全 URL（即，使用 `https:` 而不是 `http:`），并要求认证。请参阅[信息安全和数据隐私](infosec.html)以了解更多安全性注意事项。

1. **可选** 如果您的 SOE 要求认证（建议），请在相应的字段中输入用户名和密码。
