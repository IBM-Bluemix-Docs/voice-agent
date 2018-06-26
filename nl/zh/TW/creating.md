---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 建立服務

{: shortdesc}
您可以使用 {{site.data.keyword.Bluemix_short}} 型錄或 {{site.data.keyword.Bluemix_notm}} `ibmcloud` 指令，來建立 {{site.data.keyword.iva_full}} 服務實例。

## 從型錄建立服務
{: #catalog_create}

1. 移至 [{{site.data.keyword.iva_short}} 型錄頁面](https://console.bluemix.net/catalog/services/voice-agent-with-watson)。

   型錄頁面具有服務及其定價方案的相關資訊。您可以變更**服務名稱**值。

2. 按一下**建立**。

## 從指令行建立服務
{: #command_create}

1. [安裝 {{site.data.keyword.Bluemix_notm}} CLI](../../cli/reference/bluemix_cli/get_started.html)。

2. 執行 [`ibmcloud` 指令](../../cli/reference/bluemix_cli/bx_cli.html#bluemix_cli)，以使用_試用_ 方案建立 VoiceAgent 服務實例：

   ```
   ibmcloud service create VoiceAgent _Trial_ "My Voice Agent Service"
   ```
   {: codeblock}

## 後續步驟
{: #next}

從_管理_ 儀表板建立語音代理程式。請參閱[管理語音代理程式](managing.html)。
