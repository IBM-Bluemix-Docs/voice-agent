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


# Activity tracker 事件
{: #activity-tracker}

請使用 {{site.data.keyword.cloudaccesstrailfull}} 服務，來追蹤在 {{site.data.keyword.Bluemix}} 中，使用者及應用程式如何與 {{site.data.keyword.iva_full}} 服務互動。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服務會記錄由使用者起始，且會變更 {{site.data.keyword.Bluemix_notm}} 中服務狀態的活動。如需相關資訊，請參閱 [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started#getting-started)。

## 事件清單
{: #event-List}

下表列出產生事件的動作清單。

|動作|說明        |
| --- | ---- |
| `create agent: POST /config/submitconfig` |建立新的語音代理程式|
| `update agent: POST /config/submitconfig` |更新語音代理程式|
| `Update concurrency: POST /config/updatemax` |更新呼叫並行程度上限|
| `delete agent: POST /config/submitconfig` |刪除語音代理程式|
{: caption="表 1. 產生事件的動作" caption-side="top"}

## 在哪裡檢視活動事件
{: #view-event}

{{site.data.keyword.cloudaccesstrailshort}} 事件提供於 {{site.data.keyword.cloudaccesstrailshort}} 帳戶網域，這提供於產生事件的 {{site.data.keyword.Bluemix_notm}} 地區。

## 過濾事件
{: #filter_events}

### 依語音代理程式 ID 過濾
{: #filter_id}

您可以依特定語音代理程式的實例 ID 來過濾它的活動事件清單。

1. 移至 {{site.data.keyword.cloudaccesstrailshort}} 中的**管理**頁面。
2. 在**搜尋欄位**輸入 `target.name_str`，並在**搜尋**欄位輸入您的語音代理程式實例 ID 作為字串。請確認語音代理程式實例 ID 使用百分比編碼，且您使用萬用字元搜尋 _*_ 。

例如，若要搜尋您的語音代理程式實例 ID `serviceInstanceId=crn%3A...`。

  * **搜尋欄位**：`target.name_str`
  * **搜尋**：`"*crn%3A...*"`

### 依動作事件過濾
{: #filter_action}

您也可以過濾特定動作事件的活動事件清單。

1. 移至 {{site.data.keyword.cloudaccesstrailshort}} 中的**管理**頁面，並輸入每個欄位的下列配置值。

  * **檢視日誌**：`Space logs`
  * **搜尋欄位**：`action_str`
  * **搜尋**：`"action string"`

## 建立進階過濾器
{: #advanced_filters}

您也可以使用 `AND` 或 `OR` 結合**搜尋**欄位中的搜尋詞彙，來建立進階過濾器。

例如，依特定語音代理程式實例 ID 和特定動作來過濾。

* **檢視日誌**：`Space logs`
* **搜尋欄位**：`target.name_str`
* **搜尋**：`"*crn%3A...*" AND action_str:"action string"`

**記住**：請確認語音代理程式實例 ID 使用百分比編碼，且您使用萬用字元搜尋 _*_ 。
