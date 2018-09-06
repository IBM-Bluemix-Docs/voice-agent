---

copyright:
  years: 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 保护连接
{: #securing}

要保护使用 {{site.data.keyword.iva_full}} 建立的连接，可以使用传输层安全性 (TLS) 为您的 SIP 中继启用安全实时传输协议 (SRTP) 和加密。

## 在 Twilio 中设置 SRTP
{: #SRTP}

**注：**如果启用 SRTP，还会加密 SIP 消息。不需要单独启用 SRTP 和 SIP 消息加密。

1. 在 Twilio 帐户中，浏览至_弹性 SIP 中继_仪表板，然后选择**中继**。

1. 选择要使用 SRTP 保护的中继（您可以选择现有中继，也可以单击 **+** 图标来创建新中继）。

  * 要创建新中继，需要在**来源**仪表板中配置 _SIP 中继 URI_。有关更多信息，请参阅[连接 SIP 中继](connect-SIP.html)。

1. 在_一般_仪表板上，查找_保护中继_部分。单击**已禁用**将安全中继设置更改为**已启用**，并保存更改。

## 在 Twilio 中使用 TLS 仅对 SIP 消息启用加密
{: #TLS}

如果只想加密 {{site.data.keyword.iva_short}} 中的 SIP 消息，而不使用 SRTP，那么可以在 Twilio 中选择使用传输层安全性 (TLS) 的 URI 端点。

1. 在 Twilio 帐户中，浏览至_弹性 SIP 中继_仪表板，然后选择**中继**。

1. 选择要向其中添加呼叫转移的中继（您可以选择现有中继，也可以单击 **+** 图标来创建新中继）。

1. 从菜单中选择**来源**，并输入以下安全来源 URI，一次一个。添加多个主机名或 IP 地址后，如果第一个主机端点发生故障或停止服务，那么 SIP 中继提供者会将呼叫定向到所列的下一个主机名。

```
sip:us-south.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}

或者

```
sip:us-east.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}
