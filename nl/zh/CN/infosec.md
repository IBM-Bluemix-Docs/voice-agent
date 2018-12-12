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


# 信息安全和数据隐私
{: #infosec}

IBM 承诺为客户及合作伙伴提供创意数据隐私、安全性和监管解决方案。
{: shortdesc}

## 信息处理和配置选项
{: #configure_infosec}

{{site.data.keyword.iva_short}} 不会存储、收集或处理从客户接收到的数据。而是将数据路由到其他服务进行处理。在对话期间，用户可能会共享包含受保护的健康信息 (PHI)、个人可标识信息 (PII) 或 PCI 数据安全标准 (PCI DSS) 数据的信息。请参阅[体系结构](about.html#architecture){: new_window}以了解有关 {{site.data.keyword.iva_short}} 的对话流和体系结构的信息。

在配置语音代理程序实例以支持数据隐私和安全处理时，请考虑以下功能。

### 呼叫转移
{:  #calltransfer_infosec}

在将呼叫转移功能添加到语音代理程序时，您会在配置转移目标 SIP URI 时提供一个电话号码。用户不应为此转移目标提供个人电话号码。

请参阅[设置呼叫转移](call-transfer.html)以了解有关为呼叫转移配置 SIP 中继和 SIP URI 的信息。

### 事件转发
{: #event_forwarding}

您可以配置语音代理程序，以便将报告事件转发到 {{site.data.keyword.cloudantfull}} 数据库实例。这些报告事件中可以包含关于呼叫者的 PII、PHI 和 PCI DSS 数据，这些数据的以转录、对话轮次事件、呼叫详细记录事件的形式出现。呼叫数据和报告事件不会在 {{site.data.keyword.iva_short}} 中进行存储、处理和收集，用户应配置相应的外部 {{site.data.keyword.cloudant_short_notm}} 服务。**缺省情况下，事件转发处于禁用状态。**

请参阅[启用事件转发](event-forwarding.html)以配置语音代理程序用于转发报告事件。

请参阅[**{{site.data.keyword.cloudant_short_notm}}：安全性**](../Cloudant/offerings/security.html#security){: new_window}了解有关 {{site.data.keyword.cloudant_short_notm}} 的数据隐私和信息安全。

### 文本转语音高速缓存
{: #tts_caching}

为了与客户对话，{{site.data.keyword.conversationshort}} 会生成文本形式的响应，响应会被传递到 {{site.data.keyword.texttospeechshort}} 服务中，并在 {{site.data.keyword.iva_short}} 中朗读出来。{{site.data.keyword.conversationshort}} 创建的响应可能会包含敏感信息。要让 {{site.data.keyword.iva_short}} 不对从 {{site.data.keyword.texttospeechshort}} 服务接收到的包含个人数据的响应进行高速缓存，可以启用 `vgwActExcludeFromTTSCache` 操作命令以排除包含特定类型信息的发声，使其不被高速缓存。请参阅[使用 API 对语音代理程序编程](api.html#action-sequences)。

### 安全连接
{: #secure_trunking}

{{site.data.keyword.iva_short}} 基于 {{site.data.keyword.Bluemix_notm}}，并与用户配置的 SIP 中继集成。由于 SIP 中继在外部，并连接到 {{site.data.keyword.iva_short}}，因此可以在 SIP 中继与 {{site.data.keyword.iva_short}} 之间启用安全连接，方法是使用安全实时传输协议 (SRTP)，并使用安全 sip (sips) 进行加密，加密依赖于传输层安全性 (TLS)。请参阅[保护连接](secure-trunking.html)。

### 服务编排引擎 (SOE) 配置
{: #SOE_config}

您可以使用服务编排引擎 (SOE) 来处理在 {{site.data.keyword.iva_short}} 与 {{site.data.keyword.conversationshort}} 之间传递的信息，以定制与呼叫者的对话。为了维护安全连接，请确保使用安全 URL 来配置 SOE (`https`)，并进行用户认证。

请参阅[为语音代理程序配置 {{site.data.keyword.conversationshort}}](managing_SOE.html#conversation_va) 和[具有服务编排引擎的体系结构](about.html#arch-soe)。

## 与 {{site.data.keyword.iva_short}} 相关的服务
{: #related_services}

{{site.data.keyword.iva_short}} 编排不同的 {{site.data.keyword.Bluemix_notm}} 服务以根据感知服务来协调最终用户与云之间的通信。{{site.data.keyword.iva_short}} 自身不会以侵犯最终用户权利的方式来存储、收集或处理数据。但这些集成的服务可能会收集用户在对话期间共享的受保护的健康信息 (PHI)、个人可标识信息 (PII) 或 PCI 数据安全标准 (PCI DSS) 数据，具体取决于您配置相关服务的方式。要了解有关 {{site.data.keyword.iva_short}} 体系结构和对话流的信息，请参阅[体系结构](about.html#architecture){: new_window}。

请参阅下列资源以了解每个服务以及 {{site.data.keyword.Bluemix_notm}} 的注意事项。

  * [**{{site.data.keyword.Bluemix_short}}：安全合规性**](../security/compliance.html)
  * [**{{site.data.keyword.conversationfull}}：信息安全**](../conversation/information-security.html){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}：信息安全**](../text-to-speech/information-security.html){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}：信息安全**](../speech-to-text/information-security.html){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}：安全性**](../Cloudant/offerings/security.html#security){: new_window}
