---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 시작하기 튜토리얼
{{site.data.keyword.iva_full}}은 SIP(Session Initiation Protocol) 프로토콜을 사용하여 조정된 Watson 서비스 세트를 전화 네트워크와 통합하는 데 도움을 줍니다. 이 튜토리얼에서는 전화에서 호출하는 코그너티브 음성 에이전트를 설정하는 방법에 대해 설명합니다.
{: shortdesc}

이 [{{site.data.keyword.iva_full_notm}} 튜토리얼 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/)에서 첫 번째 음성 에이전트를 작성하는 방법에 대한 데모를 보십시오.
{: tip}

## 시작하기 전에
{: #prereqs}

새 계정을 작성하거나 [{{site.data.keyword.Bluemix_short}}](https://console.bluemix.net/)의 기존 계정에 로그인하십시오.

## 1단계: {{site.data.keyword.Bluemix_notm}}에서 {{site.data.keyword.iva_short}} 서비스 인스턴스 작성
{: #step1}

[{{site.data.keyword.iva_short}} 카탈로그 페이지](https://console.bluemix.net/catalog/services/voice-agent-with-watson)에서 서비스 정보를 검토한 후 **작성**을 클릭하십시오.

서비스를 작성한 후 _시작하기_ 대시보드의 음성 에이전트 엔드포인트를 기록하십시오. SIP 트렁크를 구성하려면 엔드포인트 SIP URI가 필요합니다.

## 2단계: SIP 트렁크를 작성하여 {{site.data.keyword.iva_short}}에 호출 전달
{: #step2}

1. 다음의 지원되는 제공자 중에서 SIP 트렁크를 작성하십시오. 그리고 전화번호를 SIP 트렁크와 연관시키십시오. 

  * [NetFoundry](connect-SIP.html#NetFoundry-setup)
  * [Twilio](connect-SIP.html#twilio-setup)
  * [AT&T 및 기타 SIP 트렁크 제공자](connect-SIP.html#att-other)
  * [{{site.data.keyword.iva_short}}과의 피어링](connect-SIP.html#peering)

## 3단계: 음성 에이전트 작성 및 연결 
{: #step3}

1. {{site.data.keyword.iva_short}} 대시보드의 _관리_ 대시보드로 이동하여 **음성 에이전트 작성**을 클릭하십시오.

2. 음성 에이전트에 대한 기본 설정을 입력하십시오.
  * **이름:** 음성 에이전트의 고유 이름(예: `Customer Support`)
  * **전화번호:** SIP 트렁크와 연관된 전체 전화번호(국가 및 지역 코드 포함). 예를 들어, 미국 800 번호의 경우 전화번호를 18883334444로 지정하십시오. 전화번호에는 공백 및 + ( ) - 문자가 포함될 수 있습니다.
  * **설명:** 음성 에이전트 사용에 대한 선택적 설명

3. 음성 에이전트에 대한 {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 및 {{site.data.keyword.texttospeechshort}} 서비스 인스턴스를 작성하십시오. 다음 방법 중 하나를 사용하여 음성 에이전트를 작성하도록 선택할 수 있습니다.
  * **음성 에이전트 작성**을 클릭하여 하나의 단계로 기본 구성을 사용하여 모든 서비스 및 음성 에이전트를 작성하십시오.
  * 또는 각 서비스 이름을 클릭하여 서비스를 직접 작성하십시오. 그런 다음 {{site.data.keyword.iva_short}}로 돌아가서 음성 에이전트를 별도로 작성하십시오.

   수동으로 {{site.data.keyword.conversationshort}} 서비스 인스턴스를 작성한 경우 음성 에이전트를 테스트할 수 있도록 대화를 추가하십시오. 빠르게 시작하려면 GitHub에서 [샘플 대화 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json)를 복제한 후 [샘플을 작업공간으로 가져오십시오](../conversation/configure-workspace.html#creating-workspaces).

   1. 동일한 대화 GitHub 페이지에서 행 번호 `1`을 클릭하고 **... > 행 복사**를 선택하십시오. 복사된 텍스트를 파일에 붙여넣고 JSON 파일(예: `voice-gateway-conversation-en.json`)로 저장하십시오.
   2. {{site.data.keyword.conversationshort}} 도구를 실행하십시오. _작업공간_ 페이지에서 ![작업공간 가져오기](../conversation/images/workspace_import.png) 아이콘을 클릭하고 JSON 파일을 가져오십시오. 

  또는 프로덕션 환경을 시뮬레이션하기 위한 [고유한 대화를 빌드](https://console.bluemix.net/docs/services/conversation/dialog-build.html)할 수 있습니다. 최소한 `conversation_start` 조건이 있는 노드와 기본 응답이 있는 노드가 대화에 포함되어야 합니다.

## 다음 단계
{: #next}

연관된 전화번호로 전화를 걸어서 음성 에이전트를 테스트하십시오. 응답이 들리면 음성 에이전트가 활성화된 것입니다.

응답이 들리지 않는 경우 _사용_ 대시보드에서 호출 로그와 음성 에이전트 사용을 검사할 수 있습니다. [사용 및 호출 로그 보기](logging.html)를 참조하십시오.

_관리_ 대시보드에서 음성 에이전트에 대한 설정을 편집하고 음성 에이전트를 작성 또는 제거하며 다중 Watson 서비스 위치를 음성 에이전트에 추가할 수 있습니다. 자세한 정보는 [음성 에이전트 관리](managing.html)를 참조하십시오.

또한 Twilio 계정에서 SIP 연결 보호 등의 고급 설정을 구성할 수도 있습니다. [연결 보호](secure-trunking.html)를 참조하십시오. 
