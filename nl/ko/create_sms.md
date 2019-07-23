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


# SMS 에이전트 작성
{: #sms_config_instance}

{{site.data.keyword.iva_full}} 서비스를 작성한 후 _관리_ 대시보드에서 개별 SMS 에이전트를 작성할 수 있습니다.
{: shortdesc}

1. _관리_ 대시보드의 _음성 에이전트_ 탭으로 이동하여 **Voice Agent 작성**을 클릭하십시오.

1. **에이전트 유형**의 경우, _SMS_를 선택하십시오.

1. **이름**에는 음성 에이전트의 고유 이름을 지정하십시오 (예: `Customer Support - North America`). 이름은 최대 64자까지 포함될 수 있습니다.

1. 전화번호의 경우 국가 및 지역 코드가 포함된 SIP 트렁크의 번호를 추가하십시오. 예를 들어, 미국 800 번호의 경우 전화번호를 18883334444로 지정하십시오. 전화번호에는 최대 30자를 입력할 수 있으며 공백 및 + ( ) - 문자가 포함될 수 있습니다. SMS는 사용자별로 하나의 번호만 지원합니다.

1. **SMS 제공자** 아래에 SMS 제공자에 대한 사용자 이름, 비밀번호 및 API URL을 입력하십시오. 예를 들어 _Twilio_를 사용하는 경우, 사용자 이름은 **계정 SID**이고, 비밀번호는 **인증 토큰**이며, SMS 제공자는 `https://api.twilio.com`입니다.

1. **대화** 아래에서 {{site.data.keyword.conversationshort}} 서비스 인스턴스에 대한 연결을 구성하십시오. 사용자는 자신 또는 다른 사용자가 소유하는 {{site.data.keyword.Bluemix_notm}} 계정의 {{site.data.keyword.conversationshort}} 서비스 인스턴스를 사용할 수 있습니다. 서비스 오케스트레이션 엔진(SOE)을 통해 이러한 옵션에 연결할 수도 있습니다.

   * 댈러스 또는 워싱턴 DC 지역에서 SMS 에이전트를 작성 중이며 {{site.data.keyword.conversationshort}} 서비스 인스턴스가 없는 경우에는 **서비스 인스턴스** 메뉴에서 서비스 인스턴스를 작성할 수 있습니다.
   * 또는 [**서비스 유형**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service)을 변경하여 {{site.data.keyword.conversationshort}} 대화의 다른 소스에 연결하거나 SOE와 연결할 수 있습니다.
   * 다중 서비스 위치를 구성하려면 기타 위치 옵션을 클릭하고 **위치 사용**을 선택하여 기타 {{site.data.keyword.conversationshort}} 인스턴스에 대한 연결을 구성하십시오. 자세한 정보는 [다중 Watson 서비스 위치 추가](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location)를 참조하십시오.

1. 사용자가 SMS 에이전트로 SMS 세션을 시작하도록 허용하려면 **인바운드 메시지에서 대화 시작** 상자를 선택하십시오. 

1. SMS 에이전트가 잠시 동안 응답을 수신하지 못했으며 이제 제한시간이 초과된다는 SMS 메시지를 사용자에게 보내도록 하려는 경우 **세션 제한시간 초과 알림** 상자를 선택하십시오. 

    - 세션의 제한시간 초과에 대한 사용자 정의 시간을 설정하는 등 SMS 에이전트에 사용할 수 있는 **고급 옵션**에 대한 자세한 정보는 [고급 옵션](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced)을 참조하십시오. 
    - 세션 제한시간이 초과되면 알림을 받으려는 경우에만 상자를 선택하십시오. 

1. 또한 이벤트 전달을 사용하여 {{site.data.keyword.cloudantfull}}에서 음성 에이전트에 의해 처리되는 호출과 관련된 정보를 수집하도록 선택할 수도 있습니다. 자세한 정보는 [음성 에이전트에 대한 이벤트 전달 사용](/docs/services/voice-agent?topic=voice-agent-event_forwarding)을 참조하십시오. 추가 구성 옵션은 [음성 에이전트 구성](/docs/services/voice-agent?topic=voice-agent-managing#configure_va)을 참조하십시오.

1.  **음성 에이전트 작성**을 클릭하여 SMS 에이전트 및 새 서비스를 작성하십시오.

1. [지시사항](/docs/services/voice-agent?topic=voice-agent-connect-sms)에 따라 SMS 제공자에 연결하십시오. 

SMS 에이전트를 작성한 후 전화번호로 문자를 보내 SMS 에이전트를 테스트하십시오. _사용_ 대시보드에서 상호작용에 대한 세부사항을 볼 수 있습니다. [사용 및 로그 보기](/docs/services/voice-agent?topic=voice-agent-logging)를 참조하십시오.

음성 호출 동안 고객과 음성 에이전트 간의 SMS 메시징을 사용으로 설정하려면 SMS 번호가 음성 번호와 일치해야 합니다.
{: tip}

SMS 에이전트를 작성하거나 SMS 기능을 음성 에이전트에 추가하기 전에 적절한 인증 정보를 설정하고 API 키를 생성하여 SMS 번호로 프로그래밍**해야** 합니다. 자세한 정보는 [API 키 생성 및 인증 정보 설정](/docs/services/voice-agent?topic=voice-agent-connect-sms#sms_access)을 참조하십시오.

SMS 기능에 대한 SIP 트렁크도 구성**해야** 합니다. 제공자의 지시사항을 참조하십시오(예: Twilio). Twilio 전화번호가 없는 경우, [Twilio SIP 트렁크 작성](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup)을 참조하십시오.

Twilio 번호를 갖게 되면 SMS 기능에 대해 이를 구성해야 합니다. 자세한 정보는 [SMS에 대한 Twilio 구성](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup)을 참조하십시오.

인증 정보 작성에 문제가 있는 경우, *관리자* 또는 *작성자* 액세스 권한을 ㅜ여하도록 서비스 인스턴스 관리자에게 문의하십시오.
{: tip}

## SMS 에이전트에 대한 고급 옵션
{: #sms_advanced}

**전화번호** 필드 뒤의 **고급 표시**를 클릭하십시오. 

1. 선택적 **대화 읽기 제한시간 초과** 값을 설정하십시오. 이는 SMS Gateway가 Watson Assistant에서 응답을 대기하는 시간(초)입니다. 시간이 초과되면 SMS Gateway는 Watson Assistant에 문의를 재시도합니다. 그래도 서비스에 연결할 수 없는 경우 SMS/MMS 메시지가 실패합니다. 기본적으로 30초로 설정됩니다.

1. 선택적 **세션 제한시간 초과**를 설정하십시오. 이는 SMS Gateway가 사용자로부터 응답을 수신하지 않는 경우 세션이 만료된 이후의 시간(초)입니다.

1. **대화 실패 응답 메시지**를 설정하십시오. 이는 Watson Assistant에 연결할 수 없는 경우 보내지는 기본 응답 메시지입니다. 기본적으로 이는 `We're sorry, but we can't respond to your message.`로 설정됩니다.

### 세션을 종료하기 위한 SMS 에이전트 구성
{: #sms_terminate}

{{site.data.keyword.iva_full}} SMS 에이전트는 기본적으로 구성 가능하고 30초로 설정된 세션 제한시간에 대한 값을 기반으로 세션을 종료합니다. 

노드를 {{site.data.keyword.conversationshort}} 서비스에 추가하여 사용자로부터 종료 세션 명령에 응답할 수도 있습니다.  

1. {{site.data.keyword.Bluemix_notm}} 대시보드에서 음성 에이전트가 사용하는 {{site.data.keyword.conversationshort}} 인스턴스를 선택하십시오.

1. 대시보드에서 **SMS 인텐트 종료**를 작성하십시오. 또는 음성 에이전트에 대해 이미 사용하는 기존 인텐트를 수정할 수 있습니다(예: _호출 종료_).

1. 대시보드에서 **SMS 노드 종료**를 추가하십시오. 

1. _지원에서 인식하는 경우:_ 섹션에서 이전에 작성한 **SMS 인텐트 종료** 속성을 추가하십시오. 

1. 응답을 노드에 추가하십시오. 다음의 코드 스니펫을 복사하고 붙여넣어서 필드의 코드를 대체하십시오.

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

음성 에이전트를 작성한 후 각 유형을 기반으로 해당 전화번호로 전화를 걸거나 문자를 보내서 음성 에이전트를 테스트하십시오. _사용_ 대시보드에서 상호작용에 대한 세부사항을 볼 수 있습니다. [사용 및 로그 보기](/docs/services/voice-agent?topic=voice-agent-logging)를 참조하십시오.
