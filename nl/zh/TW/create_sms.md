---

copyright:
  years: 2019
lastupdated: "2019-06-24"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 建立 SMS 代理程式
{: #sms_config_instance}

建立 {{site.data.keyword.iva_full}} 服務之後，您可以從_管理_ 儀表板建立個別的 SMS 代理程式。
{: shortdesc}

1. 移至_管理_ 儀表板上的_語音代理程式_ 標籤，然後按一下**建立語音代理程式**。

1. 在**代理程式類型**中，選取 _SMS_。

1. 在**名稱**中，指定語音代理程式的唯一名稱。例如，`Customer Support - North America`。名稱最多可以包括 64 個字元。

1. 在電話號碼中，新增來自 SIP 幹線的號碼（包括國碼和區域碼）。例如，若為美國 800 號碼，請將電話號碼指定為 18883334444。電話號碼上限為 30 個字元，包括空格和 + ( ) - 字元。SMS 僅支援每位使用者一個號碼。

1. 在 **SMS 提供者**下，輸入 SMS 提供者的使用者名稱、密碼及 API URL。例如，如果使用 _Twilio_，使用者名稱是您的**帳戶 SID**、帳戶是您的**鑑別記號**，而 SMS 提供者是 `https://api.twilio.com`

1. 在**交談**下，配置與 {{site.data.keyword.conversationshort}} 服務實例的連線。您可以在您或其他人擁有的 {{site.data.keyword.Bluemix_notm}} 帳戶中使用 {{site.data.keyword.conversationshort}} 服務實例。您也可以透過服務編排引擎 (SOE)，連接至其中任何選項。

   * 如果您在「達拉斯」或「華盛頓特區」地區中建立 SMS 代理程式，但沒有 {{site.data.keyword.conversationshort}} 服務實例，則可以在**服務實例**功能表中建立服務實例。
   * 或者，您也可以藉由變更[**服務類型**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service)，以連接至 {{site.data.keyword.conversationshort}} 對話的其他來源，或與 SOE 進行連接。
   * 如果您要配置多個服務位置，請按一下另一個位置選項，然後選取**啟用位置**以配置與其他 {{site.data.keyword.conversationshort}} 實例的連線。如需相關資訊，請參閱[新增多個 Watson 服務位置](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location)。

1. 檢查**從入埠訊息起始交談**方框，以容許使用者開始與 SMS 代理程式進行 SMS 階段作業。

1. 檢查**階段作業逾時通知**方框，讓 SMS 代理程式將 SMS 訊息傳送給使用者，警示他們代理程式在一段時間內沒有收到回應，現在將會逾時。 

    - 如需 SMS 代理程式可用**進階選項**的相關資訊（例如設定會階段作業逾時的自訂時間），請參閱[進階選項](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced)。
    - 只有在您希望於階段作業逾時情況下收到通知時，才勾選此方框。

1. 您也可以選擇啟用事件轉遞，收集 {{site.data.keyword.cloudantfull}} 中語音代理程式所處理通話的相關資訊。如需相關資訊，請參閱[啟用語音代理程式的事件轉遞](/docs/services/voice-agent?topic=voice-agent-event_forwarding)。如需其他配置選項，請參閱[配置語音代理程式](/docs/services/voice-agent?topic=voice-agent-managing#configure_va)。

1.  按一下**建立語音代理程式**，以建立您的 SMS 代理程式和任何新服務。

1. 遵循[指示](/docs/services/voice-agent?topic=voice-agent-connect-sms)，以連接至 SMS 提供者。

建立 SMS 代理程式之後，即可藉由發簡訊至其電話號碼來測試 SMS 代理程式。您可以在_用量_ 儀表板上，檢視互動的詳細資料。請參閱[檢視用量和日誌](/docs/services/voice-agent?topic=voice-agent-logging)。

若要在語音通話期間啟用客戶與語音代理程式之間的 SMS 傳訊，SMS 號碼必須與語音號碼相符。
{: tip}

在建立 SMS 代理程式或將 SMS 功能新增至語音代理程式之前，您**必須**設定適當的認證，並產生 API 金鑰以編寫至您的 SMS 號碼。如需相關資訊，請參閱[產生 API 金鑰並設定認證](/docs/services/voice-agent?topic=voice-agent-connect-sms#sms_access)。

您同時**必須**配置 SMS 功能的 SIP 幹線。請參閱提供者的指示，例如，Twilio。如果您沒有 Twilio 電話號碼，請參閱[建立 Twilio SIP 幹線](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup)。

在具備 Twilio 號碼之後，您就需要為 SMS 功能配置它。如需相關資訊，請參閱[為 SMS 配置 Twilio](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup)。

如果您在建立認證時遇到問題，請與服務實例管理者聯絡，以授與您*管理員* 或*撰寫者* 存取權。
{: tip}

## SMS 代理程式的進階選項
{: #sms_advanced}

按一下**電話號碼**欄位之後的**顯示進階**。

1. 設定選用的**交談閱讀逾時**值。這是 SMS Gateway 等待 Watson Assistant 回應的時間（以秒為單位）。如果超出此時間，SMS Gateway 會重新嘗試與 Watson Assistant 聯絡。如果仍無法聯繫服務，則 SMS/MMS 訊息失敗。依預設，設為 30 秒。

1. 設定選用的**階段作業逾時**。這是 SMS Gateway 沒有收到使用者的回應，而造成階段作業過期的時間（以秒為單位）。

1. 設定**交談失敗回覆訊息**。這是無法呼叫到 Watson Assistant 時所發送的預設回應訊息。依預設，它設為 `We're sorry, but we can't respond to your message.`。

### 配置 SMS 代理程式以終止階段作業
{: #sms_terminate}

{{site.data.keyword.iva_full}} SMS 代理程式根據階段作業逾時的值終止階段作業，該值是可配置的且依預設設為 30 秒。 

您也可以將節點新增至 {{site.data.keyword.conversationshort}} 服務中，以回應來自使用者的結束階段作業指令。 

1. 在 {{site.data.keyword.Bluemix_notm}} 儀表板中，選取語音代理程式所使用的 {{site.data.keyword.conversationshort}} 實例。

1. 從儀表板建立**終止 SMS 意圖**。或者，您也可以修改已用於語音代理程式的現有意圖，例如_結束通話_。

1. 從儀表板新增**終止 SMS 節點**。

1. 在_如果助理辨識：_ 區段中，新增您先前建立的**終止 SMS 意圖**屬性。

1. 將回應新增至節點。複製並貼上下列程式碼 Snippet，以取代欄位中的程式碼。

    ```json
        {
            "output": {
          "text": {
              "values": [
        "Thank you for using the service. Goodbye!"
                    ],
                    "selection_policy”: “sequential"
                },
                "smsAction": {
                    "command": "terminateSession"
                }
            }
        }
    ```
    {: codeblock}

建立語音代理程式之後，即可根據其類型藉由與其電話號碼通話或發簡訊至其電話號碼來測試語音代理程式。您可以在_用量_ 儀表板上，檢視互動的詳細資料。請參閱[檢視用量和日誌](/docs/services/voice-agent?topic=voice-agent-logging)。
