---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 다중 서비스 위치 구성
{: #disaster-recovery}

서비스 중복성을 위해 서로 다른 위치에 있는 다중 서비스에 음성 에이전트를 연결할 수 있습니다. 두 번째 위치는 두 번째 음성 에이전트가 아니며 백업으로만 사용됩니다.
{: shortdesc}

음성 에이전트 인스턴스에 _Lite_ 플랜을 사용하는 경우 SIP 트렁크를 하나의 엔드포인트에만 연결할 수 있습니다. 여기서 음성 에이전트 인스턴스가 작성됩니다. _Lite_ 플랜은 하나의 위치에 대한 연결만 제공하므로 연결된 서비스의 중복성을 제공할 수 있지만 음성 에이전트의 중복성은 제공할 수 없습니다. 음성 에이전트 위치에서 서비스 중단이 발생하는 경우 호출이 두 번째 위치로 전달될 수 없습니다.
{: tip}

## 중복 서비스 추가
{: #add_redundant}

언제든지 음성 에이전트를 편집하여 음성 에이전트 구성에 Watson 또는 서드파티 서비스 위치를 추가할 수 있습니다.

1. 기존 음성 에이전트에 중복 서비스를 추가하려면 <em>관리</em> 대시보드의 <em>음성 에이전트</em> 탭으로 이동하십시오. 구성할 음성 에이전트에 대해 **에이전트 편집**을 클릭하십시오.

1. 연결할 {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} 또는 {{site.data.keyword.speechtotextshort}} 서비스에 대해 **위치 1** 또는 **위치 2**를 선택하고 구성 정보를 추가하십시오. 자신의 작업공간이나 기타 작업공간에서 서드파티 서비스 또는 Watson 서비스 인스턴스를 사용할 수 있습니다. [기타 {{site.data.keyword.Bluemix_notm}} 작업공간에서 서비스 인스턴스 사용](/docs/services/voice-agent?topic=voice-agent-other_service)을 참조하십시오.

**중요:** 서비스 중복성을 원하는 경우에는 서로 다른 위치에 대해 서로 다른 서비스 지역에서 Watson 서비스 인스턴스를 사용해야 합니다.

**위치 사용** 상자를 사용하여 위치를 사용 또는 사용 안함으로 설정할 수 있습니다. **위치 1**은 기본적으로 사용되며 **위치 2**는 기본적으로 사용되지 않습니다. 각 Watson 서비스마다 최소한 하나의 위치를 사용해야 합니다.

## 복수의 Watson 서비스 위치 추가
{: #add_location}

음성 에이전트는 지리적 거리순으로 Watson 서비스 인스턴스를 사용합니다. 예를 들어, 워싱턴 DC 지역에서 음성 에이전트를 작성하고 댈러스와 시드니(호주)에서 {{site.data.keyword.conversationshort}} 서비스를 작성할 수 있습니다. 댈러스가 지리적으로 시드니보다 워싱턴 DC에 더 가깝기 때문에 음성 에이전트는 {{site.data.keyword.conversationshort}} 댈러스 지역을 사용합니다. 여러 지역의 Watson 서비스에 연결하면 Watson 서비스가 한 위치에서 오프라인인 경우에 음성 에이전트가 여분의 서비스를 사용할 수 있습니다.
