---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 疑難排解及支援
{: #troubleshooting}

使用 {{site.data.keyword.iva_full}} 時遭遇問題嗎？請檢閱一般問題的疑難排解提示，並聯繫社群以瞭解所有問題。
{: shortdesc}

## 如何疑難排解{{site.data.keyword.iva_short}}
{: #how-to}

若要疑難排解您的語音代理程式，您可以使用 logging、usage 及 event-forwarding，來尋找錯誤及失敗的記錄。這些記錄可協助您診斷及解決語音代理程式發生的問題。如果您有 {{site.data.keyword.iva_short}} 方面的問題，請嘗試下列步驟。

1. 當通話失敗時，最後的 {{site.data.keyword.conversationshort}} 回合可能會解釋該失敗。

1. 使用情形日誌會顯示在特定通話期間可能已發生的任何錯誤。請參閱[檢視用量及通話日誌](logging.html)。

1. 檢查您的服務提供者日誌，是否有信號錯誤。例如，Twilio 會針對其管理的每個 SIP 幹線提供日誌。

1. 藉由[對語音代理程式啟用事件轉遞](event-forwarding.html)，您可以配置語音代理程式，以將「通話詳細記錄 (CDR)」傳送至 Cloudant 資料庫，然後判斷通話為何失敗。其他事件（例如「{{site.data.keyword.conversationshort}} 回合事件」）可以提供通話內每個交談回合的詳細資料。

**重要事項：**CDR、轉錄及回合事件包括使用者的資訊，而這些資訊可能包含「受保護健康資訊 (PHI)」、個人識別資訊 (PII) 或「PCI 資料安全標準 (PCI DSS)」資料。若要防止公開個人資訊，您必須確保 {{site.data.keyword.cloudant_short_notm}} 實例適當地保護使用者在交談中或交談期間分享的機密資訊。


## 取得協助
{: #help}

如果您需要協助，請將問題或意見張貼到下列積極監視中的任何位置，加入我們的開發人員社群。

* 使用 `voice-agent` 標籤，張貼在 [dwAnswers 討論區 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/topics/voice-agent/) 上
* 使用 `voice-agent` 標籤，張貼在 [StackOverflow ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://stackoverflow.com/questions/tagged/voice-agent){: new_window} 上
* 透過 `#ibmvoicegateway` 頻道，在 [IBM Cloud Technology ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) 團隊中於 Slack 上尋找我們

**記住**：在張貼通話的任何日誌或記錄之前，請先移除您的來電者及使用者可能在交談期間分享的所有個人資訊。

## 疑難排解提示
{: #troubleshooting-tips}

### 當我撥打語音代理程式時，為何在電話上未收到回應？

您的通話可能未連接至服務。未正確設定 {{site.data.keyword.iva_short}} 服務實例時會發生此問題。請檢查下列語音代理程式設定：

* 驗證語音代理程式_管理_ 儀表板上的電話號碼，與 SIP 幹線提供者（例如 NetFoundry 或 Twilio）的電話號碼是否相同。

   **附註：**在語音代理程式_管理_ 儀表板上指定電話號碼時，您必須包括國碼及區域碼。例如，`18884253968`。

* 驗證 Watson 服務認證、URL 及 {{site.data.keyword.conversationshort}} 工作區 ID 都是有效的。
* 驗證已正確建立 {{site.data.keyword.conversationshort}} 工作區中的對話。
  * 針對預先建置的工作區，您可以從 GitHub 匯入[範例交談 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json)。如需在 {{site.data.keyword.conversationshort}} 工具中將範例交談儲存為 JSON 檔案後將該檔案匯入為工作區的詳細資料，請參閱[*入門指導教學* 中的步驟 3](getting-started.html#step3)。
  * 如果您已建立自己的 {{site.data.keyword.conversationshort}} 對話，則請驗證對話包含具有 `conversation_start` 條件的節點，以及具有預設回應的節點。如需詳細指示，請參閱 {{site.data.keyword.conversationshort}} 文件中的[建置對話](../conversation/dialog-build.html)。
* 查看您的通話是否列在語音代理程式的_用量_ 儀表板上。如果您看到通話的項目，則表示您的語音代理程式已連接至 Watson 服務。

### 建立語音代理程式時，為何無法指定電話號碼？

請查看現有語音代理程式是否使用您指定的電話號碼。一個電話號碼只能有一個語音代理程式。您可以從 SIP 幹線提供者佈建另一個電話號碼，並使用它來建立另一個語音代理程式。或者，[刪除_管理_ 儀表板上的現有語音代理程式](managing.html#delete_va)以釋放電話號碼，然後建立新的語音代理程式。

### 為何我的通話經常失敗？

當通話失敗，因為「服務編排引擎 (SOE)」起始一個長時間的交易，而未及時回應您的語音代理程式時，語音代理程式可能會發生問題。如果交易超過預設 {{site.data.keyword.conversationshort}} 逾時，通話便會失敗。若要避免通話失敗，SOE 可以使用 `vgwConversationResponseTimeout` 狀態變數，來修改預設 {{site.data.keyword.conversationshort}} 逾時。請參閱 [{{site.data.keyword.conversationshort}} 對話中的變數集](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html#variables-conv)。
