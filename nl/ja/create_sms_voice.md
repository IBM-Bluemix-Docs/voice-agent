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

# SMS 機能が可能なボイス・エージェントの作成
{: #sms_voice_config_instance}

{{site.data.keyword.iva_full}} サービスを作成した後、_「管理」_ダッシュボードから、SMS 機能を持つ個々の SMS エージェント、または SMS 機能だけを持つボイス・エージェントを作成できます。
ユーザーが受信するボイス・コマンドに応じて、インバウンド音声通話を受け取って SMS アウトバウンド・メッセージで応答するよう {{site.data.keyword.iva_full}} を構成することができます。それを構成するには、{{site.data.keyword.conversationshort}} サービスでノードとインテントを追加します。
{: shortdesc}


1. _「管理」_ダッシュボードの_「音声エージェント」_タブに移動して、**「音声エージェントの作成」**をクリックします。

1. **「エージェント・タイプ」**には_「音声 + SMS (Voice + SMS)」_を選択します。

1. [ボイス・エージェントの作成](/docs/services/voice-agent?topic=voice-agent-config_instance)の説明に従います。

1. **「インバウンド・メッセージから会話を開始する (Initiate conversation from inbound messages)」**ボックスにチェック・マークを付けると、ユーザーが SMS エージェントとの SMS セッションを開始できるようになります。

1. **「セッション・タイムアウトで通知する (Notify on session timeout)」**にチェック・マークを付けると、エージェントが一定時間にわたり応答を受け取っていないのでタイムアウトになるという SMS メッセージが SMS エージェントからユーザーに送られるようになります。 

   - セッション・タイムアウトのカスタム時間の設定など、SMS エージェントで使用可能な **詳細オプション**について詳しくは、[詳細オプション](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced)を参照してください。

1. [SMS エージェントの作成](/docs/services/voice-agent?topic=voice-agent-sms_config_instance)の説明に従って SMS エージェントを作成します。

1. _**注:**_ エージェントでボイスと SMS の両方を統合する場合 (例えば音声入力を受け取り SMS アウトバウンド・メッセージとして応答を返す場合)、**SMS** エージェント用にいずれかの**音声**番号を使用する**必要があります**。

### ボイスと SMS の統合用に Watson Assistant を構成する
{: #sms_outbound}

1. {{site.data.keyword.Bluemix_notm}} ダッシュボードで、ボイス・エージェントが使用する {{site.data.keyword.conversationshort}} インスタンスを選択します。

1. ダッシュボードから**アウトバウンド SMS インテント**を作成します。

1. ダッシュボードから**アウトバウンド SMS ノード**を追加します。

1. _「アシスタントが次を認識する場合: (If assistant recognizes:)」_セクションで、作成済みの **アウトバウンド SMS インテント**属性を選択します。

1. ノードに応答を追加します。以下のコード・スニペットをコピーして貼り付け、フィールド内のコードを置き換えます。

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


1. エージェントをコールしてノードをトリガーすると、発信元の電話機でテキスト・メッセージが受信されます。 

{{site.data.keyword.conversationshort}} サービスでの処理方法について詳しくは、[{{site.data.keyword.conversationshort}} について](/docs/services/assistant?topic=assistant-index#indext)を参照してください。
