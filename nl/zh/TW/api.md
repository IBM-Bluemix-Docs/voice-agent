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

# 使用 API 程式設計語音代理程式
{: #api}

您可以藉由從 {{site.data.keyword.conversationfull}} 服務內定義動作標籤及狀態變數，來控制語音代理程式的行為。動作標籤會起始您的語音代理程式在交談階段作業期間所採取的動作，而且除非另有變更，否則狀態變數會定義在整個交談都會持續保存的語音代理程式特徵。
{: shortdesc}

因為 {{site.data.keyword.iva_full}} 是以 IBM Voice Gateway 為基礎，所以 API 的運作方式會相同。如果您熟悉 Voice Gateway，則可以在 {{site.data.keyword.conversationshort}} 對話中使用與 {{site.data.keyword.iva_short}} 相同的動作及狀態變數。請參閱 [Voice Gateway API 中的動作標籤及狀態變數](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html)。
{: tip}

## 編輯對話回應中的 JSON
{: #json-editor}

動作及狀態都定義在 JSON 格式的對話節點回應中。若要編輯 JSON 程式碼，請開啟 JSON 編輯器。

1. 從 {{site.data.keyword.Bluemix_short}} 儀表板中，選取您的 {{site.data.keyword.conversationshort}} 服務實例。
1. 啟動 {{site.data.keyword.conversationshort}} 工具。
1. 按一下包含您要編輯之對話的工作區。
1. 移至**對話**標籤，然後選取您要設定動作或狀態的節點。
1. 在回應中，按一下 ![進階回應](../conversation/images/kabob.png) 圖示，然後選取**開啟 JSON 編輯器**。

在 JSON 編輯器內，您可以在 `output` 內容上定義動作，以及在 `context` 內容上定義狀態，如下列各節所述。

## 起始動作
{: #defining-actions}

若要在通話期間於語音代理程式中起始動作，您可以在 `output` 內容上，以 JSON 格式定義 {{site.data.keyword.conversationshort}} 對話節點上的動作標籤。您可以在 `vgwAction` 標籤上定義單一動作，或是在 `vgwActionSequence` 標籤上定義一系列的動作。每一個動作各包含一個 `command` 內容，後面接著選用性的 `parameter` 內容，用來為需要它們的指令定義屬性。

### 單一動作
{: #single-actions}

若要執行單一動作，請在 `vgwAction` 標籤中，使用任何必要的參數屬性來定義動作。在 `output` 內容的 `text` 區塊中，您可以選擇性地包含語音代理程式在執行動作之後所播放的話語。

`vgwAction` 標籤上的下列單一動作會告知語音代理程式在觸發節點回應時掛斷通話。因為 `vgwActHangup` 指令沒有參數，所以未定義任何參數。
```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActHangup"
    }
  }
}
```
{: codeblock}

下列動作會告知語音代理程式收集雙音多頻信號 (DTMF) 輸入，並對來電者播放已定義的文字。

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActCollectDtmf",
      "parameters": {
        "dtmfTermKey": "#"
      }
    },
    "text": {
      "values": [
        "Enter your phone number."
      ]
    }
  }
}
```
{: codeblock}

### 動作序列
{: #action-sequences}

若要對單回交談執行一個以上動作，您可以在 `vgwActionSequence` 標籤內，以 JSON 清單形式定義一系列的動作。動作會依照您定義的順序來執行。

與單一動作不同，若要讓語音代理程式在使用 `vgwActionSequence` 標籤時播放話語，動作清單必須包含 `vgwActPlayText` 動作。不同於 `vgwAction` 標籤，`output.text` 欄位中的話語不會自動播放。
{: tip}

在下列較複雜的範例中，`vgwActionSequence` 標籤上所定義的動作，會告知語音代理程式停用語音轉文字處理，並在播放話語時收集 DTMF 輸入。

```json
{
  "output": {
    "vgwActionSequence": [
      {
        "command": "vgwActPauseSTT"
      },
      {
        "command": "vgwActCollectDtmf",
        "parameters": {
          "dtmfTermKey": "#"
        }
      },
      {
        "command": "vgwActPlayText",
        "parameters": {
          "text": [
            "Enter your social security number."
          ]
        }
      }
    ]
  }
}

```
{: codeblock}


### 動作指令及屬性
{: #actions-and-attributes}

下表列出您可以在 {{site.data.keyword.conversationshort}} 對話中指定的動作，以及您可以為每一個動作定義的所有屬性。

|動作指令       |說明        |屬性       |
| ----- | ----- | ----- |
|`vgwActPlayText`|播放 {{site.data.keyword.texttospeechshort}} 服務轉換為語音的話語。| <ul><li>`text`：要播放的話語清單。選用項目。<p>例如：<br/><code>"text": [<br/>&nbsp;&nbsp;&nbsp;"Hello. How can I help you today?"<br/>&nbsp;&nbsp;&nbsp;]</code><p> 依預設，此動作會播放 `output.text` 欄位中所配置的話語清單。</li><li>`errAudioURL`：音訊檔的 URL，可在語音代理程式無法與 {{site.data.keyword.texttospeechshort}} 服務聯絡以完成動作時播放音訊檔。音訊檔必須是 WAV 格式。</li></ul>|
|`vgwActPlayUrl` |只要一播放所包含的文字，就播放音訊檔，例如，播放保留通話期間的背景音樂 (MOH)，或一般的一次性話語。如果未包括任何文字，就會立即播放音訊。檔案必須是單聲道 (mono)、PCM 編碼，並且取樣率為 8,000 Hz，且每個樣本為 16 位元。| <ul><li>`url`：要播放的 URL。必要項目。</li><li> `playURLInLoop`：選擇性地設為 `Yes` 或 `No`，指出是否重複播放 URL。預設值為 `No`。</li></ul> |
|`vgwActHangup` |掛斷通話。|沒有屬性。|
|`vgwActSetSTTConfig` |套用語音代理程式的一組參數，以傳遞至 Watson {{site.data.keyword.speechtotextshort}} 服務。{{site.data.keyword.conversationshort}} 服務會根據通話動態地定義參數。|屬性會以 JSON 內容形式透通地傳遞至 {{site.data.keyword.speechtotextshort}} 服務。|
|`vgwActSetTTSConfig` |套用語音代理程式的一組參數，以傳遞至 Watson {{site.data.keyword.texttospeechshort}} 服務。{{site.data.keyword.conversationshort}} 服務會根據通話動態地定義參數。|屬性會以 JSON 內容形式透通地傳遞至 {{site.data.keyword.texttospeechshort}} 服務。|
|`vgwActSetConversationConfig` |套用語音代理程式的一組參數，以定義 {{site.data.keyword.conversationshort}} 工作區。{{site.data.keyword.conversationshort}} 服務會根據通話動態地定義參數。| <ul><li>`url`：{{site.data.keyword.conversationshort}} 服務 API 的 `url` 認證。</li><li>`workspaceID`：{{site.data.keyword.conversationshort}} 工作區 ID</li><li>`username`：{{site.data.keyword.conversationshort}} 服務的 `username` 認證。</li><li>`password`：{{site.data.keyword.conversationshort}} 服務的 `password` 認證。</li></ul> |
|`vgwActCollectDtmf` |指示語音代理程式收集雙音多頻信號 (DTMF) 輸入。|必須定義下列其中一個屬性。<ul><li> `dtmfTermKey`：DTMF 終止鍵，以信號示意 DTMF 輸入結束。例如，"`#`"。</li><li> `dtmfCount`：要收集的 DTMF 位數。</li></ul> 符合上述任一條件時，語音代理程式就會停止收集 DTMF 輸入。|
|`vgwActPauseDTMF` |停用 DTMF 輸入。會忽略所有 DTMF 輸入，直到 `vgwActUnPauseDTMF` 動作重新啟用它為止。|沒有屬性。|
|`vgwActUnPauseDTMF` |啟用 `vgwActPauseDTMF` 動作已停用的 DTMF 輸入。|沒有屬性。|
|`vgwActExcludeFromTTSCache` |指示語音代理程式不要快取來自 {{site.data.keyword.texttospeechshort}} 服務的回應。例如，如果回應包含機密的 PHI、PII 及 PCI DSS 資料或動態資訊（例如客戶名稱或出生日期），則應該予以排除。<br/>針對您不要快取的每一個話語，必須在 {{site.data.keyword.conversationshort}} 對話節點上設定此動作標籤。|沒有屬性。|
|`vgwActPauseSTT` |暫停語音轉文字處理，直到 `vgwActUnPauseSTT` 動作重新啟用它為止。如果已啟用記錄，並暫停語音轉文字處理，則不會擷取來自來電者的音訊。|沒有屬性。|
|`vgwActUnPauseSTT` |繼續 `vgwActPauseSTT` 動作先前所暫停的語音轉文字處理。|沒有屬性。|
|`vgwActEnableSpeechBargeIn` |啟用語音插話，讓來電者可以透過發言來岔斷語音代理程式的播放。|沒有屬性。|
|`vgwActDisableSpeechBargeIn` |停用語音插話，在來電者發言時，不會岔斷語音代理程式的播放。|沒有屬性。|
|`vgwActEnableDTMFBargeIn`|啟用 DTMF 插話，讓來電者可以透過按下按鍵來岔斷語音代理程式的播放。|沒有屬性。|
|`vgwActDisableDTMFBargeIn` |停用 DTMF 插話，在來電者按下按鍵時，不會岔斷語音代理程式的播放。|沒有屬性。|
|`vgwActForceNoInputTurn` |不等待來自來電者的輸入，即強行進入新一回合的交談。|沒有屬性。|
{: caption="表 1. 您可從 {{site.data.keyword.conversationshort}} 服務起始的動作" caption-side="top"}

## 設定狀態
{: #setting-states}

為了指出兩回交談之間持續的狀態變更，語音代理程式會與所配置的 {{site.data.keyword.conversationfull}} 服務交換狀態變數。在 {{site.data.keyword.conversationshort}} 對話節點上，這些狀態變數定義為 JSON 格式的[環境定義變數](https://console.bluemix.net/docs/services/conversation/dialog-build.html#context)。

例如，您可以定義下列狀態變數，以設定與 {{site.data.keyword.conversationshort}} 服務的連線失敗時，要串流給來電者的訊息。

```json
{
  "context": {
    "vgwConversationFailedMessage": "Sorry, we're unable to connect you to our help line. Please try again later."
  }
}
```
{: codeblock}

語音代理程式假設 {{site.data.keyword.conversationshort}} 服務沒有狀態，而且在與 {{site.data.keyword.conversationshort}} 服務進行的交換之間，所有狀態會在語音代理程式上維護。針對通話內的每一回合交談，都會將狀態傳遞至 {{site.data.keyword.conversationshort}} 服務，並在 REST 訊息之 `context` 區段中從服務收回狀態。

### {{site.data.keyword.conversationshort}} 對話中設定的狀態變數
{: #state-variables-conv}

您可以在 {{site.data.keyword.conversationshort}} 對話內設定下列狀態變數，以修改語音代理程式的行為。

|狀態變數名稱        |期望值         |說明        |
| -------------- | ------ | ----------- |
|`vgwByeCustomHeader` |使用者定義 |在送出的 SIP BYE 訊息中定義自訂標頭。自訂標頭值由 `vgwByeCustomHeaderVal` 狀態變數所定義。|
|`vgwByeCustomHeaderVal` |使用者定義 |在送出的 SIP BYE 訊息中定義自訂標頭的值。自訂標頭由 `vgwByeCustomHeader` 狀態變數所定義。|
|`vgwPostResponseTimeoutCount` |時間（以毫秒為單位）|在播放回應給來電者之後，等待新話語的時間量。如果超出此值，則 {{site.data.keyword.conversationshort}} 會收到內含 "vgwPostResponseTimeout" 這個字的文字更新，指出發生逾時。|
|`vgwConversationFailedMessage` |字串 |{{site.data.keyword.conversationshort}} 服務失敗時串流給來電者的訊息。配置 {{site.data.keyword.conversationshort}} 對話，以在第一回合設定此變數。|
|`vgwSessionInactivityTimeout` |時間（以分鐘為單位）<br/><br/>預設值：`2` |閒置逾時間隔。逾時間隔值指定語音代理程式容許階段作業處於非作用中的時間長度（以分鐘為單位）。逾時到期時，語音代理程式就會結束階段作業。|
|`vgwErrAudioURL` |使用者定義 |音訊檔的 URL，可在語音代理程式嘗試播放回應但無法與 {{site.data.keyword.texttospeechshort}} 服務聯絡時播放。音訊檔必須是 WAV 格式。|
{: caption="表 2. {{site.data.keyword.conversationshort}} 服務所設定的變數" caption-side="top"}

### 語音代理程式所設定的狀態變數
{: #state-variables-iva}

|狀態變數名稱        |期望值         |說明        |
| -------------- | ----- | ----------- |
|`vgwSessionID`   |使用者定義 <br/><br/> 預設值：`Call-ID` |從 SIP INVITE 要求取回的自訂階段作業 ID 標頭。此值代表廣域階段作業 ID，而廣域階段作業 ID 用於所有與階段作業相關的語音代理程式審核日誌中。|
|`vgwSIPCallID` |SIP `Call-ID` |與通話相關聯的 SIP 通話 ID。|
|`vgwSIPRequestURI` |SIP `Request-URI` |已啟動通話的 SIP 要求 URI。|
|`vgwSIPToURI` |SIP `To` URI |與通話相關聯的 SIP `To` URI。|
|`vgwSIPFromURI` |SIP `From` URI |與通話相關聯的 SIP `From` URI。|
|`vgwBargeInOccurred` |`Yes`/`No` |指出是否發生插話。|
|`vgwHangUp` |`Yes`/`No` |指出是否結束交談。|
|`vgwHangupReason` |字串 |來電者起始掛斷或因錯誤而起始掛斷時，會將此變數傳送至 {{site.data.keyword.conversationshort}} 服務，指出通話中斷的原因。傳送至 {{site.data.keyword.conversationshort}} 服務之訊息要求中的文字也會包括 "vgwHangUp"。|
|`vgwConversationResponseTimeout` |時間（以秒為單位）<br/><br/>預設值：`5` |語音代理程式等待 {{site.data.keyword.conversationshort}} 服務回應的時間（以秒為單位）。如果超出此時間，語音代理程式會重新嘗試與 {{site.data.keyword.conversationshort}} 服務聯絡。如果仍無法聯繫服務，則通話失敗。|
|`vgwSTTResponse` |JSON 物件 |{{site.data.keyword.speechtotextshort}} 服務的最終回應（採用 JSON 格式），包括偏好假設及任何替代方案的記錄及信任評分。<p>例如，下列格式完全符合從 {{site.data.keyword.speechtotextshort}} 服務收到的格式：</p><p><code>{<br/>&nbsp;&nbsp;"result_index": 0,<br/>&nbsp;&nbsp;"warnings": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;"Unknown arguments: continuous."<br/>&nbsp;&nbsp;],<br/>&nbsp;&nbsp;"results": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"final": true,<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"alternatives": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello world",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.758<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello wooled",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.358<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;]<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}.</code></p> |
|`vgwIsDTMF` |`Yes`/`No` |指出 {{site.data.keyword.conversationshort}} 服務的輸入是否為雙音多頻信號 (DTMF)。|
{: caption="表 3. 語音代理程式所設定的變數" caption-side="top"}
