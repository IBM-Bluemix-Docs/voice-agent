---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-01"

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

## 設定狀態
{: #setting-states}

為了指出兩回交談之間持續的狀態變更，語音代理程式會與所配置的 {{site.data.keyword.conversationfull}} 服務交換狀態變數。在 {{site.data.keyword.conversationshort}} 對話節點上，這些狀態變數定義為 JSON 格式的[環境定義變數](../conversation/dialog-build.html#context)。

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
