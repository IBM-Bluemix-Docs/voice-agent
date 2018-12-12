---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 管理服務實例及語音代理程式
{: #managing}

您可以使用_管理_ 儀表板來變更服務實例配置，並建立、編輯、複製、配置或移除個別語音代理程式。您可以在服務實例中有多個語音代理程式，但每一個語音代理程式都必須要有唯一名稱及電話號碼。
{: shortdesc}

## 導覽至 Voice Agent 服務儀表板
{: #navigate_manage}

您可以從 {{site.data.keyword.Bluemix_notm}} 帳戶儀表板找到_管理_ 儀表板。

1. 移至 [{{site.data.keyword.Bluemix_notm}} 帳戶儀表板](https://console.bluemix.net/dashboard/apps)。

1. 從**服務**的清單，選取 **Voice Agent** 服務實例，以便在_管理_ 標籤上開啟服務儀表板。

## 編輯服務實例的並行連線數上限
{: #edit_service}

在所有方案中，您都會免費收到 2 個並行連線。如果您使用_標準_ 或_超值_ 方案，則可以從_實例_ 標籤的預設值[變更並行連線數上限](managing_concurrency.html)。

## 建立語音代理程式
{: #create_va}

從_管理_ 儀表板的_語音代理程式_ 標籤，[建立新的語音代理程式](managing_create.html)。

## 編輯語音代理程式
{: #edit_va}

您可以在_管理_ 儀表板的_語音代理程式_ 標籤上，編輯現有語音代理程式，以對其進行變更。若要編輯語音代理程式，請從語音代理程式的選項清單中按一下**編輯代理程式**。變更配置，然後儲存變更。

## 複製語音代理程式
{: #clone_va}

當您複製語音代理程式時，會將 Watson 服務的所有配置都複製至新的代理程式。若要複製語音代理程式，請從語音代理程式的選項清單中按一下**複製代理程式**。為您的語音代理程式提供唯一的名稱及電話號碼，並視需要變更任何配置選項，然後儲存變更。

## 刪除語音代理程式
{: #delete_va}

您可能想要刪除語音代理程式，以釋放電話號碼。一個電話號碼只能有一個語音代理程式。若要將電話號碼用於不同的語音代理程式，您必須先刪除任何使用此電話號碼的語音代理程式。

若要刪除語音代理程式，請移至_語音代理程式_ 標籤、從語音代理程式的選項清單中按一下**刪除代理程式**，然後儲存變更。即會從語音代理程式清單中移除語音代理程式。

## 配置語音代理程式
{: #configure_va}

當您建立、複製或編輯語音代理程式時，可以變更語音代理程式的配置設定，及與相關服務的連線。

* **[配置多個服務位置](managing_disaster_recovery.html)：**為您的連線服務包含多個服務位置，以支援服務備援。
* **[使用協力廠商語音及文字服務進行連接](managing_third_party.html)：**您可以將語音代理程式連接至協力廠商 API，例如 Google Cloud Speech-to-Text，而不使用 {{site.data.keyword.texttospeechshort}} 或 {{site.data.keyword.speechtotextshort}}。
* **[使用其他 {{site.data.keyword.Bluemix_notm}} 工作區中的服務](managing_other.html)：**您可以將語音代理程式配置成使用 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.speechtotextshort}} 服務實例，而這些服務實例屬於其他 {{site.data.keyword.Bluemix_short}} 帳戶中的工作區。
* **[使用服務編排引擎配置 Watson Assistant](managing_SOE.html)：**您可以透過服務編排引擎 (SOE) 連接至 {{site.data.keyword.conversationshort}} 工作區。SOE 會將訊息截取至服務並從中截取訊息，讓您可以使用協力廠商 API 進行修改。
* **[為語音代理程式啟用事件轉遞](event-forwarding.html)：**您可能想要收集及分析來自 {{site.data.keyword.iva_short}} 的通話資料，以改善交談對來電者的自然程度。您建立的每一個語音代理程式都可以將事件報告轉遞至您管理的指定 {{site.data.keyword.cloudant_short_notm}}。

## 配置進階語音代理程式選項
{: #config-advanced}

建立或複製語音代理程式時，您可以按一下**顯示進階**，來檢視下列進階配置選項。

* **{{site.data.keyword.conversationshort}} 失敗回覆訊息（選用）**：通話無法連接至 {{site.data.keyword.conversationshort}} 時，要傳送給訊息接收者的預設回覆訊息。
* **轉接失敗回覆訊息（選用）**：通話轉接失敗時，要串流給來電者的預設回覆訊息。
* **自訂 SIP INVITE 標頭（選用）**：指定要從送入的 SIP INVITE 要求擷取的自訂 SIP 標頭。
* **從 {{site.data.keyword.iva_short}} 傳送暫時鈴聲回應**：當 {{site.data.keyword.iva_short}} 處理送入的通話時，傳送 `180 ringing` 回應。預設為啟用。
* **轉接時保留通話**：在轉接期間讓來電者進入保留狀態。預設為啟用。
* **轉接失敗時中斷通話**決定通話轉接失敗時，是否中斷通話。預設為啟用。如果設定為已停用且通話轉接失敗，則 {{site.data.keyword.iva_short}} 會起始一個回合的交談。然後，{{site.data.keyword.conversationshort}} 可以中斷通話，或將它轉接至對話中所配置的不同目的地。
* **發生網路事件時通知 {{site.data.keyword.conversationshort}}**：啟用且偵測到錯誤時，{{site.data.keyword.iva_short}} 會以文字 "vgwNetworkWarningMessage" 對 {{site.data.keyword.conversationshort}} 服務起始一個回合。`vgwNetworkWarnings` 狀態變數包含在現行回合期間發生之網路事件的清單。如果已停用，則在現行回合期間發生之網路事件的清單，會以 `vgwNetworkWarning` 狀態變數中的下一回合事件進行傳送。預設為啟用。
