---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-06-24"

keywords: voice agent, creating a SIP trunk, creating and connecting your voice agent,

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 入門指導教學
{: #getting-started}
{{site.data.keyword.iva_full}} 可協助您使用「階段作業起始通訊協定 (SIP)」，將一組編排的 Watson 服務與電話網路整合。本指導教學說明如何設定可從任何電話通話的認知語音代理程式。
{: shortdesc}

{{site.data.keyword.iva_full_notm}} 中新增了新的 SMS 特性。並非此頁面中說明的所有程序都是配置 SMS 功能所必需的。有關如何將 SMS 與 {{site.data.keyword.iva_full_notm}} 連接的指示，請參閱[語音代理程式入門指導教學](/docs/services/voice-agent?topic=voice-agent-connect-sms)
{: tip}

觀看本 [{{site.data.keyword.iva_full_notm}} 指導教學 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/) 中如何建立第一個語音代理程式的示範。
{: tip}

如果您需要任何協助，請在 Slack 上找到我們，位置是在 [IBM Cloud Technology ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) 團隊的 `#ibmvoicegateway` 頻道。
{: tip}

## 開始之前
{: #prereqs}

建立新帳戶，或在 [{{site.data.keyword.Bluemix_short}}](https://cloud.ibm.com/) 登入現有帳戶。

## 步驟 1：在 {{site.data.keyword.Bluemix_notm}} 上建立 {{site.data.keyword.iva_short}} 服務實例
{: #step1}

從 [{{site.data.keyword.iva_short}} 型錄頁面](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)中，檢閱服務資訊，然後按一下**建立**。

建立服務之後，請記下_開始使用_ 儀表板上的語音代理程式端點。您需要端點 SIP URI，才能配置 SIP 幹線。

## 步驟 2：建立 SIP 幹線，以將通話轉遞至 {{site.data.keyword.iva_short}}
{: #step2}

1. 從下列任何支援的提供者建立 SIP 幹線。然後，將電話號碼與您的 SIP 幹線相關聯。

  * [NetFoundry](/docs/services/voice-agent?topic=voice-agent-connect#NetFoundry-setup)
  * [Twilio](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup)
  * [AT&T 及其他 SIP 幹線提供者](/docs/services/voice-agent?topic=voice-agent-connect#att-other)
  * [與 {{site.data.keyword.iva_short}}](/docs/services/voice-agent?topic=voice-agent-connect#peering) 對等

## 步驟 3：建立及連接語音代理程式
{: #step3}

1. 移至 {{site.data.keyword.iva_short}} 儀表板上的_管理_ 儀表板，然後按一下**建立語音代理程式**。

2. 輸入語音代理程式的基本設定：
  * **名稱：**語音代理程式的唯一名稱，例如 `Customer Support`
  * **電話號碼：**您與 SIP 幹線相關聯的完整電話號碼（包括國碼及區域碼）。例如，若為美國 800 號碼，請將電話號碼指定為 18883334444。電話號碼可以有空格及 + ( ) - 字元。
  * **說明：**其用法的選用性說明
  * **預設轉接目標：**通話可以轉接到的選用性終止 URI。

3. 建立語音代理程式的 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 及 {{site.data.keyword.texttospeechshort}} 服務實例。您可以選擇使用下列一種方法來建立語音代理程式：
  * 按一下**建立語音代理程式**，透過單一步驟以使用預設配置來建立所有服務及語音代理程式。
  * 或者，按一下每一個服務名稱以自行建立服務。然後，回到 {{site.data.keyword.iva_short}} 並分別建立語音代理程式。

   如果您已手動建立 {{site.data.keyword.conversationshort}} 服務實例，則請新增對話，以測試語音代理程式。若要快速開始使用，請從 GitHub 複製[範例交談 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json)，然後[匯入範例](/docs/services/assistant?topic=assistant-skill-dialog-add)作為技能：

   1. 在範例交談 GitHub 頁面上，按一下行號 `1`，然後選取 **... > 複製行**。將複製的文字貼入檔案中，並將其儲存為 JSON 檔案，例如 `voice-gateway-conversation-en.json`。
   2. 啟動 {{site.data.keyword.conversationshort}} 工具。在_技能_ 頁面上，按一下 ![匯入工作區](../conversation/images/workspace_import.png) 圖示，然後匯入 JSON 檔案。

  或者，您也可以[建置自己的對話](/docs/services/assistant?topic=assistant-getting-started#getting-started-build-dialog)來模擬正式作業環境。您的對話至少必須包含具有 `conversation_start` 條件的節點，以及具有預設回應的節點。


## 後續步驟
{: #next-steps}

藉由與其相關聯的電話號碼通話，來測試語音代理程式。如果您聽到回應，表示您的語音代理程式作用中！

如果您未聽到回應，則可以在_用量_ 儀表板上檢查通話日誌及語音代理程式使用情形。請參閱[檢視用量及通話日誌](/docs/services/voice-agent?topic=voice-agent-logging)。

您可以編輯語音代理程式的設定、建立或移除語音代理程式，以及從_管理_ 儀表板中將多個 Watson 服務位置新增至語音代理程式。如需相關資訊，請參閱[管理語音代理程式](/docs/services/voice-agent?topic=voice-agent-managing)。

您也可以從 Twilio 帳戶配置進階設定（例如保護 SIP 連線安全）。請參閱[保護連線安全](/docs/services/voice-agent?topic=voice-agent-securing)。
