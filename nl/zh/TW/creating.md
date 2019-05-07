---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 建立服務

您可以使用 {{site.data.keyword.Bluemix_short}} 型錄或 {{site.data.keyword.Bluemix_notm}} `ibmcloud` 指令，來建立 {{site.data.keyword.iva_full}} 服務實例。
{: shortdesc}


## 從型錄建立服務
{: #catalog_create}

1. 移至 [{{site.data.keyword.iva_short}} 型錄頁面](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)。

   型錄頁面具有服務及其定價方案的相關資訊。您可以變更**服務名稱**值。

2. 按一下**建立**，以便[從_管理_ 儀表板建立語音代理程式](/docs/services/voice-agent?topic=voice-agent-config_instance#config_instance)。

## 從指令行建立服務
{: #command_create}

1. [安裝 {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#overview)。

2. 執行 [`ibmcloud` 指令](/docs/cli/idt?topic=cloud-cli-idt-cli#idt-cli)，以使用_精簡_ 方案建立 Voice Agent 服務實例：

   ```
   ibmcloud service create VoiceAgent _Lite_ "My Voice Agent Service"
   ```
   {: codeblock}
