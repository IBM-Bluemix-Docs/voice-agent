---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 서비스 인스턴스 및 음성 에이전트 관리
{: #managing}

_관리_ 대시보드를 사용하여 서비스 인스턴스 구성을 변경하고 개별 음성 에이전트를 작성, 편집, 복제, 구성 또는 제거할 수 있습니다. 서비스 인스턴스에 다중 음성 에이전트가 있을 수 있지만 각 음성 에이전트의 이름과 전화번호가 고유해야 합니다.
{: shortdesc}

## 음성 에이전트 서비스 대시보드로 이동
{: #navigate_manage}

{{site.data.keyword.iva_short}} 서비스 대시보드에서 _관리_ 대시보드를 찾을 수 있습니다.

1. [{{site.data.keyword.Bluemix_notm}} 계정 리소스 목록](https://cloud.ibm.com/resources)으로 이동하십시오. 

1. **서비스** 목록에서 **음성 에이전트** 서비스 인스턴스를 선택하여 _관리_ 탭에서 서비스 대시보드를 여십시오.

## 서비스 인스턴스에 대한 최대 동시 연결 수 편집
{: #edit_service}

모든 플랜에서 사용자는 무료로 2개의 동시 연결을 수신합니다. _표준_ 또는 _프리미엄_ 플랜을 사용하는 경우 _인스턴스_ 탭에서 기본 설정으로부터 [최대 동시 연결 수를 변경](managing_concurrency.html)할 수 있습니다.

## 음성 에이전트 작성
{: #create_va}

_관리_ 대시보드의 _음성 에이전트_ 탭에서 [새 음성 에이전트를 작성](managing_create.html)하십시오.

## 음성 에이전트 편집
{: #edit_va}

_관리_ 대시보드의 _음성 에이전트_ 탭에서 편집하여 기존 음성 에이전트를 변경할 수 있습니다. 음성 에이전트를 편집하려면 음성 에이전트에 대한 옵션 목록에서 **에이전트 편집**을 클릭하십시오. 구성을 변경한 후 변경사항을 저장하십시오.

## 음성 에이전트 복제
{: #clone_va}

음성 에이전트를 복제하면 Watson 서비스에 대한 모든 구성이 새 에이전트로 복사됩니다. 음성 에이전트를 복제하려면 음성 에이전트에 대한 옵션 목록에서 **에이전트 복제**를 클릭하십시오. 음성 에이전트에 고유 이름과 전화번호를 제공하고 필요에 따라 구성 옵션을 변경한 후 변경사항을 저장하십시오.

## 음성 에이전트 삭제
{: #delete_va}

전화번호를 해제하기 위해 음성 에이전트를 삭제할 수 있습니다. 전화번호마다 하나의 음성 에이전트만 있을 수 있습니다. 전화번호를 다른 음성 에이전트용으로 사용하려면 먼저 해당 전화번호를 사용 중인 음성 에이전트를 삭제해야 합니다.

음성 에이전트를 삭제하려면 _음성 에이전트_ 탭으로 이동하여 음성 에이전트에 대한 옵션 목록에서 **에이전트 삭제**를 클릭한 후 변경사항을 저장하십시오. 음성 에이전트가 음성 에이전트 목록에서 제거됩니다.

## 음성 에이전트 구성
{: #configure_va}

음성 에이전트를 작성, 복제 또는 편집할 때 음성 에이전트의 구성 설정과 관련 서비스에 대한 연결을 변경할 수 있습니다.

* **[다중 서비스 위치 구성](managing_disaster_recovery.html):** 연결된 서비스가 서비스 중복성을 지원하도록 다중 서비스 위치를 포함하십시오.
* **[서드파티 음성 및 텍스트 서비스와 연결](managing_third_party.html):** {{site.data.keyword.texttospeechshort}} 또는 {{site.data.keyword.speechtotextshort}}를 사용하는 대신에 음성 에이전트를 Google Cloud Speech-to-Text와 같은 서드파티 API에 연결할 수 있습니다.
* **[다른 {{site.data.keyword.Bluemix_notm}} 작업공간에서 서비스 사용](managing_other.html):** 다른 {{site.data.keyword.Bluemix_short}} 계정의 작업공간에 속해 있는 {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 또는 {{site.data.keyword.speechtotextshort}} 서비스 인스턴스를 사용하도록 음성 에이전트를 구성할 수 있습니다.
* **[서비스 오케스트레이션 엔진을 사용하여 Watson Assistant 구성](managing_SOE.html):** 서비스 오케스트레이션 엔진(SOE)을 통해 {{site.data.keyword.conversationshort}} 작업공간에 연결할 수 있습니다. SOE는 서드파티 API를 사용하여 수정할 수 있도록 서비스로 보내고 받는 메시지를 인터셉트합니다.
* **[음성 에이전트에 대한 이벤트 전달 사용](event-forwarding.html):** {{site.data.keyword.iva_short}}에서 호출 데이터를 수집하고 분석하여 호출자와의 자연스러운 대화 능력을 개선할 수 있습니다. 사용자가 작성하는 각 음성 에이전트는 사용자가 관리하는 지정된 {{site.data.keyword.cloudant_short_notm}}로 이벤트 보고서를 전달할 수 있습니다.

## 고급 음성 에이전트 옵션 구성
{: #config-advanced}

음성 에이전트를 작성하거나 복제하는 경우 **고급 표시**를 클릭하여 다음 고급 구성 옵션을 볼 수 있습니다.

* **{{site.data.keyword.conversationshort}} 실패 응답 메시지(선택사항)**: 호출을 {{site.data.keyword.conversationshort}}에 연결할 수 없는 경우 메시지 수신인에게 보내는 기본 응답 메시지입니다.
* **전송 오류 응답 메시지(선택사항)**: 호출 전송에 실패한 경우 호출자에게 스트리밍되는 기본 응답 메시지입니다.
* **사용자 정의 SIP INVITE 헤더(선택사항)**: 수신 SIP INVITE 요청에서 추출할 사용자 정의 SIP 헤더를 지정합니다.
* **{{site.data.keyword.iva_short}}**의 임시 벨소리 응답 보내기: {{site.data.keyword.iva_short}}이 수신 호출을 처리할 때 `180 벨소리` 응답을 보냅니다. 기본적으로 이 설정을 사용합니다.
* **전송 시 호출자 보류**: 전송 중에 호출자를 보류합니다. 기본적으로 이 설정을 사용합니다.
* **전송 실패 시 호출 연결 끊기**: 호출 전송에 실패하면 호출 연결을 끊을지 여부를 판별합니다.  기본적으로 이 설정을 사용합니다. 설정이 사용되지 않고 호출 전송에 실패한 경우 {{site.data.keyword.iva_short}}이 대화 턴을 시작합니다. 그런 다음 {{site.data.keyword.conversationshort}}가 호출 연결을 끊거나 대화 상자에 구성된 다른 대상으로 전송할 수 있습니다.
* **네트워크 이벤트 시 {{site.data.keyword.conversationshort}}에 알림**: 이 설정이 사용되고 네트워크 오류가 발견된 경우, {{site.data.keyword.iva_short}}이 "vgwNetworkWarningMessage" 텍스트를 사용하여 {{site.data.keyword.conversationshort}} 서비스에 대한 턴을 시작합니다. `vgwNetworkWarnings` 상태 변수에는 현재 턴에서 발생한 네트워크 이벤트 목록이 포함됩니다. 설정이 사용되지 않는 경우 현재 턴에서 발생한 네트워크 이벤트의 목록은 `vgwNetworkWarning` 상태 변수의 다음 턴 이벤트에 전송됩니다. 기본적으로 이 설정을 사용합니다.
