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


# 与第三方语音和文字服务连接
{: #third-party}

在使用_管理_仪表板来创建、克隆或编辑语音代理程序时，可以连接第三方语音和文字服务。
{: shortdesc}

或者，要动态配置语音和文字服务连接，您可以[使用 {{site.data.keyword.conversationshort}} 进行动态配置](api_dynamic_config.html)。这样，您就可以使用操作标记和状态变量来更改语音代理程序配置了。

## 从 {{site.data.keyword.iva_short}} 连接到 Google Speech-to-Text
{: #stt_va}

您可以选择将语音代理程序连接到第三方语音转文字服务，例如 [Google Cloud Speech-to-Text ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.google.com/speech-to-text/)，而不使用 {{site.data.keyword.speechtotextfull}} 实例。

1. 导航到_管理_仪表板上的_语音代理程序_选项卡，然后选择**编辑**现有语音代理程序或**创建新的语音代理程序**。

1. 在_语音转文字_服务配置中，请选择 **Google 语音转文字服务实例**。

1. 为您的服务实例选择**语言**。

1. 输入 Google Cloud Speech-to-Text 服务凭证。
  * [设置服务帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标") 时，您可以在 Google Cloud Platform 中生成服务凭证作为 JSON 密钥](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account)。以下代码示例包含您在 Google Cloud Platform 上生成的样本凭证字段。

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

1. **可选** 选择**显示高级**，以有效的 JSON 格式输入 Google 定义的特殊配置设置。以下示例显示了为英语（美国）实例启用不雅言辞过滤功能的 Google 配置设置。
  ```json
  {
    "languageCode": "en-US",
    "profanityFilter": false
  }
  ```
  {: codeblock}

  如果您在服务配置中选择的语言不同于您在 `languageCode` 中定义的语言，那么 {{site.data.keyword.iva_short}} 会使用 `languageCode` JSON 配置定义的语言来覆盖您的选择。
  {: tip}

## 从 {{site.data.keyword.iva_short}} 连接到 Google Text-to-Speech
{: #tts_va}

您可以选择将语音代理程序连接到第三方语音转文字服务，例如 [Google Cloud Text-to-Speech ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.google.com/text-to-speech/)，而不是使用 {{site.data.keyword.texttospeechfull}} 实例。

1. 导航到_管理_仪表板上的_语音代理程序_选项卡，然后选择**编辑**现有语音代理程序或**创建新的语音代理程序**。

1. 在您的_文字转语音_服务配置中，选择 **Google Text to Speech 服务实例**。

1. 为您的服务实例选择**语言**和**语音**。

1. 输入 Google Cloud Text-to-Speech 服务凭证。
  * [设置服务帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标") 时，您可以在 Google Cloud Platform 中生成服务凭证作为 JSON 密钥](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account)。以下代码示例包含您在 Google Cloud Platform 上生成的样本凭证字段。

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

1. **可选** 选择**显示高级**，以有效的 JSON 格式输入 Google 定义的特殊配置设置。以下示例显示了德语女声语音的 Google 配置设置。

  如果您在服务配置中选择的语言不同于您在 `languageCode` 中定义的语言，那么 {{site.data.keyword.iva_short}} 会使用 `languageCode` JSON 配置定义的语言来覆盖您的选择。
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
