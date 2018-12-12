---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 서비스 오케스트레이션 엔진을 사용하여 {{site.data.keyword.conversationshort}} 구성
{: #conversation_va}

{{site.data.keyword.conversationshort}} 서비스 인스턴스를 구성하는 대신 서비스 오케스트레이션 엔진(SOE)에 연결할 수 있습니다.
{: shortdesc}

[서비스 오케스트레이션 엔진(SOE)](about.html#arch-soe)을 통해 {{site.data.keyword.conversationshort}} 작업공간에 연결할 수 있습니다. SOE는 서드파티 API를 사용하여 수정할 수 있도록 서비스로 보내고 받는 메시지를 인터셉트합니다.

## SOE에 대한 연결 구성
{: #how-to}

1. 음성 에이전트에 대한 _관리_ 페이지의 _음성 에이전트_ 탭에서 {{site.data.keyword.conversationshort}} 구성 섹션으로 이동하십시오.

1. **서비스 오케스트레이션 엔진**을 **서비스 유형**으로 선택하십시오.

1. **지역**을 **서비스 유형**으로 선택하십시오.

1. **URL** 필드에 SOE 작업공간의 전체 URL(예: `https://iva-soesample.myorg.net/SOE/myWorkspace`)을 입력하십시오.

  **중요**: 데이터 보안을 위해 `http:` 대신 `https:`를 사용하여 SOE 작업공간에 보안 URL을 사용해야 하고 인증을 요구해야 합니다. 보안 고려사항에 대해 자세히 보려면 [정보 보안 및 데이터 개인정보 보호](infosec.html)를 참조하십시오.

1. **선택사항** SOE에 인증이 필요한 경우(권장됨) 사용자 이름과 비밀번호를 각 필드에 입력하십시오.
