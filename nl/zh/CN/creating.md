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


# 创建服务

可以使用 {{site.data.keyword.Bluemix_short}}“目录”或 {{site.data.keyword.Bluemix_notm}} `ibmcloud` 命令来创建 {{site.data.keyword.iva_full}} 服务实例。
{: shortdesc}


## 通过目录创建服务
{: #catalog_create}

1. 转至 [{{site.data.keyword.iva_short}} 目录页面](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)。

   该目录页面包含有关服务及其价格套餐的信息。您可以更改**服务名称**值。

2. 单击**创建**，以[使用_管理_仪表板创建语音代理程序](/docs/services/voice-agent?topic=voice-agent-config_instance#config_instance)。

## 通过命令行创建服务
{: #command_create}

1. [安装 {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli#overview)。

2. 运行 [`ibmcloud` 命令](/docs/cli/idt?topic=cloud-cli-idt-cli#idt-cli)。这将创建使用_轻量_套餐的语音代理程序服务实例：

   ```
   ibmcloud service create VoiceAgent _Lite_ "My Voice Agent Service"
   ```
   {: codeblock}
