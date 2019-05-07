---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-01"
subcollection: "voice-agent"

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
1. 单击包含要编辑的对话的技能。
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

## 设置状态
{: #setting-states}

为了指示在各轮对话间保持的状态的变化，语音代理程序会与配置的 {{site.data.keyword.conversationfull}} 服务交换状态变量。这些状态变量在 {{site.data.keyword.conversationshort}} 对话节点上以 JSON 格式的[上下文变量](/docs/services/assistant?topic=assistant-dialog-build#dialog-build)形式进行定义。

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
