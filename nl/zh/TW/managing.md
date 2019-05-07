---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 管理服務實例及語音代理程式
{: #managing}

您可以使用_管理_ 儀表板來變更服務實例配置，並建立、編輯、複製、配置或移除個別語音代理程式。您在服務實例中可以有多個語音代理程式，而每個語音代理程式最多可以有 1000 個唯一號碼和說明。
不過，每個語音代理程式都必須具有唯一名稱且至少有一個電話號碼。

* **附註**：單一 {{site.data.keyword.iva_full}} 服務實例最多可以有 150 個語音代理程式。
{: shortdesc}

## 導覽至 Voice Agent 服務儀表板
{: #navigate_manage}

您可以從 {{site.data.keyword.iva_short}} 服務儀表板找到_管理_ 儀表板。

1. 移至 [{{site.data.keyword.Bluemix_notm}} 帳戶資源清單](https://cloud.ibm.com/resources)。

1. 從**服務**的清單，選取 **Voice Agent** 服務實例，以便在_管理_ 標籤上開啟服務儀表板。

## 語音代理程式摘要
{: #agent_summary}

如果您已經有一個現有的語音代理程式，則可以查看代理程式的所有號碼、說明及配置設定的摘要。若要查看摘要，請按一下語音代理程式**名稱**左側的下移鍵按鈕。摘要即會展開。

雖然語音代理程式可能包含多個號碼，但在代理程式摘要上只會顯示選取的**主要號碼**。依預設，這是第一個新增至語音代理程式的號碼，僅用於顯示，且沒有任何功能用途。如果您想要顯示語音代理程式中的其他號碼，請參閱[管理多個號碼](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num)。

您可以從代理程式摘要中，查看語音代理程式中的所有號碼。在配置摘要展開之後，按一下**檢視號碼**按鈕，所有號碼的清單即會顯示在新的**管理**對話框中。如需使用**管理**對話框的相關資訊，請參閱[管理多個號碼](/docs/services/voice-agent?topic=voice-agent-multi_num)頁面。

## 編輯服務實例的並行連線數上限
{: #edit_service}

在所有方案中，您都會免費收到 2 個並行連線。如果您使用_標準_ 或_超值_ 方案，則可以從_實例_ 標籤的預設值[變更並行連線數上限](/docs/services/voice-agent?topic=voice-agent-edit_concurrency)。

## 建立語音代理程式
{: #create_va}

從_管理_ 儀表板的_語音代理程式_ 標籤，[建立新的語音代理程式](/docs/services/voice-agent?topic=voice-agent-config_instance)。

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

## 依號碼或說明來搜尋語音代理程式
{: #search}

您可以根據儲存在代理中的號碼或說明來搜索語音代理程式。

在_搜尋_ 列中，您可以鍵入號碼或說明。鍵入時，搜尋結果將自動更新。  

## 配置語音代理程式
{: #configure_va}

當您建立、複製或編輯語音代理程式時，可以變更語音代理程式的配置設定，及與相關服務的連線。

* **[配置多個號碼](/docs/services/voice-agent?topic=voice-agent-multi_num)：**您可以將語音代理程式配置成包括多個電話號碼。
* **[配置多個服務位置](/docs/services/voice-agent?topic=voice-agent-disaster-recovery)：**為您的連線服務包含多個服務位置，以支援服務備援。
* **[使用協力廠商語音及文字服務進行連接](/docs/services/voice-agent?topic=voice-agent-third-party)：**您可以將語音代理程式連接至協力廠商 API，例如 Google Cloud Speech-to-Text，而不使用 {{site.data.keyword.texttospeechshort}} 或 {{site.data.keyword.speechtotextshort}}。
* **[使用其他 {{site.data.keyword.Bluemix_notm}} 工作區中的服務](/docs/services/voice-agent?topic=voice-agent-other_service)：**您可以將語音代理程式配置成使用 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.speechtotextshort}} 服務實例，而這些服務實例屬於其他 {{site.data.keyword.Bluemix_short}} 帳戶中的工作區。
* **[使用服務編排引擎配置 Watson Assistant](/docs/services/voice-agent?topic=voice-agent-conversation_va)：**您可以透過服務編排引擎 (SOE) 連接至 {{site.data.keyword.conversationshort}} 技能。SOE 會將訊息截取至服務並從中截取訊息，讓您可以使用協力廠商 API 進行修改。
* **[為語音代理程式啟用事件轉遞](/docs/services/voice-agent?topic=voice-agent-event_forwarding)：**您可能想要收集及分析來自 {{site.data.keyword.iva_short}} 的通話資料，以改善交談對來電者的自然程度。您建立的每一個語音代理程式都可以將事件報告轉遞至您管理的指定 {{site.data.keyword.cloudant_short_notm}}。

## 配置進階語音代理程式選項
{: #config-advanced}

建立或複製語音代理程式時，您可以按一下**顯示進階**，來檢視下列進階配置選項。

* **交談閱讀逾時（選用）**：這個選項設定語音代理程式等待 Watson Assistant 回應的時間（以秒為單位）。如果超出此時間，語音代理程式會重新嘗試與 Watson Assistant 聯絡。如果仍無法聯繫服務，則通話失敗。依預設，設為 5 秒。
* **{{site.data.keyword.conversationshort}} 失敗回覆訊息（選用）**：通話無法連接至 {{site.data.keyword.conversationshort}} 時，要傳送給訊息接收者的預設回覆訊息。您最多可以輸入 1024 個字元。
* **轉接失敗回覆訊息（選用）**：通話轉接失敗時，要串流給來電者的預設回覆訊息。您最多可以輸入 1024 個字元。
* **自訂 SIP INVITE 標頭（選用）**：指定要從送入的 SIP INVITE 要求擷取的自訂 SIP 標頭。您最多可以輸入 1024 個字元。
* **從 {{site.data.keyword.iva_short}} 傳送暫時鈴聲回應**：當 {{site.data.keyword.iva_short}} 處理送入的通話時，傳送 `180 ringing` 回應。預設為啟用。
* **轉接時保留通話**：在轉接期間讓來電者進入保留狀態。預設為啟用。
* **轉接失敗時中斷通話**決定通話轉接失敗時，是否中斷通話。預設為啟用。如果設定為已停用且通話轉接失敗，則 {{site.data.keyword.iva_short}} 會起始一個回合的交談。然後，{{site.data.keyword.conversationshort}} 可以中斷通話，或將它轉接至對話中所配置的不同目的地。
* **發生網路事件時通知 {{site.data.keyword.conversationshort}}**：啟用且偵測到錯誤時，{{site.data.keyword.iva_short}} 會以文字 "vgwNetworkWarningMessage" 對 {{site.data.keyword.conversationshort}} 服務起始一個回合。`vgwNetworkWarnings` 狀態變數包含在現行回合期間發生之網路事件的清單。如果已停用，則在現行回合期間發生之網路事件的清單，會以 `vgwNetworkWarning` 狀態變數中的下一回合事件進行傳送。預設為啟用。
