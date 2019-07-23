---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# サービス・インスタンスとボイス・エージェントの管理
{: #managing}

_「管理」_ダッシュボードで、サービス・インスタンスの構成変更、個々のボイス・エージェントの作成、編集、複製、構成、削除を行えます。 サービス・インスタンスの中に複数のボイス・エージェントを作成できます。各ボイス・エージェントには、最大 1000 個の固有の番号と説明を含めることができます。 ただし、各ボイス・エージェントには固有の名前と少なくとも 1 つの電話番号が必要です。

* **注**: 単一の {{site.data.keyword.iva_full}} サービス・インスタンスには、最大 150 のボイス・エージェントを作成できます。
{: shortdesc}

## 音声エージェント・サービスのダッシュボードにナビゲートする
{: #navigate_manage}

_「管理」_ダッシュボードは、{{site.data.keyword.iva_short}} サービスのダッシュボードにあります。

1. [{{site.data.keyword.Bluemix_notm}} アカウントのリソース・リスト](https://cloud.ibm.com/resources)に移動します。

1. **「サービス」**のリストから、**音声エージェント**・サービスのインスタンスを選択して、_「管理」_タブにこのサービスのダッシュボードを開きます。

## ボイス・エージェントのサマリー
{: #agent_summary}

既存のボイス・エージェントが既に存在する場合は、そのエージェントのすべての番号、説明、および構成設定のサマリーを表示できます。 サマリーを表示するには、ボイス・エージェントの**「名前」**の左にあるドロップダウン矢印ボタンをクリックします。 そうすると、サマリーが展開されます。

ボイス・エージェントには複数の番号が含まれる場合がありますが、エージェントのサマリーでは**「1 次番号 (Primary Number)」**のみが表示されるように選択されています。 デフォルトで、これはボイス・エージェントに最初に追加された番号です。表示のみを目的としており、機能的な目的はありません。 ボイス・エージェントから別の番号を表示する方法については、[複数の番号の管理](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num)を参照してください。

エージェント・サマリーでボイス・エージェントのすべての番号を確認できます。 構成のサマリーが展開された後、**「番号の表示 (View Numbers)」**ボタンをクリックすると、すべての番号のリストが新しい**「管理」**ダイアログ・ボックスに表示されます。 **「管理」**ダイアログ・ボックスの操作について詳しくは、[複数の番号の管理](/docs/services/voice-agent?topic=voice-agent-multi_num)のページを参照してください。

## サービス・インスタンスの最大同時接続数の編集
{: #edit_service}

どのプランでも、2 つの同時接続を無料で受け取ります。 _標準_ プランまたは_プレミアム_・プランを使用している場合は、_「インスタンス」_タブで、[最大同時接続数](/docs/services/voice-agent?topic=voice-agent-edit_concurrency)をデフォルト設定から変更できます。

## ボイス・エージェントの作成
{: #create_va}

_「管理」_ダッシュボードの_「音声エージェント」_タブで、[ボイス・エージェントを新規作成](/docs/services/voice-agent?topic=voice-agent-config_instance)できます。

## ボイス・エージェントの編集
{: #edit_va}

_「管理」_ダッシュボードの_「音声エージェント」_タブで、既存のボイス・エージェントを編集して変更できます。 ボイス・エージェントを編集するには、ボイス・エージェントのオプションのリストから**「エージェントの編集 (Edit Agent)」**をクリックします。 構成を変更し、変更内容を保存します。

## ボイス・エージェントの複製
{: #clone_va}

ボイス・エージェントを複製するときは、Watson サービスのすべての構成が新規エージェントにコピーされます。 ボイス・エージェントを複製するには、ボイス・エージェントのオプションのリストから**「エージェントの複製 (Clone Agent)」**をクリックします。 ボイス・エージェントに固有の名前と電話番号を指定して、必要に応じて構成オプションを変更し、変更内容を保存します。

## ボイス・エージェントの削除
{: #delete_va}

ボイス・エージェントを削除して電話番号を解放できます。 1 つの電話番号を複数のボイス・エージェントに指定することはできません。 ある電話番号を別のボイス・エージェントで使用するには、まずその電話番号を使用しているボイス・エージェントを削除する必要があります。

ボイス・エージェントを削除するには、_「音声エージェント」_タブに移動し、該当するボイス・エージェントのオプション・リストから**「エージェントの削除」**をクリックし、変更を保存します。 ボイス・エージェントがボイス・エージェントのリストから削除されます。

## 番号または説明によるボイス・エージェントの検索
{: #search}

ボイス・エージェントに保存されている番号または説明に基づいてエージェントを検索できます。

_「検索」_バーに番号または説明を入力できます。 入力していくと、検索結果が自動的に更新されます。  

## ボイス・エージェントの構成
{: #configure_va}

ボイス・エージェントの作成、複製、または編集を行う際には、ボイス・エージェントや関連サービスへの接続に関する構成設定を変更できます。

* **[複数の電話番号の構成](/docs/services/voice-agent?topic=voice-agent-multi_num):** 複数の電話番号が含まれるようボイス・エージェントを構成できます。
* **[複数のサービスの場所を構成する](/docs/services/voice-agent?topic=voice-agent-disaster-recovery):** 接続対象サービスの場所を複数カ所にすることで、サービスの冗長性を確保できます。
* **[サード・パーティーの音声テキスト変換サービスに接続する](/docs/services/voice-agent?topic=voice-agent-third-party):** {{site.data.keyword.texttospeechshort}} や {{site.data.keyword.speechtotextshort}} を使用する代わりに、Google Cloud Speech-to-Text などのサード・パーティー API にボイス・エージェントを接続できます。
* **[他の {{site.data.keyword.Bluemix_notm}} ワークスペースのサービスを使用する](/docs/services/voice-agent?topic=voice-agent-other_service):** 他の {{site.data.keyword.Bluemix_short}} アカウントのワークスペースに属する {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、または {{site.data.keyword.speechtotextshort}} のサービス・インスタンスを使用するようにボイス・エージェントを構成できます。
* **[Watson Assistant にサービス・オーケストレーション・エンジンを構成する](/docs/services/voice-agent?topic=voice-agent-conversation_va):** サービス・オーケストレーション・エンジン (SOE) を経由して {{site.data.keyword.conversationshort}} スキルに接続することができます。 SOE はサービスとの間で送受信されるメッセージを代行受信し、サード・パーティー API を使用して変更できるようにします。
* **[ボイス・エージェントのイベント転送を有効にする](/docs/services/voice-agent?topic=voice-agent-event_forwarding):** より自然な会話を発信者に提供するために、{{site.data.keyword.iva_short}} の通話データを収集、分析することができます。 作成する各ボイス・エージェントは、管理対象の指定された {{site.data.keyword.cloudant_short_notm}} にイベント・レポートを転送することができます。 

## ボイス・エージェントの拡張オプションの構成
{: #config-advanced}

ボイス・エージェントを作成または複製するときに、**「詳細の表示 (Show advanced)」**をクリックすると、以下の拡張構成オプションを表示できます。

* **会話読み取りタイムアウト (オプション)(Conversation read timeout (optional))**: このオプションは、ボイス・エージェントが Watson Assistant からの応答を待つ時間を秒単位で設定します。 この時間を過ぎると、ボイス・エージェントは Watson Assistant との通信を再試行します。 それでもサービスに到達できない場合、通話は失敗します。 デフォルトで 5 秒に設定されます。
* **{{site.data.keyword.conversationshort}} 失敗応答メッセージ (オプション) ({{site.data.keyword.conversationshort}} failure reply message (optional))**: 通話が {{site.data.keyword.conversationshort}} に接続できない場合にメッセージ受信者に送信されるデフォルトの応答メッセージ。 1024 文字まで入力することができます。
* **転送失敗応答メッセージ (オプション)(Transfer failure reply message (optional))**: 通話中転送が失敗した場合に発信者に対して流されるデフォルトの応答メッセージ。 1024 文字まで入力することができます。
* **カスタム SIP INVITE ヘッダー (オプション) (Custom SIP INVITE Header (optional))**: 着信した SIP INVITE 要求から取り出すカスタム SIP ヘッダーを指定します。 1024 文字まで入力することができます。
* **{{site.data.keyword.iva_short}} から仮のリンギング応答を送信する (Send provisional ringing response from {{site.data.keyword.iva_short}})**: {{site.data.keyword.iva_short}} が着信を処理する間 `180 リンギング`応答を送信します。 デフォルトでは有効です。
* **転送時に発信者を保留にする (Put caller on hold on transfer)**: 転送時に発信者を保留にします。 デフォルトでは有効です。
* **転送が失敗したときに通話を切断する (Disconnect call on transfer failure)**: 通話中転送が失敗した場合に通話を切断するかどうかを指定します。  デフォルトでは有効です。 この設定を無効にした場合に通話中転送が失敗すると、{{site.data.keyword.iva_short}} が会話のターンを開始します。 その後、ダイアログでの構成に応じて、{{site.data.keyword.conversationshort}} は通話を切断することも、別の宛先に転送することもできます。
* **ネットワーク・イベント時に {{site.data.keyword.conversationshort}} に通知する (Notify {{site.data.keyword.conversationshort}} on network events)**: このオプションを有効にした場合、ネットワーク・エラーが検出されると、{{site.data.keyword.iva_short}} は "vgwNetworkWarningMessage" というテキストで {{site.data.keyword.conversationshort}} へのターンを開始します。 `vgwNetworkWarnings` 状態変数には、現在のターンで発生したネットワーク・イベントのリストが入ります。 このオプションを無効にした場合、現在のターンで発生したネットワーク・イベントのリストは、次のターン・イベントで `vgwNetworkWarnings` 状態変数に入れて送信されます。 デフォルトでは有効です。
