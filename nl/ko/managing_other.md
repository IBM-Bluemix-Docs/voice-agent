---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 다른 {{site.data.keyword.Bluemix_notm}} 작업공간에서 서비스 인스턴스 사용
{: #other_service}

다른 {{site.data.keyword.Bluemix_short}} 계정의 작업공간에 속해 있는 {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 또는 {{site.data.keyword.speechtotextshort}} 서비스 인스턴스를 사용하도록 음성 에이전트를 구성할 수 있습니다.
{: shortdesc}

음성 에이전트를 기타 서비스 인스턴스에 연결하려면 서비스 인스턴스에 대한 API 키 또는 사용자 이름과 비밀번호 인증 정보를 사용할 수 있습니다.

1. _관리_ 대시보드의 _음성 에이전트_ 탭에서 **새 음성 에이전트 작성** 또는 편집할 음성 에이전트를 선택하십시오.

1. {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 또는 {{site.data.keyword.speechtotextshort}}에서 **기타 서비스 인스턴스**를 **서비스 유형**으로 선택한 후 **지역**을 선택하십시오.

1. **사용자 이름 및 비밀번호** 또는 **API 키**를 선택하고 서비스 인증 정보를 입력하십시오.
  이러한 값을 찾으려면 구성할 서비스 인스턴스로 이동하여 **서비스 인증 정보**를 선택한 후 **인증 정보 보기**를 선택하십시오.

  * **사용자 이름 및 비밀번호**: **URL**, **사용자 이름** 및 **비밀번호** 필드에서 {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 또는 {{site.data.keyword.texttospeechshort}} 서비스 인스턴스에 대한 인증 정보를 구성하십시오.
  * **API 키**: **URL** 및 **API 키** 필드에서 {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 또는 {{site.data.keyword.texttospeechshort}} 서비스 인스턴스에 대한 인증 정보를 구성하십시오.

  인증 정보는 {{site.data.keyword.Bluemix_notm}} 사용자 이름 및 비밀번호가 아니라 특정 서비스 인스턴스에 대한 암호화된 인증 정보입니다.
  {:tip}

1. 서비스 인스턴스 정보를 입력하십시오.

  * **{{site.data.keyword.conversationshort}}:** **작업공간 ID** 필드에 음성 에이전트와 함께 사용할 작업공간의 ID를 입력하십시오. 작업공간 ID를 찾으려면 도구를 실행하고 통합할 작업공간에서 조치 아이콘(**&vellip;**)을 클릭하고 **세부사항 보기**를 선택하십시오.
  * **{{site.data.keyword.speechtotextshort}}:** **모델 유형 선택**에서 **협대역**, **광대역** 또는 **협대역 및 광대역 모두**를 선택한 후 언어 **모델**을 선택하십시오.
  * **{{site.data.keyword.texttospeechshort}}:** **음성** 필드에서 서비스가 사용하는 언어 및 음성을 선택하십시오.  서비스에 대한 음성을 지정해야 합니다.

**중요:** 음성 에이전트가 작동하려면 {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} 및 {{site.data.keyword.texttospeechshort}}를 동일한 언어로 구성해야 합니다. [지원되는 언어](about.html#supported-languages)를 참조하십시오.
