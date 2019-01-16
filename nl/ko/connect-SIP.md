---

copyright:
  years: 2018
lastupdated: "2018-12-05"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# SIP 트렁크 연결
{: #connect}

다음 목록에서 {{site.data.keyword.iva_full}}과의 통합에 사용할 SIP 트렁크 제공자를 선택할 수 있습니다.
{: #shortdesc}

* [NetFoundry](#NetFoundry-setup)
* [Twilio](#twilio-setup)
* [AT&T 및 기타 제공자](#att-other)
* [{{site.data.keyword.iva_short}}과의 피어링](#peering)
* [지원되는 설정 요청](#request-setup)

## NetFoundry SIP 트렁크 및 전화번호 작성
{: #NetFoundry-setup}

**참고:** 계정을 작성하려면 신용카드가 필요하며, 이는 사용량에 따라 정기적으로 비용 청구됩니다. 이미 NetFoundry 계정을 보유한 경우에는 기존 계정을 사용할 수 있습니다.

1. [NetFoundry![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson.netfoundry.io/watson-login){: new_window} 웹 사이트에서 계정을 작성하십시오.

1. _Watson 계정_ 기본 페이지로 이동하십시오.

1. 번호를 가져올 지역을 선택하십시오.

  **참고:** 사용 가능한 지역에 대한 Netfoundry 웹 사이트를 확인하십시오. 새 지역이 계속 추가됩니다.

1. **구매**를 클릭하고 화면의 지시사항에 따라 구매를 완료하십시오.

1. 일단 지불이 정상적으로 처리되면 SIP 트렁크 전화번호가 계정에 표시됩니다.

국가 및 지역 코드를 포함하여 이 전화번호는 음성 에이전트를 설정하고 호출 전송을 구성하는 데 필요합니다. [음성 에이전트 작성 및 연결](getting-started.html#step3)을 참조하십시오.


## Twilio SIP 트렁크 작성
{: #twilio-setup}

**참고:** [Twilio 계정 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.twilio.com/try-twilio){: new_window}을 작성하려면 신용카드가 필요하며, 이는 구성하는 SIP 트렁크의 사용량을 기반으로 정기적으로 비용 청구됩니다. 이미 Twilio 계정이 있는 경우 기존 계정을 사용할 수 있습니다.

  1. [Twilio 웹 사이트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.twilio.com/try-twilio){: new_window}에서 Twilio 계정을 작성하십시오.

  1. Twilio 계정을 사용하여 SIP 트렁크를 작성하십시오.

  1. Twilio 웹 사이트에서 Elastic SIP Trunking 대시보드로 이동하십시오.

  1. 탐색줄에서 **트렁크**를 선택하고 SIP 트렁크를 작성하십시오. SIP 트렁크가 이미 있는 경우 **+** 아이콘을 클릭하십시오. 결과 대화 상자에서 SIP 트렁크의 이름을 입력하고 **작성**을 클릭하십시오.

  1. Elastic SIP Trunks 페이지에서 SIP 트렁크를 선택하십시오.

  1. SIP 트렁크에 대한 탐색줄에서 **시작**을 선택하고 시작 SIP URI를 구성하십시오. **+** 아이콘을 선택하여 다중 호스트 이름을 포함시키면 서비스 장애를 방지할 수 있습니다.

  IP 주소 또는 호스트 이름은 {{site.data.keyword.iva_short}} 서비스 인스턴스의 _시작하기_ 대시보드에서 기록한 값입니다. 시작 URI를 구성할 때 시작 URI는 SIP URI 형식이어야 합니다(예: `sip:us-south.voiceagent.cloud.ibm.com/`). 다중 호스트 이름 또는 IP 주소를 포함하면 첫 번째 호스트 엔드포인트가 실패하거나 서비스가 중단된 경우에 SIP 트렁크 제공자가 다음에 나열된 호스트 이름으로 호출을 전달합니다.

  1. SIP 트렁크에 대한 탐색줄에서 **번호**를 선택하십시오. 그런 다음 전화번호를 작성하여 SIP 트렁크에 지정하십시오.

  번호 페이지에서 **번호 구매**를 클릭하거나 이미 번호가 있는 경우 **+** 아이콘을 클릭하십시오. 사용자 지역의 새 전화번호를 프로비저닝할 수 있는 패널이 표시됩니다. SIP 트렁크로 되돌아가서 번호 아이콘을 클릭하여 작성한 SIP 트렁크에 번호를 지정하십시오.

  국가 및 지역 코드를 포함하여 이 전화번호는 음성 에이전트를 설정하는 데 필요합니다. [음성 에이전트 작성 및 연결](getting-started.html#step3)을 참조하십시오.

## {{site.data.keyword.iva_short}}과의 피어링
{: #peering}

{{site.data.keyword.iva_short}}에서는 IPSec 터널 등의 피어 연결을 지원합니다. {{site.data.keyword.iva_short}}에 대해 피어링하기 위해 서버 IP 주소의 화이트리스트를 작성할 수 있습니다.

1. _관리_ 대시보드로 이동하여 _인스턴스_ 탭을 선택하십시오.

1. **새 IP 추가** 아이콘을 클릭하여 새 IP 주소의 화이트리스트를 작성하십시오.

1. **IP 닉네임** 및 **IP 주소**를 추가하십시오.

## AT&T 및 기타 제공자와 연결
{: #att-other}

{{site.data.keyword.iva_short}}에서는 AT&T&reg; 및 기타 SIP 트렁크 제공자와 연결할 수 있도록 지원합니다. 하지만 이러한 연결은 셀프 서비스 설정이 아니며 추가 지원이 필요합니다. [지원되는 설정 요청](#request-setup)을 참조하십시오.

## 지원되는 설정 요청
{: #request-setup}

다음 프로세스를 사용하여 AT&T 또는 기타 SIP 트렁크 제공자와 연결하거나 {{site.data.keyword.iva_short}}과 피어링하거나 50개가 넘는 동시 연결을 요청할 수 있도록 지원되는 네트워크 설정을 요청할 수 있습니다.

1. 새 [{{site.data.keyword.Bluemix_notm}} 지원 티켓](https://cloud.ibm.com/unifiedsupport/tickets/add)을 여십시오.

1. **티켓 유형**에 대해 **기술적**을 선택하십시오.

1. **자원 컨텍스트 선택**에 대해 **Cloud Foundry**를 선택하십시오.

1. **기술적 지원 영역**에서 **애플리케이션 서비스**를 선택하십시오.

1. {{site.data.keyword.iva_short}} 인스턴스에 대해 **지역**, **조직** 및 **영역**을 선택하십시오.

1. **연관된 리소스**에 대해 {{site.data.keyword.iva_short}} 서비스 인스턴스를 선택하십시오.

1. **심각도**에 대해 **심각도 4 - 최소 영향**을 선택하십시오.

1. **주제**에 대해 `{{site.data.keyword.iva_short}} 지원되는 네트워크 설정`을 입력하십시오.

1. **간략한 설명** 섹션에서 {{site.data.keyword.iva_short}} 서비스에 연결하거나 음성 에이전트에 대한 50개가 넘는 동시 연결을 요청하는 방법을 설명하십시오. _표준_ 또는 _프리미엄_ 플랜을 보유한 사용자는 피어 연결을 사용할 수 있습니다. _표준_ 또는 _프리미엄_ 플랜에서 _Lite_ 플랜으로 인스턴스를 전환하거나 인스턴스를 삭제하는 경우에는 피어 연결이 사용 안함으로 설정됩니다.

  SIP 트렁크 제공자 또는 피어 연결(예: IPSec 터널)을 사용하여 연결할 수 있습니다. 티켓에서 PDF 또는 이미지 형식으로 네트워크 토폴로지를 설명하는 네트워크 다이어그램을 첨부할 수 있습니다. 원하는 서비스 기능을 자세히 설명하는 백서를 첨부할 수도 있습니다.

  **간략한 설명**에 다음 정보를 포함시키십시오.
  * 회사 이름
  * {{site.data.keyword.Bluemix_notm}} 계정 ID
  * {{site.data.keyword.iva_short}} 서비스 대시보드 URL
  * 유스 케이스
  * IP 주소 또는 SIP 트렁크 제공자 정보를 포함하는 네트워크 다이어그램
