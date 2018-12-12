---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-16"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 使用協力廠商語音及文字服務進行連接
{: #third-party}

在_管理_ 儀表板上建立、複製或編輯語音代理程式時，您可以連接協力廠商語音及文字服務。
{: shortdesc}

或者，若要在進行中配置語音及文字服務連線，您可以[使用動態配置搭配 {{site.data.keyword.conversationshort}}](api_dynamic_config.html)。這容許您以動作標籤及狀態變數變更語音代理程式配置。

## 從 {{site.data.keyword.iva_short}} 連接至 Google Speech-to-Text
{: #stt_va}

您可以選擇將語音代理程式連接至協力廠商語音轉文字服務，例如 [Google Cloud Speech-to-Text ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.google.com/speech-to-text/)，而非使用 {{site.data.keyword.speechtotextfull}} 實例。

1. 導覽至_管理_ 儀表板上的_語音代理程式_ 標籤，然後選取**編輯**現有語音代理程式或**建立新的語音代理程式**。

1. 在您的 _Speech to Text_ 服務配置中，選擇 **Google Speech to Text 服務實例**。

1. 為服務實例選擇**語言**。

1. 輸入您的 Google Cloud Speech-to-Text 服務認證。
  * 當您[設定服務帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account)，您可以在 Google Cloud Platform 中產生服務認證作為 JSON 金鑰。下列程式碼範例包含您在 Google Cloud Platform 上產生的範例認證欄位。

    ```json
    {
      "type": "",
      "auth_uri": "",
      "client_id": "",
      "token_uri": "",
      "project_id": "",
      "private_key": "",
      "client_email": "",
      "private_key_id": "",
      "client_x509_cert_url": "",
      "auth_provider_x509_cert_url": ""
    }
    ```
    {: codeblock}

1. **選用**：選取**顯示進階**，以有效的 JSON 格式輸出 Google 所定義的特殊配置設定。下列範例顯示針對美式英文實例啟用褻瀆過濾器的 Google 配置設定。
  ```json
  {
    "languageCode": "en-US",
    "profanityFilter": false
  }
  ```
  {: codeblock}

  如果您在服務配置中選取的語言與 `languageCode` 中定義的語言不同，{{site.data.keyword.iva_short}} 會將您的選項改寫為 `languageCode` JSON 配置所定義的語言。
  {: tip}

## 從 {{site.data.keyword.iva_short}} 連接至 Google Text-to-Speech
{: #tts_va}

您可以選擇將語音代理程式連接至協力廠商語音轉文字服務，例如 [Google Cloud Text-to-Speech ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.google.com/text-to-speech/)，而非使用 {{site.data.keyword.texttospeechfull}} 實例。

1. 導覽至_管理_ 儀表板上的_語音代理程式_ 標籤，然後選取**編輯**現有語音代理程式或**建立新的語音代理程式**。

1. 在 _Text to Speech_ 服務配置中，選擇 **Google Text to Speech 服務實例**。

1. 為服務實例選擇**語言**及**語音**。

1. 輸入您的 Google Cloud Text-to-Speech 服務認證。
  * 當您[設定服務帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account)，您可以在 Google Cloud Platform 中產生服務認證作為 JSON 金鑰。下列程式碼範例包含您在 Google Cloud Platform 上產生的範例認證欄位。

    ```json
    {
      "type": "",
      "auth_uri": "",
      "client_id": "",
      "token_uri": "",
      "project_id": "",
      "private_key": "",
      "client_email": "",
      "private_key_id": "",
      "client_x509_cert_url": "",
      "auth_provider_x509_cert_url": ""
    }
    ```
    {: codeblock}

1. **選用**：選取**顯示進階**，以有效的 JSON 格式輸出 Google 所定義的特殊配置設定。下列範例顯示針對女聲講德文的 Google 配置設定。

  如果您在服務配置中選取的語言與 `languageCode` 中定義的語言不同，{{site.data.keyword.iva_short}} 會將您的選項改寫為 `languageCode` JSON 配置所定義的語言。
  {: tip}

  ```json
  {
  "config": {
    "audioConfig": {
      "speakingRate": 1.3
    },
    "voiceConfig": {
      "ssmGender": "FEMALE",
      "languageCode": "de-DE"
    }
  }
  }
  ```
  {: codeblock}
