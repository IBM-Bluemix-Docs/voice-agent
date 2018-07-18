---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 使用 API 对语音代理程序编程
{: #api}

可以通过在 {{site.data.keyword.conversationfull}} 服务中定义操作标记和状态变量来控制语音代理程序的行为。操作标记用于启动语音代理程序在对话会话期间执行的操作。状态变量用于定义语音代理程序在整个对话期间持续保持的特征（除非另有更改）。
{: shortdesc}

{{site.data.keyword.iva_full}} 基于 IBM Voice Gateway，因此 API 的工作方式与之相同。如果您熟悉 Voice Gateway，那么可以在 {{site.data.keyword.conversationshort}} 对话中使用与 {{site.data.keyword.iva_short}} 相同的操作和状态变量。请参阅 [Voice Gateway API 中的操作标记和状态变量](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html)。
{: tip}

## 在对话响应中编辑 JSON
{: #json-editor}

操作和状态在对话节点响应中以 JSON 格式进行定义。要编辑 JSON 代码，请打开 JSON 编辑器。

1. 在 {{site.data.keyword.Bluemix_short}}“仪表板”中，选择 {{site.data.keyword.conversationshort}} 服务实例。
1. 启动 {{site.data.keyword.conversationshort}} 工具。
1. 单击包含要编辑的对话的工作空间。
1. 转至**对话**选项卡，然后选择要在其中设置操作或状态的节点。
1. 在响应中，单击 ![高级响应](../conversation/images/kabob.png) 图标，然后选择**打开 JSON 编辑器**。

在 JSON 编辑器中，可以在 `output` 属性上定义操作，在 `context` 属性上定义状态，如以下部分中所述。

## 启动操作
{: #defining-actions}

要在呼叫期间在语音代理程序中启动操作，可以使用 `output` 属性以 JSON 格式在 {{site.data.keyword.conversationshort}} 对话节点上定义操作标记。您可以在 `vgwAction` 标记上定义单个操作，或者在 `vgwActionSequence` 标记上定义操作序列。每个操作都包含一个 `command` 属性，后跟一个可选的 `parameter` 属性，用于定义命令所需的参数属性。

### 单个操作
{: #single-actions}

要执行单个操作，请使用任何必需的参数属性在 `vgwAction` 标记中定义该操作。在 `output` 属性的 `text` 代码块中，可以加入语音代理程序在执行操作后要播放的话语（此为可选步骤）。

`vgwAction` 标记中的以下单个操作会指示语音代理程序在节点响应被触发时挂断呼叫。`vgwActHangup` 命令没有参数，因此未定义任何参数。
```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActHangup"
    }
  }
}
```
{: codeblock}

以下操作会指示语音代理程序收集双音多频信号 (DTMF) 输入并向呼叫者播放定义的文本。

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActCollectDtmf",
      "parameters": {
        "dtmfTermKey": "#"
      }
    },
    "text": {
      "values": [
        "Enter your phone number."
      ]
    }
  }
}
```
{: codeblock}

### 操作序列
{: #action-sequences}

要对单轮对话执行一个或多个操作，可以在 `vgwActionSequence` 标记中以 JSON 列表形式定义操作序列。操作会按照定义的顺序执行。

与单个操作不同，在使用 `vgwActionSequence` 标记时，操作列表必须包含 `vgwActPlayText` 操作，语音代理程序才能播放话语。与 `vgwAction` 标记相反，`output.text` 字段中的话语不会自动播放。
{: tip}

在以下较为复杂的示例中，`vgwActionSequence` 标记中定义的操作会指示语音代理程序在播放话语期间，禁用语音转文字处理并收集 DTMF 输入。

```json
{
  "output": {
    "vgwActionSequence": [
      {
        "command": "vgwActPauseSTT"
      },
      {
        "command": "vgwActCollectDtmf",
        "parameters": {
          "dtmfTermKey": "#"
        }
      },
      {
        "command": "vgwActPlayText",
        "parameters": {
          "text": [
            "Enter your social security number."
          ]
        }
      }
    ]
  }
}

```
{: codeblock}


### 操作命令和属性
{: #actions-and-attributes}

下表列出了可以在 {{site.data.keyword.conversationshort}} 对话中指定的操作以及可以为每个操作定义的任何属性。

|操作命令|描述|属性|
| ----- | ----- | ----- |
|`vgwActPlayText`|播放由 {{site.data.keyword.texttospeechshort}} 服务转换为语音的话语。| <ul><li>`text`：要播放的话语的列表。可选。<p>例如：
<br/><code>"text": [<br/>&nbsp;&nbsp;&nbsp;"Hello. How can I help you today?"<br/>&nbsp;&nbsp;&nbsp;]</code><p> 缺省情况下，该操作会播放在 `output.text` 字段中配置的话语列表。</li><li>`errAudioURL`：语音代理程序无法联系 {{site.data.keyword.texttospeechshort}} 服务来完成操作时播放的音频文件的 URL。该音频文件必须为 WAV 格式。</li></ul>|
|`vgwActPlayUrl`|在回放所包含的文本之后立即播放音频文件，例如播放等待音乐 (MOH) 或常用的一次性话语。如果未包含文本，那么将立即播放音频。音频文件必须是单声道 (mono)、PCM 编码，而且采样率为 8,000 Hz 且每个样本为 16 位。| <ul><li>`url`：要播放的 URL。必需。</li><li> `playURLInLoop`：（可选）设置为 `Yes` 或 `No`，以指示是否循环播放该 URL。缺省值为 `No`。</li></ul> |
|`vgwActHangup`|挂断呼叫。|无属性。|
|`vgwActSetSTTConfig`|应用一组参数，供语音代理程序传递到 Watson {{site.data.keyword.speechtotextshort}} 服务。{{site.data.keyword.conversationshort}} 服务会根据呼叫来动态定义参数。|参数属性将作为 JSON 属性以透明方式传递到 {{site.data.keyword.speechtotextshort}} 服务。|
|`vgwActSetTTSConfig`|应用一组参数，供语音代理程序传递到 Watson {{site.data.keyword.texttospeechshort}} 服务。{{site.data.keyword.conversationshort}} 服务会根据呼叫来动态定义参数。|参数属性将作为 JSON 属性以透明方式传递到 {{site.data.keyword.texttospeechshort}} 服务。|
|`vgwActSetConversationConfig` |应用一组参数，供语音代理程序用于定义 {{site.data.keyword.conversationshort}} 工作空间。{{site.data.keyword.conversationshort}} 服务会根据呼叫来动态定义参数。| <ul><li>`url`：{{site.data.keyword.conversationshort}} 服务 API 的 `url` 凭证。</li><li>`workspaceID`：{{site.data.keyword.conversationshort}} 工作空间标识</li><li>`username`：{{site.data.keyword.conversationshort}} 服务的 `username` 凭证。</li><li>`password`：{{site.data.keyword.conversationshort}} 服务的 `password` 凭证。</li></ul> |
|`vgwActCollectDtmf`|指示语音代理程序收集双音多频信号 (DTMF) 输入。|必须定义以下其中一个属性。<ul><li> `dtmfTermKey`：DTMF 终止键，用于指示 DTMF 输入结束。例如，“`#`”。</li><li> `dtmfCount`：要收集的 DTMF 数字数。</li></ul> 满足上述任一条件时，语音代理程序会停止收集 DTMF 输入。|
|`vgwActPauseDTMF`|禁用 DTMF 输入。在 `vgwActUnPauseDTMF` 操作重新启用 DTMF 输入之前，将忽略所有 DTMF 输入。|无属性。|
|`vgwActUnPauseDTMF`|启用由 `vgwActPauseDTMF` 操作禁用的 DTMF 输入。|无属性。|
|`vgwActExcludeFromTTSCache`|指示语音代理程序不对来自 {{site.data.keyword.texttospeechshort}} 服务的响应进行高速缓存。例如，应排除包含敏感 PHI、PII 和 PCI DSS 数据或动态信息（例如，客户姓名或生日）的响应。<br/>必须在 {{site.data.keyword.conversationshort}} 对话节点上为您不想高速缓存的每个话语设置此操作标记。|无属性。|
|`vgwActPauseSTT`|在 `vgwActUnPauseSTT` 操作重新启用语音转文字处理之前，暂停该处理。如果录音已启用，但语音转文字处理已暂停，那么不会捕获来自呼叫者的音频。|无属性。|
|`vgwActUnPauseSTT`|恢复先前由 `vgwActPauseSTT` 操作暂停的语音转文字处理。|无属性。|
|`vgwActEnableSpeechBargeIn`|启用语音打断，以允许呼叫者通过讲话中断语音代理程序的回放。|无属性。|
|`vgwActDisableSpeechBargeIn`|禁用语音打断，以禁止呼叫者通过讲话中断语音代理程序的回放。|无属性。|
|`vgwActEnableDTMFBargeIn`|启用 DTMF 打断，以允许呼叫者通过按下某个键中断语音代理程序的回放。|无属性。|
|`vgwActDisableDTMFBargeIn`|禁用 DTMF 打断，以禁止呼叫者通过按下某个键中断语音代理程序的回放。|无属性。|
|`vgwActForceNoInputTurn`|强制进行新一轮对话，而不等待来自呼叫者的输入。|无属性。|
{: caption="表 1. 可从 {{site.data.keyword.conversationshort}} 服务启动的操作" caption-side="top"}

## 设置状态
{: #setting-states}

为了指示在各轮对话间保持的状态的变化，语音代理程序会与配置的 {{site.data.keyword.conversationfull}} 服务交换状态变量。这些状态变量在 {{site.data.keyword.conversationshort}} 对话节点上以 JSON 格式的[上下文变量](https://console.bluemix.net/docs/services/conversation/dialog-build.html#context)形式进行定义。

例如，可以定义以下状态变量来设置与 {{site.data.keyword.conversationshort}} 服务连接失败时，向呼叫者传送的消息。

```json
{
  "context": {
    "vgwConversationFailedMessage": "Sorry, we're unable to connect you to our help line. Please try again later."
  }
}
```
{: codeblock}

语音代理程序假定 {{site.data.keyword.conversationshort}} 服务是无状态的，并且在与 {{site.data.keyword.conversationshort}} 服务交换状态期间，所有状态都在语音代理程序上进行维护。对于一次呼叫期间的每轮对话，都会通过 REST 消息的 `context` 部分将状态传递到 {{site.data.keyword.conversationshort}} 服务，并从该服务接收返回的状态。

### 在 {{site.data.keyword.conversationshort}} 对话中设置的状态变量
{: #state-variables-conv}

可以在 {{site.data.keyword.conversationshort}} 对话中设置以下状态变量来修改语音代理程序的行为。

|状态变量名称|期望值|描述|
| -------------- | ------ | ----------- |
|`vgwByeCustomHeader`|用户定义|在传出 SIP BYE 消息中定义定制头。定制头值由 `vgwByeCustomHeaderVal` 状态变量定义。|
|`vgwByeCustomHeaderVal`|用户定义|在传出 SIP BYE 消息中定义定制头的值。定制头由 `vgwByeCustomHeader` 状态变量定义。|
|`vgwPostResponseTimeoutCount`|时间（毫秒）|将响应回放给呼叫者后等待新话语的时间量。如果超过此值，{{site.data.keyword.conversationshort}} 会收到包含文字“vgwPostResponseTimeout”的文本更新内容以指示发生了超时。|
|`vgwConversationFailedMessage`|文本字符串|在 {{site.data.keyword.conversationshort}} 服务失败时传送给呼叫者的消息。配置 {{site.data.keyword.conversationshort}} 对话，以在第一个轮次中设置此变量。|
|`vgwSessionInactivityTimeout`|时间（分钟）<br/><br/>缺省值：`2`|不活动状态的超时间隔。超时间隔值（以分钟为单位）用于指定语音代理程序允许会话处于不活动状态的时长。当超时到期时，语音代理程序会结束会话。|
|`vgwErrAudioURL`|用户定义|语音代理程序尝试回放响应但无法联系 {{site.data.keyword.texttospeechshort}} 服务时播放的音频文件的 URL。该音频文件必须为 WAV 格式。|
{: caption="表 2. {{site.data.keyword.conversationshort}} 服务设置的变量" caption-side="top"}

### 语音代理程序设置的状态变量
{: #state-variables-iva}

|状态变量名称|期望值|描述|
| -------------- | ----- | ----------- |
|`vgwSessionID`|用户定义<br/><br/> 缺省值：`Call-ID`|从 SIP INVITE 请求中提取的定制会话标识头。该值表示与会话相关的所有语音代理程序审计日志中使用的全局会话标识。|
|`vgwSIPCallID`|SIP `Call-ID`|与呼叫相关联的 SIP 呼叫标识。|
|`vgwSIPRequestURI`|SIP `Request-URI`|启动呼叫的 SIP 请求 URI。|
|`vgwSIPToURI` |SIP `To` URI|与呼叫相关联的 SIP `To` URI。|
|`vgwSIPFromURI`|SIP `From` URI|与呼叫相关联的 SIP `From` URI。|
|`vgwBargeInOccurred`|`Yes`/`No`|指示是否发生了打断。|
|`vgwHangUp`|`Yes`/`No`|指示对话是否已结束。|
|`vgwHangupReason`|字符串|如果呼叫被呼叫者挂断或由于错误被挂断，那么系统会将此变量发送给 {{site.data.keyword.conversationshort}} 服务，以指示呼叫连接断开的原因。在发送给 {{site.data.keyword.conversationshort}} 服务的消息请求文本中，还会包含“vgwHangUp”。|
|`vgwConversationResponseTimeout`|时间（秒）<br/><br/>缺省值：`5`|语音代理程序等待 {{site.data.keyword.conversationshort}} 服务响应的时间（以秒为单位）。如果超过此时间，语音代理程序会重新尝试联系 {{site.data.keyword.conversationshort}} 服务。如果仍无法联系服务，那么呼叫失败。|
|`vgwSTTResponse`|JSON 对象|来自 {{site.data.keyword.speechtotextshort}} 服务的最终响应（JSON 格式），内容包含首选假设及任何备选假设的脚本和置信度分数。<p>例如，以下格式与从 {{site.data.keyword.speechtotextshort}} 服务收到的格式完全一致：</p><p><code>{<br/>&nbsp;&nbsp;"result_index": 0,<br/>&nbsp;&nbsp;"warnings": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;"Unknown arguments: continuous."<br/>&nbsp;&nbsp;],<br/>&nbsp;&nbsp;"results": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"final": true,<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"alternatives": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello world",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.758<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello wooled",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.358<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;]<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}.</code></p> |
|`vgwIsDTMF`|`Yes`/`No`|指示 {{site.data.keyword.conversationshort}} 服务的输入是否为双音多频信号 (DTMF)。|
{: caption="表 3. 语音代理程序设置的变量" caption-side="top"}
