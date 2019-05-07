---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-08"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# API의 조치 태그 및 상태 변수
{: #api-reference}

참조 자료를 사용하여 음성 에이전트가 대화 세션 중에 수행하는 조치를 시작하는 조치 태그를 찾거나 별도로 변경되지 않는 한 대화 전체에서 지속되는 음성 에이전트 특성을 정의하는 상태 변수를 찾으십시오.
{: shortdesc}

상태를 설정하고 조치 순서를 시작하는 방법의 예제와 코드 예제는 [API를 사용한 음성 에이전트 프로그래밍](/docs/services/voice-agent?topic=voice-agent-api)을 참조하십시오.

{{site.data.keyword.iva_full}}은 IBM Voice Gateway를 기반으로 하므로 API가 동일한 방식으로 작동합니다. Voice Gateway에 익숙한 경우 {{site.data.keyword.conversationshort}} 대화에서 {{site.data.keyword.iva_short}}과 동일한 조치 및 상태 변수를 사용할 수 있습니다. [Voice Gateway API의 조치 태그 및 상태 변수](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html)를 참조하십시오.
{: tip}

## 조치 명령 및 속성
{: #actions-and-attributes}

다음 표에는 {{site.data.keyword.conversationshort}} 대화에서 지정할 수 있는 조치와 각 조치에 대해 정의할 수 있는 속성이 나열되어 있습니다.

|조치 명령 |설명 |속성 |
| ----- | ----- | ----- |
|`vgwActPlayText`|{{site.data.keyword.texttospeechshort}} 서비스를 통해 음성으로 변환된 발화를 재생합니다. | <ul><li>`text`: 재생할 발화 목록입니다. 선택사항. <p>예: <br/><code>"text": [<br/>&nbsp;&nbsp;&nbsp;"Hello. How can I help you today?"<br/>&nbsp;&nbsp;&nbsp;]</code><p> 기본적으로, 조치는 `output.text` 필드에서 구성된 발화의 목록을 재생합니다. </li><li>`errAudioURL`: 음성 에이전트가 {{site.data.keyword.texttospeechshort}} 서비스에 연결하여 조치를 완료할 없는 경우 재생되는 오디오 파일의 URL입니다. 오디오 파일은 WAV 형식이어야 합니다.</li></ul>|
|`vgwActPlayUrl` |포함된 텍스트가 재생된 직후 오디오 파일을 재생합니다(예: 공통 일회성 발화 또는 대기 중 음악(MOH) 재생). 텍스트가 포함되지 않은 경우 오디오가 즉시 재생됩니다. 파일은 PCM으로 인코딩된 단일 채널(모노) 파일이어야 하며 샘플당 16비트의 샘플링 주기가 8,000Hz여야 합니다. | <ul><li>`url`: 재생할 URL입니다. 필수.</li><li> `playURLInLoop`: 선택적으로 `Yes` 또는 `No`로 설정하여 루프로 URL을 재생할지 여부를 표시하십시오. 기본값은 `No`입니다.</li></ul> |
|`vgwActHangup` |전화를 끊습니다. |속성이 없습니다. |
|`vgwActSetSTTConfig` |음성 에이전트가 Watson {{site.data.keyword.speechtotextshort}} 서비스에 전달할 매개변수 세트를 적용합니다. {{site.data.keyword.conversationshort}} 서비스가 호출에 따라 동적으로 매개변수를 정의합니다. |속성은 JSON 특성으로 {{site.data.keyword.speechtotextshort}} 서비스에 투명하게 전달됩니다. |
|`vgwActSetTTSConfig` |음성 에이전트가 Watson {{site.data.keyword.texttospeechshort}} 서비스에 전달할 매개변수 세트를 적용합니다. {{site.data.keyword.conversationshort}} 서비스가 호출에 따라 동적으로 매개변수를 정의합니다. |속성은 JSON 특성으로 {{site.data.keyword.texttospeechshort}} 서비스에 투명하게 전달됩니다.  |
|`vgwActSetConversationConfig` |음성 에이전트가 {{site.data.keyword.conversationshort}} 작업공간을 정의하기 위한 매개변수 세트를 정의합니다. {{site.data.keyword.conversationshort}} 서비스가 호출에 따라 동적으로 매개변수를 정의합니다. | <ul><li>`url`: {{site.data.keyword.conversationshort}} 서비스 API에 대한 `url` 인증 정보입니다.</li><li>`workspaceID`: {{site.data.keyword.conversationshort}} workspace ID</li><li>`username`: {{site.data.keyword.conversationshort}} 서비스에 대한 `username` 인증 정보(최대 64자)입니다. </li><li>`password`: {{site.data.keyword.conversationshort}} 서비스에 대한 `password` 인증 정보(최대 256자)입니다. </li></ul> |
|`vgwActCollectDtmf` |음성 에이전트에 DTMF(Dual-Tone Multi-Frequency) 신호 입력을 수집하도록 지시합니다. |다음 속성 중 하나가 정의되어야 합니다. <ul><li> `dtmfTermKey`: DTMF 입력 종료 신호를 보내는 DTMF 종료 키입니다 (예: "`#`"). </li><li> `dtmfCount`: 수집할 DTMF 숫자 수입니다.</li></ul> 이러한 조건 중 하나가 충족되면 음성 에이전트가 DTMF 입력 수집을 중지합니다. |
|`vgwActPauseDTMF` |DTMF 입력을 사용 안함으로 설정합니다. `vgwActUnPauseDTMF` 조치에 의해 다시 사용으로 설정될 때까지 모든 DTMF 입력은 무시됩니다. |속성이 없습니다. |
|`vgwActUnPauseDTMF` |`vgwActPauseDTMF` 조치에 의해 사용 안함으로 설정된 DTMF 입력을 사용으로 설정합니다. |속성이 없습니다. |
|`vgwActExcludeFromTTSCache` |음성 에이전트에 {{site.data.keyword.texttospeechshort}} 서비스의 응답을 캐시하지 않도록 지시합니다. 예를 들어, 민감한 PHI, PII 및 PCI DSS 데이터 또는 고객 이름이나 생일과 같은 동적 정보가 포함된 응답은 제외되어야 합니다. <br/>이 조치 태그는 캐시하지 않으려는 각 발화에 대해 {{site.data.keyword.conversationshort}} 대화 노드에서 설정되어야 합니다. |속성이 없습니다. |
|`vgwActPauseSTT` |`vgwActUnPauseSTT` 조치로 다시 사용으로 설정될 때까지 음성-문자 변환 처리를 일시정지합니다. 레코딩이 사용으로 설정되고 음성-문자 변환 처리가 일시정지되면 호출자의 오디오가 캡처되지 않습니다. |속성이 없습니다. |
|`vgwActUnPauseSTT` |이전에 `vgwActPauseSTT` 조치로 일시정지된 음성-문자 변환 처리를 재개합니다. |속성이 없습니다. |
|`vgwActEnableSpeechBargeIn` |호출자가 음성을 통해 음성 에이전트의 재생을 인터럽트할 수 있도록 음성 끼어들기를 사용으로 설정합니다. |속성이 없습니다. |
|`vgwActDisableSpeechBargeIn` |호출자가 말할 때 음성 에이전트의 재생이 인터럽트되지 않도록 음성 끼어들기를 사용 안함으로 설정합니다. |속성이 없습니다. |
|`vgwActEnableDTMFBargeIn`|호출자가 키를 눌러 음성 에이전트의 재생을 인터럽트할 수 있도록 DTMF 끼어들기를 사용으로 설정합니다. |속성이 없습니다. |
|`vgwActDisableDTMFBargeIn` |호출자가 키를 누를 때 음성 에이전트의 재생이 인터럽트되지 않도록 음성 끼어들기를 사용 안함으로 설정합니다. |속성이 없습니다. |
|`vgwActForceNoInputTurn` |호출자의 입력을 대기하지 않고 강제로 대화를 새로 시작합니다. |속성이 없습니다. |
{: caption="표 1. {{site.data.keyword.conversationshort}} 서비스에서 시작할 수 있는 조치" caption-side="top"}

## {{site.data.keyword.conversationshort}} 대화에서 설정되는 상태 변수
{: #state-variables-conv}

{{site.data.keyword.conversationshort}} 대화 내에서 다음과 같은 상태 변수를 설정하여 음성 에이전트의 동작을 수정할 수 있습니다.

|상태 변수 이름 |예상 값 |설명 |
| -------------- | ------ | ----------- |
|`vgwByeCustomHeader` |사용자 정의 |발신 SIP BYE 메시지의 사용자 정의 헤더를 정의합니다. 사용자 정의 헤더 값은 `vgwByeCustomHeaderVal` 상태 변수에서 정의됩니다.  |
|`vgwByeCustomHeaderVal` |사용자 정의 |발신 SIP BYE 메시지의 사용자 정의 헤더 값을 정의합니다. 사용자 정의 헤더는 `vgwByeCustomHeader` 상태 변수에서 정의됩니다. |
|`vgwPostResponseTimeoutCount` |시간(밀리초) |응답이 호출자에게 재생된 후 새 발화를 대기하는 시간입니다. 이 값이 초과되는 경우 {{site.data.keyword.conversationshort}}는 제한시간 초과가 발생했음을 나타내는 "vgwPostResponseTimeout"이라는 텍스트 업데이트를 수신합니다.|
|`vgwConversationFailedMessage` |텍스트 문자열 |{{site.data.keyword.conversationshort}} 서비스가 실패하는 경우 호출자에게 스트리밍되는 메시지입니다. 첫 번째 대화에서 이 변수를 설정하도록 {{site.data.keyword.conversationshort}} 대화를 구성하십시오. |
|`vgwSessionInactivityTimeout` | 시간(분) <br/><br/>기본값: `2` |비활동 제한시간 간격입니다. 제한시간 간격 값은 음성 에이전트가 세션이 비활성 상태에 있도록 허용하는 기간(분)을 지정합니다. 제한시간이 만료되면 음성 에이전트가 세션을 종료합니다. |
|`vgwErrAudioURL` |사용자 정의 |음성 에이전트가 응답을 재생하려고 시도할 때 {{site.data.keyword.texttospeechshort}} 서비스에 연결할 수 없는 경우 재생되는 오디오 파일의 URL입니다. 오디오 파일은 WAV 형식이어야 합니다. |
{: caption="표 2. {{site.data.keyword.conversationshort}} 서비스에서 설정되는 변수" caption-side="top"}

## 음성 에이전트에서 설정되는 변수
{: #state-variables-iva}

|상태 변수 이름 |예상 값 |설명 |
| -------------- | ----- | ----------- |
|`vgwSessionID`   | 사용자 정의 <br/><br/> 기본값: `Call-ID` | SIP INVITE 요청에서 가져온 사용자 정의 세션 ID 헤더입니다. 이 값은 세션과 관련된 모든 음성 에이전트 감사 로그에서 사용되는 글로벌 세션 ID를 나타냅니다. |
|`vgwSIPCallID` |SIP `Call-ID` |호출과 연관된 SIP 호출 ID입니다. |
|`vgwSIPRequestURI` |SIP `Request-URI` |호출을 시작한 SIP 요청 URI입니다. |
|`vgwSIPToURI` |SIP `To` URI |호출과 연관된 SIP `To` URI입니다. |
|`vgwSIPFromURI` |SIP `From` URI |호출과 연관된 SIP `From` URI입니다. |
|`vgwBargeInOccurred` |`Yes`/`No` |끼어들기가 발생했는지 여부를 표시합니다. |
|`vgwHangUp` |`Yes`/`No` |대화가 종료되었음을 표시합니다. |
|`vgwHangupReason` |문자열 |호출자에 의해 또는 오류 때문에 끊김이 시작되는 경우에는 호출의 연결이 끊어진 이유를 표시하기 위해 이 변수가 {{site.data.keyword.conversationshort}} 서비스로 전송됩니다. 또한 {{site.data.keyword.conversationshort}} 서비스에 전송되는 메시지 요청의 텍스트에 "vgwHangUp"이 포함됩니다. |
|`vgwConversationResponseTimeout` | 시간(초) <br/><br/>기본값: `5`  |음성 에이전트가 {{site.data.keyword.conversationshort}} 서비스의 응답을 대기하는 시간(초)입니다. 이 시간이 초과되면 음성 에이전트가 {{site.data.keyword.conversationshort}} 서비스에 연결하려고 재시도합니다. 여전히 서비스에 연결할 수 없는 경우 호출이 실패합니다. |
|`vgwSTTResponse` |JSON 오브젝트 | 선호되는 가설과 대안에 대한 기록 및 신뢰도 점수를 포함한 JSON 형식으로 된 {{site.data.keyword.speechtotextshort}} 서비스의 최종 응답입니다. <p>예를 들어, 다음 형식은 {{site.data.keyword.speechtotextshort}} 서비스에서 수신된 형식과 정확하게 일치합니다.</p><p><code>{<br/>&nbsp;&nbsp;"result_index": 0,<br/>&nbsp;&nbsp;"warnings": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;"Unknown arguments: continuous."<br/>&nbsp;&nbsp;],<br/>&nbsp;&nbsp;"results": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"final": true,<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"alternatives": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello world",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.758<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello wooled",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.358<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;]<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}.</code></p> |
|`vgwIsDTMF` |`Yes`/`No` |{{site.data.keyword.conversationshort}} 서비스에 대한 입력이 DTMF(Dual-Tone Multi-Frequency) 신호인지 여부를 표시합니다. |
{: caption="표 3. 음성 에이전트에서 설정되는 변수" caption-side="top"}
