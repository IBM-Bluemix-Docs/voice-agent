---

copyright:
  years: 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 信息安全和数据隐私
{: #infosec}

IBM 承诺为客户及合作伙伴提供创意数据隐私、安全性和监管解决方案。
{: shortdesc}

## 信息处理和配置选项
{: #configure_infosec}

要操作服务并优化用户体验，{{site.data.keyword.iva_short}} 将收集并存储少量个人信息 (PI)，并依照[数据处理附录 (DPA)](https://www.ibm.com/support/customer/csol/terms/){: new_window} 和 [DPA Exhibit](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=00C4CE004FA711E7AA10752A2F494A7C){: new_window} 来处理这些信息。{{site.data.keyword.iva_short}} 不会存储、收集或处理任何语音或 SMS 会话中包含的数据。而是将数据路由到其他服务进行处理。在对话期间，用户可能会共享包含受保护的健康信息 (PHI)、个人可标识信息 (PII) 或 PCI 数据安全标准 (PCI DSS) 数据的信息。请参阅[体系结构](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}以了解有关 {{site.data.keyword.iva_short}} 的对话流和体系结构的信息。

在配置语音代理程序实例以支持数据隐私和安全处理时，请考虑以下功能。

### 呼叫转移
{:  #calltransfer_infosec}

在将呼叫转移功能添加到语音代理程序时，您会在配置转移目标 SIP URI 时提供一个电话号码。用户不应为此转移目标提供个人电话号码。

请参阅[设置呼叫转移](/docs/services/voice-agent?topic=voice-agent-call-transfer)以了解有关为呼叫转移配置 SIP 中继和 SIP URI 的信息。

### 事件转发
{: #infosec_event_forwarding}

您可以配置语音代理程序，以便将报告事件转发到 {{site.data.keyword.cloudantfull}} 数据库实例。这些报告事件中可以包含关于呼叫者的 PII、PHI 和 PCI DSS 数据，这些数据的以转录、对话轮次事件、呼叫详细记录事件的形式出现。呼叫数据、SMS 数据和报告事件不会在 {{site.data.keyword.iva_short}} 中进行存储、处理或收集，用户应配置相应的外部 {{site.data.keyword.cloudant_short_notm}} 服务。**缺省情况下，事件转发处于禁用状态。**

请参阅[启用事件转发](/docs/services/voice-agent?topic=voice-agent-event_forwarding)以配置语音代理程序用于转发报告事件。

请参阅[**{{site.data.keyword.cloudant_short_notm}}：安全性**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}了解有关 {{site.data.keyword.cloudant_short_notm}} 的数据隐私和信息安全。

### 文本转语音高速缓存
{: #tts_caching}

为了与客户对话，{{site.data.keyword.conversationshort}} 会生成文本形式的响应，响应会被传递到 {{site.data.keyword.texttospeechshort}} 服务中，并在 {{site.data.keyword.iva_short}} 中朗读出来。{{site.data.keyword.conversationshort}} 创建的响应可能会包含敏感信息。要让 {{site.data.keyword.iva_short}} 不对从 {{site.data.keyword.texttospeechshort}} 服务接收到的包含个人数据的响应进行高速缓存，可以启用 `vgwActExcludeFromTTSCache` 操作命令以排除包含特定类型信息的发声，使其不被高速缓存。请参阅[使用 API 对语音代理程序编程](/docs/services/voice-agent?topic=voice-agent-api#action-sequences)。

语音代理程序实例删除后，TTS 高速缓存将在 24 小时内清除。这也称为 `TTS 高速缓存超时值`。

### 安全连接
{: #secure_trunking}

{{site.data.keyword.iva_short}} 基于 {{site.data.keyword.Bluemix_notm}}，并与用户配置的 SIP 中继集成。由于 SIP 中继在外部，并连接到 {{site.data.keyword.iva_short}}，因此可以在 SIP 中继与 {{site.data.keyword.iva_short}} 之间启用安全连接，方法是使用安全实时传输协议 (SRTP)，并使用安全 sip (sips) 进行加密，加密依赖于传输层安全性 (TLS)。请参阅[保护连接](/docs/services/voice-agent?topic=voice-agent-securing)。

缺省情况下，SMS 数据使用 TLS 加密。请参阅 [Voice Gateway：数据处理](https://www.ibm.com/support/knowledgecenter/en/SS4U29/gdpr_considerations.html#GDPR_dataProcessing){: new_window}，以获取更多信息。

### 服务编排引擎 (SOE) 配置
{: #SOE_config}

您可以使用服务编排引擎 (SOE) 来处理在 {{site.data.keyword.iva_short}} 与 {{site.data.keyword.conversationshort}} 之间传递的信息，以定制与呼叫者的对话。为了维护安全连接，请确保使用安全 URL 来配置 SOE (`https`)，并进行用户认证。

请参阅[为语音代理程序配置 {{site.data.keyword.conversationshort}}](/docs/services/voice-agent?topic=voice-agent-conversation_va#conversation_va) 和
[具有服务编排引擎的体系结构](/docs/services/voice-agent?topic=voice-agent-about#arch-soe)。

## SMS/MMS 支持
{: #SMS_MMS}

### 数据处理
{: #data_handling}

{{site.data.keyword.iva_short}} 不会存储、收集或处理 SMS 数据。MMS 图像会在服务外部存储，并由服务提供者处理。客户必须参考其 SMS 提供者的安全/隐私协议。{{site.data.keyword.iva_short}} 仅处理 SMS 消息中嵌入的图像的文本链接。

服务编排引擎或 {{site.data.keyword.conversationshort}} 向用户发送 MMS 消息（包含或不包含 SMS 短信）时，一个或多个可公开访问的媒体 URL 会发送到 Twilio。Twilio 不支持非公共 URL。用户应避免通过 MMS 发送敏感或个人信息。

{{site.data.keyword.iva_short}} 屏蔽消息日志中的呼叫者标识，以避免收集此类个人身份信息。

### 认证
{: #authentication}

通过使用 [IAM 认证](/docs/services/voice-agent?topic=voice-agent-iam#sms_access){: new_window}，服务提供者可以保护入站 SMS 消息。

## 与 {{site.data.keyword.iva_short}} 相关的服务
{: #related_services}

{{site.data.keyword.iva_short}} 编排不同的 {{site.data.keyword.Bluemix_notm}} 服务以根据感知服务来协调最终用户与云之间的通信。{{site.data.keyword.iva_short}} 自身不会以侵犯最终用户权利的方式来存储、收集或处理数据。但这些集成的服务可能会收集用户在对话期间共享的受保护的健康信息 (PHI)、个人可标识信息 (PII) 或 PCI 数据安全标准 (PCI DSS) 数据，具体取决于您配置相关服务的方式。要了解有关 {{site.data.keyword.iva_short}} 体系结构和对话流的信息，请参阅[体系结构](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}。

请参阅下列资源以了解每个服务以及 {{site.data.keyword.Bluemix_notm}} 的注意事项。

  * [**{{site.data.keyword.Bluemix_short}}：安全合规性**](/docs/overview?topic=overview-security#security)
  * [**{{site.data.keyword.conversationfull}}：信息安全**](/docs/services/assistant?topic=assistant-information-security#information-security){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}：信息安全**](/docs/services/text-to-speech?topic=text-to-speech-information-security){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}：信息安全**](/docs/services/speech-to-text?topic=speech-to-text-information-security){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}：安全性**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}
