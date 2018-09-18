---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 서비스 작성

{: shortdesc}
{{site.data.keyword.Bluemix_short}} 카탈로그 또는 {{site.data.keyword.Bluemix_notm}} `ibmcloud` 명령을 사용하여 {{site.data.keyword.iva_full}} 서비스 인스턴스를 작성할 수 있습니다.

## 카탈로그에서 서비스 작성
{: #catalog_create}

1. [{{site.data.keyword.iva_short}} 카탈로그 페이지](https://console.bluemix.net/catalog/services/voice-agent-with-watson)로 이동하십시오.

   카탈로그 페이지에는 서비스 및 가격 책정 플랜에 대한 정보가 있습니다. **서비스 이름** 값을 변경할 수 있습니다.

2. **작성**을 클릭하십시오.

## 명령행에서 서비스 작성
{: #command_create}

1. [{{site.data.keyword.Bluemix_notm}} CLI를 설치](../../cli/index.html#overview)하십시오.

2. _평가판_ 플랜으로 음성 에이전트 서비스 인스턴스를 작성하는 [`ibmcloud` 명령](../../cli/idt/commands.html#idt-cli)을 실행하십시오.

   ```
   ibmcloud service create VoiceAgent _Trial_ "My Voice Agent Service"
   ```
   {: codeblock}

## 다음 단계
{: #next}

_관리_ 대시보드에서 음성 에이전트를 작성하십시오. [음성 에이전트 관리](managing.html)를 참조하십시오.
