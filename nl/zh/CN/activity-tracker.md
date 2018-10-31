---

copyright:
  years: 2018
lastupdated: "2018-10-08"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 活动跟踪程序事件
{: #activity-tracker}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服务，以跟踪用户和应用程序与 {{site.data.keyword.Bluemix}} 中的 {{site.data.keyword.iva_full}} 服务进行交互的方式。{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服务记录用户发起的活动，这些活动会更改 {{site.data.keyword.Bluemix_notm}} 中服务的状态。有关更多信息，请参阅 [{{site.data.keyword.cloudaccesstrailshort}}](./cloud-activity-tracker/index.html#getting-started-with-cla)。

## 事件列表
{: #event-List}

下表列出了生成事件的操作。

|操作|描述|
| --- | ---- |
| `create agent: POST /config/submitconfig` |创建新语音代理程序|
| `update agent: POST /config/submitconfig` |更新语音代理程序|
| `Update concurrency: POST /config/updatemax` |更新最大程度的调用并行|
| `delete agent: POST /config/submitconfig` |删除语音代理程序|
{: caption="表 1. 生成事件的操作" caption-side="top"}

## 查看活动事件的位置
{: #view-event}

{{site.data.keyword.cloudaccesstrailshort}} 事件在生成相应事件的 {{site.data.keyword.Bluemix_notm}} 区域中可用的 {{site.data.keyword.cloudaccesstrailshort}} 帐户域中可用。

## 过滤事件
{: #filter_events}

### 按语音代理程序标识进行过滤
{: #filter_id}

您可以按语音代理程序的实例标识过滤活动事件的列表，以获取特定的语音代理程序。

1. 转至 {{site.data.keyword.cloudaccesstrailshort}} 中的**管理**页面。
2. 在**搜索字段**中输入 `target.name_str`，并在**搜索**字段中以字符串的形式输入语音代理程序实例标识。请检查语音代理程序实例标识是否进行了百分比编码，以及您是否使用通配符 _*_ 进行搜索。

例如，搜索语音代理程序实例标识，`serviceInstanceId=crn%3A...`。

  * **搜索字段**：`target.name_str`
  * **搜索**：`"*crn%3A...*"`

### 按操作事件进行过滤
{: #filter_action}

您还可以过滤活动事件的列表，以获取特定的活动事件

1. 转至 {{site.data.keyword.cloudaccesstrailshort}} 中的**管理**页面，然后为其中每个字段输入以下配置值。

  * **查看日志**：`Space logs`
  * **搜索字段**：`action_str`
  * **搜索**：`"action string"`

## 创建高级过滤器
{: #advanced_filters}

您还可以通过使用 `AND` 或 `OR` 来创建高级过滤器，以在**搜索**字段中对搜索项进行组合。

例如，通过特定的语音代理程序实例标识和特定的操作来进行过滤。

* **查看日志**：`Space logs`
* **搜索字段**：`target.name_str`
* **搜索**：`"*crn%3A...*" AND action_str:"action string"`

**切记**：请检查语音代理程序实例标识是否进行了百分比编码，以及您是否使用通配符 _*_ 进行搜索。
