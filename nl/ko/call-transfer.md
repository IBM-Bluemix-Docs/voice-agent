---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 호출 전송 설정
{: #call-transfer}

호출자가 대화 중에 실시간 상담원과 통화하도록 요청하는 경우 음성 에이전트가 자동으로 호출을 전송하도록 호출 전송을 설정할 수 있습니다.
{: shortdesc}

## 호출 전송 정보
{: #about-ct}

호출 전송을 사용으로 설정하면 호출자가 대화 중에 실시간 상담원과 통화하도록 요청하는 경우 음성 에이전트가 호출을 경로 재지정합니다. {{site.data.keyword.iva_short}}에서는 SIP REFER를 사용하여 SIP 트렁크 제공자에게 다시 호출하여 처리하도록 하고 전송된 전화 호출은 다시 표시하지 않습니다.

SIP 제공자 구성에서 종료 URI 또는 전화 URI를 설정하여 호출 전송을 사용으로 설정할 수 있습니다. 그런 다음 {{site.data.keyword.conversationshort}} 인스턴스의 대화 상자 노드에서 API 조치에 대한 전송 대상을 정의합니다. 전송 대상은 종료 URI와 전화번호가 있는 SIP URI 또는 전화번호가 있는 전화 URI입니다. 음성 에이전트의 사용자 정의 및 지원되는 조치에 대한 자세한 정보는 [API를 사용하여 음성 에이전트 프로그래밍](/docs/services/voice-agent?topic=voice-agent-api)을 참조하십시오.

## 1단계: 종료 URI 설정
{: #termination-setup}

SIP URI 구성에서 종료 URI 대신 전화 URI를 사용 중인 경우, `trasnferTarget`에 대해 `tel:+18889990000`과 같은 전화 URI를 사용할 수 있습니다. SIP URI를 사용 중인 경우 `transferTarget`에 대한 종료 URI가 필요합니다.
{: tip}

### NetFoundry에서 종료 URI 설정
{: #termination-netfoundry}

[NetFoundry 계정![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson.netfoundry.io/watson-login){: new_window}의 전송할 대상 전화번호를 기록하십시오. 나중에 {{site.data.keyword.conversationshort}} 대화 상자에서 이 전화번호 및 종료 URI를 전송 대상으로 지정할 수 있습니다. 개인 전화번호를 사용하지 마십시오.

전송 대상에서 사용할 다음 NetFoundry 종료 URI를 복사하십시오.

```
dal.watson-va.netfoundry.net
```
{: codeblock}

[호출 전송을 위한 {{site.data.keyword.conversationshort}} 구성](#conversation-setup) 시 NetFoundry 계정에서 종료 URI를 수동으로 구성하지 않아도 됩니다.

### Twilio에서 종료 URI 설정
{: #termination-Twilio}

1. Twilio 계정에서 _Elastic SIP Trunking_ 대시보드로 이동하여 **트렁크**를 선택하십시오.

1. 기존 트렁크를 선택하거나 **+** 아이콘을 클릭하여 새 트렁크를 작성한 후 호출 전송을 추가하려는 트렁크를 선택하십시오.

  * 새 트렁크를 작성할 때 **시작** 대시보드에서 _SIP 트렁크 URI_를 구성해야 합니다.  자세한 정보는 [SIP 트렁크 연결](/docs/services/voice-agent?topic=voice-agent-connect)을 참조하십시오.

1. 탐색줄에서 **종료**를 선택하고 종료 URI의 이름을 입력하십시오.

  * 종료 URI 이름은 고유해야 합니다. Twilio는 선택한 이름의 가용성을 자동으로 확인합니다. Twilio 서비스에 대한 세부사항은 [SIP 트렁크 종료 설정 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window}을 참조하십시오.

1. 탐색줄에서 **일반**을 선택하여 _일반 설정_을 표시하십시오. **호출 전송(SIP REFER)** 표제에서 설정을 **사용**으로 전환한 후 **트렁크를 통해 PSTN으로 호출 전송 가능**을 선택하십시오.

1. 종료 URI 구성 및 호출 전송 사용 설정을 완료하려면 **저장**을 클릭하십시오.

1. 전송할 대상 전화번호와 종료 URI를 기록하십시오. 전화번호가 개인 전화번호가 아닌지 확인하십시오. 전화번호 및 종료 URI를 사용하여 {{site.data.keyword.conversationshort}} 대화 상자에서 전송 대상을 지정할 수 있습니다.


## 2단계: 호출 전송을 위한 {{site.data.keyword.conversationshort}} 구성
{: #conversation-setup}

{{site.data.keyword.conversationshort}} 서비스에서의 작업에 대해 자세히 알아보려면 [{{site.data.keyword.conversationshort}} 정보](/docs/services/assistant?topic=assistant-index#indext)를 참조하십시오.

1. {{site.data.keyword.Bluemix_notm}} 대시보드에서 음성 에이전트가 사용하는 {{site.data.keyword.conversationshort}} 인스턴스를 선택하십시오.

1. _시작하기_ 대시보드에서 **도구 실행** 단추를 클릭하십시오.

1. 편집할 스킬에서 **시작하기**를 클릭하십시오.

1. **인텐트 추가**를 클릭하고 인텐트의 이름(예: _전송_)을 입력하십시오.

  자세한 정보를 입력하거나 나중에 돌아와서 인텐트를 편집하고 정제할 수 있습니다.

1. 호출 전송 인텐트를 작성한 후에 _대화_ 탭을 선택하십시오.

1. **노드 추가**를 클릭하고 노드의 이름(예: _호출 전송_)을 입력하십시오.

1. 작성한 인텐트를 찾으려면 _조건 검사:_ 섹션에 **호출 전송 인텐트**를 입력하십시오.

1. _응답 조치:_ 섹션에서 **&vellip;** 아이콘을 클릭하고 **JSON 편집기 열기**를 선택하십시오. 다음의 코드 스니펫을 복사하고 붙여넣어서 필드의 코드를 대체하십시오.

  * 전화 URI를 사용하는 경우 `transferTarget`에서 SIP URI를 사용자의 전화 URI로 대체하십시오. 예를 들면, `"transferTarget":"tel:+18889990000"`.

  * **참고**: `transferTarget` URI가 `+`로 시작하는지 확인하십시오.

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

1. `transferTarget` 종료 URI 또는 전화 URI에 있는 전화번호가 SIP 트렁크에 있는 전화번호와 올바로 일치되는지 확인하십시오.

**중요**: 전송 대상의 SIP URI에는 전화번호와 사용자가 작성한 종료 URI가 포함됩니다. 전송 대상에 개인 전화번호를 사용하지 마십시오. 예를 들어 전화번호가 `18889990000`이고 종료 URI가 `mysiptrunk.pstn.twilio.com`인 경우 전체 SIP URI는 `sip:+18889990000\\@mysiptrunk.pstn.twilio.com`입니다. Netfoundry를 사용하고 전화번호가 `18889990000`인 경우 전체 SIP URI는 `sip:+18889990000\\@dal.watson-va.netfoundry.net`입니다.

**참고**: `transferTarget` URI가 `+`로 시작하며 256자까지 포함할 수 있는지 확인하십시오. 

## 다음 단계
{: #Next}

연관된 전화번호로 전화하여 음성 에이전트를 테스트하고 인텐트에서 식별한 주요 용어를 사용하십시오. 음성 에이전트가 사용자의 경로를 재지정하면 작동하는 것입니다.

이제 **전송** 인텐트 및 대화를 정제하고 선택한 주요 용어와 구문에 응답하도록 구성할 수 있습니다.
