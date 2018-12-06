---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-08"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# API のアクション・タグと状態変数
{: #api}

この参照資料を使用して、アクション・タグや状態変数を見つけてください。アクション・タグは、会話セッション中にボイス・エージェントが実行するアクションを開始します。状態変数は、ボイス・エージェントの特性を定義します。特性は、変更されない限り、会話が終わるまで維持されます。
{: shortdesc}

状態を設定してアクション・シーケンスを開始する方法を示すサンプル・コードや例については、[API を使用したボイス・エージェントのプログラミング](api.html)を参照してください。

{{site.data.keyword.iva_full}} は IBM Voice Gateway に基づいているため、API は同じ仕方で機能します。 Voice Gateway を使い慣れている場合は、{{site.data.keyword.iva_short}} でも {{site.data.keyword.conversationshort}} ダイアログで同じアクションと状態変数を使用できます。 [Voice Gateway API のアクション・タグおよび状態変数](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html)を参照してください。
{: tip}

## アクション・コマンドと属性
{: #actions-and-attributes}

次の表は、{{site.data.keyword.conversationshort}} ダイアログで指定できるアクションと、各アクションに対して定義できる属性の一覧です。

| アクション・コマンド | 説明 | 属性 |
| ----- | ----- | ----- |
| `vgwActPlayText`| {{site.data.keyword.texttospeechshort}} サービスによって音声に変換された発話を再生します。 | <ul><li>`text`: 再生する発話のリスト。 オプション。 <p>例:<br/><code>"text": [<br/>&nbsp;&nbsp;&nbsp;"Hello. How can I help you today?"<br/>&nbsp;&nbsp;&nbsp;]</code><p> デフォルトでは、アクションは `output.text` フィールドに構成された一連の発話を再生します。 </li><li>`errAudioURL`: ボイス・エージェントが {{site.data.keyword.texttospeechshort}} サービスと通信してアクションを実行することができない場合に再生する音声ファイルの URL。 音声ファイルは WAV 形式である必要があります。</li></ul>|
| `vgwActPlayUrl` | 含められたテキストが再生された直後に音声ファイルを再生します (保留音 (MOH) や共通の一回限りの発話を再生するためなど)。 テキストが含められていない場合、音声は即座に再生されます。 このファイルは、単一チャネル (モノ) である必要があり、PCM でエンコードし、8,000 Hz のサンプリング・レートとサンプルごとに 16 ビットの容量を持たせる必要があります。 | <ul><li>`url`: 再生する URL。 必須。</li><li> `playURLInLoop`: (オプション) URL をループで再生するかどうかを指定する場合は、これを `Yes` または `No` に設定します。 デフォルト値は `No` です。</li></ul> |
| `vgwActHangup` | 通話を停止します。 | 属性はありません。 |
| `vgwActSetSTTConfig` | Watson {{site.data.keyword.speechtotextshort}} サービスに渡すボイス・エージェントの一連のパラメーターを適用します。 {{site.data.keyword.conversationshort}} サービスは、通話に基づいてパラメーターを動的に定義します。 | 属性は、JSON プロパティーとして、{{site.data.keyword.speechtotextshort}} サービスに透過的に渡されます。 |
| `vgwActSetTTSConfig` | Watson {{site.data.keyword.texttospeechshort}} サービスに渡すボイス・エージェントの一連のパラメーターを適用します。 {{site.data.keyword.conversationshort}} サービスは、通話に基づいてパラメーターを動的に定義します。 |  属性は、JSON プロパティーとして、{{site.data.keyword.texttospeechshort}} サービスに透過的に渡されます。  |
| `vgwActSetConversationConfig` | {{site.data.keyword.conversationshort}} ワークスペースを定義するためのボイス・エージェントの一連のパラメーターを適用します。 {{site.data.keyword.conversationshort}} サービスは、通話に基づいてパラメーターを動的に定義します。 | <ul><li>`url`: {{site.data.keyword.conversationshort}} サービス API の `url` 資格情報。</li><li>`workspaceID`: {{site.data.keyword.conversationshort}} ワークスペース ID</li><li>`username`: {{site.data.keyword.conversationshort}} サービス の `username` 資格情報。</li><li>`password`: {{site.data.keyword.conversationshort}} サービス の `password` 資格情報。</li></ul> |
| `vgwActCollectDtmf` | デュアルトーン複数周波数 (DTMF) の入力を収集するようにボイス・エージェントに指示します。 | 以下の属性のいずれかを定義する必要があります。 <ul><li> `dtmfTermKey`: DTMF 終了キー。DTMF 入力の終了を通知します。 例えば、「`#`」などです。 </li><li> `dtmfCount`: 収集する DTMF ディジット。</li></ul> これらの条件のいずれかが満たされた場合、ボイス・エージェントは DTMF 入力の収集を停止します。 |
| `vgwActPauseDTMF` | DTMF 入力を無効にします。 `vgwActUnPauseDTMF` アクションによって再び有効にされるまで、すべての DTMF 入力が無視されます。 | 属性はありません。 |
| `vgwActUnPauseDTMF` | `vgwActPauseDTMF` アクションによって無効にされた DTMF 入力を有効にします。 | 属性はありません。 |
| `vgwActExcludeFromTTSCache` | {{site.data.keyword.texttospeechshort}} サービスからの応答をキャッシュしないように、ボイス・エージェントに指示します。 例えば、機密性の高い PHI、PII、PCI DSS のデータや顧客の名前や誕生日の日付などの動的情報を含む応答は、除外する必要があります。 <br/>このアクション・タグは、キャッシュしたくない発話ごとに {{site.data.keyword.conversationshort}} ダイアログ・ノードで設定する必要があります。 | 属性はありません。 |
| `vgwActPauseSTT` | `vgwActUnPauseSTT` アクションによって再度有効にされるまで、音声テキスト化処理を一時停止します。 録音を有効にして、音声テキスト化処理を一時停止している場合、発信者からの音声は取り込まれません。 | 属性はありません。 |
| `vgwActUnPauseSTT` | `vgwActPauseSTT` アクションによって以前に一時停止された音声テキスト化処理を再開します。 | 属性はありません。 |
| `vgwActEnableSpeechBargeIn` | 音声バージインを有効にして、ボイス・エージェントの再生を発信者が発話で中断できるようにします。 | 属性はありません。 |
| `vgwActDisableSpeechBargeIn` | 音声バージインを無効にして、発信者が話しても、ボイス・エージェントの再生が中断されないようにします。 | 属性はありません。 |
| `vgwActEnableDTMFBargeIn`| DTMF バージインを有効にして、ボイス・エージェントの再生を発信者がキーを押して中断できるようにします。 | 属性はありません。 |
| `vgwActDisableDTMFBargeIn` | DTMF バージインを無効にして、発信者がキーを押しても、ボイス・エージェントの再生が中断されないようにします。 | 属性はありません。 |
| `vgwActForceNoInputTurn` | 発信者からの入力を待たずに、強制的に会話のターンを交替します。 | 属性はありません。 |
{: caption="表 1. {{site.data.keyword.conversationshort}} サービスから開始できるアクション" caption-side="top"}

## {{site.data.keyword.conversationshort}} ダイアログで設定される状態変数
{: #state-variables-conv}

{{site.data.keyword.conversationshort}} ダイアログ内で以下の状態変数を設定することにより、ボイス・エージェントの動作を変更することができます。

| 状態変数名 | 予期される値 | 説明 |
| -------------- | ------ | ----------- |
| `vgwByeCustomHeader` | ユーザー定義 | 出力 SIP BYE メッセージのカスタム・ヘッダーを定義します。 カスタム・ヘッダーの値は、`vgwByeCustomHeaderVal` 状態変数で定義します。  |
| `vgwByeCustomHeaderVal` | ユーザー定義 | 出力 SIP BYE メッセージのカスタム・ヘッダーの値を定義します。 カスタム・ヘッダーは、`vgwByeCustomHeader` 状態変数で定義します。 |
| `vgwPostResponseTimeoutCount` | 時間 (ミリ秒単位) | 応答が発信者に対して再生された後に、新しい発話を待機する時間。 この値を超過すると、{{site.data.keyword.conversationshort}} は、タイムアウトが発生したことを示す「vgwPostResponseTimeout」という語句を含んだテキスト更新を受け取ります。|
| `vgwConversationFailedMessage` | テキスト・ストリング | {{site.data.keyword.conversationshort}} サービスが失敗したときに、発信者に対して流されるメッセージ。 最初のターンでこの変数を設定するように {{site.data.keyword.conversationshort}} ダイアログを構成してください。 |
| `vgwSessionInactivityTimeout` | 時間 (分単位) <br/><br/>デフォルト: `2` | 非アクティブ・タイムアウト間隔。 このタイムアウト間隔の値は、ボイス・エージェントでセッションを非アクティブにできる長さを分単位で指定します。 タイムアウトの時間が満了すると、ボイス・エージェントはセッションを終了します。 |
| `vgwErrAudioURL` | ユーザー定義 | ボイス・エージェントが応答を再生しようとしたときに {{site.data.keyword.texttospeechshort}} サービスと通信できなかった場合に再生される音声ファイルの URL。 音声ファイルは WAV 形式である必要があります。 |
{: caption="表 2. {{site.data.keyword.conversationshort}} サービスによって設定される変数" caption-side="top"}

## ボイス・エージェントによって設定される状態変数
{: #state-variables-iva}

| 状態変数名 | 予期される値 | 説明 |
| -------------- | ----- | ----------- |
| `vgwSessionID`   | ユーザー定義 <br/><br/> デフォルト: `Call-ID` | SIP INVITE 要求からプルされるカスタム・セッション ID ヘッダー。 この値は、セッションに関連するすべてのボイス・エージェント監査ログで使用されるグローバル・セッション ID を表します。 |
| `vgwSIPCallID` | SIP `Call-ID` | 通話に関連付けられた SIP 通話 ID。 |
| `vgwSIPRequestURI` | SIP `Request-URI` | 通話を開始した SIP 要求 URI。 |
| `vgwSIPToURI` | SIP `To` URI | 通話に関連付けられた SIP `To` URI。 |
| `vgwSIPFromURI` | SIP `From` URI | 通話に関連付けられた SIP `From` URI。 |
| `vgwBargeInOccurred` | `Yes` / `No` | バージインが発生するかどうかを示します。 |
| `vgwHangUp` | `Yes` / `No` | 会話が終了したかどうかを指定します。 |
| `vgwHangupReason` | 文字列 | 発信者によって、またはエラーのためにハングアップが始まったときに、通話が切断された理由を示すため、この変数が {{site.data.keyword.conversationshort}} サービスに送信されます。 {{site.data.keyword.conversationshort}} サービスに送信されるメッセージ要求のテキストには、「vgwHangUp」も含まれます。 |
| `vgwConversationResponseTimeout` | 時間 (秒数)<br/><br/>デフォルト: `5`  | {{site.data.keyword.conversationshort}} サービスからの応答をボイス・エージェントが待機する秒数。 この時間を過ぎると、ボイス・エージェントは {{site.data.keyword.conversationshort}} サービスとの通信を再試行します。 それでもサービスに到達できない場合、通話は失敗します。 |
| `vgwSTTResponse` | JSON オブジェクト | JSON 形式の {{site.data.keyword.speechtotextshort}} サービスからの最終応答。これには、推奨候補および代替候補のトランスクリプトと信頼性スコアが含まれます。 <p>例えば、次の形式は、{{site.data.keyword.speechtotextshort}} サービスから受け取る形式と正確に一致します。</p><p><code>{<br/>&nbsp;&nbsp;"result_index": 0,<br/>&nbsp;&nbsp;"warnings": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;"Unknown arguments: continuous."<br/>&nbsp;&nbsp;],<br/>&nbsp;&nbsp;"results": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"final": true,<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"alternatives": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello world",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.758<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello wooled",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.358<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;]<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}.</code></p> |
| `vgwIsDTMF` | `Yes` / `No` | {{site.data.keyword.conversationshort}} サービスへの入力がデュアルトーン複数周波数 (DTMF) かどうかを示します。 |
{: caption="表 3. ボイス・エージェントによって設定される変数" caption-side="top"}
