---

copyright:
  years: 2018
lastupdated: "2018-11-12"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 查看使用情况和呼叫日志
{: #logging}

可以在 {{site.data.keyword.Bluemix_notm}}“仪表板”中查看语音代理程序的使用情况历史记录和呼叫日志。
{: shortdesc}

## 关于日志记录

{{site.data.keyword.iva_full}} 的日志记录会自动启用。在_使用情况_仪表板中，可以查看语音代理程序呼叫日志。

_使用情况_仪表板会显示有关服务使用情况以及套餐中剩余可用资源的快速统计信息。此信息包括当月遇到的最大并发连接数以及套餐中可用的最大并发连接数。在_呼叫分钟_框中，您可以查看套餐中包含的免费分钟数以及已用的分钟数。_呼叫日志_部分位于_快速统计信息_之后。

可以按日期以及按语音代理程序名称或号码来过滤_呼叫日志_和_呼叫分钟_，以减少显示的呼叫数并隔离特定的呼叫日志。此外，您可以过滤_呼叫日志_以仅显示失败的呼叫。

要了解有关创建和编辑语音代理程序的更多信息，请参阅[管理语音代理程序](/docs/services/voice-agent?topic=voice-agent-managing)。

##  查看呼叫日志

1. 在 {{site.data.keyword.iva_short}} 仪表板中，浏览至_使用情况_仪表板以查看_快速统计信息_和_呼叫日志_。在_呼叫日志_表中，每一行对应一个呼叫。

      对于每个呼叫，可以查看语音代理程序的名称和电话号码、开始和停止时间以及呼叫持续时间。此外，还可能会在语音代理程序名称旁看到一个警告符号，该符号指示呼叫失败。

1.  可以通过查看特定日期的呼叫以及按语音代理程序名称或号码过滤呼叫，从而过滤呼叫列表。还可以选择仅显示失败的呼叫。

1. 要访问单个呼叫的呼叫故障日志，请单击该呼叫的**操作**列中的点，以展开菜单。然后，选择**故障日志**。此选项仅对失败的呼叫显示。

1. 可以使用以下方法在新视图中查看消息日志的详细信息列表：
  * 搜索故障日志
  * 根据日志类型（**错误**或**警告**）过滤消息
  * 下载数据集
  * 按时间戳记对故障日志进行升序或降序排序

1. 要详细查看任何故障日志消息，请单击您感兴趣的表行开头的箭头以展开视图。在 [Voice Gateway 系统消息](https://www.ibm.com/support/knowledgecenter/SS4U29/messages.html){:new_window}中，可以查看有关日志消息的更多详细信息。

1. 单击页面开头的后退箭头以返回到_使用情况_仪表板。

## 相关链接
要了解有关日志记录的更多详细信息，请参阅 IBM Voice Gateway 文档中的[故障诊断](https://www.ibm.com/support/knowledgecenter/SS4U29/troubleshooting.html){:new_window}。
