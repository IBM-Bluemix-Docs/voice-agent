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

# 编辑最大并发连接数
{: #edit_concurrency}

如果使用_标准_或_高端_套餐，那么可以更改最大并发连接数的缺省设置。
{: shortdesc}

所有套餐都可以免费获取 2 个并发连接。有关更多信息，请参阅[价格套餐](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)。在_管理_仪表板上，可以在**最大并发连接数**中查看您的所列套餐中允许的最大并发连接数。还可以在**已使用的最大并发连接数**中查看您的语音代理程序当月使用的最大并发连接数。

1. 转至_管理_仪表板的_实例_选项卡，以编辑您套餐中的最大并发连接数。

1. 如果想要更改套餐中的最大并发连接数，请单击**编辑**图标。

1. 在_编辑最大并发连接数_中，输入最大并发连接数，然后单击**保存**。

可通过自助服务设置的最小并发连接数为 10，最大并发连接数为 50。如果语音代理程序需要 50 个以上的并发连接，请参阅[请求网络设置协助](/docs/services/voice-agent?topic=voice-agent-connect#request-setup)。

## 并发连接定价信息
{: #concurrent-charge}

  * _轻量_和_标准_套餐包含 2 个免费的并发连接。
  * _高端_套餐可按实例进行定制。
  * 在_标准_套餐中，最小容量为 10 个并发连接。
  * 并发连接的使用量是按月分派的。如果某一天的使用量超过 2 个并发连接，那么将按每日费率进行收费。例如，您的套餐免费支持 2 个并发连接，而您设置的最大限制为 12 个连接。如果某一天只使用 5 个，那么将收取 3 个的费用。
  * 如果使用_标准_或_高端_套餐，那么可以购买更大的并发连接容量。
  * 系统会按每日费率对您在一天内使用的最大并发连接容量进行收费。

有关套餐、费率和特色服务的更多信息，请参阅[价格套餐](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)。
