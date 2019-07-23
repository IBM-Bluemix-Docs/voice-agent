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

# SMS 사용 음성 에이전트 작성
{: #sms_voice_config_instance}

{{site.data.keyword.iva_full}} SMS 기능으로 개별 음성 에이전트 또는 _관리_ 대시보드에서 SMS 기능만 있는 음성 에이전트를 작성할 수 있습니다. 인바운드 음성 호출을 수신하도록 {{site.data.keyword.iva_full}}를 구성하고 사용자가 수신한 음성 명령에 따라 SMS 아웃바운드 메시지로 응답할 수 있습니다. 구성하려면 {{site.data.keyword.conversationshort}} 서비스에서 노드 및 인텐트를 추가하십시오.
{: shortdesc}


1. _관리_ 대시보드의 _음성 에이전트_ 탭으로 이동하여 **Voice Agent 작성**을 클릭하십시오.

1. **에이전트 유형**의 경우, _Voice + SMS_를 선택하십시오.

1. [음성 에이전트 작성](/docs/services/voice-agent?topic=voice-agent-config_instance)의 지시사항을 따르십시오.

1. 사용자가 SMS 에이전트로 SMS 세션을 시작하도록 허용하려면 **인바운드 메시지에서 대화 시작** 상자를 선택하십시오. 

1. SMS 에이전트가 잠시 동안 응답을 수신하지 못했으며 이제 제한시간이 초과된다는 SMS 메시지를 사용자에게 보내도록 하려는 경우 **세션 제한시간 초과 알림**을 선택하십시오. 

   - 세션의 제한시간 초과에 대한 사용자 정의 시간을 설정하는 등 SMS 에이전트에 사용할 수 있는 **고급 옵션**에 대한 자세한 정보는 [고급 옵션](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced)을 참조하십시오. 

1. [SMS 에이전트 작성](/docs/services/voice-agent?topic=voice-agent-sms_config_instance)의 지시사항에 따라 SMS 에이전트를 작성하십시오. 

1. _**참고:**_ 음성 입력을 수신하거나 응답으로 SMS 아웃바운드 메시지를 다시 보내는 등 에이전트가 음성 및 SMS 통합을 가지도록 하려면 **SMS** 에이전트에 대한 **음성** 번호 중 하나를 사용**해야** 합니다.

### 음성 및 SMS 통합용 Watson Assistant 구성
{: #sms_outbound}

1. {{site.data.keyword.Bluemix_notm}} 대시보드에서 음성 에이전트가 사용하는 {{site.data.keyword.conversationshort}} 인스턴스를 선택하십시오.

1. 대시보드에서 **아웃바운드 SMS 인텐트**를 작성하십시오. 

1. 대시보드에서 **아웃바운드 SMS 노드**를 추가하십시오. 

1. _지원에서 인식하는 경우:_ 섹션에서 이전에 작성한 **아웃바운드 SMS 인텐트** 속성을 선택하십시오. 

1. 응답을 노드에 추가하십시오. 다음의 코드 스니펫을 복사하고 붙여넣어서 필드의 코드를 대체하십시오.

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


1. 에이전트를 호출하고 노드를 트리거하여 사용자가 호출하는 전화번호로 텍스트 메시지를 수신하십시오. 

{{site.data.keyword.conversationshort}} 서비스에서의 작업에 대해 자세히 알아보려면 [{{site.data.keyword.conversationshort}} 정보](/docs/services/assistant?topic=assistant-index#indext)를 참조하십시오.
