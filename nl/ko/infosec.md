---

copyright:
  years: 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 정보 보안 및 데이터 개인정보 보호
{: #infosec}

IBM은 고객과 파트너에게 혁신적인 데이터 개인정보 보호, 보안 및 통제 솔루션을 제공하기 위해 노력하고 있습니다.
{: shortdesc}

## 정보 처리 및 구성 옵션
{: #configure_infosec}

서비스를 조작하고 사용자 경험을 최적화하기 위해 {{site.data.keyword.iva_short}}에서는 [DPA(Data Processing Addendum)](https://www.ibm.com/support/customer/csol/terms/){: new_window} 및 [DPA Exhibit](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=00C4CE004FA711E7AA10752A2F494A7C){: new_window}과 함께 처리되는 최소한의 개인 정보(PI) 세트를 수집하고 저장합니다. {{site.data.keyword.iva_short}}의 경우 음성 또는 SMS 대화의 일부인 데이터를 저장, 수집 또는 처리하지 않습니다. 대신 데이터는 처리를 위해 다른 서비스로 라우팅됩니다. 대화 중에 사용자는 PHI(Protected Health Information), PII(Personally Identifiable Information) 또는 PCI DSS(Data Security Standard) 데이터가 포함된 정보를 공유할 수 있습니다. {{site.data.keyword.iva_short}}의 대화 플로우 및 아키텍처에 대해 자세히 보려면 [아키텍처](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}를 참조하십시오.

데이터 개인정보 보호 및 보안 처리를 지원하도록 음성 에이전트 인스턴스를 구성하는 경우 다음 기능을 고려하십시오.

### 호출 전송
{:  #calltransfer_infosec}

음성 에이전트에 호출 전송 기능을 추가하는 경우, 전송 대상 SIP URI를 구성할 때 전화번호를 제공합니다. 사용자는 이 전송 대상에 개인 전화번호를 제공하지 않아야 합니다.

호출 전송을 위한 SIP URI 및 SIP 트렁크 구성에 대해 알아보려면 [호출 전송 설정](/docs/services/voice-agent?topic=voice-agent-call-transfer)을 참조하십시오.

### 이벤트 전달
{: #infosec_event_forwarding}

{{site.data.keyword.cloudantfull}} 데이터베이스 인스턴스에 보고 이벤트를 전달하도록 음성 에이전트를 구성할 수 있습니다. 이러한 보고 이벤트에는 표기, 대화 턴 이벤트 및 호출 세부사항 레코드(CDR) 이벤트 양식의 호출자에 대한 PII, PHI 및 PCI DSS 데이터가 포함될 수 있습니다. 호출 데이터, SMS 데이터 및 보고 이벤트는 {{site.data.keyword.iva_short}} 내에서 저장되거나 처리되거나 수집되지 않으며 사용자는 외부 {{site.data.keyword.cloudant_short_notm}} 서비스를 적절하게 구성해야 합니다. **기본적으로 이벤트 전달은 사용할 수 없습니다.**

보고 이벤트를 전달하도록 음성 에이전트를 구성하려면 [이벤트 전달 사용](/docs/services/voice-agent?topic=voice-agent-event_forwarding)을 참조하십시오.

{{site.data.keyword.cloudant_short_notm}}의 데이터 개인정보 보호 및 정보 보안에 대한 자세한 정보는 [**{{site.data.keyword.cloudant_short_notm}}: 보안**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}을 참조하십시오.

### 문자-음성 변환 캐싱
{: #tts_caching}

고객과 대화하기 위해 {{site.data.keyword.conversationshort}}은 응답을 텍스트로 만들며, 이 응답은 {{site.data.keyword.texttospeechshort}} 서비스로 전달되고 {{site.data.keyword.iva_short}}에서 이를 큰 소리로 읽습니다. {{site.data.keyword.conversationshort}}이 작성하는 응답에는 민감한 정보가 포함될 수 있습니다. {{site.data.keyword.iva_short}}이 개인 데이터가 포함된, {{site.data.keyword.texttospeechshort}} 서비스에서 수신된 응답을 캐시하지 않도록 하기 위해 `vgwActExcludeFromTTSCache` 조치 명령을 사용하여 특정 유형의 정보가 포함된 발화가 캐시되지 않도록 할 수 있습니다. [API를 사용한 음성 에이전트 프로그래밍](/docs/services/voice-agent?topic=voice-agent-api#action-sequences)을 참조하십시오.

음성 에이전트 인스턴스가 삭제되면 TTS 캐시가 24시간 후에 지워집니다. 이를 `TTS cache timeout value`라 합니다.

### 보안 연결
{: #secure_trunking}

{{site.data.keyword.iva_short}}은 {{site.data.keyword.Bluemix_notm}}를 기반으로 하며 사용자가 구성하는 SIP 트렁크와 통합합니다. SIP 트렁크가 외부에 있고 {{site.data.keyword.iva_short}}에 연결되므로, SRTP(Secure Real Time Transport Protocol)로 SIP 트렁크와 {{site.data.keyword.iva_short}} 간 보안 연결을 사용하고 TLS(Transport Layer Security)를 필요로 하는 보안 sip(sips)로 암호화를 사용할 수 있습니다. [연결 보호](/docs/services/voice-agent?topic=voice-agent-securing)를 참조하십시오.

기본적으로 SMS 데이터는 TLS로 암호화됩니다. 자세한 정보는 [음성 게이트웨이: 데이터 처리](https://www.ibm.com/support/knowledgecenter/en/SS4U29/gdpr_considerations.html#GDPR_dataProcessing){: new_window}를 참조하십시오. 

### 서비스 오케스트레이션 엔진(SOE) 구성
{: #SOE_config}

서비스 오케스트레이션 엔진(SOE)을 통해 {{site.data.keyword.iva_short}}과 {{site.data.keyword.conversationshort}} 간에 전달되는 정보를 처리하여 호출자와의 대화를 사용자 정의할 수 있습니다. 보안 연결을 유지보수하려면 보안 URL `https` 및 사용자 인증을 사용하여 SOE를 구성하는지 확인하십시오.

[음성 에이전트에 맞게 {{site.data.keyword.conversationshort}} 구성](/docs/services/voice-agent?topic=voice-agent-conversation_va#conversation_va) 및 [서비스 오케스트레이션 엔진을 사용한 아키텍처](/docs/services/voice-agent?topic=voice-agent-about#arch-soe)를 참조하십시오.

## SMS/MMS 지원
{: #SMS_MMS}

### 데이터 처리
{: #data_handling}

{{site.data.keyword.iva_short}}은 SMS 데이터를 저장, 수집 또는 처리하지 않습니다. MMS 이미지는 서비스 외부에 저장되며 서비스 제공자에 의해 처리됩니다. 고객은 해당 SMS 제공자의 보안/개인정보 보호 계약을 참조해야 합니다. {{site.data.keyword.iva_short}}은 SMS 메시지에 임베드된 이미지에 대한 텍스트 링크만 처리합니다. 

서비스 오케스트레이션 엔진 또는 {{site.data.keyword.conversationshort}}에서 사용자에게 MMS 메시지를 발송할 경우(SMS 텍스트 메시지가 있든 없든), 하나 이상의 공개적으로 액세스 가능한 미디어 URL이 Twilio로 전송됩니다. Twilio는 비공개 URL을 지원하지 않습니다. 사용자는 MMS를 통해 민감한 정보나 개인 정보를 전송하는 것을 피해야 합니다.

{{site.data.keyword.iva_short}}은 이러한 유형의 개인 식별 가능 정보를 수집하지 않도록 메시지 로그에서 호출자 ID를 마스킹합니다.

### 인증
{: #authentication}

인바운드 SMS 메시지는 [IAM 인증](/docs/services/voice-agent?topic=voice-agent-iam#sms_access){: new_window}을 통해 서비스 제공자와 함께 보안됩니다. 

## {{site.data.keyword.iva_short}} 관련 서비스
{: #related_services}

{{site.data.keyword.iva_short}}은 여러 {{site.data.keyword.Bluemix_notm}} 서비스를 오케스트레이션하여 일반 사용자와 클라우드 기반 코그너티브 서비스 간 통신을 조정합니다. {{site.data.keyword.iva_short}} 자체는 일반 사용자의 권한을 침해하는 방식으로 데이터를 저장하거나 수집하거나 처리하지 않습니다. 하지만 관련 서비스를 구성하는 방법에 따라 이러한 서비스는 대화 중에 사용자가 공유하는 PHI(Protected Health Information), PII(Personally Identifiable Information) 또는 PCI DSS(Data Security Standard) 데이터를 수집할 수 있습니다. {{site.data.keyword.iva_short}} 아키텍처 및 대화 플로우에 대해 알아보려면 [아키텍처](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}를 참조하십시오.

각 서비스 및 {{site.data.keyword.Bluemix_notm}}에 대한 고려사항을 알아보려면 다음 리소스를 참조하십시오.

  * [**{{site.data.keyword.Bluemix_short}}: 보안 준수**](/docs/overview?topic=overview-security#security)
  * [**{{site.data.keyword.conversationfull}}: 정보 보안**](/docs/services/assistant?topic=assistant-information-security#information-security){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}: 정보 보안**](/docs/services/text-to-speech?topic=text-to-speech-information-security){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}: 정보 보안**](/docs/services/speech-to-text?topic=speech-to-text-information-security){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: 보안**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}
