---

copyright:
  years: 2019
lastupdated: "2019-06-17"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 定价常见问题
{: #faq-pricing}

## 使用 {{site.data.keyword.iva_short}} 标准服务的价格是多少？
{: #faq-pricing-zero}
{: faq}

 有关更多信息，请参阅[定价页面](https://cloud.ibm.com/catalog/services/voice-agent-with-watson){: external}。

## “按分钟定价”是什么意思？
{: #faq-pricing-one}
{: faq}

价格基于您发送到服务的音频量（分钟数）。价格不取决于服务处理音频所花费的时间长度。


## 每次呼叫 API 时，您是否都计算最接近的分钟数？
{: #faq-pricing-two}
{: faq}

“{{site.data.keyword.IBM_notm}} 不是将服务收到的每个 API 呼叫的音频长度计算到最接近的分钟数，而是 {{site.data.keyword.IBM_notm}} 会汇总每月使用情况，然后在每月月底计算最接近的分钟数。每次呼叫的持续时间都会四舍五入到下一分钟。例如，如果第一次呼叫的长度为 3.1 秒，而第二次呼叫的长度为 25.9 秒，那么 {{site.data.keyword.IBM_notm}} 会将第一次呼叫计算为 4 秒，而第二次呼叫计算为 26 秒。然后音频的总持续时间计算为 1 分钟。” 


## 如何计算并发连接以及应用的位置？
{: #faq-pricing-three}
{: faq}

并发连接仅适用于语音呼叫（而非 SMS）。并发连接计算为同时与服务实例中定义的任何电话号码的连接数。按实际每日最大并发连接数计费，按月收费。

## 最大并发连接的定义是什么以及如何进行更改？

{: #faq-pricing-four}
{: faq}

最大并发连接数是任何时候允许的最大连接数，也是计费的最大连接数。最大并发连接数可以在[仪表板](https://cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-edit_concurrency)中进行定义和更改。标准套餐中最大并发容量是 50 个连接，如果您需要更多，可以开具支持凭单。

## 入站和出站 SMS/MMS 消息如何计费？

{: #faq-pricing-five}
{: faq}

入站消息不计费，直到响应发送到用户为止。出站消息通过 Voice Gateway 或作为入站消息的响应发送给用户时会创建会话。对响应的出站和入站消息进行计费（如果适用）。
出站和入站消息都计费，直到会话超时为止。会话超时后，会话环境也会相应被废弃。缺省会话超时为 3600 秒，用户可以在仪表板上设置会话持续时间超时。
