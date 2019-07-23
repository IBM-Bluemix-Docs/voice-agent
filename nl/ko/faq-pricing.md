---

copyright:
  years: 2019
lastupdated: "2019-06-17"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 가격 FAQ
{: #faq-pricing}

## {{site.data.keyword.iva_short}} 표준 서비스 사용을 위한 가격은 얼마입니까?
{: #faq-pricing-zero}
{: faq}

 자세한 정보는 [가격 페이지](https://cloud.ibm.com/catalog/services/voice-agent-with-watson){: external}를 참조하십시오.

## "분당 가격"은 무슨 의미입니까?
{: #faq-pricing-one}
{: faq}

가격은 사용자가 서비스에 보내는 오디오의 양(분)을 기반으로 합니다. 가격은 서비스가 오디오를 처리하는 데 걸리는 시간에 따라 달라집니다. 


## API로의 모든 호출에 가장 가까운 시간(분)으로 계산합니까? 
{: #faq-pricing-two}
{: faq}

'{{site.data.keyword.IBM_notm}}에서는 서비스가 가장 가까운 시간(분)까지 수신하는 모든 API에 대한 오디오의 길이를 계산하지 않습니다. 대신 {{site.data.keyword.IBM_notm}}에서는 당월 동안의 사용량을 집계한 후 월말에 가장 가까운 시간(분)까지 계산합니다. 각 호출의 지속 기간은 다음 시간(분)으로 반올림됩니다. 예를 들어 첫 번째 호출이 3.1초 동안 이루어지고 두 번째 호출이 25.9초 동안 이루어지는 경우, {{site.data.keyword.IBM_notm}}에서는 첫 번째 호출을 4초로, 두 번째 호출을 26초로 계산합니다. 그런 다음 총 오디오 지속 기간이 1분으로 계산됩니다.'


## 동시 연결은 어떻게 계산되고 어디에 적용됩니까? 
{: #faq-pricing-three}
{: faq}

동시 연결은 SMS가 아닌 음성 호출에만 적용됩니다. 동시 연결은 서비스 인스턴스에 동시에 정의된 모든 전화번호에 대한 연결 수로 계산됩니다. 사용된 실제 일일 최대 동시 연결 수는 월별 요금에 따라 청구되고, 적립됩니다. 

## 최대 동시 연결의 정의와 변경 방법은 무엇입니까?

{: #faq-pricing-four}
{: faq}

최대 동시 연결은 언제든지 허용되는 최대 연결 수이며, 청구되는 최대 연결 수입니다. 최대 동시 연결은 [대시보드](https://cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-edit_concurrency)에서 정의하고 변경할 수 있습니다. 표준 플랜의 최대 동시 용량은 50개의 연결이며, 더 필요한 경우 지원 티켓을 열 수 있습니다.

## 인바운드 및 아웃바운드 SMS/MMS 메시지 청구 방법은 무엇입니까?

{: #faq-pricing-five}
{: faq}

응답이 사용자에게 보내질 때까지 인바운드 메시지가 청구되지 않습니다. 세션은 아웃바운드 메시지가 Voice Gateway를 통해 또는 인바운드 메시지에 대한 응답으로 사용자에게 전송될 때 작성됩니다. 해당되는 경우 응답되는 아웃바운드 및 인바운드 메시지가 모두 청구됩니다. 세션 제한시간이 초과될 때까지 아웃바운드 및 인바운드 메시지 둘 다 청구됩니다. 세션 제한시간이 초과되고 나면 대화 컨텍스트가 무시됩니다. 기본 세션 제한시간은 3600초이며, 사용자는 대시보드에서 세션 제한시간의 지속 기간을 설정할 수 있습니다. 
