---

copyright:
  years: 2018
lastupdated: "2018-06-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 設定通話轉接
{: #call-transfer}

您可以設定通話轉接，因此，如果來電者在交談期間要求與即時代理程式交談，則語音代理程式會自動轉接該通話。
{: shortdesc}

## 關於通話轉接
{: #about-ct}

透過啟用通話轉接，如果來電者在交談期間要求與即時代理程式交談，則語音代理程式將會重新導向該通話。您可以藉由在 SIP 提供者配置中設定終止 URI，啟用通話轉接。然後，您可以在 {{site.data.keyword.conversationshort}} 實例的對話節點，在 API 動作上定義轉接目標。您的轉接目標是包含終止 URI 及電話號碼的 SIP URI。如需所支援動作以及自訂語音代理程式的相關資訊，請參閱[使用 API 程式設計語音代理程式](api.html)。

## 步驟 1：設定終止 URI
{: #termination-setup}

### 在 NetFoundry 中設定終止 URI
{: #termination-netfoundry}

記下 [NetFoundry 帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson.netfoundry.io/watson-login){: new_window} 中您要轉接到的電話號碼。稍後，您可以在 {{site.data.keyword.conversationshort}} 對話中將此電話號碼及終止 URI 指定為轉接目標。請不要使用個人電話號碼。

您可以複製下列 NetFoundry 終止 URI，以用於轉接目標。

```
dal.watson-va.netfoundry.net
```
{: codeblock}

[配置 {{site.data.keyword.conversationshort}} 進行通話轉接時](#conversation-setup)，您不需要在 NetFoundry 中手動配置終止 URI。

### 在 Twilio 中設定終止 URI
{: #termination-Twilio}

1. 在 Twilio 帳戶中，導覽至_彈性 SIP 幹線_ 儀表板，然後選取**幹線**。

1. 選擇要新增通話轉接的幹線，方法是選取現有幹線，或按一下 **+** 圖示來建立新的幹線。

  * 如果您建立新幹線，則需要在**起源**儀表板中配置 _SIP 幹線 URI_。如需相關資訊，請參閱[連接 SIP 幹線](connect-SIP.html)。

1. 在導覽列上選取**終止**，然後輸入終止 URI 的名稱。

  * 終止 URI 名稱必須是唯一的。Twilio 會自動檢查您針對可用性所選擇的名稱。如需 Twilio 服務的詳細資料，請參閱 [SIP 幹線終止設定 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window}。

1. 在_鑑別_ 區段中，按一下 **+** 圖示，將語音代理程式 IP 位址新增至「存取控制 IP」清單。

  新增下列兩個 IP 位址：
   * 169.60.154.134（美國南部服務地區）
   * 169.61.86.179（美國東部服務地區）

1. 按一下**儲存**，完成終止 URI 的配置。

請記下您要轉接到的電話號碼及終止 URI。請確定電話號碼不是個人電話號碼。您可以在 {{site.data.keyword.conversationshort}} 對話中，使用電話號碼及終止 URI 來指定轉接目標。


## 步驟 2：配置 {{site.data.keyword.conversationshort}} 以進行通話轉接
{: #conversation-setup}

若要進一步瞭解如何在 {{site.data.keyword.conversationshort}} 服務中工作，請參閱[關於 {{site.data.keyword.conversationshort}}](../conversation/index.html#about)。

1. 在 {{site.data.keyword.Bluemix_notm}} 儀表板中，選取語音代理程式所使用的 {{site.data.keyword.conversationshort}} 實例。

1. 從_開始使用_ 儀表板中，按一下**啟動工具**按鈕。

1. 在您要編輯的工作區上，按一下**開始使用**。

1. 按一下**新增目的**，然後輸入目的名稱，例如_轉接_。

  您可以輸入更多詳細資訊，或稍後回來編輯及修正目的。

1. 在您建立通話轉接目的之後，請選取_對話_ 標籤。

1. 按一下**新增節點**，然後輸入節點的名稱，例如_通話轉接_。

1. 在_如果機器人辨識：_ 區段中，鍵入**通話轉接目的**來尋找您進行的目的。

1. 針對_則回應：_ 區段，按一下 **&vellip;** 圖示，然後選取**開啟 JSON 編輯器**。複製並貼上下列程式碼 Snippet，以取代欄位中的程式碼。

```json
{
    "output": {
   "text": {
     "values": [ "Please hold on while I connect you with a live agent." ],
     "selection_policy": "sequential"
   },
   "vgwAction": {
     "command": "vgwActTransfer",
     "parameters": {
       "transferTarget": "sip:18889990000\\@dal.watson-va.netfoundry.net"
            }
        }
    }
}
```
{: codeblock}

**請記住**：轉接目標的 SIP URI 包括一個電話號碼及您建立的終止 URI。請不要在轉接目標中使用個人電話號碼。例如，如果電話號碼是 `18889990000`，而終止 URI 是 `mysiptrunk.pstn.twilio.com`，則完整 SIP URI 是 `sip:18889990000\\@mysiptrunk.pstn.twilio.com`。如果您使用 Netfoundry，而且電話號碼為 `18889990000`，則完整 SIP URI 是 `sip:18889990000\\@dal.watson-va.netfoundry.net`。

## 後續步驟
{: #Next}

藉由與相關聯的電話號碼通話，來測試語音代理程式，並使用您在目的中識別的重要詞彙。如果您的語音代理程式將您重新導向，則表示它有用！

現在，您可以修正及配置**轉接**目的和對話，來回應您選擇的重要詞彙和詞組。
