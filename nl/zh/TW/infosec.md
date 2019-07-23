---

copyright:
  years: 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 資訊安全及資料隱私
{: #infosec}

IBM 致力於提供客戶和合作夥伴創新的資料隱私、安全及控管解決方案。
{: shortdesc}

## 資訊處理及配置選項
{: #configure_infosec}

為操作服務並最佳化使用者體驗，{{site.data.keyword.iva_short}} 將收集及儲存一組最小的個人資訊 (PI)，該資訊將依據我們的[資料處理附錄 (DPA)](https://www.ibm.com/support/customer/csol/terms/){: new_window} 和 [DPA 證明文件](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=00C4CE004FA711E7AA10752A2F494A7C){: new_window}來處理。{{site.data.keyword.iva_short}} 不存儲、收集或處理屬於任何語音或 SMS 交談的資料。相反地，資料會遞送至不同的服務以進行處理。在交談期間，使用者可能會分享包含受保護健康資訊 (PHI)、個人識別資訊 (PII) 或 PCI 資料安全標準 (PCI DSS) 資料的資訊。請參閱[架構](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}，以進一步瞭解 {{site.data.keyword.iva_short}} 的交談流程和架構。

在配置語音代理程式實例以便支援資料隱私和安全處理時，請考量下列特性。

### 通話轉接
{:  #calltransfer_infosec}

為語音代理程式新增通話轉接功能時，您會在配置轉接目標 SIP URI 時提供電話號碼。使用者不應該針對此轉接目標提供個人電話號碼。

請參閱[設定通話轉接](/docs/services/voice-agent?topic=voice-agent-call-transfer)，以瞭解如何針對通話轉接配置 SIP 幹線及 SIP URI。

### 事件轉遞
{: #infosec_event_forwarding}

您可以將語音代理程式配置成將報告事件轉遞至 {{site.data.keyword.cloudantfull}} 資料庫實例。這些報告事件可能包含關於來電者的 PII、PHI 及 PCI DSS 資料，其格式為轉錄、Conversation 各回交談事件，以及呼叫詳細記錄 (CDR) 事件。在 {{site.data.keyword.iva_short}} 內不會儲存、處理或收集通話資料、SMS 資料及報告事件，使用者應該適當地配置其外部 {{site.data.keyword.cloudant_short_notm}} 服務。**依預設，會停用事件轉遞。**

請參閱[啟用事件轉遞](/docs/services/voice-agent?topic=voice-agent-event_forwarding)，以將語音代理程式配置為轉遞報告事件。

請參閱 [**{{site.data.keyword.cloudant_short_notm}}：安全**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}，以取得 {{site.data.keyword.cloudant_short_notm}} 的資料隱私和資訊安全相關資訊。

### Text to Speech 快取
{: #tts_caching}

為了與客戶交談，{{site.data.keyword.conversationshort}} 會將回應製作為文字、傳給 {{site.data.keyword.texttospeechshort}} 服務，然後在 {{site.data.keyword.iva_short}} 大聲朗讀。{{site.data.keyword.conversationshort}} 建立的回應可能會包含機密性資訊。要避免 {{site.data.keyword.iva_short}} 快取從 {{site.data.keyword.texttospeechshort}} 服務所收到、包含個人資料的回應，您可以啟用 `vgwActExcludeFromTTSCache` 動作指令，排除包含特定類型資訊的話語不要快取。請參閱[使用 API 程式設計語音代理程式](/docs/services/voice-agent?topic=voice-agent-api#action-sequences)。

在刪除「語音代理程式」實例之後，即會在 24 小時內清除 TTS 快取。這稱為 `TTS 快取逾時值`。

### 安全連線
{: #secure_trunking}

{{site.data.keyword.iva_short}} 是以 {{site.data.keyword.Bluemix_notm}} 為基礎，並且與使用者配置的 SIP 幹線整合。由於 SIP 幹線屬於外部，且會連接至 {{site.data.keyword.iva_short}}，您可以在 SIP 幹線與 {{site.data.keyword.iva_short}} 之間使用「安全即時傳輸通訊協定 (SRTP)」啟用安全連線，以及使用安全 SIP (SIPS) 啟用加密。SIPS 是依賴「傳輸層安全 (TLS)」。請參閱[保護連線安全](/docs/services/voice-agent?topic=voice-agent-securing)。

依預設，SMS 資料已使用 TLS 加密。如需相關資訊，請參閱 [Voice Gateway：資料處理](https://www.ibm.com/support/knowledgecenter/en/SS4U29/gdpr_considerations.html#GDPR_dataProcessing){: new_window}。

### 服務編排引擎 (SOE) 配置
{: #SOE_config}

您可以使用「服務編排引擎 (SOE)」來處理 {{site.data.keyword.iva_short}} 與 {{site.data.keyword.conversationshort}} 之間的資訊傳遞，以便自訂與來電者的交談。若要維護安全連線，請務必使用安全 URL `https` 和使用者鑑別來配置 SOE。

請參閱[為語音代理程式配置 {{site.data.keyword.conversationshort}}](/docs/services/voice-agent?topic=voice-agent-conversation_va#conversation_va) 和[具有服務編排引擎的架構](/docs/services/voice-agent?topic=voice-agent-about#arch-soe)。

## SMS/MMS 支援
{: #SMS_MMS}

### 資料處理
{: #data_handling}

{{site.data.keyword.iva_short}} 不存儲、收集或處理 SMS 資料。MMS 影像存儲在我們的服務之外，由服務提供者處理。客戶必須參考其 SMS 提供者的安全/隱私合約。{{site.data.keyword.iva_short}} 僅處理嵌入在 SMS 訊息中的影像的文字鏈結。

當服務編排引擎或 {{site.data.keyword.conversationshort}} 將 MMS 訊息傳送至使用者（含有或不含 SMS 文字訊息）時，一個以上公用可存取的媒體 URL 即會傳送至 Twilio。Twilio 不支援非公用 URL。使用者應避免透過 MMS 傳送機密或個人資訊。

{{site.data.keyword.iva_short}} 會遮罩訊息日誌中的來電顯示，以避免收集這類型的個人識別資訊。

### 鑑別
{: #authentication}

透過使用 [IAM 鑑別](/docs/services/voice-agent?topic=voice-agent-iam#sms_access){: new_window}，服務提供者可保護入埠 SMS 訊息的安全。

## 與 {{site.data.keyword.iva_short}} 相關的服務
{: #related_services}

{{site.data.keyword.iva_short}} 會編排不同的 {{site.data.keyword.Bluemix_notm}} 服務，以協調一般使用者與雲端認知服務之間的通訊。{{site.data.keyword.iva_short}} 本身不會以違反一般使用者權利的方式儲存、收集或處理資料。不過，視您配置相關服務的方式而定，這些整合式服務可能會收集使用者在交談期間分享的受保護健康資訊 (PHI)、個人識別資訊 (PII) 或 PCI 資料安全標準 (PCI DSS) 資料。若要瞭解 {{site.data.keyword.iva_short}} 架構及交談流程，請參閱[架構](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}。

請參閱下列資源，以尋找每個服務和 {{site.data.keyword.Bluemix_notm}} 的考量。

  * [**{{site.data.keyword.Bluemix_short}}：安全規範**](/docs/overview?topic=overview-security#security)
  * [**{{site.data.keyword.conversationfull}}：資訊安全**](/docs/services/assistant?topic=assistant-information-security#information-security){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}：資訊安全**](/docs/services/text-to-speech?topic=text-to-speech-information-security){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}：資訊安全**](/docs/services/speech-to-text?topic=speech-to-text-information-security){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}：安全**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}
