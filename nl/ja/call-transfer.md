---

copyright:
  years: 2018
lastupdated: "2018-06-14"

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

通話中転送を有効にすると、発信者が会話の途中でライブ・エージェントと話すことを要求した場合に、ボイス・エージェントが自動的に通話をリダイレクトします。 SIP プロバイダー構成で終了 URI を設定することで、通話中転送を有効にすることができます。 次に、{{site.data.keyword.conversationshort}} インスタンスのダイアログ・ノードで API アクションに転送ターゲットを定義します。 転送ターゲットは、終了 URI と電話番号が含まれた SIP URI です。サポートされているアクションとボイス・エージェントのカスタマイズ方法について詳しくは、[API を使用したボイス・エージェントのプログラミング](api.html)を参照してください。

## ステップ 1: 終了 URI のセットアップ
{: #termination-setup}

### NetFoundry での終了 URI のセットアップ
{: #termination-netfoundry}

転送先の [NetFoundry アカウント ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson.netfoundry.io/watson-login){: new_window} の電話番号をメモします。後で、{{site.data.keyword.conversationshort}} ダイアログでこの電話番号と終了 URI を転送先として指定できます。以下の NetFoundry 終了 URI をコピーして、転送ターゲットに使用できます。

```
dal.watson-va.netfoundry.net
```
{: codeblock}

[通話中転送用に {{site.data.keyword.conversationshort}} を構成する](#conversation-setup)場合は、NetFoundry アカウントで終了 URI を手動で構成する必要はありません。

### Twilio での終了 URI のセットアップ
{: #termination-Twilio}

1. Twilio アカウントで、_「弾力的な SIP トランクの接続 (Elastic SIP Trunking)」_ダッシュボードにナビゲートして**「トランク (Trunks)」**を選択します。

1. 既存のトランクを選択するか**「+」**アイコンをクリックして新規作成することにより、通話中転送を追加するトランクを選択します。

  * 新しいトランクを作成する場合、**「起点 (Origination)」**ダッシュボードで_「SIP トランク URI (SIP Trunk URI)」_を構成する必要があります。  詳しくは、[SIP トランクの接続](connect-SIP.html)を参照してください。

1. ナビゲーション・バーで**「終了 (Termination)」**を選択し、終了 URI の名前を入力します。

  * 終了 URI の名前は固有でなければなりません。 Twilio は選択された名前が使用可能かどうかを自動検査します。 Twilio のサービスについて詳しくは、[SIP トランクの終了設定 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window} を参照してください。

1. _「認証」_セクションで、**「+」**アイコンをクリックして、ボイス・エージェントの IP アドレスをアクセス制御 IP リストに追加します。

  以下の両方の IP アドレスを追加します。
   * 169.60.154.134 (米国南部サービス地域)
   * 169.61.86.179 (米国東部サービス地域)

1. **「保存」**をクリックして、終了 URI の構成を完了します。

転送先の電話番号と終了 URI をメモします。 後で、{{site.data.keyword.conversationshort}} ダイアログでそれらを転送先として指定できます。


## ステップ 2: 通話中転送のための {{site.data.keyword.conversationshort}} の構成
{: #conversation-setup}

{{site.data.keyword.conversationshort}} サービスでの処理方法について詳しくは、[{{site.data.keyword.conversationshort}} について](../conversation/index.html#about)を参照してください。

1. {{site.data.keyword.Bluemix_notm}} ダッシュボードで、ボイス・エージェントが使用する {{site.data.keyword.conversationshort}} インスタンスを選択します。

1. _「開始 (Getting started)」_ダッシュボードから、**「起動ツール (Launch tool)」**ボタンをクリックします。

1. 編集するワークスペースで**「開始 (Getting started)」**をクリックします。

1. **「インテントの追加 (Add intent)」**をクリックして、インテントの名前 (_Transfer_ など) を入力します。

  さらに詳細情報を入力したり、後に再びインテントを編集して詳細化したりすることもできます。

1. 通話中転送インテントを作成した後に、_「ダイアログ (Dialog)」_タブを選択します。

1. **「ノードの追加 (Add node)」**をクリックして、ノードの名前 (_Call Transfer_ など) を入力します。

1. _「ボットが次のものを認識した場合: (If the bot recognizes:)」_セクションで、**Call transfer インテント**と入力して、作成したインテントを検索します。

1. _「次のように応答する: (Then respond with:)」_セクションで、**「&vellip;」**アイコンをクリックして、**「JSON エディターを開く (Open JSON editor)」**を選択します。 以下のコード・スニペットをコピーして貼り付け、フィールド内のコードを置き換えます。

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
                "transferTarget": "sip:18889990000\\@dal.watson-va.netfoundry.net"
            }
        }
    }
}
```
{: codeblock}

**注**: 転送ターゲットの SIP URI には、電話番号と作成した終了 URI が含まれます。 例えば、電話番号が `18889990000` で終了 URI が `mysiptrunk.pstn.twilio.com` の場合、完全な SIP URI は `sip:18889990000\\@mysiptrunk.pstn.twilio.com` となります。Netfoundry を使用し、電話番号が `18889990000` である場合、完全な SIP URI は `sip:18889990000\\@dal.watson-va.netfoundry.net` となります。

## 次のステップ
{: #Next}

ボイス・エージェントに関連付けられた電話番号を呼び出してインテント内に指定したキー用語を使用することにより、ボイス・エージェントをテストします。 ボイス・エージェントによってリダイレクトが行われれば、成功です。

これで、選択したキー用語と語句に応答するように、**転送**インテントおよびダイアログを詳細化して構成できるようになりました。
