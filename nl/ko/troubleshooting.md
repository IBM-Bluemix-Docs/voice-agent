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

# 문제점 해결 및 지원
{: #troubleshooting}

{{site.data.keyword.iva_full}}에 문제가 있습니까? 일반적인 문제점에 대한 문제점 해결 팁을 검토하고 질문이 있는 경우 커뮤니티에 문의하십시오.
{: shortdesc}

## {{site.data.keyword.iva_short}} 문제점 해결 방법
{: #how-to}

음성 에이전트의 문제점을 해결하기 위해 로깅, 사용 및 이벤트 전달을 사용하여 오류 및 장애 레코드를 찾을 수 있습니다. 이러한 레코드를 사용하면 음성 에이전트의 문제점을 진단하고 해결할 수 있습니다. {{site.data.keyword.iva_short}}에 문제점이 있는 경우 다음 단계를 시도하십시오.

1. 호출에 실패하면 최종 {{site.data.keyword.conversationshort}} 턴에서 실패에 대해 설명합니다.

1. 사용 로그는 특정 호출 중에 발생했을 수 있는 오류를 표시합니다. [사용 및 호출 로그 보기](logging.html)를 참조하십시오.

1. 서비스 제공자 로그에서 신호 오류를 확인하십시오. 예를 들어, Twilio는 호스팅하는 각 SIP 트렁크에 대해 로그를 제공합니다.

1. [음성 에이전트에 이벤트 전달을 사용](event-forwarding.html)하여 CDR(Call Detail Records)을 Cloudant 데이터베이스로 전달하도록 음성 에이전트를 구성한 다음 호출 실패 이유를 판별할 수 있습니다. {{site.data.keyword.conversationshort}} 턴 이벤트와 같은 기타 이벤트는 호출 내 모든 대화 턴에 대한 세부사항을 제공할 수 있습니다.

**중요:** CDR, 기록 및 변환 이벤트에는 잠재적으로 PHI(Protected Health Information), PII(Personally Identifiable Information) 또는 PCI DSS(Data Security Standard) 데이터가 있을 수 있는 사용자의 정보가 포함되어 있습니다. 개인 정보가 노출되지 않도록 하려면 사용자가 대화에서 또는 대화 중에 공유하는 기밀 정보를 {{site.data.keyword.cloudant_short_notm}} 인스턴스에서 적절히 보호하도록 해야 합니다. 


## 도움 받기
{: #help}

도움이 필요한 경우 계속해서 모니터되는 다음 위치에 질문이나 댓글을 게시하여 개발자 커뮤니티에 참여하십시오.

* `voice-agent` 태그를 포함하여 [dwAnswers 포럼 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/topics/voice-agent/)에 게시
* `voice-agent` 태그를 포함하여 [StackOverflow ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://stackoverflow.com/questions/tagged/voice-agent){: new_window}에 게시
* [IBM Cloud Technology ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) 팀 Slack의 `#ibmvoicegateway` 채널에서 찾기

**기억**: 호출의 로그 또는 레코드를 게시하기 전에 호출자 및 사용자가 대화 중에 공유한 개인 정보를 모두 제거하십시오.

## 문제점 해결 팁
{: #troubleshooting-tips}

### 내 음성 에이전트에 전화를 걸었을 때 전화로 응답을 받지 못하는 이유는 무엇입니까?

호출이 서비스에 연결되지 않았을 가능성이 있습니다. 이 문제점은 {{site.data.keyword.iva_short}} 서비스 인스턴스가 올바르게 설정되지 않은 경우에 발생합니다. 다음과 같은 음성 에이전트 설정을 확인하십시오.

* 음성 에이전트 _관리_ 대시보드의 전화번호가 SIP 트렁크 제공자(예: NetFoundry 또는 Twilio)의 전화번호와 동일한지 확인하십시오.

   **참고:** 음성 에이전트 _관리_ 대시보드에 전화번호를 지정할 때 국가 및 지역 코드를 포함해야 합니다. 예: `18884253968`.

* Watson 서비스 신임 정보, URL 및 {{site.data.keyword.conversationshort}} 작업공간 ID가 모두 유효한지 확인하십시오.
* {{site.data.keyword.conversationshort}} 작업공간의 대화가 올바르게 작성되었는지 확인하십시오.
  * GitHub에서 사전 빌드된 작업공간에 대한 [샘플 대화 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json)를 가져올 수 있습니다. {{site.data.keyword.conversationshort}} 도구에서 JSON 파일로서 샘플 대화 저장 이후 작업공간으로서 파일 가져오기에 대한 세부사항은 [*시작하기 튜토리얼*의 3단계](getting-started.html#step3)를 참조하십시오. 
  * 자체 {{site.data.keyword.conversationshort}} 대화를 작성한 경우에는 `conversation_start` 조건이 있는 노드와 기본 응답이 있는 노드가 대화에 포함되는지 확인하십시오. 자세한 지시사항은 {{site.data.keyword.conversationshort}} 문서에서 [대화 빌드](../conversation/dialog-build.html)를 참조하십시오.
* 전화 통화가 음성 에이전트 _사용_ 대시보드에 나열되어 있는지 여부를 확인하십시오. 전화 통화에 대한 항목이 표시되면 음성 에이전트가 Watson 서비스에 연결된 것입니다.

### 음성 에이전트를 작성할 때 전화번호를 지정할 수 없는 이유는 무엇입니까?

지정한 전화번호를 기존의 음성 에이전트에서 사용하는지 확인하십시오. 전화번호에는 하나의 음성 에이전트만 있을 수 있습니다. SIP 트렁크 제공자의 다른 전화번호를 프로비저닝하고 이를 사용하여 다른 음성 에이전트를 작성할 수 있습니다. 또는 [_관리_ 대시보드에서 기존 음성 에이전트를 삭제](managing.html#delete_va)하여 전화번호를 해제한 후에 새 음성 에이전트를 작성하십시오. 

### 자주 호출에 실패하는 이유는 무엇입니까?

서비스 오케스트레이션 엔진(SOE)이 장기 트랜잭션을 시작하기 때문에 호출에 실패하는 경우 음성 에이전트에 문제점이 있을 수 있으며 적절한 때에 사용자 음성 에이전트에 응답하지 않습니다. 트랜잭션이 기본 {{site.data.keyword.conversationshort}} 제한시간을 초과하면 호출에 실패합니다. 호출 실패를 방지하기 위해 SOE는 `vgwConversationResponseTimeout` 상태 변수를 사용하여 기본 {{site.data.keyword.conversationshort}} 제한시간을 수정할 수 있습니다. [{{site.data.keyword.conversationshort}} 대화 상자에 설정된 변수](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html#variables-conv)를 참조하십시오.
