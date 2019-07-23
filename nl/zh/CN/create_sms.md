---

copyright:
  years: 2019
lastupdated: "2019-06-24"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 创建 SMS 代理程序
{: #sms_config_instance}

创建 {{site.data.keyword.iva_full}} 服务后，可以使用_管理_仪表板来创建单个 SMS 代理程序。
{: shortdesc}

1. 转至_管理_仪表板上的_语音代理程序_选项卡，然后单击**创建语音代理程序**。

1. 针对**代理程序类型**，选择 _SMS_。

1. 对于**名称**，请为语音代理程序指定唯一名称。例如，`Customer Support - North America`。该名称可以包含最多 64 个字符。

1. 对于电话号码，请从 SIP 中继添加号码，包括国家和地区代码。例如，对于美国 800 号码，请将电话号码指定为 18883334444。电话号码最多不超过 30 个字符，包括空格和 + ( ) - 字符。SMS 仅支持每个用户一个号码。

1. 在 **SMS 提供者**下，输入用户名、密码和 SMS 提供者的 API URL。例如，如果使用 _Twilio_，那么用户名是**帐户 SID**，密码是您的**认证令牌**，而 SMS 提供者是 `https://api.twilio.com`

1. 在**会话**下，配置与 {{site.data.keyword.conversationshort}} 服务实例的连接。您可以使用自己或其他人拥有的 {{site.data.keyword.Bluemix_notm}} 帐户中的 {{site.data.keyword.conversationshort}} 服务实例。还可以通过服务编排引擎 (SOE) 连接到其中任一实例。

   * 如果要在达拉斯或华盛顿区域创建 SMS 代理程序，但没有 {{site.data.keyword.conversationshort}} 服务实例，那么可以使用**服务实例**菜单创建一个服务实例。
   * 或者，可以通过更改[**服务类型**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service)来连接到 {{site.data.keyword.conversationshort}} 对话的其他源或与 SOE 连接。
   * 如果您想要配置多个服务位置，请单击其他位置选项，并选择**启用位置**以配置到其他 {{site.data.keyword.conversationshort}} 实例的连接。有关更多信息，请参阅[添加多个 Watson 服务位置](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location)。

1. 勾选**通过自入站消息启动会话**框，以允许用户启动与 SMS 代理程序的 SMS 会话。

1. 勾选**会话超时通知**框，以便 SMS 代理程序向用户发送 SMS 消息，提醒用户代理程序在一段时间内未收到响应，现在即将超时。 

    - 请参阅[高级选项](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced)，以获取有关可用于 SMS 代理程序的**高级选项**，例如，为会话设置超时的定制时间。
    - 仅当您希望在会话超时时收到通知才勾选此框。

1. 也可以选择启用事件转发，以收集 {{site.data.keyword.cloudantfull}} 中语音代理程序所处理的呼叫的相关信息。有关更多信息，请参阅[为语音代理程序启用事件转发](/docs/services/voice-agent?topic=voice-agent-event_forwarding)。有关更多配置选项，请参阅[配置语音代理程序](/docs/services/voice-agent?topic=voice-agent-managing#configure_va)。

1.  单击**创建语音代理程序**以创建 SMS 代理程序和任何新服务。

1. 遵循[指示信息](/docs/services/voice-agent?topic=voice-agent-connect-sms)以连接到 SMS 提供者。

创建 SMS 代理程序后，通过向其电话号码发短信来进行测试。在_使用情况_仪表板上，可以查看有关交互的详细信息。请参阅[查看使用情况和日志](/docs/services/voice-agent?topic=voice-agent-logging)。

要在语音呼叫期间启用客户与语音代理程序之间的 SMS 消息传递，SMS 号码必须与语音号码匹配。
{: tip}

创建 SMS 代理程序或向语音代理程序添加 SMS 功能之前，您**必须**已设置适当的凭证，并生成 API 密钥以编程到您的 SMS 号码。有关更多信息，请参阅[生成 API 密钥并设置凭证](/docs/services/voice-agent?topic=voice-agent-connect-sms#sms_access)。

您还**必须**为 SMS 功能配置 SIP 中继。请查看提供者的指示信息，例如 Twilio。如果您没有 Twilio 电话号码，请参阅[创建 Twilio SIP 中继](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup)。

有了 Twilio 号码之后，您还需要对其进行配置以用于 SMS 功能。有关更多信息，请参阅[配置 Twilio 以使用 SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup)。

如果创建凭证时遇到困难，请联系服务实例管理员为您授予*管理者*或*写入者*访问权。
{: tip}

## SMS 代理程序的高级选项
{: #sms_advanced}

单击**电话号码**字段后面的**显示高级**。

1. 设置可选的**会话读取超时**值。这是 SMS Gateway 等待来自 Watson Assistant 的响应的时间（以秒为单位）。如果超过此时间，SMS Gateway 会重新尝试联系 Watson Assistant。如果仍无法联系服务，那么 SMS/MMS 消息失败。缺省设置为 30 秒。

1. 设置可选的**会话超时**。这是 SMS Gateway 未收到用户响应而导致会话超时前的时间（以秒为单位）。

1. 设置**会话失败回复消息**。这是无法联系 Watson Assistant 时发送的缺省响应消息。缺省情况下，消息设置为`对不起，我们无法响应您的消息`。

### 配置用于终止会话的 SMS 代理程序
{: #sms_terminate}

{{site.data.keyword.iva_full}} SMS 代理程序会根据会话超时的值终止会话，该值可配置且缺省设置为 30 秒。 

还可以向 {{site.data.keyword.conversationshort}} 服务添加节点，以响应用户的结束会话命令。 

1. 在 {{site.data.keyword.Bluemix_notm}}“仪表板”中，选择您的语音代理程序使用的 {{site.data.keyword.conversationshort}} 实例。

1. 通过仪表板创建**终止 SMS 意向**。或者，您可以修改已用于语音代理程序的现有意向，例如_结束呼叫_。

1. 通过仪表板添加**终止 SMS 节点**。

1. 在_如果助手识别：_部分中，添加先前创建的**终止 SMS 意向**属性。

1. 将响应添加到节点。复制并粘贴以下代码片段，以替换字段中的代码：

    ```json
        {
            "output": {
   "text": {
     "values": [
        "Thank you for using the service. Goodbye!"
                    ],
                    "selection_policy”: “sequential"
                },
                "smsAction": {
                    "command": "terminateSession"
                }
            }
        }
    ```
    {: codeblock}

创建语音代理程序后，根据其类型通过呼叫其电话号码或向其电话号码发短信来进行测试。在_使用情况_仪表板上，可以查看有关交互的详细信息。请参阅[查看使用情况和日志](/docs/services/voice-agent?topic=voice-agent-logging)。
