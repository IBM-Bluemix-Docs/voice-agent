---

copyright:
  years: 2018
lastupdated: "2018-08-29"

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

{{site.data.keyword.iva_short}}은 고객에게서 받은 데이터를 저장하거나 수집하거나 처리하지 않습니다. 대신 데이터는 처리를 위해 다른 서비스로 라우팅됩니다. 대화 중에 사용자는 PHI(Protected Health Information), PII(Personally Identifiable Information) 또는 PCI DSS(Data Security Standard) 데이터가 포함된 정보를 공유할 수 있습니다. {{site.data.keyword.iva_short}}의 대화 플로우 및 아키텍처에 대해 자세히 보려면 [아키텍처](about.html#architecture){: new_window}를 참조하십시오.

데이터 개인정보 보호 및 보안 처리를 지원하도록 음성 에이전트 인스턴스를 구성하는 경우 다음 기능을 고려하십시오.

### 호출 전송
{:  #calltransfer_infosec}

음성 에이전트에 호출 전송 기능을 추가하는 경우, 전송 대상 SIP URI를 구성할 때 전화번호를 제공합니다. 사용자는 이 전송 대상에 개인 전화번호를 제공하지 않아야 합니다.

호출 전송을 위한 SIP URI 및 SIP 트렁크 구성에 대해 알아보려면 [호출 전송 설정](call-transfer.html)을 참조하십시오.

### 이벤트 전달
{: #event_forwarding}

{{site.data.keyword.cloudantfull}} 데이터베이스 인스턴스에 보고 이벤트를 전달하도록 음성 에이전트를 구성할 수 있습니다. 이러한 보고 이벤트에는 표기, 대화 턴 이벤트 및 호출 세부사항 레코드(CDR) 이벤트 양식의 호출자에 대한 PII, PHI 및 PCI DSS 데이터가 포함될 수 있습니다. 호출 데이터 및 보고 이벤트는 {{site.data.keyword.iva_short}} 내에서 저장되거나 처리되거나 수집되지 않으며 사용자는 외부 {{site.data.keyword.cloudant_short_notm}} 서비스를 적절하게 구성해야 합니다. **기본적으로 이벤트 전달은 사용할 수 없습니다.**

보고 이벤트를 전달하도록 음성 에이전트를 구성하려면 [이벤트 전달 사용](event-forwarding.html)을 참조하십시오.

{{site.data.keyword.cloudant_short_notm}}의 데이터 개인정보 보호 및 정보 보안에 대한 자세한 정보는 [**{{site.data.keyword.cloudant_short_notm}}: 보안**](../Cloudant/offerings/security.html#security){: #new_window}을 참조하십시오.

### 문자-음성 변환 캐싱
{: #tts_caching}

고객과 대화하기 위해 {{site.data.keyword.conversationshort}}은 응답을 텍스트로 만들며, 이 응답은 {{site.data.keyword.texttospeechshort}} 서비스로 전달되고 {{site.data.keyword.iva_short}}에서 이를 큰 소리로 읽습니다. {{site.data.keyword.conversationshort}}이 작성하는 응답에는 민감한 정보가 포함될 수 있습니다. {{site.data.keyword.iva_short}}이 개인 데이터가 포함된, {{site.data.keyword.texttospeechshort}} 서비스에서 수신된 응답을 캐시하지 않도록 하기 위해 `vgwActExcludeFromTTSCache` 조치 명령을 사용하여 특정 유형의 정보가 포함된 발화가 캐시되지 않도록 할 수 있습니다. [API를 사용한 음성 에이전트 프로그래밍](api.html#action-sequencess)을 참조하십시오.

### 보안 연결
{: #secure_trunking}

{{site.data.keyword.iva_short}}은 {{site.data.keyword.Bluemix_notm}}를 기반으로 하며 사용자가 구성하는 SIP 트렁크와 통합합니다. SIP 트렁크가 외부에 있고 {{site.data.keyword.iva_short}}에 연결되므로, SRTP(Secure Real Time Transport Protocol)로 SIP 트렁크와 {{site.data.keyword.iva_short}} 간 보안 연결을 사용하고 TLS(Transport Layer Security)를 필요로 하는 보안 sip(sips)로 암호화를 사용할 수 있습니다. [연결 보호](secure-trunking.html)를 참조하십시오.

### 서비스 오케스트레이션 엔진(SOE) 구성
{: #SOE_config}

서비스 오케스트레이션 엔진(SOE)을 통해 {{site.data.keyword.iva_short}}과 {{site.data.keyword.conversationshort}} 간에 전달되는 정보를 처리하여 호출자와의 대화를 사용자 정의할 수 있습니다. 보안 연결을 유지보수하려면 보안 URL `https` 및 사용자 인증을 사용하여 SOE를 구성하는지 확인하십시오.

[음성 에이전트에 맞게 {{site.data.keyword.conversationshort}} 구성](managing.html#conversation_va) 및 [서비스 오케스트레이션 엔진을 사용한 아키텍처](about.html#arch-soe)를 참조하십시오.

## {{site.data.keyword.iva_short}} 관련 서비스
{: #related_services}

{{site.data.keyword.iva_short}}은 여러 {{site.data.keyword.Bluemix_notm}} 서비스를 오케스트레이션하여 일반 사용자와 클라우드 기반 코그너티브 서비스 간 통신을 조정합니다. {{site.data.keyword.iva_short}} 자체는 일반 사용자의 권한을 침해하는 방식으로 데이터를 저장하거나 수집하거나 처리하지 않습니다. 하지만 관련 서비스를 구성하는 방법에 따라 이러한 서비스는 대화 중에 사용자가 공유하는 PHI(Protected Health Information), PII(Personally Identifiable Information) 또는 PCI DSS(Data Security Standard) 데이터를 수집할 수 있습니다. {{site.data.keyword.iva_short}} 아키텍처 및 대화 플로우에 대해 알아보려면 [아키텍처](about.html#architecture){: new_window}를 참조하십시오.

각 서비스 및 {{site.data.keyword.Bluemix_notm}}에 대한 고려사항을 알아보려면 다음 리소스를 참조하십시오.

  * [**{{site.data.keyword.Bluemix_short}}: 보안 준수**](../../security/compliance.html)
  * [**{{site.data.keyword.conversationfull}}: 정보 보안**](../conversation/information-security.html){: #new_window}
  * [**{{site.data.keyword.texttospeechfull}}: 정보 보안**](../text-to-speech/information-security.html){: #new_window}
  * [**{{site.data.keyword.speechtotextfull}}: 정보 보안**](../speech-to-text/information-security.html){: #new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: 보안**](../Cloudant/offerings/security.html#security){: #new_window}
