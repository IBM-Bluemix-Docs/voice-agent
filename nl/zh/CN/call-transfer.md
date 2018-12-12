---

copyright:
  years: 2018
lastupdated: "2018-11-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 设置呼叫转移
{: #call-transfer}

设置呼叫转移后，如果呼叫者在对话期间请求与人工代理通话，语音代理程序会自动转移该呼叫。
{: shortdesc}

## 关于呼叫转移
{: #about-ct}

启用呼叫转移后，如果呼叫者在对话期间请求与人工代理通话，语音代理程序会重定向该呼叫。您可以通过以下方法来启用呼叫转移：在 SIP 提供者配置中设置终止 URI。然后，在 {{site.data.keyword.conversationshort}} 实例的对话节点中配置转移目标或定义 API 操作。转移目标是包含终止 URI 和电话号码的 SIP URI。

有关支持的操作和定制语音代理程序的更多信息，请参阅[使用 API 对语音代理程序编程](api.html)。

## 步骤 1：设置终止 URI
{: #termination-setup}

### 在 NetFoundry 中设置终止 URI
{: #termination-netfoundry}

记下 [NetFoundry 帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson.netfoundry.io/watson-login){: new_window} 中要转移到的电话号码。以后，可以在 {{site.data.keyword.conversationshort}} 对话中将此电话号码和终止 URI 指定为转移目标。不要使用个人电话号码。

您可以复制以下 NetFoundry 终止 URI，以便在创建语音代理程序或在 {{site.data.keyword.conversationshort}} 对话中配置转移目标时使用。

```
dal.watson-va.netfoundry.net
```
{: codeblock}

在[将 {{site.data.keyword.conversationshort}} 配置用于呼叫转移](#conversation-setup)时，不需要在 NetFoundry 帐户中手动配置终止 URI。

### 在 Twilio 中设置终止 URI
{: #termination-Twilio}

1. 在 Twilio 帐户中，浏览至_弹性 SIP 中继_仪表板，然后选择**中继**。

1. 选择要向其中添加呼叫转移的中继（您可以选择现有中继，也可以单击 **+** 图标来创建新中继）。

  * 要创建新中继，需要在**来源**仪表板中配置 _SIP 中继 URI_。有关更多信息，请参阅[连接 SIP 中继](connect-SIP.html)。

1. 从导航栏中选择**终止**，然后输入终止 URI 的名称。

  * 终止 URI 名称必须唯一。Twilio 会自动检查您选择的名称以确定其是否可用。有关 Twilio 服务的更多详细信息，请参阅 [SIP 中继终止设置 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window}。

1. 在_认证_部分中，单击 **+** 图标以将语音代理程序 IP 地址添加到访问控制 IP 列表中。

  添加以下两个 IP 地址：
   * 169.60.154.134（达拉斯服务区域）
   * 169.61.86.179（华盛顿服务区域）

1. 单击**保存**以完成终止 URI 的配置。

请记下要转移到的电话号码和终止 URI。确保电话号码不是个人电话号码。

您可以在创建语音代理程序或在 {{site.data.keyword.conversationshort}} 对话中配置转移目标时使用电话号码和终止 URI。


## 步骤 2：将 {{site.data.keyword.conversationshort}} 配置用于呼叫转移
{: #conversation-setup}

要了解有关 {{site.data.keyword.conversationshort}} 服务的工作原理的更多信息，请参阅[关于 {{site.data.keyword.conversationshort}}](../conversation/index.html#about)。

1. 在 {{site.data.keyword.Bluemix_notm}}“仪表板”中，选择您的语音代理程序使用的 {{site.data.keyword.conversationshort}} 实例。

1. 在_开始使用_仪表板中，单击**启动工具**按钮。

1. 单击要编辑的工作空间上的**开始使用**。

1. 单击**添加意向**，然后输入意向名称，例如_转移_。

  您可以输入更多详细信息，也可以过些时候再回来编辑和优化意向。

1. 创建呼叫转移意向后，选择_对话_选项卡。

1. 单击**添加节点**，然后输入节点名称，例如_呼叫转移_。

1. 在_如果机器人识别：_部分中，键入**呼叫转移意向**以找到您创建的意向。

1. 在_那么响应：_部分中，单击 **&vellip;** 图标，然后选择**打开 JSON 编辑器**。复制并粘贴以下代码片段，以替换字段中的代码：

```json
{
    "output": {
   "text": {
     "values": [ "Please hold on while I connect you with a live agent." ],
     "selection_policy": "sequential"
   },
   "vgwAction": {
     "command": "vgwActTransfer",
     "parameters": {
       "transferTarget": "sip:18889990000\\@dal.watson-va.netfoundry.net"
            }
        }
    }
}
```
{: codeblock}

**请记住**：转移目标的 SIP URI 包含电话号码和您所创建的终止 URI。不要在转移目标中使用个人电话号码。例如，如果电话号码为 `18889990000`，终止 URI 为 `mysiptrunk.pstn.twilio.com`，那么完整的 SIP URI 为 `sip:18889990000\\@mysiptrunk.pstn.twilio.com`。如果使用 Netfoundry 且电话号码为 `18889990000`，那么完整 SIP URI 为 `sip:18889990000\\@dal.watson-va.netfoundry.net`。

为了保护个人可标识信息 (PII)，在配置转移目标 SIP URI 时，请勿使用个人电话号码。请参阅 [{{site.data.keyword.iva_short}} 和信息处理](infosec.html#configure_infosec){:new_window}以了解有关 PII 和配置的更多信息。
{: tip}

## 后续步骤
{: #Next}

通过呼叫与语音代理程序相关联的电话号码来测试语音代理程序，然后使用您在意向中确定的关键术语。如果语音代理程序进行了重定向，说明设置成功！

现在，可以优化并配置**转移**意向和对话，以响应所选的关键术语和短语。
