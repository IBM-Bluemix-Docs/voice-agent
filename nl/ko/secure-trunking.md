---

copyright:
  years: 2018
lastupdated: "2018-06-14"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 연결 보호
{: #securing}

{{site.data.keyword.iva_full}}과의 연결을 보안하기 위해 SIP 트렁크에 TLS(Transport Layer Security)를 사용하여 암호화 및 SRTP(Secure Real Time Transport Protocol)를 사용으로 설정할 수 있습니다.

## Twilio에서 SRTP 설정
{: #SRTP}

**참고:** SRTP를 사용하면 SIP 메시지도 암호화됩니다. SRTP 및 SIP 메시지 암호화를 따로따로 사용으로 설정하지 않아도 됩니다.

1. Twilio 계정에서 _Elastic SIP Trunking_ 대시보드로 이동하여 **트렁크**를 선택하십시오.

1. 기존 트렁크를 선택하거나 **+** 아이콘을 클릭하여 새 트렁크를 작성하여 SRTP를 사용하여 보안할 트렁크를 선택하십시오.

  * 새 트렁크를 작성할 때 **시작** 대시보드에서 _SIP 트렁크 URI_를 구성해야 합니다.  자세한 정보는 [SIP 트렁크 연결](/docs/services/voice-agent?topic=voice-agent-connect)을 참조하십시오.

1. _일반_ 대시보드에서 _트렁크 보호_ 섹션을 찾으십시오. **사용 안함**을 클릭하여 트렁크 보호 설정을 **사용**으로 변경하고 변경사항을 저장하십시오.

## Twilio에서 TLS를 사용하여 SIP 메시지에만 암호화 사용
{: #TLS}

SRTP를 사용하지 않고 {{site.data.keyword.iva_short}}에서 SIP 메시지만 암호화하려는 경우 Twilio에서 TLS(Transport Layer Security)를 사용하는 URI 엔드포인트를 선택할 수 있습니다.

1. Twilio 계정에서 _Elastic SIP Trunking_ 대시보드로 이동하여 **트렁크**를 선택하십시오.

1. 기존 트렁크를 선택하거나 **+** 아이콘을 클릭하여 새 트렁크를 작성한 후 호출 전송을 추가하려는 트렁크를 선택하십시오.

1. 메뉴에서 **오리진**을 선택하고 차례로 다음의 보안 오리진 URI를 입력하십시오. 다중 호스트 이름 또는 IP 주소를 포함하면 첫 번째 호스트 엔드포인트가 실패하거나 서비스가 중단된 경우에 SIP 트렁크 제공자가 다음에 나열된 호스트 이름으로 호출을 전달합니다.

```
sip:us-south.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}

또는

```
sip:us-east.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}
