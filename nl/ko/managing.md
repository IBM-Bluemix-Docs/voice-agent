---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-19"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 음성 에이전트 관리
{: #managing}

_관리_ 대시보드에서 음성 에이전트를 작성, 편집, 복제, 구성 및 제거할 수 있습니다. 다중 음성 에이전트가 있을 수 있지만 각 음성 에이전트의 이름과 전화번호가 고유해야 합니다.
{: shortdesc}

<!-- Title should be task oriented and descriptive-->

## 음성 에이전트 작성
{: #config_instance}

음성 에이전트를 작성할 때 {{site.data.keyword.iva_short}}에서 사용할 수 있는 사용 가능한 Watson 서비스 인스턴스를 자동으로 검색합니다. 서비스가 사용 가능하지 않은 경우 음성 서비스와 함께 작성하도록 선택하거나 다른 {{site.data.keyword.Bluemix_short}} 계정 영역의 서비스에 연결할 수 있습니다.

1. **음성 에이전트 작성**을 클릭하십시오.

1. **이름**에는 음성 에이전트의 고유 이름을 지정하십시오(예: `Customer Support - North America`).

1. **전화번호**에는 국가 및 지역 코드가 포함된 SIP 트렁크의 번호를 추가하십시오. 예를 들어, 미국 800 번호의 경우 전화번호를 `18883334444`로 지정하십시오. 전화번호에는 공백 및 `+ ( ) -` 문자가 포함될 수 있습니다.

1. 선택적으로 음성 에이전트에 대해 설명하십시오.

1. 호출 전송을 사용으로 설정하려면 **전송 대상**에 대한 종료 URI를 구성할 수 있습니다. [호출 전송 설정](call-transfer.html)을 참조하십시오. 전송 대상에 개인 전화번호를 사용하지 마십시오. 

1. Watson 서비스 인스턴스에 대한 연결을 구성하십시오. **위치 1** 및 **위치 2** 모두에 대한 연결을 구성하여 다중 Watson 서비스 인스턴스에 연결할 수 있습니다. 다중 서비스 인스턴스에 연결하면 가동 중단 시에 음성 에이전트가 대체 서비스 인스턴스로 전환할 수 있습니다. [다중 Watson 서비스 위치 추가](#add_location)를 참조하십시오. 

**중요**: _평가판_ 및 _라이트_ 계정은 {{site.data.keyword.iva_short}} 서비스 인스턴스가 작성된 위치에만 연결할 수 있습니다. 두 번째 위치는 두 번째 음성 에이전트가 아닙니다. 재해 복구를 위한 백업으로만 작동합니다.

1. **{{site.data.keyword.conversationshort}}** 아래에서 **위치 1 사용** 또는 **위치 2 사용**을 클릭하여 {{site.data.keyword.conversationshort}} 서비스 인스턴스에 대한 연결을 구성하십시오. 자신이나 다른 사용자가 소유하는 {{site.data.keyword.Bluemix_notm}} 계정에서 {{site.data.keyword.conversationshort}} 인스턴스나 {{site.data.keyword.virtualagentfull}} 인스턴스를 사용할 수 있습니다. 서비스 오케스트레이션 엔진을 통해 이러한 옵션에 연결할 수도 있습니다.

    * 미국 남부 지역에서 음성 에이전트를 작성 중이며 {{site.data.keyword.conversationshort}} 서비스 인스턴스가 없는 경우에는 **서비스 인스턴스** 메뉴에서 서비스 인스턴스를 작성할 수 있습니다.
    * 또는 [**서비스 유형**](#other_service)을 변경하여 {{site.data.keyword.conversationshort}} 대화의 다른 소스에 연결할 수 있습니다.
    * 다중 서비스 위치를 구성하려면 기타 위치 옵션을 클릭하고 **위치 사용**을 선택하여 기타 {{site.data.keyword.conversationshort}} 인스턴스에 대한 연결을 구성하십시오. [다중 Watson 서비스 위치 추가](#add_location)를 참조하십시오. 

1. **{{site.data.keyword.speechtotextshort}}**에서 **위치 1 사용** 또는 **위치 2 사용**을 클릭하여 {{site.data.keyword.speechtotextshort}} 서비스 인스턴스의 기본 구성을 검토하십시오. 미국 남부 지역에서 음성 에이전트를 작성 중이며 {{site.data.keyword.speechtotextshort}} 서비스 인스턴스가 없는 경우에는 **서비스 인스턴스** 메뉴에서 서비스 인스턴스를 작성할 수 있습니다. 또는 [**서비스 유형**](#other_service)을 변경하여 음성 에이전트를 다른 {{site.data.keyword.Bluemix_notm}} 계정 영역의 {{site.data.keyword.speechtotextshort}} 인스턴스에 연결할 수 있습니다. {{site.data.keyword.iva_short}}은 협대역 모델만 지원합니다.

    다중 서비스 위치를 구성하려면 기타 위치 옵션을 클릭하고 **위치 사용**을 선택하여 기타 {{site.data.keyword.speechtotextshort}} 인스턴스에 대한 연결을 구성하십시오. [다중 Watson 서비스 위치 추가](#add_location)를 참조하십시오. 

1. **{{site.data.keyword.texttospeechshort}}**에서 **위치 1 사용** 또는 **위치 2 사용**을 클릭하여 {{site.data.keyword.texttospeechshort}} 서비스 인스턴스의 기본 구성을 검토하십시오. 미국 남부 지역에서 음성 에이전트를 작성 중이며 {{site.data.keyword.texttospeechshort}} 서비스 인스턴스가 없는 경우에는 **서비스 인스턴스** 메뉴에서 서비스 인스턴스를 작성할 수 있습니다. 또는 [**서비스 유형**](#other_service)을 변경하여 음성 에이전트를 다른 {{site.data.keyword.Bluemix_notm}} 계정 영역의 {{site.data.keyword.texttospeechshort}} 인스턴스에 연결할 수 있습니다. 

    다중 서비스 위치를 구성하려면 기타 위치 옵션을 클릭하고 **위치 사용**을 선택하여 기타 {{site.data.keyword.texttospeechshort}} 인스턴스에 대한 연결을 구성하십시오. [다중 Watson 서비스 위치 추가](#add_location)를 참조하십시오. 

1. 또한 이벤트 전달을 사용하여 {{site.data.keyword.cloudantfull}}에서 음성 에이전트에 의해 처리되는 호출과 관련된 정보를 수집하도록 선택할 수도 있습니다. [음성 에이전트에 대한 이벤트 전달 사용](event-forwarding.html)을 참조하십시오. 추가 구성 옵션은 [음성 에이전트 구성](#configure_va)을 참조하십시오. 

1. **음성 에이전트 작성**을 클릭하여 음성 에이전트 및 새 서비스를 작성하십시오.

음성 에이전트를 작성한 후 전화번호로 전화를 걸어서 음성 에이전트를 테스트하십시오. _사용_ 대시보드에서 전화 통화에 대한 세부사항을 볼 수 있습니다.  

## 최대 동시 연결 수 편집
{: #edit_concurrency}

_표준_ 플랜을 사용하는 경우 기본 설정에서 최대 동시 연결 수를 변경할 수 있습니다. 모든 플랜에서 사용자는 무료로 2개의 동시 연결을 수신합니다. 자세한 정보는 [가격 책정 플랜](https://console.bluemix.net/catalog/services/voice-agent-with-watson)을 참조하십시오. 

_관리_ 대시보드에서 _최대 동시 연결 수**에 나열된 플랜에서 허용된 최대 동시 연결 수를 볼 수 있습니다. 또한 **사용된 최대 동시 연결 수**에서 당월 중에 음성 에이전트에 의해 사용된 최대 동시 연결 수를 볼 수 있습니다.

플랜에서 최대 동시 연결 수를 변경하려면 **편집** 아이콘을 클릭하십시오. _최대 동시 연결 수 편집_ 창에서 최대 동시 연결 수를 선택하고 **저장**을 클릭하십시오. 셀프 서비스를 통해 설정할 수 있는 최소 동시 연결 수는 10개이며 최대값은 50개입니다. 음성 에이전트에 대한 50개가 넘는 동시 연결이 필요한 경우 [지원되는 네트워크 설정 요청](connect-SIP.html#request-setup)을 참조하십시오.

### 동시 연결 가격 책정 정보
{: #concurrent-charge}

  * _라이트_, _평가판_ 및 _표준_ 플랜에는 비용 없이 2개의 동시 연결이 포함됩니다.
  * _프리미엄_ 플랜은 인스턴스로 사용자 정의됩니다.
  * _표준_ 계정에는 최소 10개의 동시 연결 용량이 있습니다.
  * 동시 연결 사용은 월 단위입니다. 하루에 2개가 넘는 동시 연결을 사용하는 경우 일 단위로 비용이 청구됩니다.
  * _표준_ 또는 _프리미엄_ 플랜이 있는 경우 더 많은 동시 연결 용량을 구매할 수 있습니다.
  * 하루에 사용한 최대 동시 연결 용량에 대해 일 단위로 비용이 청구됩니다. 예를 들어, 사용자 플랜이 2개의 동시 연결을 무료로 지원하고 사용자는 최대 연결 한계를 12개로 설정하는 경우가 있기 때문입니다. 하루에 5개만 사용하는 경우 3개에 대해 비용이 청구됩니다.

플랜, 요금 및 기능에 대한 자세한 정보는 [가격 책정 플랜](https://console.bluemix.net/catalog/services/voice-agent-with-watson)을 참조하십시오.

## 음성 에이전트 편집
{: #edit_va}

편집을 통해 기존 음성 에이전트를 변경할 수 있습니다. 음성 에이전트를 편집하려면 음성 에이전트에 대한 옵션 목록에서 **에이전트 편집**을 클릭하십시오. 구성을 변경한 후 변경사항을 저장하십시오.

## 음성 에이전트 복제
{: #clone_va}

음성 에이전트를 복제하면 Watson 서비스에 대한 모든 구성이 새 에이전트로 복사됩니다. 음성 에이전트를 복제하려면 음성 에이전트에 대한 옵션 목록에서 **에이전트 복제**를 클릭하십시오. 음성 에이전트에 고유 이름과 전화번호를 제공하고 필요에 따라 구성 옵션을 변경한 후 변경사항을 저장하십시오.

## 음성 에이전트 삭제
{: #delete_va}

전화번호를 해제하기 위해 음성 에이전트를 삭제할 수 있습니다. 전화번호에는 하나의 음성 에이전트만 있을 수 있습니다. 전화번호를 다른 음성 에이전트용으로 사용하려면 먼저 해당 전화번호를 사용 중인 음성 에이전트를 삭제해야 합니다.

음성 에이전트를 삭제하려면 음성 에이전트에 대한 옵션 목록에서 **에이전트 삭제**를 클릭한 후 변경사항을 저장하십시오. 음성 에이전트가 음성 에이전트 목록에서 제거됩니다.

## 음성 에이전트 구성
{: #configure_va}

### 고급 옵션 구성
{: #config-advanced}

음성 에이전트를 작성하거나 복제하는 경우 **고급 표시**를 클릭하여 다음 고급 구성 옵션을 볼 수 있습니다.

* **{{site.data.keyword.conversationshort}} 실패 응답 메시지(선택사항)**: 호출을 {{site.data.keyword.conversationshort}}에 연결할 수 없는 경우 메시지 수신인에게 보내는 기본 응답 메시지입니다.
* **전송 오류 응답 메시지(선택사항)**: 호출 전송에 실패한 경우 호출자에게 스트리밍되는 기본 응답 메시지입니다.
* **{{site.data.keyword.iva_short}}**의 임시 벨소리 응답 보내기: {{site.data.keyword.iva_short}}이 수신 호출을 처리할 때 `180 벨소리` 응답을 보냅니다. 기본적으로 이 설정을 사용합니다.
* **전송 시 호출자 보류**: 전송 중에 호출자를 보류합니다. 기본적으로 이 설정을 사용합니다.
* **전송 실패 시 호출 연결 끊기**: 호출 전송에 실패하면 호출 연결을 끊을지 여부를 판별합니다. 기본적으로 이 설정을 사용합니다. 설정이 사용되지 않고 호출 전송에 실패한 경우 {{site.data.keyword.iva_short}}이 대화 턴을 시작합니다. 그런 다음 {{site.data.keyword.conversationshort}}가 호출 연결을 끊거나 대화 상자에 구성된 다른 대상으로 전송할 수 있습니다.
* **네트워크 이벤트 시 {{site.data.keyword.conversationshort}}에 알림**: 이 설정이 사용되고 네트워크 오류가 발견된 경우, {{site.data.keyword.iva_short}}이 "vgwNetworkWarningMessage" 텍스트를 사용하여 {{site.data.keyword.conversationshort}} 서비스에 대한 턴을 시작합니다. `vgwNetworkWarnings` 상태 변수에는 현재 턴에서 발생한 네트워크 이벤트 목록이 포함됩니다. 설정이 사용되지 않는 경우 현재 턴에서 발생한 네트워크 이벤트의 목록은 `vgwNetworkWarning` 상태 변수의 다음 턴 이벤트에 전송됩니다. 기본적으로 이 설정을 사용합니다.

### 복수의 Watson 서비스 위치 추가
{: #add_location}

_표준_ 또는 _프리미엄_ 계정이 있는 경우 서비스 중복성을 위해 서로 다른 위치의 여러 Watson 서비스에 음성 에이전트를 연결할 수 있습니다. _평가판_ 및 _라이트_ 계정은 {{site.data.keyword.iva_short}} 서비스 인스턴스가 작성된 위치에만 연결할 수 있습니다. 두 번째 위치는 두 번째 음성 에이전트가 아닙니다. 재해 복구를 위한 백업으로만 작동합니다.

음성 에이전트는 지리적 거리순으로 Watson 서비스 인스턴스를 사용합니다. 예를 들어, 미국 동부 지역에서 음성 에이전트를 작성하고 미국 남부와 시드니(호주)에서 {{site.data.keyword.conversationshort}} 서비스를 작성할 수 있습니다. 미국 남부가 지리적으로 시드니보다 미국 동부에 더 가깝기 때문에 음성 에이전트는 {{site.data.keyword.conversationshort}} 미국 남부 지역을 사용합니다. 여러 지역의 Watson 서비스에 연결하면 Watson 서비스가 한 위치에서 오프라인인 경우에 음성 에이전트가 여분의 서비스를 사용할 수 있습니다. 

언제든지 음성 에이전트 구성에 Watson 서비스 위치를 추가할 수 있습니다. 음성 에이전트 작성 시 여러 서비스 위치 인스턴스 연결에 대한 정보는 [음성 에이전트 작성](#creating)을 참조하십시오.

기존 음성 에이전트에 Watson 서비스 위치를 추가하려면 구성할 음성 에이전트에 대해 **에이전트 편집**을 클릭하십시오. 연결할 {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} 또는 {{site.data.keyword.speechtotextshort}} 인스턴스에 대해 **위치 1** 또는 **위치 2**를 선택하고 구성 정보를 추가하십시오. 자신의 작업공간이나 기타 작업공간에서 Watson 서비스 인스턴스를 사용할 수 있습니다. [기타 {{site.data.keyword.Bluemix_notm}} 작업공간에서 서비스 인스턴스 사용](#other_services)을 참조하십시오. 

**중요:** 서비스 중복성을 원하는 경우에는 서로 다른 위치에 대해 서로 다른 서비스 지역에서 Watson 서비스 인스턴스를 사용해야 합니다. 

**위치 사용** 상자를 사용하여 위치를 사용 또는 사용 안함으로 설정할 수 있습니다. **위치 1**은 기본적으로 사용되며 **위치 2**는 기본적으로 사용되지 않습니다. 각 Watson 서비스마다 최소한 하나의 위치를 사용해야 합니다. 

### 다른 {{site.data.keyword.Bluemix_notm}} 작업공간에서 서비스 인스턴스 사용
{: #other_service}

다른 {{site.data.keyword.Bluemix_short}} 계정의 작업공간에 속해 있는 {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 또는 {{site.data.keyword.speechtotextshort}} 서비스 인스턴스를 사용하도록 음성 에이전트를 구성할 수 있습니다.음성 에이전트를 기타 서비스 인스턴스에 연결하려면 서비스 인스턴스에 대한 API 키 또는 사용자 이름과 비밀번호 신임 정보를 사용할 수 있습니다. 

1. **서비스 유형** 및 **지역**을 선택하십시오. 

1. **사용자 이름 및 비밀번호** 또는 **API 키**를 선택하고 서비스 신임 정보를 입력하십시오.
  이러한 값을 찾으려면 구성할 서비스 인스턴스로 이동하여 **서비스 신임 정보**를 선택한 후 **신임 정보 보기**를 선택하십시오.

  * **사용자 이름 및 비밀번호**: **URL**, **사용자 이름** 및 **비밀번호** 필드에서 {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 또는 {{site.data.keyword.texttospeechshort}} 서비스 인스턴스에 대한 신임 정보를 구성하십시오. 
  * **API 키**: **URL** 및 **API 키** 필드에서 {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 또는 {{site.data.keyword.texttospeechshort}} 서비스 인스턴스에 대한 신임 정보를 구성하십시오. 

  신임 정보는 {{site.data.keyword.Bluemix_notm}} 사용자 이름 및 비밀번호가 아니라 특정 서비스 인스턴스에 대한 암호화된 신임 정보입니다.
{:tip}

1. 서비스 인스턴스 정보를 입력하십시오. 

  * **{{site.data.keyword.conversationshort}}:** **작업공간 ID** 필드에 음성 에이전트와 함께 사용할 작업공간의 ID를 입력하십시오. 작업공간 ID를 찾으려면 도구를 실행하고 통합할 작업공간에서 조치 아이콘(**&vellip;**)을 클릭하고 **세부사항 보기**를 선택하십시오.

  * **{{site.data.keyword.speechtotextshort}}:** **모델** 필드에서 서비스에 대한 음성 언어 및 형식을 선택하십시오. {{site.data.keyword.iva_short}}은 협대역 모델만 지원합니다.

  * **{{site.data.keyword.texttospeechshort}}:** **음성** 필드에서 서비스가 사용하는 언어 및 음성을 선택하십시오. 서비스에 대한 음성을 지정해야 합니다. 

**중요:** 음성 에이전트가 작동하려면 {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 및 {{site.data.keyword.texttospeechshort}}를 동일한 언어로 구성해야 합니다. [지원되는 언어](about.html#supported-languages)를 참조하십시오.

### 음성 에이전트에 대한 {{site.data.keyword.conversationshort}} 구성
{: #conversation_va}

{{site.data.keyword.conversationshort}} 서비스 인스턴스를 구성하는 대신 서비스 오케스트레이션 엔진(SOE) 또는 Watson {{site.data.keyword.virtualagentshort}}에 연결할 수 있습니다.

* **서비스 오케스트레이션 엔진**: [서비스 오케스트레이션 엔진(SOE)](about.html#arch-soe)을 통해 {{site.data.keyword.conversationshort}} 작업공간 또는 {{site.data.keyword.virtualagentshort}}에 액세스하십시오. SOE는 써드파티 API를 사용하여 수정할 수 있도록 서비스로 보내고 받는 메시지를 인터셉트합니다.

  **URL** 필드에 SOE 작업공간의 전체 URL(예: `https://iva-soesample.myorg.net/SOE/myWorkspace`)을 입력하십시오. SOE에 인증이 필요한 경우(권장됨) 사용자 이름과 비밀번호를 각 필드에 입력하십시오.

* **Watson {{site.data.keyword.virtualagentshort}}**: {{site.data.keyword.conversationshort}} 작업공간 대신 {{site.data.keyword.virtualagentshort}} 챗봇에 연결하십시오. [{{site.data.keyword.virtualagentshort}}](../virtual-agent/getting-started.html#getting-started)는 {{site.data.keyword.conversationshort}} 서비스를 기반으로 빌드되었지만 기계 학습 경험 없이 시작할 수 있도록 사전 학습된 기능을 제공합니다.

  **URL** 필드에 {{site.data.keyword.virtualagentshort}}의 URL 신임 정보(예: `https://api.ibm.com/virtualagent/run/api`)를 입력하십시오. **클라이언트 ID** 및 **클라이언트 시크릿** 필드에는 API 호출에 대한 `X-IBM-Client-Id` 및 `X-IBM-Client-Secret` 헤더 파일에 맵핑되는 인증 키를 입력하십시오. **봇 ID** 필드에 이 음성 에이전트용으로 사용할 봇의 ID를 입력하십시오. 이러한 값을 찾는 방법에 대한 정보는 {{site.data.keyword.virtualagentshort}} 문서에서 [에이전트 공개](../virtual-agent/publish.html)를 참조하십시오. 
