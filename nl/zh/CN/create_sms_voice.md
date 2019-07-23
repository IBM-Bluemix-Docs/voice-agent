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

# 创建支持 SMS 的语音代理程序
{: #sms_voice_config_instance}

创建 {{site.data.keyword.iva_full}} 服务后，可以从_管理_仪表板创建具有 SMS 功能的单个语音代理程序或仅具有 SMS 功能的语音代理程序。您可以配置 {{site.data.keyword.iva_full}}，以接收入站语音呼叫并使用 SMS 出站消息进行响应，具体取决于用户收到的语音命令。要进行配置，请在 {{site.data.keyword.conversationshort}} 服务中添加节点和意向。
{: shortdesc}


1. 转至_管理_仪表板上的_语音代理程序_选项卡，然后单击**创建语音代理程序**。

1. 针对**代理程序类型**，选择_语音 + SMS_。

1. 遵循[创建语音代理程序](/docs/services/voice-agent?topic=voice-agent-config_instance)中的指示信息。

1. 勾选**通过自入站消息启动会话**框，以允许用户启动与 SMS 代理程序的 SMS 会话。

1. 勾选**会话超时通知**，以便 SMS 代理程序向用户发送 SMS 消息，提醒用户代理程序在一段时间内未收到响应，现在即将超时。 

   - 请参阅[高级选项](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced)，以获取有关可用于 SMS 代理程序的**高级选项**，例如，为会话设置超时的定制时间。

1. 遵循[创建 SMS 代理程序](/docs/services/voice-agent?topic=voice-agent-sms_config_instance)中的指示信息，以创建 SMS 代理程序。

1. _**注：**_对于同时具有语音和 SMS 集成的代理程序，例如接收语音输入并发回 SMS 出站消息进行回复，您**必须**使用 **SMS** 代理程序的其中一个**语音**号码。

### 配置 Watson Assistant 以进行语音和 SMS 集成
{: #sms_outbound}

1. 在 {{site.data.keyword.Bluemix_notm}}“仪表板”中，选择您的语音代理程序使用的 {{site.data.keyword.conversationshort}} 实例。

1. 通过仪表板创建**出站 SMS 意向**。

1. 通过仪表板添加**出站 SMS 节点**。

1. 在_如果助手识别：_部分中，选择先前创建的**出站 SMS 意向**属性。

1. 将响应添加到节点。复制并粘贴以下代码片段，以替换字段中的代码：

    ```json
        {
            "output": {
   "text": {
     "values": [
        "Okay. I will send you a text message now."
                ],
     "selection_policy": "sequential"
   },
                "vgwActionSequence": [
                {
                    "command": "vgwActSendSMS",
                    "parameters": {
                    "message": "This is a test message from Watson Assistant"
                    }
                },
                {
                    "command": "vgwActPlayText"
                }
                ]
            }
        }
    ```
    {: codeblock}


1. 呼叫您的代理程序并触发节点，以在发出呼叫的电话上接收短信。 

要了解有关 {{site.data.keyword.conversationshort}} 服务的工作原理的更多信息，请参阅[关于 {{site.data.keyword.conversationshort}}](/docs/services/assistant?topic=assistant-index#indext)。
