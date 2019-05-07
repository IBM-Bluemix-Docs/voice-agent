---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 通話中転送のセットアップ
{: #call-transfer}

通話中転送をセットアップして、発信者が会話の途中でライブ・エージェントと話すことを要求した場合に、ボイス・エージェントが自動的に通話を転送するように設定できます。
{: shortdesc}

## 通話中転送について
{: #about-ct}

通話中転送を有効にすると、発信者が会話の途中でライブ・エージェントと話すことを要求した場合に、ボイス・エージェントが自動的に通話をリダイレクトします。 {{site.data.keyword.iva_short}} は、SIP の REFER を使用して、コールバックを処理のために SIP トランク・プロバイダーに送信し、転送される電話の通話をアンカーしません。

通話中転送は、SIP プロバイダー構成で終了 URI または電話 URI を設定することで有効にできます。 その後、{{site.data.keyword.conversationshort}} インスタンスのダイアログ・ノードで API アクションの転送ターゲットを指定します。 転送ターゲットは、終了 URI と電話番号が含まれた SIP URI、または電話番号が含まれた電話 URI です。 サポートされているアクションとボイス・エージェントのカスタマイズ方法について詳しくは、[API を使用したボイス・エージェントのプログラミング](/docs/services/voice-agent?topic=voice-agent-api)を参照してください。

## ステップ 1: 終了 URI のセットアップ
{: #termination-setup}

SIP URI 構成で終了 URI ではなく電話 URI を使用する場合は、`transferTarget` に `tel:+18889990000` などの電話 URI を使用することができます。SIP URI を使用する場合は、`transferTarget` に終了 URI を使用する必要があります。
{: tip}

### NetFoundry での終了 URI のセットアップ
{: #termination-netfoundry}

転送先の [NetFoundry アカウント ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson.netfoundry.io/watson-login){: new_window} の電話番号をメモします。 後で、{{site.data.keyword.conversationshort}} ダイアログでこの電話番号と終了 URI を転送先として指定できます。 個人の電話番号を使用しないでください。

次の NetFoundry の終了 URI をコピーして、転送ターゲットで使用します。

```
dal.watson-va.netfoundry.net
```
{: codeblock}

[通話中転送用に {{site.data.keyword.conversationshort}} を構成する](#conversation-setup)場合は、NetFoundry アカウントで終了 URI を手動で構成する必要はありません。

### Twilio での終了 URI のセットアップ
{: #termination-Twilio}

1. Twilio アカウントで、_「弾力的な SIP トランクの接続 (Elastic SIP Trunking)」_ダッシュボードにナビゲートして**「トランク (Trunks)」**を選択します。

1. 既存のトランクを選択するか**「+」**アイコンをクリックして新規作成することにより、通話中転送を追加するトランクを選択します。

  * 新しいトランクを作成する場合、**「起点 (Origination)」**ダッシュボードで_「SIP トランク URI (SIP Trunk URI)」_を構成する必要があります。  詳しくは、[SIP トランクの接続](/docs/services/voice-agent?topic=voice-agent-connect)を参照してください。

1. ナビゲーション・バーで**「終了 (Termination)」**を選択し、終了 URI の名前を入力します。

  * 終了 URI の名前は固有でなければなりません。 Twilio は選択された名前が使用可能かどうかを自動検査します。 Twilio のサービスについて詳しくは、[SIP トランクの終了設定 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window} を参照してください。

1. ナビゲーション・バーで**「一般」**を選択して、_「一般設定 (General settings)」_を表示します。 **「通話中転送 (SIP REFER) (Call Transfer (SIP REFER))」**見出しの下で、設定を**「有効」**に切り替えて、**「トランクを介した PSTN への通話中転送を許可する (Allow Call Transfers to the PSTN via your Trunk)」**を選択します。

1. **「保存」**をクリックして、終了 URI の構成と通話中転送の有効化を完了します。

1. 転送先の電話番号と終了 URI をメモします。 電話番号が、個人の電話番号でないことを確認してください。 {{site.data.keyword.conversationshort}} ダイアログで、この電話番号と終了 URI を使用して転送ターゲットを指定できます。


## ステップ 2: 通話中転送のための {{site.data.keyword.conversationshort}} の構成
{: #conversation-setup}

{{site.data.keyword.conversationshort}} サービスでの処理方法について詳しくは、[{{site.data.keyword.conversationshort}} について](/docs/services/assistant?topic=assistant-index#indext)を参照してください。

1. {{site.data.keyword.Bluemix_notm}} ダッシュボードで、ボイス・エージェントが使用する {{site.data.keyword.conversationshort}} インスタンスを選択します。

1. _「開始 (Getting started)」_ダッシュボードから、**「起動ツール (Launch tool)」**ボタンをクリックします。

1. 編集するスキルで**「開始 (Getting started)」**をクリックします。

1. **「インテントの追加 (Add intent)」**をクリックして、インテントの名前 (_Transfer_ など) を入力します。

  さらに詳細情報を入力したり、後に再びインテントを編集して詳細化したりすることもできます。

1. 通話中転送インテントを作成した後に、_「ダイアログ (Dialog)」_タブを選択します。

1. **「ノードの追加 (Add node)」**をクリックして、ノードの名前 (_Call Transfer_ など) を入力します。

1. _「ボットが次のものを認識した場合: (If the bot recognizes:)」_セクションで、**Call transfer インテント**と入力して、作成したインテントを検索します。

1. _「次のように応答する: (Then respond with:)」_セクションで、**「&vellip;」**アイコンをクリックして、**「JSON エディターを開く (Open JSON editor)」**を選択します。 以下のコード・スニペットをコピーして貼り付け、フィールド内のコードを置き換えます。

  * 電話 URI を使用する場合、`transferTarget` の SIP URI を電話 URI に置き換えます。 例えば、`"transferTarget":"tel:+18889990000"` のようにします。

  * **注**: `transferTarget` URI の先頭文字が `+` になっていることを確認してください。

  ```json
  {
      "output": {
          "text": {
              "values": [ "ライブエージェントと接続しています。このままお待ちください。(Please hold on while I connect you with a live agent.)" ],
     "selection_policy": "sequential"
          },
   "vgwAction": {
              "command": "vgwActTransfer",
     "parameters": {
                  "transferTarget": "sip:+18889990000\\@dal.watson-va.netfoundry.net"
              }
          }
      }
  }
  ```
  {: codeblock}

1. `transferTarget` の終了 URI または電話 URI の電話番号が SIP トランク内の電話番号と正確に一致していることを確認します。

**注**: 転送ターゲットの SIP URI には、電話番号と作成した終了 URI が含まれます。 転送ターゲットで、個人の電話番号を使用しないでください。 例えば、電話番号が `18889990000` で、終了 URI が `mysiptrunk.pstn.twilio.com` の場合、完全な SIP URI は `sip:+18889990000\\@mysiptrunk.pstn.twilio.com` になります。 Netfoundry を使用していて、電話番号が `18889990000` の場合、完全な SIP URI は `sip:+18889990000\\@dal.watson-va.netfoundry.net` になります。

**注**: `transferTarget` URI の先頭文字が `+` になっており、最大 256 文字にできることを確認してください。

## 次のステップ
{: #Next}

ボイス・エージェントに関連付けられた電話番号を呼び出してインテント内に指定したキー用語を使用することにより、ボイス・エージェントをテストします。 ボイス・エージェントによってリダイレクトが行われれば、成功です。

これで、選択したキー用語と語句に応答するように、**転送**インテントおよびダイアログを詳細化して構成できるようになりました。
