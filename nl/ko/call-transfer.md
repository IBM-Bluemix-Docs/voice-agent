---

copyright:
  years: 2018
lastupdated: "2018-06-14"

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

호출 전송을 사용으로 설정하면 호출자가 대화 중에 실시간 상담원과 통화하도록 요청하는 경우 음성 에이전트가 호출을 경로 재지정합니다. SIP 제공자 구성에서 종료 URI를 설정하여 호출 전송을 사용으로 설정할 수 있습니다. 그리고 {{site.data.keyword.conversationshort}} 인스턴스의 대화 노드에서 API 조치의 전송 대상을 정의하십시오. 전송 대상은 종료 URI 및 전화번호가 포함된 SIP URI입니다. 음성 에이전트의 사용자 정의 및 지원되는 조치에 대한 자세한 정보는 [API를 사용하여 음성 에이전트 프로그래밍](api.html)을 참조하십시오. 

## 1단계: 종료 URI 설정
{: #termination-setup}

### NetFoundry에서 종료 URI 설정
{: #termination-netfoundry}

[NetFoundry 계정![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson.netfoundry.io/watson-login){: new_window}의 전송할 대상 전화번호를 기록하십시오. 나중에 {{site.data.keyword.conversationshort}} 대화 상자에서 이 전화번호 및 종료 URI를 전송 대상으로 지정할 수 있습니다. 전송 대상에서 사용할 다음 NetFoundry 종료 URI를 복사할 수 있습니다.

```
dal.watson-va.netfoundry.net
```
{: codeblock}

[호출 전송을 위한 {{site.data.keyword.conversationshort}} 구성](#conversation-setup) 시 NetFoundry 계정에서 종료 URI를 수동으로 구성하지 않아도 됩니다.

### Twilio에서 종료 URI 설정 
{: #termination-Twilio}

1. Twilio 계정에서 _Elastic SIP Trunking_ 대시보드로 이동하여 **트렁크**를 선택하십시오.

1. 기존 트렁크를 선택하거나 **+** 아이콘을 클릭하여 새 트렁크를 작성한 후 호출 전송을 추가하려는 트렁크를 선택하십시오.

  * 새 트렁크를 작성할 때 **시작** 대시보드에서 _SIP 트렁크 URI_를 구성해야 합니다. 자세한 정보는 [SIP 트렁크 연결](connect-SIP.html)을 참조하십시오. 

1. 탐색줄에서 **종료**를 선택하고 종료 URI의 이름을 입력하십시오.

  * 종료 URI 이름은 고유해야 합니다. Twilio는 선택한 이름의 가용성을 자동으로 확인합니다. Twilio 서비스에 대한 세부사항은 [SIP 트렁크 종료 설정 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window}을 참조하십시오.

1. _인증_ 섹션에서 **+** 아이콘을 클릭하여 음성 에이전트 IP 주소를 액세스 제어 IP 목록에 추가하십시오.

  다음 IP 주소를 모두 추가하십시오.
   * 169.60.154.134(미국 남부 서비스 지역)
   * 169.61.86.179(미국 동부 서비스 지역)

1. **저장**을 클릭하여 종료 URI 구성을 완료하십시오.

전송할 대상 전화번호와 종료 URI를 기록하십시오. 나중에 {{site.data.keyword.conversationshort}} 대화 상자에서 이를 전송 대상으로 지정할 수 있습니다. 


## 2단계: 호출 전송을 위한 {{site.data.keyword.conversationshort}} 구성
{: #conversation-setup}

{{site.data.keyword.conversationshort}} 서비스에서의 작업에 대해 자세히 알아보려면 [{{site.data.keyword.conversationshort}} 정보](../conversation/index.html#about)를 참조하십시오. 

1. {{site.data.keyword.Bluemix_notm}} 대시보드에서 음성 에이전트가 사용하는 {{site.data.keyword.conversationshort}} 인스턴스를 선택하십시오.

1. _시작하기_ 대시보드에서 **도구 실행** 단추를 클릭하십시오.

1. 편집할 작업공간에서 **시작하기**를 클릭하십시오.

1. **인텐트 추가**를 클릭하고 인텐트의 이름(예: _전송_)을 입력하십시오.

  자세한 정보를 입력하거나 나중에 돌아와서 인텐트를 편집하고 정제할 수 있습니다.

1. 호출 전송 인텐트를 작성한 후에 _대화_ 탭을 선택하십시오.

1. **노드 추가**를 클릭하고 노드의 이름(예: _호출 전송_)을 입력하십시오.

1. 작성한 인텐트를 찾으려면 _조건 검사:_ 섹션에 **호출 전송 인텐트**를 입력하십시오.

1. _응답 조치:_ 섹션에서 **&vellip;** 아이콘을 클릭하고 **JSON 편집기 열기**를 선택하십시오. 다음의 코드 스니펫을 복사하고 붙여넣어서 필드의 코드를 대체하십시오. 

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
       "transferTarget": "sip:18889990000\\@dal.watson-va.netfoundry.net"
            }
        }
    }
}
```
{: codeblock}

**참고**: 전송 대상의 SIP URI에는 전화번호와 사용자가 작성한 종료 URI가 포함됩니다. 예를 들어, 전화번호가 `18889990000`이고 종료 URI가 `mysiptrunk.pstn.twilio.com`인 경우 전체 SIP URI는 `sip:18889990000\\@mysiptrunk.pstn.twilio.com`입니다. Netfoundry를 사용하며 전화번호가 `18889990000`인 경우 전체 SIP URI는 `sip:18889990000\\@dal.watson-va.netfoundry.net`입니다.

## 다음 단계
{: #Next}

연관된 전화번호로 전화하여 음성 에이전트를 테스트하고 인텐트에서 식별한 주요 용어를 사용하십시오. 음성 에이전트가 사용자의 경로를 재지정하면 작동하는 것입니다.

이제 **전송** 인텐트 및 대화를 정제하고 선택한 주요 용어와 구문에 응답하도록 구성할 수 있습니다.
