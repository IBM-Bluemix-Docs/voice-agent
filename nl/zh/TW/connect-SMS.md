---

copyright:
  years: 2019
lastupdated: "2019-06-21"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 連接至 SMS 提供者
{: #connect-sms}

您可以從下列清單中選擇用來與 {{site.data.keyword.iva_full}} 整合的 SMS 提供者。
{: #shortdesc}

* [Twilio](#twilio-setup)

## 產生 API 金鑰和設定認證
{: #sms_access}

您只能為帳戶中已處於活動狀態的角色建立認證。若為 SMS 和「語音 + SMS」代理程式，您必須已指派*撰寫者* 或*管理員* 角色。請參閱[步驟 9 邀請使用者並指派起始存取權](/docs/services/voice-agent?topic=voice-agent-iam#step1)。

1. 在 {{site.data.keyword.iva_short}} 實例的*儀表板* 上，按一下**新建認證 (+)**。 
2. 在蹦現的新對話框中，輸入**名稱**，然後在**角色**下拉功能表下，選取*撰寫者* 或*管理員*。 
    - **附註：**若為任何 SMS 相關功能，您**_必須_** 選取*撰寫者* 或*管理員* 角色。 
3. 按一下**新增**。
4. 在新建立的認證旁，按一下**檢視認證**。記下 JSON Script 中的 `APIKEY` 值，以在[為 SMS 配置 Twilio](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup) 中使用。

## 為 SMS 配置 Twilio
{: #twilio-setup}

1. 存取您的 Twilio 電話號碼，請在[這裡](https://www.twilio.com/console/phone-numbers/)尋找，然後選取已指派給 _SMS_ 或_語音 + SMS_ 代理程式的電話號碼。 

1. 向下捲動至**傳訊**區段。在_配置_ 欄位中，從下拉功能表中選取 **Webhook、TwiML Bin、函數、Studio 或 Proxy**。

1. 在_傳入訊息_ 欄位中，從下拉功能表中選取 **Webhook**。

1. 在 **Webhook** 旁的空 URL 欄位中，遵循您代理程式地區的指示進行操作。 

    - 如果您建立的代理程式位於華盛頓州地區，請在欄位中寫入 `https://apikey:YOUR_API_KEY@sms-east.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv`。
    - 如果您建立的代理程式位於達拉斯地區，請在欄位中寫入 `https://apikey:YOUR_API_KEY@sms-south.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv`。
    - 使用您之前建立的認證中的 `APIKEY` 來取代前面 URL 中的 `YOUR_API_KEY`。請參閱[產生 API 金鑰和設定認證](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_access)。 

1. 按一下**儲存**。 
