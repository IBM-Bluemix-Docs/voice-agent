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


# 创建服务

{: shortdesc}
可以使用 {{site.data.keyword.Bluemix_short}} 目录或 {{site.data.keyword.Bluemix_notm}} `ibmcloud` 命令来创建 {{site.data.keyword.iva_full}} 服务实例。

## 通过目录创建服务
{: #catalog_create}

1. 转至 [{{site.data.keyword.iva_short}} 目录页面](https://console.bluemix.net/catalog/services/voice-agent-with-watson)。

   该目录页面包含有关服务及其价格套餐的信息。您可以更改**服务名称**值。

2. 单击**创建**。

## 通过命令行创建服务
{: #command_create}

1. [安装 {{site.data.keyword.Bluemix_notm}} CLI](../../cli/index.html#overview)。

2. 运行 [`ibmcloud` 命令](../../cli/idt/commands.html#idt-cli)来创建使用_试用_套餐的 Voice Agent 服务实例：

   ```
   ibmcloud service create VoiceAgent _Trial_ "My Voice Agent Service"
   ```
   {: codeblock}

## 后续步骤
{: #next}

在_管理_仪表板上，创建语音代理程序。请参阅[管理语音代理程序](managing.html)。
