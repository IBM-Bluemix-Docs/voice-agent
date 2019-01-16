---

copyright:
  years: 2018
lastupdated: "2018-12-04"


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

启用呼叫转移后，如果呼叫者在对话期间请求与人工代理通话，语音代理程序会重定向该呼叫。{{site.data.keyword.iva_short}} 使用 SIP REFER 将呼叫定向回 SIP 中继提供者以进行处理，并且不会锚定已转移的电话呼叫。

您可以通过在 SIP 提供者配置中设置终止 URI 或电话 URI 来启用呼叫转移。然后在 {{site.data.keyword.conversationshort}} 实例的对话节点中的 API 操作上定义转移目标。转移目标是包含终止 URI 和电话号码的 SIP URI，或是包含电话号码的电话 URI。有关支持的操作和定制语音代理程序的更多信息，请参阅[使用 API 对语音代理程序编程](api.html)。

## 步骤 1：设置终止 URI
{: #termination-setup}

如果在 SIP URI 配置中使用的是电话 URI 而不是终止 URI，那么对于 `trasnferTarget`，您可以使用电话 URI（例如 `tel:+18889990000`）。如果使用的是终止 URI，那么对于 `transferTarget`，您需要一个终止 URI。
{: tip}

### 在 NetFoundry 中设置终止 URI
{: #termination-netfoundry}

记下 [NetFoundry 帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson.netfoundry.io/watson-login){: new_window} 中要转移到的电话号码。以后，可以在 {{site.data.keyword.conversationshort}} 对话中将此电话号码和终止 URI 指定为转移目标。不要使用个人电话号码。

复制以下 NetFoundry 终止 URI 以用于转移目标。

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

1. 从导航栏中选择**常规**以查看_常规设置_。在**呼叫转移 (SIP REFER)** 标题下，将设置切换为**已启用**并选择**允许通过中继向 PSTN 呼叫转移。**

1. 单击**保存**以完成对终止 URI 的配置并启用呼叫转移。

1. 请记下要转移到的电话号码和终止 URI。确保电话号码不是个人电话号码。可以使用电话号码和终止 URI 来指定 {{site.data.keyword.conversationshort}} 对话中的转移目标。


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

  * 如果使用的是电话 URI，那么请使用电话 URI 替换掉 `transferTarget` 中的 SIP URI。例如，`"transferTarget":"tel:+18889990000"`。

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
       "transferTarget": "sip:+18889990000\\@dal.watson-va.netfoundry.net"
              }
          }
      }
  }
  ```
  {: codeblock}

1. 请检查 `transferTarget` 终止 URI 中的电话号码，或电话 URI 是否正确匹配了 SIP 中继中的电话号码。

**请记住**：转移目标的 SIP URI 包含电话号码和您所创建的终止 URI。不要在转移目标中使用个人电话号码。例如，如果电话号码为 `18889990000`，终止 URI 为 `mysiptrunk.pstn.twilio.com`，那么完整的 SIP URI 为 `sip:+18889990000\\@mysiptrunk.pstn.twilio.com`。如果使用 Netfoundry 且电话号码为 `18889990000`，那么完整 SIP URI 为 `sip:+18889990000\\@dal.watson-va.netfoundry.net`。

## 后续步骤
{: #Next}

通过呼叫与语音代理程序相关联的电话号码来测试语音代理程序，然后使用您在意向中确定的关键术语。如果语音代理程序进行了重定向，说明设置成功！

现在，可以优化并配置**转移**意向和对话，以响应所选的关键术语和短语。
