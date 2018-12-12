---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-16"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 서드파티 음성 및 텍스트 서비스와 연결
{: #third-party}

_관리_ 대시보드에서 음성 에이전트를 작성, 복제 또는 편집할 때 서드파티 음성 및 텍스트 서비스에 연결할 수 있습니다.
{: shortdesc}

또는 작동 중에 음성 및 텍스트 서비스 연결을 구성하려면 [{{site.data.keyword.conversationshort}}에 동적 구성을 사용](api_dynamic_config.html)할 수 있습니다. 이를 통해 조치 태그와 상태 변수를 사용하여 음성 에이전트 구성을 변경할 수 있습니다.

## {{site.data.keyword.iva_short}}에서 Google Speech-to-Text에 연결
{: #stt_va}

{{site.data.keyword.speechtotextfull}} 인스턴스를 사용하는 대신 음성 에이전트를 서드파티 음성-문자 변환 서비스(예: [Google Cloud Speech-to-Text ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.google.com/speech-to-text/))에 연결하도록 선택할 수 있습니다.

1. _관리_ 대시보드의 _음성 에이전트_ 탭으로 이동하여 기존 음성 에이전트 **편집** 또는 **새 음성 에이전트 작성**을 선택하십시오.

1. _Speech to Text_ 서비스 구성에서 **Google Speech to Text 서비스 인스턴스**를 선택하십시오.

1. 서비스 인스턴스에 대한 **언어**를 선택하십시오.

1. Google Cloud Speech-to-Text 서비스 인증 정보를 입력하십시오.
  * [서비스 계정을 설정할 때 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account) Google Cloud Platform에서 서비스 인증 정보를 JSON 키로 생성할 수 있습니다. 다음 코드 예제에는 Google Cloud Platform에서 생성하는 샘플 인증 정보 필드가 포함되어 있습니다.

    ```json
    {
      "type": "",
      "auth_uri": "",
      "client_id": "",
      "token_uri": "",
      "project_id": "",
      "private_key": "",
      "client_email": "",
      "private_key_id": "",
      "client_x509_cert_url": "",
      "auth_provider_x509_cert_url": ""
    }
    ```
    {: codeblock}

1. **선택사항** 올바른 JSON 형식으로 Google에서 정의된 특수 구성 설정을 입력하려면 **고급 표시**를 선택하십시오.
  다음 예는 영어(미국) 인스턴스에 대한 비속어 필터를 사용으로 설정하는 Google 구성 설정을 보여줍니다.
  ```json
  {
    "languageCode": "en-US",
    "profanityFilter": false
  }
  ```
  {: codeblock}

  `languageCode`에서 정의한 언어와 다른 서비스 구성의 언어를 선택하면 {{site.data.keyword.iva_short}}에서 사용자 선택사항을 `languageCode` JSON 구성에 정의된 언어로 겹쳐씁니다.
  {: tip}

## {{site.data.keyword.iva_short}}에서 Google Text-to-Speech에 연결
{: #tts_va}

{{site.data.keyword.texttospeechfull}} 인스턴스를 사용하는 대신에 음성 에이전트를 서드파티 음성-문자 변환 서비스(예: [Google Cloud Text-to-Speech ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.google.com/text-to-speech/))에 연결하도록 선택할 수 있습니다.

1. _관리_ 대시보드의 _음성 에이전트_ 탭으로 이동하여 기존 음성 에이전트 **편집** 또는 **새 음성 에이전트 작성**을 선택하십시오.

1. _Text to Speech_ 서비스 구성에서 **Google Text to Speech 서비스 인스턴스**를 선택하십시오.

1. 서비스 인스턴스에 대한 **언어** 및 **음성**을 선택하십시오.

1. Google Cloud Text-to-Speech 서비스 인증 정보를 입력하십시오.
  * [서비스 계정을 설정할 때 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account) Google Cloud Platform에서 서비스 인증 정보를 JSON 키로 생성할 수 있습니다. 다음 코드 예제에는 Google Cloud Platform에서 생성하는 샘플 인증 정보 필드가 포함되어 있습니다.

    ```json
    {
      "type": "",
      "auth_uri": "",
      "client_id": "",
      "token_uri": "",
      "project_id": "",
      "private_key": "",
      "client_email": "",
      "private_key_id": "",
      "client_x509_cert_url": "",
      "auth_provider_x509_cert_url": ""
    }
    ```
    {: codeblock}

1. **선택사항** 올바른 JSON 형식으로 Google에서 정의된 특수 구성 설정을 입력하려면 **고급 표시**를 선택하십시오.
  다음 예는 독일어로 말하는 여성 음성에 대한 Google 구성 설정을 보여줍니다.

  `languageCode`에서 정의한 언어와 다른 서비스 구성의 언어를 선택하면 {{site.data.keyword.iva_short}}에서 사용자 선택사항을 `languageCode` JSON 구성에 정의된 언어로 겹쳐씁니다.
  {: tip}

  ```json
  {
  "config": {
    "audioConfig": {
      "speakingRate": 1.3
    },
    "voiceConfig": {
      "ssmGender": "FEMALE",
      "languageCode": "de-DE"
    }
  }
  }
  ```
  {: codeblock}
