---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# API を使用したボイス・エージェントのプログラミング
{: #api}

{{site.data.keyword.conversationfull}} サービスからアクション・タグと状態変数を定義することによって、ボイス・エージェントの動作を制御できます。 アクション・タグは、会話セッション中にボイス・エージェントが実行するアクションを開始します。状態変数は、ボイス・エージェントの特性を定義し、この定義は特に変更されない限り、その会話中維持されます。
{: shortdesc}

{{site.data.keyword.iva_full}} は IBM Voice Gateway に基づいているため、API は同じ仕方で機能します。 Voice Gateway を使い慣れている場合は、{{site.data.keyword.iva_short}} でも {{site.data.keyword.conversationshort}} ダイアログで同じアクションと状態変数を使用できます。 [Voice Gateway API のアクション・タグおよび状態変数](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html)を参照してください。
{: tip}

## ダイアログ応答での JSON の編集
{: #json-editor}

アクションと状態は両方とも、JSON 形式のダイアログ・ノード応答で定義されています。 この JSON コードを編集するには、JSON エディターを開きます。

1. {{site.data.keyword.Bluemix_short}} ダッシュボードから、{{site.data.keyword.conversationshort}} サービス・インスタンスを選択します。
1. {{site.data.keyword.conversationshort}} ツールを起動します。
1. 編集するダイアログが含まれるワークスペースをクリックします。
1. 「**ダイアログ**」タブに進み、アクションまたは状態を設定するノードを選択します。
1. 応答で ![拡張応答](../conversation/images/kabob.png) アイコンをクリックし、**「JSON エディターを開く (Open JSON editor)」**を選択します。

この JSON エディター内では、続くセクションで説明するように、アクションを `output` プロパティーで、状態を `context` プロパティーでそれぞれ定義することができます。

## アクションの開始
{: #defining-actions}

通話中にボイス・エージェントでアクションを開始するには、JSON 形式の {{site.data.keyword.conversationshort}} ダイアログ・ノードの `output` プロパティーでアクション・タグを定義します。 `vgwAction` タグで単一のアクションを定義するか、`vgwActionSequence` タグでアクションのシーケンスを定義できます。 各アクションは、`command` プロパティーと、その後ろにオプションで指定される `parameter` プロパティー (コマンドに必要な属性を定義する) で構成されます。

### 単一アクション
{: #single-actions}

単一アクションを実行するには、`vgwAction` タグで、必要なパラメーター属性とともにアクションを定義します。 `output` プロパティーの `text` ブロックに、ボイス・エージェントがアクションの実行後に再生する発話を任意で含めることもできます。

以下の `vgwAction` タグの単一アクションは、ノードの応答がトリガーされたら通話を終了するようにボイス・エージェントに指示しています。 `vgwActHangup` コマンドにはパラメーターがないため、何も定義されていません。
```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActHangup"
    }
  }
}
```
{: codeblock}

以下のアクションは、デュアルトーン複数周波数 (DTMF) 信号の入力を収集すること、および発信者に対して定義されたテキストを再生することを、ボイス・エージェントに指示しています。

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActCollectDtmf",
      "parameters": {
        "dtmfTermKey": "#"
      }
    },
    "text": {
      "values": [
        "Enter your phone number."
      ]
    }
  }
}
```
{: codeblock}

### アクション・シーケンス
{: #action-sequences}

1 回の会話のターンで 1 つ以上のアクションを実行するには、`vgwActionSequence` タグ内に JSON リストとしてアクション・シーケンスを定義します。 アクションは、定義順に実行されます。

`vgwActionSequence` タグを使用する場合は、単一アクションとは異なり、ボイス・エージェントが発話を再生するには、アクションのリストに `vgwActPlayText` アクションが含まれている必要があります。 `vgwAction` タグとは違って、`output.text` フィールドの発話は自動的には再生されません。
{: tip}

より複雑な次の例では、`vgwActionSequence` タグの定義済みアクションにより、発話の再生中に音声のテキスト化処理を無効にして DTMF 入力を収集するようボイス・エージェントに指示しています。

```json
{
  "output": {
    "vgwActionSequence": [
      {
        "command": "vgwActPauseSTT"
      },
      {
        "command": "vgwActCollectDtmf",
        "parameters": {
          "dtmfTermKey": "#"
        }
      },
      {
        "command": "vgwActPlayText",
        "parameters": {
          "text": [
            "Enter your social security number."
          ]
        }
      }
    ]
  }
}

```
{: codeblock}

## 状態の設定
{: #setting-states}

会話のターンが交替しても持続する状態の変更を示すため、ボイス・エージェントは構成済みの {{site.data.keyword.conversationfull}} サービスと状態変数を交換します。 これらの状態変数は、{{site.data.keyword.conversationshort}} ダイアログ・ノードで、JSON 形式の [コンテキスト変数](../conversation/dialog-build.html#context)として定義されます。

例えば、{{site.data.keyword.conversationshort}} サービスへの接続が失敗した場合に発信者に流されるメッセージを設定するには、以下の状態変数を定義できます。

```json
{
  "context": {
    "vgwConversationFailedMessage": "Sorry, we're unable to connect you to our help line. Please try again later."
  }
}
```
{: codeblock}

ボイス・エージェントは、{{site.data.keyword.conversationshort}} サービスがステートレスであること、{{site.data.keyword.conversationshort}} サービスとの交換から次の交換までの間、すべての状態がボイス・エージェントで維持されることを想定します。 通話内で会話のターンが替わるごとに、状態が {{site.data.keyword.conversationshort}} サービスに渡され、REST メッセージの `context` セクションに入れられてサービスから戻されます。
