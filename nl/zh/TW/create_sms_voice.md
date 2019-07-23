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

# 建立已啟用 SMS 的語音代理程式
{: #sms_voice_config_instance}

建立 {{site.data.keyword.iva_full}} 服務之後，您可以從_管理_ 儀表板建立具有 SMS 功能的個別語音代理程式，或僅具有 SMS 功能的語音代理程式。您可以配置 {{site.data.keyword.iva_full}} 來接收入埠語音通話與回應 SMS 出埠訊息，取決於使用者所接收的語音指令。為進行配置，請在 {{site.data.keyword.conversationshort}} 服務中新增節點和意圖。
{: shortdesc}


1. 移至_管理_ 儀表板上的_語音代理程式_ 標籤，然後按一下**建立語音代理程式**。

1. 在**代理程式類型**中，選取_語音 + SMS_。

1. 遵循[建立語音代理程式](/docs/services/voice-agent?topic=voice-agent-config_instance)中的指示。

1. 檢查**從入埠訊息起始交談**方框，以容許使用者開始與 SMS 代理程式進行 SMS 階段作業。

1. 檢查**階段作業逾時通知**，讓 SMS 代理程式將 SMS 訊息傳送給使用者，警示他們代理程式在一段時間內沒有收到回應，現在將會逾時。 

   - 如需 SMS 代理程式可用**進階選項**的相關資訊（例如設定會階段作業逾時的自訂時間），請參閱[進階選項](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced)。

1. 遵循[建立 SMS 代理程式](/docs/services/voice-agent?topic=voice-agent-sms_config_instance)中的指示，以建立 SMS 代理程式。

1. _**附註：**_ 若要讓代理程式同時具備語音和 SMS 整合（例如，接收「語音」輸入並送回 SMS 出埠訊息以進行回覆），您**必須**為 **SMS** 代理程式使用其中一個**語音**號碼。

### 配置 Watson Assistant 以進行語音和 SMS 整合
{: #sms_outbound}

1. 在 {{site.data.keyword.Bluemix_notm}} 儀表板中，選取語音代理程式所使用的 {{site.data.keyword.conversationshort}} 實例。

1. 從儀表板建立**出埠 SMS 意圖**。

1. 從儀表板新增**出埠 SMS 節點**。

1. 在_如果助理辨識：_ 區段中，選取您先前建立的**出埠 SMS 意圖**屬性。

1. 將回應新增至節點。複製並貼上下列程式碼 Snippet，以取代欄位中的程式碼。

    ```json
        {
            "output": {
          "text": {
              "values": [
        "Okay. I will send you a text message now."
                ],
              "selection_policy": "sequential"
          },
                "vgwActionSequence": [
                {
                    "command": "vgwActSendSMS",
                    "parameters": {
                    "message": "This is a test message from Watson Assistant"
                    }
                },
                {
                    "command": "vgwActPlayText"
                }
                ]
            }
        }
    ```
    {: codeblock}


1. 呼叫代理程式並觸發節點，以在您所撥打的電話上接收文字訊息。 

若要進一步瞭解如何在 {{site.data.keyword.conversationshort}} 服務中工作，請參閱[關於 {{site.data.keyword.conversationshort}}](/docs/services/assistant?topic=assistant-index#indext)。
