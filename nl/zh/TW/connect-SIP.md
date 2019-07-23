---

copyright:
  years: 2019
lastupdated: "2019-02-15"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 連接 SIP 幹線
{: #connect}

您可以從下列清單中選擇用來與 {{site.data.keyword.iva_full}} 整合的 SIP 幹線提供者。
{: #shortdesc}

* [Nexmo](#nexmo-setup)
* [NetFoundry](#NetFoundry-setup)
* [Twilio](#twilio-setup)
* [Voximplant](#voximplant-setup)
* [與 {{site.data.keyword.iva_short}} 的對等作業](#peering)
* [AT&T 及其他提供者](#att-other)
* [要求輔助設定](#request-setup)

## 建立 Nexmo 語音應用程式
{: #nexmo-setup}

  **附註：**建立 [Nexmo 帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://dashboard.nexmo.com/sign-up){: new_window} 需要信用卡，這會根據您所配置之 SIP 幹線使用而定期向您收取費用。如果您已有 Nexmo 帳戶，則可以使用現有帳戶。

  1. 在 [Nexmo 網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://dashboard.nexmo.com/sign-up){: new_window} 上建立 Nexmo 帳戶。

  1. 遵循 Nexmo [GitHub 儲存庫 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/nexmo-community/watson-voice-agent){: new_window} 的 README 指示。GitHub 儲存庫包含開始使用的範例。

  1. 佈建 Nexmo 電話號碼且您的應用程式在執行中之後，請用 Nexmo 電話號碼配置您的語音代理程式。

  1. 撥打 Nexmo 電話號碼來測試您的配置。


## 建立 NetFoundry SIP 幹線及電話號碼
{: #NetFoundry-setup}

**附註：**建立帳戶需要信用卡，這會根據您的使用定期向您收取費用。如果您已有 NetFoundry 帳戶，則可以使用現有帳戶。

1. 在 [NetFoundry ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson.netfoundry.io/watson-login){: new_window} 網站上建立帳戶。

1. 移至 _Watson 帳戶_ 主頁面。

1. 選取您要號碼來自哪個地區。

  **附註：**請檢查 Netfoundry 網站，以取得可用的地區。會持續新增地區。

1. 按一下**購買**，並遵循畫面指示來完成購買。

1. 順利處理付款之後，您的 SIP 幹線電話號碼會顯示在帳戶中。

您需要此電話號碼來設定語音代理程式，並配置通話轉接（包括國碼及區域碼）。請參閱[建立及連接語音代理程式](/docs/services/voice-agent?topic=voice-agent-getting-started#step3)。


## 建立 Twilio SIP 幹線
{: #twilio-setup}

**附註：**建立 [Twilio 帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.twilio.com/try-twilio){: new_window} 需要信用卡，這會根據您所配置之 SIP 幹線使用而定期向您收取費用。如果您已有 Twilio 帳戶，則可以使用現有帳戶。

  1. 在 [Twilio 網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.twilio.com/try-twilio){: new_window} 上建立 Twilio 帳戶。

  1. 使用 Twilio 帳戶建立 SIP 幹線。

  1. 從 Twilio 網站中，移至「彈性 SIP 幹線」儀表板。

  1. 從導覽列中選取**幹線**，然後建立 SIP 幹線。如果您已有 SIP 幹線，請按一下 **+** 圖示。在產生的對話框中，輸入 SIP 幹線的名稱，然後按一下**建立**。

  1. 從「彈性 SIP 幹線」頁面中，選取您的 SIP 幹線。

  1. 從 SIP 幹線的導覽列中，選取**起源**，然後配置起源 SIP URI。您可以選取 **+** 圖示包括多個主機名稱，以防止服務失敗。

  IP 位址或主機名稱是您在 {{site.data.keyword.iva_short}} 服務實例的_開始使用_ 儀表板上記下的值。當您配置起源 URI 時，它必須是 SIP URI 格式，例如 `sip:us-south.voiceagent.cloud.ibm.com/`。藉由包含多個主機名稱或 IP 位址，如果第一個主機端點失敗或未提供服務，則您的 SIP 幹線提供者會將通話導向至下一個列出的主機名稱。

  1. 從 SIP 幹線的導覽列中，選取**號碼**。然後，建立電話號碼，並將它指派給 SIP 幹線。

  在「號碼」頁面上，按一下**購買號碼**，或者，如果您已有號碼，則請按一下 **+** 圖示。即會顯示畫面，您可以在地區中的何處佈建新電話號碼。返回 SIP 幹線，然後按一下「號碼」圖示，以將號碼指派給您所建立的 SIP 幹線。

  您需要此電話號碼來設定語音代理程式（包括國碼及區域碼）。請參閱[建立及連接語音代理程式](/docs/services/voice-agent?topic=voice-agent-getting-started#step3)。

  **附註**：如果您是使用精簡/試用 Twilio 帳戶來測試 {{site.data.keyword.iva_short}} 上的轉接，則務必要_驗證_ 轉接目標。請參閱 [Twilio 的官方網站](https://support.twilio.com/hc/en-us/articles/223136107-How-does-Twilio-s-Free-Trial-work-)上的相關指示。

## 使用 Voximplant 進行連接
{: #voximplant-setup}

1. 建立 [Voximplant 開發人員帳戶](https://voximplant.com/sign-up/)。

1. 移至 [Voximplant 控制面板](https://manage.voximplant.com/numbers/my_numbers)。在功能表上，選取**號碼**，然後按一下**購買新的電話號碼**。您可以檢查**實際**或**測試號碼**，然後在清單中選取一個號碼，接著按一下**購買選取項目**來購買一個電話號碼。

1. 在語音代理程式設定中指定此號碼。

1. 移至 _Voximplant 控制面板_ 的[應用程式區段](https://manage.voximplant.com/applications)，建立一個名為 **Watson** 的應用程式。

1. 在此應用程式中，切換至**情境**標籤，並建立含有下列程式碼的 **watson 情境**：
    ```javascript
      VoxEngine.addEventListener(AppEvents.CallAlerting, (e) => {
        let call2 = VoxEngine.callSIP("sip:12025550186@us-south.voiceagent.cloud.ibm.com");
        VoxEngine.easyProcess(e.call, call2);
      })
    ```
    {: codeblock}

    請注意 **callSIP** 函數呼叫：
      * 替換為您在步驟 2 中所購買的 Voximplant 號碼，而不是使用 `12025550186`。 
      * 替換為您的語音代理程式 SIP 端點，而不是使用 `us-south.voiceagent.cloud.ibm.com`。{{site.data.keyword.iva_full}} 文件的_開始使用_ 頁面上會指定此端點。請參閱[*入門指導教學*](/docs/services/voice-agent?topic=voice-agent-getting-started#step1)。
    
1. 移至**遞送**標籤，以建立 **watson 規則**。指定 **watson 情境**作為指派的情境。

1. 開啟**號碼**標籤的**附加項目**（但是空的）和**可用項目**區段。切換至**可用項目**，選取您的號碼，然後按一下**附加**。在開啟的視窗中，指定 **watson 規則**，然後按一下**附加**。

## 與 {{site.data.keyword.iva_short}} 的對等作業
{: #peering}

{{site.data.keyword.iva_short}} 支援與客戶 PBX（例如 Asterisk）的對等節點連線。若要與 {{site.data.keyword.iva_short}} 對等作業，您可以將伺服器的 IP 位址設為白名單。

1. 移至_管理_ 儀表板，並選取_實例_ 標籤。

1. 按一下**新增 IP** 圖示，將新的 IP 位址設為白名單。

1. 新增 **IP 暱稱**及 **IP 位址**。

## 使用 AT&T 及其他提供者進行連線
{: #att-other}

{{site.data.keyword.iva_short}} 支援使用 AT&T&reg; 及其他 SIP 幹線提供者進行連線。不過，這些連線不會進行自助式設定，而且需要額外協助。請參閱[要求輔助設定](#request-setup)。

## 要求輔助設定
{: #request-setup}

您可以要求設定輔助網路，以與 AT&T 或其他 SIP 幹線提供者連接、與 {{site.data.keyword.iva_short}} 對等，或使用下列處理程序來要求超過 50 個的並行連線。

您可以在 {{site.data.keyword.iva_short}} 實例中，將例如 Asterisk 的 PBX 設為白名單。唯有在公用網際網路白名單不是可接受的解決方案時，才開立支援問題單。請參閱[將 IP 位址設為白名單](/docs/services/voice-agent?topic=voice-agent-whitelist_IP#whitelist_IP)。

1. 開立新的 [{{site.data.keyword.Bluemix_notm}} 支援問題單](https://cloud.ibm.com/unifiedsupport/tickets/add)

1. 針對**問題單類型**，選取**技術**。

1. 針對**選取資源環境定義**，選擇 **Cloud Foundry**。

1. 針對**技術支援區域**，選擇**應用程式服務**。

1. 選擇 {{site.data.keyword.iva_short}} 實例的**地區**、**組織**及**空間**。

1. 針對**相關聯資源**，選取 {{site.data.keyword.iva_short}} 服務實例。

1. 針對**嚴重性**，選擇**嚴重性 4 - 最小影響**

1. 針對**主旨**，輸入 `{{site.data.keyword.iva_short}} assisted network setupup`。

1. 在**簡要說明**區段中，說明要如何連接至 {{site.data.keyword.iva_short}} 服務，或為您的語音代理程式要求超過 50 個的並行連線。對等節點連線適用於具有_標準_ 或_超值_ 方案的使用者。如果您將實例從_標準_ 或_超值_ 方案，切換成_精簡_ 方案，或是您刪除實例的話，便會停用對等節點連線。

  您可以使用 SIP 幹線提供者或對等節點連線（例如 IPSec 通道）進行連接。在您的問題單中，您可以附加 PDF 或影像格式的網路圖，以說明網路拓蹼。您也可以附加任何白皮書，以詳細說明您要的服務功能。

  請在您的**簡要說明**中包含下列資訊：
  * 公司名稱
  * {{site.data.keyword.Bluemix_notm}} 帳戶 ID
  * 您的 {{site.data.keyword.iva_short}} 服務儀表板 URL
  * 使用案例
  * 網路圖表與 IP 位址或 SIP 幹線提供者資訊
