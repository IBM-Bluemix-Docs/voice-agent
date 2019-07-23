---

copyright:
  years: 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# _관리_ 대시보드에서 음성 에이전트 작성
{: #config_instance}

{{site.data.keyword.iva_full}} 서비스를 작성한 후 _관리_ 대시보드에서 개별 음성 에이전트를 작성할 수 있습니다.
{: shortdesc}


## 음성 에이전트 작성
{: #create_instance}

음성 에이전트를 작성할 때 {{site.data.keyword.iva_short}}에서 사용할 수 있는 사용 가능한 Watson 서비스 인스턴스를 자동으로 검색합니다. 서비스가 사용 가능하지 않은 경우 음성 서비스와 함께 작성하도록 선택하거나 다른 {{site.data.keyword.Bluemix_short}} 계정 영역의 서비스에 연결할 수 있습니다. 음성 에이전트를 서비스 오케스트레이션 엔진, Google Speech to Text 또는 Google Text to Speech 인스턴스에 연결하도록 선택할 수도 있습니다.

1. _관리_ 대시보드의 _음성 에이전트_ 탭으로 이동하여 **Voice Agent 작성**을 클릭하십시오.

1. **이름**에는 음성 에이전트의 고유 이름을 지정하십시오 (예: `Customer Support - North America`). 이름은 최대 64자까지 포함될 수 있습니다.

1. **전화번호**에는 국가 및 지역 코드가 포함된 SIP 트렁크의 번호를 추가하십시오. 예를 들어, 미국 800 번호의 경우 전화번호를 `18883334444`로 지정하십시오. 전화번호에는 공백 및 `+ ( ) -` 문자가 최대 30까지 포함될 수 있습니다.

1. 기본적으로 이 전화번호는 서비스에 대한 **기본 번호**로 설정됩니다. 이는 단순히 번호 목록이 있는 경우 사용자에게 표시되는 첫 번째 번호이며 표시 용도일 뿐입니다. 기본 번호 변경에 대해서는 [기본 번호 설정](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num)을 참조하십시오.

1. **전화번호** 옆에 있는 **관리**를 클릭하여 여러 개의 번호를 한 음성 에이전트에 추가하도록 선택할 수도 있습니다. 여러 개의 번호를 설정하고 연관시키는 방법에 대한 정보는 [음성 에이전트 인스턴스에 여러 개의 전화번호 구성](/docs/services/voice-agent?topic=voice-agent-multi_num)을 참조하십시오. **관리** 대화 상자에서 번호를 편집하고 개별 번호에 대한 설명을 추가할 수도 있습니다.

1. 또는 음성 에이전트에 여러 개의 번호가 있는 경우, **전화번호** 필드가 회색으로 처리됩니다. 번호를 편집하려는 경우 회색으로 표시된 **전화번호** 필드를 클릭하거나 **관리**를 클릭하면 됩니다. [번호 및/또는 여러 개의 번호에 대한 설명 편집](/docs/services/voice-agent?topic=voice-agent-multi_num#edit_num)을 참조하십시오.

1. 선택적으로 최대 256자를 사용하여 음성 에이전트에 대해 설명하십시오.

1. 호출 전송을 사용으로 설정하려면 **기본 전송 대상**에 대한 종료 URI를 입력하십시오. 종료 URI를 설정하는 방법에 대한 정보는 [호출 전송 설정](/docs/services/voice-agent?topic=voice-agent-call-transfer)을 참조하십시오. 전송 대상에 개인 전화번호를 사용하지 마십시오. **기본 전송 대상** 종료 URI에는 최대 256자를 포함할 수 있습니다.

1. Watson 서비스 인스턴스에 대한 연결을 구성하십시오. **위치 1** 및 **위치 2** 모두에 대한 연결을 구성하여 다중 Watson 서비스 인스턴스에 연결할 수 있습니다. 다중 서비스 인스턴스에 연결하면 가동 중단 시에 음성 에이전트가 대체 서비스 인스턴스로 전환할 수 있습니다. [다중 Watson 서비스 위치 추가](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location)를 참조하십시오.

1. **대화** 아래에서 **위치 1** 또는 **위치 2**를 클릭하고 선택한 위치를 사용으로 설정하여 {{site.data.keyword.conversationshort}} 서비스 인스턴스에 대한 연결을 구성하십시오. 사용자는 자신 또는 다른 사용자가 소유하는 {{site.data.keyword.Bluemix_notm}} 계정의 {{site.data.keyword.conversationshort}} 서비스 인스턴스를 사용할 수 있습니다. 서비스 오케스트레이션 엔진을 통해 이러한 옵션에 연결할 수도 있습니다.

   * 댈러스 또는 워싱턴 DC 지역에서 음성 에이전트를 작성 중이며 {{site.data.keyword.conversationshort}} 서비스 인스턴스가 없는 경우에는 **서비스 인스턴스** 메뉴에서 서비스 인스턴스를 작성할 수 있습니다.
   * 또는 [**서비스 유형**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service)을 변경하여 {{site.data.keyword.conversationshort}} 대화의 다른 소스에 연결하거나 SOE와 연결할 수 있습니다.
   * 다중 서비스 위치를 구성하려면 기타 위치 옵션을 클릭하고 **위치 사용**을 선택하여 기타 {{site.data.keyword.conversationshort}} 인스턴스에 대한 연결을 구성하십시오. [다중 Watson 서비스 위치 추가](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location)를 참조하십시오.

1. **{{site.data.keyword.speechtotextshort}}**에서 **위치 1** 또는 **위치 2**를 선택하고 해당 위치를 사용으로 설정하여 {{site.data.keyword.speechtotextshort}} 서비스 인스턴스의 기본 구성을 검토하십시오. 다음을 통해 구성을 사용자 정의할 수 있습니다.
   * 음성 에이전트를 **서비스 유형**으로 기존 인스턴스에 연결하려면 **내 음성-문자 변환 인스턴스**를 선택하십시오. 다음으로, **모델 유형 선택**에서 **협대역**, **광대역** 또는 **협대역 및 광대역 모두**를 선택한 후 언어 **모델**을 선택하십시오.
   * 댈러스 또는 워싱턴 DC 지역에서 음성 에이전트를 작성 중이며 {{site.data.keyword.speechtotextshort}} 서비스 인스턴스가 없는 경우에는 **서비스 인스턴스** 메뉴에서 서비스 인스턴스를 작성할 수 있습니다.
   * **서비스 유형**으로 [다른 {{site.data.keyword.Bluemix_notm}} 작업공간의 {{site.data.keyword.speechtotextshort}} 인스턴스](/docs/services/voice-agent?topic=voice-agent-other_service) 또는 Google Cloud Speech-to-Text와 같은 [서드파티 음성-문자 변환 서비스](/docs/services/voice-agent?topic=voice-agent-third-party#third-party)를 선택할 수 있습니다.
   * 다중 서비스 위치를 구성하려면 기타 위치 옵션을 클릭하고 **위치 사용**을 선택하여 기타 {{site.data.keyword.speechtotextshort}} 인스턴스에 대한 연결을 구성하십시오. [다중 Watson 서비스 위치 추가](/docs/services/voice-agent?topic=voice-agent-disaster-recovery)를 참조하십시오.

1. **{{site.data.keyword.texttospeechshort}}**에서 **위치 1** 또는 **위치 2**를 클릭하고 해당 위치를 사용으로 설정하여 {{site.data.keyword.texttospeechshort}} 서비스 인스턴스의 기본 구성을 검토하십시오. 다음을 통해 구성을 사용자 정의할 수 있습니다.
   * 댈러스 또는 워싱턴 DC 지역에서 음성 에이전트를 작성 중이며 {{site.data.keyword.texttospeechshort}} 서비스 인스턴스가 없는 경우에는 **서비스 인스턴스** 메뉴에서 서비스 인스턴스를 작성할 수 있습니다.
   * **서비스 유형**으로 [다른 {{site.data.keyword.Bluemix_notm}} 작업공간의 {{site.data.keyword.texttospeechshort}} 인스턴스](/docs/services/voice-agent?topic=voice-agent-other_service) 또는 Google Cloud Text-to-Speech와 같은 [서드파티 문자-음성 변환 서비스](/docs/services/voice-agent?topic=voice-agent-third-party)를 선택할 수 있습니다.
   * 다중 서비스 위치를 구성하려면 기타 위치 옵션을 클릭하고 **위치 사용**을 선택하여 기타 {{site.data.keyword.texttospeechshort}} 인스턴스에 대한 연결을 구성하십시오. [다중 Watson 서비스 위치 추가](/docs/services/voice-agent?topic=voice-agent-disaster-recovery)를 참조하십시오.

1. 또한 이벤트 전달을 사용하여 {{site.data.keyword.cloudantfull}}에서 음성 에이전트에 의해 처리되는 호출과 관련된 정보를 수집하도록 선택할 수도 있습니다. [음성 에이전트에 대한 이벤트 전달 사용](/docs/services/voice-agent?topic=voice-agent-event_forwarding)을 참조하십시오. 추가 구성 옵션은 [음성 에이전트 구성](/docs/services/voice-agent?topic=voice-agent-managing#configure_va)을 참조하십시오.

1. **음성 에이전트 작성**을 클릭하여 음성 에이전트 및 새 서비스를 작성하십시오.

음성 에이전트를 작성한 후 전화번호로 전화를 걸어서 음성 에이전트를 테스트하십시오. _사용_ 대시보드에서 전화 통화에 대한 세부사항을 볼 수 있습니다. [사용 및 호출 로그 보기](/docs/services/voice-agent?topic=voice-agent-logging)를 참조하십시오.   
