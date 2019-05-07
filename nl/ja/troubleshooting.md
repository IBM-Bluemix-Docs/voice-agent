---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# トラブルシューティングとサポート
{: #troubleshooting}

{{site.data.keyword.iva_full}} で問題が発生しましたか? 一般的な問題のトラブルシューティングのヒントを確認し、ご質問があればコミュニティーにお問い合わせください。
{: shortdesc}

## {{site.data.keyword.iva_short}} をトラブルシューティングする方法
{: #how-to}

ボイス・エージェントの問題をトラブルシューティングするには、ロギング、使用ログ、およびイベント転送を使用して、エラーや障害のレコードを見つけます。 これらのレコードは、ボイス・エージェントの問題の診断と解決に役立ちます。 {{site.data.keyword.iva_short}} で問題が発生している場合は、以下の手順を試してください。

1. 通話が失敗すると、{{site.data.keyword.conversationshort}} の最終ターンでその失敗について説明される場合があります。

1. 使用ログに、特定の通話中に発生した可能性があるエラーが示されます。 [使用状況と通話ログの表示](/docs/services/voice-agent?topic=voice-agent-logging)を参照してください。

1. 信号エラーがないか、サービス・プロバイダーのログを確認します。 例えば、Twilio では、ホストされている各 SIP トランクのログを利用できます。

1. [ボイス・エージェントのイベント転送を有効化](/docs/services/voice-agent?topic=voice-agent-event_forwarding)することで、発着信詳細記録 (CDR) を Cloudant データベースに転送するようにボイス・エージェントを構成できます。これにより、通話が失敗した理由を調べられます。 {{site.data.keyword.conversationshort}} ターン・イベントなど、通話中のすべての会話ターンに関する詳細を提供できるターンがあります。

**重要:** CDR イベント、転写イベント、およびターン・イベントにはユーザーからの情報が取り込まれますが、それには保護医療情報 (PHI)、個人情報 (PII)、または PCI データ・セキュリティー基準 (PCI DSS) のデータが含まれている可能性があります。 個人情報の漏えいを防ぐため、会話内および会話中にユーザーどうしがやりとりする機密情報が {{site.data.keyword.cloudant_short_notm}} インスタンスで適切に保護されるようにする必要があります。


## ヘルプの利用
{: #help}

支援が必要な場合は、以下の任意の場所に質問やコメントを投稿して開発者コミュニティーに参加してください。この場所はすべて頻繁に監視されています。

* `voice-agent` タグを使用して、[dwAnswers フォーラム ![外部リンクのアイコン](../../icons/launch-glyph.svg "外部リンクのアイコン")](https://developer.ibm.com/answers/topics/voice-agent/) に投稿する
* `voice-agent` タグを使用して、[StackOverflow![外部リンクのアイコン](../../icons/launch-glyph.svg "外部リンクのアイコン")](http://stackoverflow.com/questions/tagged/voice-agent){: new_window} に投稿する
* Slack で、[IBM Cloud テクノロジー![外部リンクのアイコン](../../icons/launch-glyph.svg "外部リンクのアイコン")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) チーム内の `#ibmvoicegateway` チャネルの下を確認する

**注**: 通話のログまたはレコードを投稿する前に、会話の中で発信者とユーザーが共有した可能性のあるすべての個人情報を削除してください。

## トラブルシューティングのヒント
{: #troubleshooting-tips}

### ボイス・エージェントを呼び出しても電話の応答がありません。なぜでしょうか

通話がサービスに接続していなかった可能性があります。 この問題は、{{site.data.keyword.iva_short}}サービス・インスタンスが正しく設定されていない場合に発生します。 以下のボイス・エージェントの設定を確認してください。

* ボイス・エージェントの_「管理」_ ダッシュボードの電話番号が NetFoundry や Twilio などの SIP トランキング・プロバイダーから取得した電話番号と同じであること。

   **注:** ボイス・エージェントの_「管理」_ ダッシュボードで電話番号を指定するときには、国別コードと市外局番を含める必要があります。 例えば、`18884253968` などと指定します。

* Watson サービス資格情報、URL、および {{site.data.keyword.conversationshort}} ワークスペース ID がすべて有効であること。
* {{site.data.keyword.conversationshort}} スキルのダイアログが正しく作成されていること。
  * 事前ビルドされたスキルとして、GitHub にある [会話サンプル ![外部リンクのアイコン](../../icons/launch-glyph.svg "外部リンクのアイコン")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json)をインポートすることができます。 会話サンプルを JSON ファイルとして保存し、そのファイルを {{site.data.keyword.conversationshort}} ツールでスキルとしてインポートする方法について詳しくは、[*入門チュートリアル*のステップ 3](/docs/services/voice-agent?topic=voice-agent-getting-started-tutorial#step3) を参照してください。
  * 独自の {{site.data.keyword.conversationshort}} ダイアログを作成した場合、`conversation_start` 条件を含むノードと、デフォルトの応答を含むノードがダイアログに含まれていることを確認してください。 詳しくは、{{site.data.keyword.conversationshort}} 資料の[ダイアログの作成](/docs/services/assistant?topic=assistant-getting-started#getting-started-build-dialog)を参照してください。
* ボイス・エージェントの_「使用 (Usage)」_ダッシュボードに電話通話がリストされているかどうか確認してください。 電話通話の項目があれば、ボイス・エージェントは Watson サービスに接続されていることになります。

### ボイス・エージェントの作成時に電話番号を指定できません。なぜでしょうか

指定した電話番号が既存のボイス・エージェントによって使用されていないか確認してください。 1 つの電話番号を複数のボイス・エージェントに指定することはできません。 SIP トランキング・プロバイダーから別の電話番号を取得し、それを使用して別のボイス・エージェントを作成することができます。 あるいは、[_「管理」_ダッシュボードで既存のボイス・エージェントを削除して](/docs/services/voice-agent?topic=voice-agent-managing#delete_va)その電話番号を解放してから、新しいボイス・エージェントを作成してください。

### 通話が頻繁に失敗する理由

サービス・オーケストレーション・エンジン (SOE) が、長時間実行されるトランザクションを開始したためにタイミング良くボイス・エージェントに応答せず、通話が失敗した場合、ボイス・エージェントに問題が発生する可能性があります。 トランザクションがデフォルトの {{site.data.keyword.conversationshort}} タイムアウトを超過すると、通話は失敗します。 通話失敗を回避するために、SOE では、`vgwConversationResponseTimeout` 状態変数を使用してデフォルトの {{site.data.keyword.conversationshort}} タイムアウトを変更できます。 [{{site.data.keyword.conversationshort}} ダイアログで設定される変数](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html#variables-conv)を参照してください。
