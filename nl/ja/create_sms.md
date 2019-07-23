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


# SMS エージェントの作成
{: #sms_config_instance}

{{site.data.keyword.iva_full}} サービスを作成した後、_「管理」_ダッシュボードから個々の SMS エージェントを作成できます。
{: shortdesc}

1. _「管理」_ダッシュボードの_「音声エージェント」_タブに移動して、**「音声エージェントの作成」**をクリックします。

1. **「エージェント・タイプ」**には_「SMS」_を選択します。

1. **「名前」**に、ボイス・エージェントの固有の名前を指定します。 例えば、`Customer Support - North America` と指定します。 この名前の最大長は 64 文字です。

1. 「電話番号」では、SIP トランクから取得した国別コードと市外局番を含む番号を追加します。例えば、米国の 800 ナンバーの場合は、電話番号を 18883334444 のように指定します。電話番号は最大 30 文字で、スペースや + ( ) - 文字を含めることができます。SMS ではユーザーごとに 1 つの番号だけがサポートされます。

1. **「SMS プロバイダー」**の下で、ユーザー名、パスワード、SMS プロバイダーの API URL を入力します。例えば _Twilio_ を使用する場合、ユーザー名は**アカウント SID**、パスワードは**認証トークン**、SMS プロバイダーは `https://api.twilio.com` です。

1. **「会話」**の下で、{{site.data.keyword.conversationshort}} サービス・インスタンスへの接続を構成します。自分または他の人が所有する {{site.data.keyword.Bluemix_notm}} アカウントの {{site.data.keyword.conversationshort}} サービス・インスタンスを使用できます。 また、サービス・オーケストレーション・エンジン (SOE) を介して、このいずれかのオプションに接続することもできます。

   * ダラスまたはワシントン DC の地域で SMS エージェントを作成する場合、{{site.data.keyword.conversationshort}} サービス・インスタンスがなければ、**「サービス・インスタンス」**メニューからそれを作成できます。
   * また、[**「サービス・タイプ」**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service)を変更して {{site.data.keyword.conversationshort}} ダイアログの他のソースに接続したり SOE を使用して接続したりすることもできます。
   * 複数のサービス・ロケーションを構成する場合は、他のロケーション・オプションをクリックし、**「ロケーションの有効化 (Enable location)」**を選択して、他の {{site.data.keyword.conversationshort}} インスタンスへの接続を構成します。 詳しくは、[複数の Watson サービス・ロケーションの追加](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location)を参照してください。

1. **「インバウンド・メッセージから会話を開始する (Initiate conversation from inbound messages)」**ボックスにチェック・マークを付けると、ユーザーが SMS エージェントとの SMS セッションを開始できるようになります。

1. **「セッション・タイムアウトで通知する (Notify on session timeout)」**ボックスにチェック・マークを付けると、エージェントが一定時間にわたり応答を受け取っていないのでタイムアウトになるという SMS メッセージが SMS エージェントからユーザーに送られるようになります。 

    - セッション・タイムアウトのカスタム時間の設定など、SMS エージェントで使用可能な **詳細オプション**について詳しくは、[詳細オプション](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced)を参照してください。
    - セッション・タイムアウト時に通知が必要な場合にのみ、このボックスにチェック・マークを付けてください。

1. イベント転送を有効にして、ボイス・エージェントが処理した通話に関する情報を、{{site.data.keyword.cloudantfull}} で収集することもできます。 詳しくは、[ボイス・エージェントのイベント転送の有効化](/docs/services/voice-agent?topic=voice-agent-event_forwarding)を参照してください。他の構成オプションについては、[ボイス・エージェントの構成](/docs/services/voice-agent?topic=voice-agent-managing#configure_va)を参照してください。

1.  **「ボイス・エージェントの作成 (Create voice agent)」**をクリックして、SMS エージェントと新しいサービスを作成します。

1. [手順](/docs/services/voice-agent?topic=voice-agent-connect-sms)に従って SMS プロバイダーに接続します。

SMS エージェントを作成した後、その電話番号をテキストで送信して SMS エージェントをテストします。_「使用状況」_ダッシュボードで、対話についての詳細情報を確認できます。[使用状況とログの表示](/docs/services/voice-agent?topic=voice-agent-logging)を参照してください。

音声通話中の顧客とボイス・エージェントの間の SMS メッセージングを可能にするには、SMS 番号が音声番号と一致する必要があります。
{: tip}

SMS エージェントを作成するかボイス・エージェントに SMS 機能を追加する前に、適切な資格情報をセットアップし、API キーを生成して SMS 番号にプログラムする**必要があります**。詳しくは、[API キーの生成と資格情報の設定](/docs/services/voice-agent?topic=voice-agent-connect-sms#sms_access)を参照してください。

さらに、SMS 機能用の SIP トランクを構成する**必要があります**。Twilio などのプロバイダーの資料を参照してください。Twilio 電話番号がない場合、[Twilio SIP トランクの作成](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup)を参照してください。

Twilio 番号を取得したら、SMS 機能用にそれを構成する必要があります。詳しくは、[Twilio for SMS の構成](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup)を参照してください。

資格情報の作成で問題が発生した場合は、サービス・インスタンス管理者に依頼して、*管理者 (マネージャー)* または*ライター*のアクセス権限を取得してください。
{: tip}

## SMS エージェントの拡張オプション
{: #sms_advanced}

**「電話番号」**フィールドの後の**「詳細の表示 (Show Advanced)」**をクリックします。

1. オプションの**「会話読み取りタイムアウト (Conversation read timeout)」**の値を設定します。これは、SMS Gateway が Watson Assistant からの応答を待つ時間 (秒数) です。この時間を過ぎると、SMS Gateway は Watson Assistant への連絡を再試行します。それでもサービスに到達できない場合、SMS/MMS メッセージは失敗します。デフォルトで 30 秒に設定されています。

1. オプションの**「セッション・タイムアウト」**を設定します。これは、SMS Gateway がユーザーからの応答を受信しない場合にセッションが期限切れになるまでの時間 (秒数) です。

1. **「会話が失敗した場合の応答メッセージ (Conversation failure reply message)」**を設定します。これは、Watson Assistant に到達できない場合に送られるデフォルトの応答メッセージです。デフォルトでは、`We're sorry, but we can't respond to your message.` (申し訳ありません、メッセージに応答できません) に設定されています。

### セッションの強制終了に関する SMS エージェントの構成
{: #sms_terminate}

{{site.data.keyword.iva_full}} SMS エージェントは、セッション・タイムアウトの値に基づいてセッションを強制終了します。この値は構成可能で、デフォルトで 30 秒に設定されています。 

また、ユーザーからのセッション終了コマンドに応答する目的で {{site.data.keyword.conversationshort}} サービスにノードを追加することもできます。 

1. {{site.data.keyword.Bluemix_notm}} ダッシュボードで、ボイス・エージェントが使用する {{site.data.keyword.conversationshort}} インスタンスを選択します。

1. ダッシュボードから **SMS 強制終了インテント**を作成します。または、ボイス・エージェント用に既に使用している既存のエージェントを変更することもできます。例えば_「コールの終了 (End the call)」_などです。

1. ダッシュボードから **SMS 強制終了ノード**を追加します。

1. _「アシスタントが次を認識する場合: (If assistant recognizes:)」_セクションで、作成済みの **SMS 強制終了インテント**属性を追加します。

1. ノードに応答を追加します。以下のコード・スニペットをコピーして貼り付け、フィールド内のコードを置き換えます。

    ```json
        {
            "output": {
                 "text": {
                    "values": [
                        "Thank you for using the service. Goodbye!"
                    ],
                    "selection_policy”: “sequential"
                },
                "smsAction": {
                    "command": "terminateSession"
                }
            }
        }
    ```
    {: codeblock}

ボイス・エージェントを作成した後、その種類に応じて電話番号を呼び出すか電話番号にテキストを送信して、ボイス・エージェントをテストします。_「使用状況」_ダッシュボードで、対話についての詳細情報を確認できます。[使用状況とログの表示](/docs/services/voice-agent?topic=voice-agent-logging)を参照してください。
