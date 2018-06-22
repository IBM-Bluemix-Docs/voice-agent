---

copyright:
  years: 2018
lastupdated: "2018-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 连接 SIP 中继
{: #connect}

您可以从以下列表中选择 SIP 中继提供者，用于与 {{site.data.keyword.iva_full}} 集成。
{: #shortdesc}

* [NetFoundry](#NetFoundry-setup)
* [Twilio](#twilio-setup)
* [AT&T 以及其他提供者](#att-other)
* [与 {{site.data.keyword.iva_short}}](#peering) 对等 
* [请求协助进行设置](#request-setup)

## 创建 NetFoundry SIP 中继和电话号码
{: #NetFoundry-setup}

**注：**创建帐户需要信用卡，并根据使用情况定期收取费用。如果您已经拥有 NetFoundry 帐户，可以使用现有帐户。

1. 在 [NetFoundry![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson.netfoundry.io/watson-login){: new_window} Web 站点上创建帐户。

1. 转至 _Watson 帐户_ 主页。

1. 选择号码所在区域。

  **注：**请检查 Netfoundry Web 站点以查找可用区域。将持续添加新区域。

1. 单击**购买**，按照屏幕上的指示信息完成购买。

1. 成功付款后，您的帐户中将显示 SIP 中继电话号码。

您需要使用此电话号码设置语音代理程序和配置呼叫转移，包括国家和地区编码。请参阅[创建和连接语音代理程序](getting-started.html#step3)。


## 创建 Twilio SIP 中继
{: #twilio-setup}

**注**：创建 [Twilio 帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.twilio.com/try-twilio){: new_window} 需要信用卡，因为会根据配置的 SIP 中继的使用情况定期收取费用。如果您有 Twilio 帐户，可以使用现有帐户。

  1. 在 [Twilio Web 站点 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.twilio.com/try-twilio){: new_window} 上创建 Twilio 帐户。

  1. 使用 Twilio 帐户创建 SIP 中继。

  1. 在 Twilio Web 站点中，转至“弹性 SIP 中继”仪表板。

  1. 从导航栏中选择**中继**，然后创建 SIP 中继。如果您有 SIP 中继，请单击 **+** 图标。在出现的对话框中，输入 SIP 中继的名称，然后单击**创建**。

  1. 在“弹性 SIP 中继”页面中，选择您的 SIP 中继。

  1. 针对您的 SIP 中继，从导航栏中选择**来源**，然后配置来源 SIP URI。您可以选择 **+** 图标来添加多个主机名，以防止服务发生故障。

  IP 地址或主机名是您从 {{site.data.keyword.iva_short}} 服务实例的_开始使用_仪表板上记下的值。配置来源 URI 时，必须使用 SIP URI 格式，例如 `sip:us-south.voiceagent.cloud.ibm.com/`。添加多个主机名或 IP 地址后，如果第一个主机端点发生故障或停止服务，那么 SIP 中继提供者会将呼叫定向到所列的下一个主机名。

  1. 针对您的 SIP 中继，从导航栏中选择**号码**。然后，创建电话号码，并将其分配给您的 SIP 中继。

  在“号码”页面上，单击**购买号码**。如果您有号码，请单击 **+** 图标。在显示的面板上，可以提供您所在区域的新电话号码。返回到所创建的 SIP 中继，然后单击“号码”图标，将该号码分配给该 SIP 中继。

  您需要使用此电话号码设置语音代理程序，包括国家和地区编码。请参阅[创建和连接语音代理程序](getting-started.html#step3)。


## 连接 AT&T 以及其他提供者
{: #att-other}

{{site.data.keyword.iva_short}} 支持连接 AT&T&reg; 以及其他 SIP 中继提供者。但是，这些连接不是自助服务设置，需要额外协助。请参阅[请求协助进行设置](#request-setup)。

## 与 {{site.data.keyword.iva_short}} 对等
{: #peering}

{{site.data.keyword.iva_short}} 支持对等连接，例如 IPSec 隧道。但是，这些连接不是自助服务设置，需要额外协助。请参阅[请求协助进行设置](#request-setup)。

## 请求协助进行设置
{: #request-setup}

您可以请求协助进行网络设置以与 AT&T 或其他 SIP 中继提供商连接、与 {{site.data.keyword.iva_short}} 进行配对或者使用以下过程请求超过 50 个并发连接。

1. 开一个新的 [{{site.data.keyword.Bluemix_notm}} 支持凭单](https://console.bluemix.net/unifiedsupport/tickets/add)

1. 对于**凭单类型**，选择**技术**。

1. 对于**选择资源上下文**，选择 **Cloud Foundry**。

1. 对于**支持的技术领域**，选择**应用程序服务**。

1. 为您的 {{site.data.keyword.iva_short}} 实例，选择**区域**、**组织**以及**空间**。

1. 对于**关联的资源**，选择 {{site.data.keyword.iva_short}} 服务实例。

1. 对于**严重性**，选择**严重性 4 - 影响最小**。

1. 对于**主题**，输入 `{{site.data.keyword.iva_short}} 协助进行的网络设置`。

1. 在**简要描述**部分，描述您打算如何连接 {{site.data.keyword.iva_short}} 服务或者对于语音代理程序请求 50 个以上的并发连接。您可以通过使用 SIP 中继提供者或者对等连接来进行连接，例如 IPSec 隧道。在您的凭单中，您可以随附一个 PDF 或图像格式的网络图，描述网络拓扑。您还可以随附任何白皮书，详细描写您想要的服务功能。
