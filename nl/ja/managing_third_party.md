---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# サード・パーティーの音声テキスト変換サービスに接続する
{: #third-party}

_「管理」_ダッシュボードでボイス・エージェントを作成、複製、または編集して、サード・パーティーの音声テキスト変換サービスを接続できます。
{: shortdesc}

別の方法として、処理中に音声テキスト変換サービスの接続を構成するために、[{{site.data.keyword.conversationshort}} の動的構成を使用](/docs/services/voice-agent?topic=voice-agent-dynamic-donfig)できます。 この方法では、アクション・タグと状態変数を使用してボイス・エージェントの構成を変更できます。

## {{site.data.keyword.iva_short}} から Google Speech-to-Text に接続する
{: #stt_va}

{{site.data.keyword.speechtotextfull}} インスタンスを使用する代わりに、[Google Cloud Speech-to-Text ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.google.com/speech-to-text/) などのサード・パーティーの音声認識サービスにボイス・エージェントを接続できます。

1. _「管理」_ダッシュボードの_「音声エージェント」_タブにナビゲートし、既存のボイス・エージェントの**「編集」**または**「ボイス・エージェントの新規作成 (Create new voice agent)」**を選択します。

1. _「音声認識テキスト」_サービス構成で、**「Google Speech to Text サービス・インスタンス」**を選択します。

1. サービス・インスタンスの**「言語」**を選択します。お好みの言語がドロップダウン・メニューのリストに含まれない場合、**「その他」**を選択して、[拡張構成](/docs/services/voice-agent?topic=voice-agent-third-party#advanced)でいつでも言語を設定できます。

1. Google Cloud Speech-to-Text サービス資格情報を入力します。最大 3072 文字の制限があります。
  * [サービス・アカウントを設定 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account) するときに、Google Cloud Platform でサービス資格情報を JSON キーとして生成できます。 以下のサンプル・コードには、Google Cloud Platform で生成する資格情報フィールドの例が含まれています。

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

1. **オプション** **「拡張を表示」**を選択して、Google によって定義された特殊な構成設定を、有効な JSON 形式で入力します。
  以下の例は、米国英語インスタンスで不適切表現フィルターを有効にする Google 構成設定を示しています。
  ```json
  {
    "languageCode": "en-US",
    "profanityFilter": false
  }
  ```
  {: codeblock}

  サービス構成で選択した言語と、`languageCode` で定義した言語が異なっている場合、{{site.data.keyword.iva_short}} は、選択された言語を、この `languageCode` の JSON 構成で定義された言語で上書きします。
  {: tip}

## {{site.data.keyword.iva_short}} から Google Text-to-Speech に接続する
{: #tts_va}

{{site.data.keyword.texttospeechfull}} インスタンスを使用する代わりに、[Google Cloud Text-to-Speech ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.google.com/text-to-speech/) などのサード・パーティーの音声合成サービスにボイス・エージェントを接続できます。

1. _「管理」_ダッシュボードの_「音声エージェント」_タブにナビゲートし、既存のボイス・エージェントの**「編集」**または**「ボイス・エージェントの新規作成 (Create new voice agent)」**を選択します。

1. _Text to Speech_ サービス構成で、**「Google Text to Speech サービス・インスタンス (Google Text to Speech service instance)」**を選択します。

1. サービス・インスタンスの**「言語」**と**「音声」**を選択します。お好みの言語がドロップダウン・メニューのリストに含まれない場合、**「その他」**を選択して、[拡張構成](/docs/services/voice-agent?topic=voice-agent-third-party#advanced)でいつでも言語を設定できます。

1. Google Cloud Text-to-Speech サービス資格情報を入力します。最大 3072 文字の制限があります。
  * [サービス・アカウントを設定 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.google.com/video-intelligence/docs/common/auth#set_up_a_service_account) するときに、Google Cloud Platform でサービス資格情報を JSON キーとして生成できます。 以下のサンプル・コードには、Google Cloud Platform で生成する資格情報フィールドの例が含まれています。

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

{: #advanced}
1. **オプション** **「拡張を表示」**を選択して、Google によって定義された特殊な構成設定を、有効な JSON 形式で入力します。
  以下の例は、ドイツ語の女性音声に関する Google 構成設定を示しています。

  サービス構成で選択した言語と、`languageCode` で定義した言語が異なっている場合、{{site.data.keyword.iva_short}} は、選択された言語を、この `languageCode` の JSON 構成で定義された言語で上書きします。
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
