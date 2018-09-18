---

copyright:
  years: 2018
lastupdated: "2018-08-24"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 음성 에이전트에 대한 이벤트 전달 사용
{: #event_forwarding}

{{site.data.keyword.cloudantfull}} 데이터베이스 서비스를 사용하여 {{site.data.keyword.iva_full}}의 음성 에이전트에서 처리되는 호출에 대한 정보를 수집하도록 이벤트 전달을 사용으로 설정할 수 있습니다.
{: shortdesc}

{{site.data.keyword.iva_short}}에서 호출 데이터를 수집하고 분석하여 호출자와의 자연스러운 대화 능력을 개선할 수 있습니다. 사용자가 작성하는 각 음성 에이전트는 사용자가 관리하는 지정된 {{site.data.keyword.cloudant_short_notm}}로 이벤트 보고서를 전달할 수 있습니다. 관련 이벤트에는 CDR(Call Detail Record) 이벤트, 기록 이벤트 및 변환 이벤트 보고서가 포함됩니다. [이벤트 보고](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}에서 전달 가능한 이벤트의 유형에 대해 자세히 알아볼 수 있습니다.

이러한 이벤트의 데이터를 분석하면 대화를 조정하고 인텐트를 정제하며 전체 호출자 환경을 개선하는 데 도움이 될 수 있습니다.

음성 에이전트를 작성하거나 편집할 때 이벤트 전달을 사용하도록 선택할 수도 있습니다. 음성 에이전트 작성 및 편집에 대한 세부사항은 [음성 에이전트 관리](managing.html)를 참조하십시오. 이벤트 전달을 사용으로 설정하려면 계정 이름 및 비밀번호를 포함한 {{site.data.keyword.cloudant_short_notm}} 계정 정보를 제공해야 합니다.

**중요:** CDR, 기록 및 변환 이벤트에는 잠재적으로 PHI(Protected Health Information), PII(Personally Identifiable Information) 또는 PCI DSS(Data Security Standard) 데이터가 있을 수 있는 사용자의 정보가 포함되어 있습니다. 개인 정보가 노출되지 않도록 하려면 사용자가 대화에서 또는 대화 중에 공유하는 기밀 정보를 {{site.data.keyword.cloudant_short_notm}} 인스턴스에서 적절히 보호하도록 해야 합니다. [정보 보안 및 데이터 개인정보 보호: 이벤트 전달](infosec.html#event_forwarding) 및 [{{site.data.keyword.cloudant_short_notm}}: 보안](../Cloudant/offerings/security.html#security)을 참조하십시오.


## 이벤트 전달 사용
{: #enable-event-forwarding}

{{site.data.keyword.Bluemix_short}}의 _관리_ 대시보드에서 음성 에이전트를 작성하거나 편집할 때 이벤트 전달을 사용하도록 설정할 수 있습니다.

1. **이벤트 전달** 섹션에서 {{site.data.keyword.texttospeechshort}}에 대한 구성 섹션 다음에 나오는 **이벤트 전달 사용**을 선택하십시오.

1. **내 {{site.data.keyword.cloudant_short_notm}} 서비스 인스턴스** 또는 **기타 {{site.data.keyword.cloudant_short_notm}} 서비스 인스턴스**를 선택하십시오.
  * **내 {{site.data.keyword.cloudant_short_notm}} 서비스 인스턴스**를 사용 중인 경우 목록에서 **{{site.data.keyword.cloudant_short_notm}} account** 이름 및 사용자 이름을 선택하십시오.
  * **기타 {{site.data.keyword.cloudant_short_notm}} 서비스 인스턴스**를 사용 중인 경우에는 계정에 대한 {{site.data.keyword.cloudant_short_notm}} 사용자 이름과 비밀번호, 또는 API 키를 입력하십시오.

1. 전달하려는 각 이벤트 유형에 대해 **사용**을 선택한 후 이벤트를 전달하려는 데이터베이스를 선택하십시오.
  * CDR(Call Detail Record) 이벤트
  * 기록 이벤트
  * 변환 이벤트

1. 데이터베이스에서 이벤트 보고서가 올바르게 전달되었는지 확인하십시오.

## 관련 링크
* [IBM Voice Gateway: 이벤트 보고](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
* [정보 보안 및 데이터 개인정보 보호](infosec.html)
* [{{site.data.keyword.cloudant_short_notm}}: 보안](../Cloudant/offerings/security.html#security)
