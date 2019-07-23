---

copyright:
  years: 2019
lastupdated: "2019-06-21"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# SMS 제공자에 연결
{: #connect-sms}

다음 목록에서 {{site.data.keyword.iva_full}}과의 통합에 사용할 SMS 제공자를 선택할 수 있습니다.
{: #shortdesc}

* [Twilio](#twilio-setup)

## API 키 생성 및 인증 정보 설정
{: #sms_access}

사용자 계정에서 이미 활성인 역할에 대해서만 인증 정보를 작성할 수 있습니다. SMS 및 Voice + SMS 에이전트의 경우, *작성자* 또는 *관리자* 역할이 지정되어 있어야 합니다. [9단계. 사용자 초대 및 초기 액세스 지정](/docs/services/voice-agent?topic=voice-agent-iam#step1)을 참조하십시오.

1. {{site.data.keyword.iva_short}} 인스턴스의 *대시보드*에서 **새 인증 정보(+)**를 클릭하십시오. 
2. 새 대화 상자가 팝업되면 **이름**을 입력하고, **역할** 드롭 다운 메뉴 아래에서 *작성자* 또는 *관리자*. 
    - **참고:** SMS 관련 기능의 경우, *작성자* 또는 *관리자* 역할 중 하나를 선택**_해야_** 합니다. 
3. **추가**를 클릭하십시오.
4. 새로 작성된 인증 정보 옆에 있는 **인증 정보 보기**를 클릭하십시오. [SMS에 대한 Twilio 구성](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup)에 사용할 JSON 스크립트에서 `APIKEY`의 값을 기록해 두십시오.

## SMS에 대한 Twilio 구성 
{: #twilio-setup}

1. [여기](https://www.twilio.com/console/phone-numbers/)에서 찾은 Twilio 전화번호에 액세스하고, _SMS_ 또는 _Voice + SMS_ 에이전트에 지정된 전화번호를 선택하십시오.  

1. **메시징** 섹션으로 스크롤을 내리십시오. _CONFIGURE WITH_ 필드에서 드롭 다운 메뉴에서 **웹훅, TwiML Bins, Functions, Studio 또는 프록시**를 선택하십시오.

1. _A MESSAGE COMES IN_ 필드의 드롭 다운 메뉴에서 **웹훅**을 선택하십시오.

1. **웹훅** 옆에 있는 빈 URL 필드에서 에이전트의 지역을 기반으로 지시사항을 따르십시오.  

    - 작성한 에이전트가 워싱턴 지역을 기반으로 하는 경우 필드에 `https://apikey:YOUR_API_KEY@sms-east.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv`를 쓰십시오. 
    - 작성한 에이전트가 댈러스 지역을 기반으로 하는 경우 필드에 `https://apikey:YOUR_API_KEY@sms-south.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv`를 쓰십시오. 
    - 앞의 URL에 있는 `YOUR_API_KEY`를 이전에 작성한 인증 정보에서 `APIKEY`로 바꾸십시오. [API 키 생성 및 인증 정보 설정](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_access)을 참조하십시오. 

1. **저장**을 클릭하십시오. 
