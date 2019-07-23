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

# API를 사용하여 음성 에이전트 프로그래밍
{: #api}

{{site.data.keyword.conversationfull}} 서비스 내에서 조치 태그 및 상태 변수를 정의하여 음성 에이전트의 동작을 제어할 수 있습니다. 조치 태그는 음성 에이전트가 대화 세션 중에 수행하는 조치를 시작하고 상태 변수는 별도로 변경되지 않는 한 대화 전체에서 지속되는 음성 에이전트 특성을 정의합니다.
{: shortdesc}

{{site.data.keyword.iva_full}}은 IBM Voice Gateway를 기반으로 하므로 API가 동일한 방식으로 작동합니다. Voice Gateway 및 SMS Gateway에 익숙한 경우, {{site.data.keyword.conversationshort}} 대화에서 {{site.data.keyword.iva_short}}과 동일한 조치 및 상태 변수를 사용할 수 있습니다. [API의 조치 태그 및 상태 변수](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html) 및 [SMS Gateway의 API](https://www.ibm.com/support/knowledgecenter/SS4U29/sms_api.html)를 각각 참조하십시오.
{: tip}

## 대화 응답에서 JSON 편집
{: #json-editor}

조치 및 상태는 모두 JSON 형식으로 대화 노드 응답에서 정의됩니다. JSON 코드를 편집하려면 JSON 편집기를 여십시오.

1. {{site.data.keyword.Bluemix_short}} 대시보드에서 {{site.data.keyword.conversationshort}} 서비스 인스턴스를 선택하십시오.
1. {{site.data.keyword.conversationshort}} 도구를 실행하십시오.
1. 편집할 대화를 포함하는 스킬을 클릭하십시오.
1. **대화** 탭으로 이동하여 조치 또는 상태를 설정할 노드를 선택하십시오.
1. 응답에서 ![고급 응답](../conversation/images/kabob.png) 아이콘을 클릭하고 **JSON 편집기 열기**를 선택하십시오.

다음 섹션에서 설명된 대로 JSON 편집기 내에서 `output` 특성에 조치를 정의하고 `context` 특성에 상태를 정의할 수 있습니다.

## 조치 시작
{: #defining-actions}

호출 중에 음성 에이전트에서 조치를 시작하려면 {{site.data.keyword.conversationshort}} 대화 노드에서 JSON 형식으로 `output` 특성에 대한 조치 태그를 정의할 수 있습니다. `vgwAction` 태그에 단일 조치를 정의하거나 `vgwActionSequence` 태그에 조치 순서를 정의할 수 있습니다. 각 조치는 `command` 특성으로 구성되며 속성이 필요한 명령에 대한 속성을 정의하기 위한 선택적 `parameter` 특성이 다음에 옵니다.

### 단일 조치
{: #single-actions}

단일 조치를 수행하려면 필요한 매개변수 속성을 사용하여 `vgwAction` 태그에 조치를 정의하십시오. `output` 특성의 `text` 블록에서 선택으로 조치가 수행된 후 음성 에이전트가 재생하는 발화를 포함할 수 있습니다.

`vgwAction` 태그의 다음 단일 조치는 노드 응답이 트리거되었을 때 전화를 끊도록 음성 에이전트에 알립니다. `vgwActHangup` 명령에는 매개변수가 없으므로 아무 것도 정의되지 않았습니다.
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

다음 조치는 DTMF(Dual-Tone Multi-Frequency) 신호 입력을 수집하고 호출자에게 정의된 텍스트를 재생하도록 음성 에이전트에 알립니다.

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

### 조치 순서
{: #action-sequences}

단일 대화에서 하나 이상의 조치를 수행하려는 경우 `vgwActionSequence` 태그 내에 일련의 조치를 JSON 목록으로 정의할 수 있습니다. 정의한 순서대로 조치가 수행됩니다.

단일 조치와 다르게 `vgwActionSequence` 태그를 사용할 때 음성 에이전트가 발화를 재생하도록 하려면 `vgwActPlayText` 조치가 조치 목록에 포함되어야 합니다. `vgwAction` 태그와 대조적으로 `output.text` 필드의 발화는 자동으로 재생되지 않습니다.
{: tip}

다음의 보다 복잡한 예에서 `vgwActionSequence` 태그의 정의된 조치는 음성-문자 변환 처리를 사용 안함으로 설정하고 발화 재생 시 DTMF 입력을 수집하도록 음성 에이전트에 알립니다.

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

## 상태 설정
{: #setting-states}

대화 전환 사이에 유지되는 상태의 변경사항을 표시하기 위해 음성 에이전트가 {{site.data.keyword.conversationfull}} 서비스와 상태 변수를 교환합니다. 이러한 상태 변수는 {{site.data.keyword.conversationshort}} 대화 노드에서 JSON 형식의 [컨텍스트 변수](/docs/services/assistant?topic=assistant-dialog-build#dialog-build)로 정의됩니다.

예를 들어, {{site.data.keyword.conversationshort}} 서비스에 대한 연결이 실패하는 경우 호출자에게 스트리밍되는 메시지를 설정하기 위해 다음 상태 변수를 정의할 수 있습니다.

```json
{
  "context": {
    "vgwConversationFailedMessage": "Sorry, we're unable to connect you to our help line. Please try again later."
  }
}
```
{: codeblock}

음성 에이전트에서는 {{site.data.keyword.conversationshort}} 서비스가 Stateless이며 모든 상태가 {{site.data.keyword.conversationshort}} 서비스와 교환되는 사이에 음성 에이전트에서 유지보수되어야 한다고 간주합니다. 호출 내 대화 턴마다 상태가 {{site.data.keyword.conversationshort}} 서비스로 전달되고 REST 메시지의 `컨텍스트` 섹션에서 서비스로부터 다시 수신됩니다.
