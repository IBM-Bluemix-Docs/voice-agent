---

copyright:
  years: 2018
lastupdated: "2018-10-30"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 활동 트래커 이벤트
{: #activity-tracker}

{{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자 및 애플리케이션이 {{site.data.keyword.Bluemix}}의 {{site.data.keyword.iva_full}} 서비스와 상호작용하는 방법을 추적할 수 있습니다.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 서비스는 {{site.data.keyword.Bluemix_notm}}의 서비스 상태를 변경하는 사용자가 시작한 활동을 기록합니다. 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started#getting-started)의 내용을 참조하십시오.

## 이벤트 목록
{: #event-List}

다음 표에는 이벤트를 생성하는 조치가 나열되어 있습니다.

| 조치|설명 |
| --- | ---- |
| `create agent: POST /config/submitconfig` | 새 음성 에이전트 작성 |
| `update agent: POST /config/submitconfig` | 음성 에이전트 업데이트 |
| `Update concurrency: POST /config/updatemax` | 최대 호출 동시성 업데이트 |
| `delete agent: POST /config/submitconfig` | 음성 에이전트 삭제 |
{: caption="표 1. 이벤트를 생성하는 조치" caption-side="top"}

## 활동 이벤트 확인 위치
{: #view-event}

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 이 이벤트가 생성된 {{site.data.keyword.Bluemix_notm}} 지역에서 사용 가능한 {{site.data.keyword.cloudaccesstrailshort}} 계정 도메인에서 사용할 수 있습니다.

## 이벤트 필터링
{: #filter_events}

### 음성 에이전트 ID별 필터링
{: #filter_id}

특정 음성 에이전트에 대한 활동 이벤트 목록을 해당 인스턴스 ID별로 필터링할 수 있습니다.

1. {{site.data.keyword.cloudaccesstrailshort}}의 **관리** 페이지로 이동하십시오.
2. **검색 필드**에 `target.name_str`을 입력하고 문자열인 **검색** 필드에 해당 음성 에이전트 인스턴스 ID를 입력하십시오. 음성 에이전트 인스턴스 ID가 백분율로 인코딩되었고 와일드카드 검색, _*_를 사용하는지 확인하십시오.

예를 들어, 음성 에이전트 인스턴스 ID를 검색하려면 `serviceInstanceId=crn%3A...`를 입력하십시오.

  * **검색 필드**: `target.name_str`
  * **검색**: `"*crn%3A...*"`

### 조치 이벤트별 필터링
{: #filter_action}

특정 조치 이벤트에 대한 활동 이벤트 목록을 필터링할 수도 있습니다.

1. {{site.data.keyword.cloudaccesstrailshort}}의 **관리** 페이지로 이동하여 각 필드에 대해 다음 구성 값을 입력하십시오.

  * **로그 보기**: `Space logs`
  * **검색 필드**: `action_str`
  * **검색**: `"action string"`

## 고급 필터 작성
{: #advanced_filters}

**검색** 필드에서 `AND` 또는 `OR`를 통해 검색어를 결합하여 고급 필터를 작성할 수도 있습니다.

예를 들어, 특정 음성 에이전트 인스턴스 ID 및 특정 조치별로 필터링하십시오.

* **로그 보기**: `Space logs`
* **검색 필드**: `target.name_str`
* **검색**: `"*crn%3A...*" AND action_str:"action string"`

**중요:** 음성 에이전트 인스턴스 ID가 백분율로 인코딩되었고 와일드카드 검색, _*_를 사용하는지 확인하십시오.
