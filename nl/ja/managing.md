---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-19"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# ボイス・エージェントの管理
{: #managing}

_「管理」_ダッシュボードでボイス・エージェントを作成、編集、複製、構成、削除することができます。 複数のボイス・エージェントを作成することも可能ですが、各ボイス・エージェントには固有の名前と電話番号が必要です。
{: shortdesc}

<!-- Title should be task oriented and descriptive-->

## ボイス・エージェントの作成
{: #config_instance}

ボイス・エージェントの作成時に、{{site.data.keyword.iva_short}} は使用可能な Watson サービス・インスタンスを自動的に検索します。 サービスを使用できない場合は、ボイス・エージェントと一緒に作成するか、別の {{site.data.keyword.Bluemix_short}} アカウント・スペースのサービスに接続することができます。

1. **「ボイス・エージェントの作成 (Create a Voice Agent)」**をクリックします。

1. **「名前」**に、ボイス・エージェントの固有の名前を指定します。 例えば、`Customer Support - North America` などと指定します。

1. **「電話番号 (Phone number)」**に、SIP トランクから取得した、国別コードと市外局番を含む番号を追加します。 例えば、米国の着信課金用電話番号 (800 ナンバー)の場合は、`18883334444` と指定します。 電話番号にはスペースや `+ ( ) -` の文字を含めることができます。

1. オプションで、ボイス・エージェントの説明を入力します。

1. 通話中転送を有効にする場合は、**「転送ターゲット (Transfer Target)」**で終了 URI を構成することができます。[通話中転送のセットアップ](call-transfer.html)を参照してください。転送ターゲットに個人の電話番号を使用しないでください。

1. Watson サービス・インスタンスへの接続を構成します。 **「ロケーション 1 (Location 1)」**と**「ロケーション 2 (Location 2)」**の両方に接続を構成して、複数の Watson サービス・インスタンスに接続することができます。複数のサービス・インスタンスに接続できるので、障害発生時には、ボイス・エージェントを別のサービス・インスタンスに切り替えることができます。 [複数の Watson サービス・ロケーションの追加](#add_location)を参照してください。

**重要**: _トライアル_・アカウントと_ライト_・アカウントは、{{site.data.keyword.iva_short}} サービス・インスタンスが作成されている場所にのみ接続できます。 2 番目の場所は、2 番目のボイス・エージェントではありません。 災害復旧用のバックアップとしてのみ機能します。

1. **{{site.data.keyword.conversationshort}}** の下で、**「ロケーション 1 の有効化 (Enable location 1)」**または**「ロケーション 2 の有効化 (Enable location 2)」**をクリックして、{{site.data.keyword.conversationshort}} サービス・インスタンスへの接続を構成します。自分自身または他の人が所有する {{site.data.keyword.Bluemix_notm}} アカウントの {{site.data.keyword.conversationshort}} インスタンスまたは {{site.data.keyword.virtualagentfull}} インスタンスを使用することができます。 サービス・オーケストレーション・エンジンを使用してこれらのオプションのいずれかに接続することもできます。

    * 米国南部地域でボイス・エージェントを作成する場合、{{site.data.keyword.conversationshort}} サービス・インスタンスがなければ、**「サービス・インスタンス (Service instance)」**メニューから作成できます。
    * あるいは、[**「サービス・タイプ (Service type)」**](#other_service)を変更することによって {{site.data.keyword.conversationshort}} ダイアログの他のソースに接続することもできます。
    * 複数のサービス・ロケーションを構成する場合は、他のロケーション・オプションをクリックし、**「ロケーションの有効化 (Enable location)」**を選択して、他の {{site.data.keyword.conversationshort}} インスタンスへの接続を構成します。 [複数の Watson サービス・ロケーションの追加](#add_location)を参照してください。

1. **{{site.data.keyword.speechtotextshort}}** の下で、**「ロケーション 1 の有効化 (Enable location 1)」**または**「ロケーション 2 の有効化 (Enable location 2)」**をクリックして、{{site.data.keyword.speechtotextshort}} サービス・インスタンスのデフォルト構成を確認します。米国南部地域でボイス・エージェントを作成する場合、{{site.data.keyword.speechtotextshort}} サービス・インスタンスがなければ、**「サービス・インスタンス (Service instance)」**メニューから作成できます。 あるいは、[**「サービス・タイプ (Service type)」**](#other_service)を変更することによって別の {{site.data.keyword.Bluemix_notm}} アカウント・スペースの {{site.data.keyword.speechtotextshort}} インスタンスにボイス・エージェントを接続することもできます。 {{site.data.keyword.iva_short}} では、狭周波数帯域モデルのみがサポートされています。

    複数のサービス・ロケーションを構成する場合は、他のロケーション・オプションをクリックし、**「ロケーションの有効化 (Enable location)」**を選択して、他の {{site.data.keyword.speechtotextshort}} インスタンスへの接続を構成します。 [複数の Watson サービス・ロケーションの追加](#add_location)を参照してください。

1. **{{site.data.keyword.texttospeechshort}}** の下で、**「ロケーション 1 の有効化 (Enable location 1)」**または**「ロケーション 2 の有効化 (Enable location 2)」**をクリックして、{{site.data.keyword.texttospeechshort}} サービス・インスタンスのデフォルト構成を確認します。米国南部地域でボイス・エージェントを作成しようとしており、{{site.data.keyword.texttospeechshort}} サービス・インスタンスがない場合には、**「サービス・インスタンス (Service instance)」**メニューから作成することができます。 あるいは、[**「サービス・タイプ (Service type)」**](#other_service)を変更することによって別の {{site.data.keyword.Bluemix_notm}} アカウント・スペースの {{site.data.keyword.texttospeechshort}} インスタンスにボイス・エージェントを接続することもできます。

    複数のサービス・ロケーションを構成する場合は、他のロケーション・オプションをクリックし、**「ロケーションの有効化 (Enable location)」**を選択して、他の {{site.data.keyword.texttospeechshort}} インスタンスへの接続を構成します。 [複数の Watson サービス・ロケーションの追加](#add_location)を参照してください。

1. イベント転送を有効にして、ボイス・エージェントが処理した通話に関する情報を、{{site.data.keyword.cloudantfull}} で収集することもできます。 [ボイス・エージェントのイベント転送の有効化](event-forwarding.html)を参照してください。 他の構成オプションについては、[ボイス・エージェントの構成](#configure_va)を参照してください。

1. **「ボイス・エージェントの作成 (Create voice agent)」**をクリックして、ボイス・エージェントと新しいサービスを作成します。

ボイス・エージェントを作成した後、その電話番号を呼び出してボイス・エージェントをテストします。 _「使用 (Usage)」_ダッシュボードで電話通話に関する詳細を表示できます。  

## 同時接続最大数の編集
{: #edit_concurrency}

_標準_ プランを使用している場合は、同時接続の最大数をデフォルト設定から変更できます。 どのプランでも、2 つの同時接続を無料で受け取ります。 詳しくは、[価格プラン](https://console.bluemix.net/catalog/services/voice-agent-with-watson)を参照してください。

_「管理」_ ダッシュボードの**「同時接続最大数 (Maximum concurrent connections)」**に、ご利用プランで許可されている同時接続の最大数がリストされます。 また、**「使用された同時接続最大数 (Maximum concurrent connections used)」**には、当月にボイス・エージェントによって使用された同時接続の最大数も表示されます。

プランの同時接続最大数を変更するには、**「編集」**アイコンをクリックします。 _「同時接続最大数の編集 (Edit maximum concurrent connections)」_ ウィンドウで、同時接続の最大数を選択し、**「保存」**をクリックします。 セルフサービスによって設定可能な同時接続数の最小値は 10 で、最大値は 50 です。 ボイス・エージェントで 50 を超える同時接続が必要な場合は、[要補助ネットワーク・セットアップの要求](connect-SIP.html#request-setup)を参照してください。

### 同時接続の価格設定情報
{: #concurrent-charge}

  * _ライト_、_トライアル_、および_標準_ の各プランには、2 つの同時接続が無料で含まれています。
  * _プレミアム_・プランは、インスタンスごとにカスタマイズされています。
  * _標準_ アカウントでは、同時接続容量は最低 10 です。
  * 同時接続の使用は、月単位で日割り計算されます。 2 つを超える同時接続を 1 日で使用すると、1 日分の料金が請求されます。
  * _標準_ プランまたは_プレミアム_・プランでは、より多くの同時接続容量を購入できます。
  * 1 日の料金は、1 日に使用した最大同時接続容量について請求されます。 例えば、プランで 2 つの無料同時接続がサポートされていて、接続の上限を 12 に設定したとします。 1 日に 5 つのみを使用した場合は、3 つ分が請求されます。

プラン、料金、および機能について詳しくは、[価格プラン](https://console.bluemix.net/catalog/services/voice-agent-with-watson)を参照してください。

## ボイス・エージェントの編集
{: #edit_va}

既存のボイス・エージェントを編集して変更することができます。 ボイス・エージェントを編集するには、ボイス・エージェントのオプションのリストから**「エージェントの編集 (Edit Agent)」**をクリックします。 構成を変更し、変更内容を保存します。

## ボイス・エージェントの複製
{: #clone_va}

ボイス・エージェントを複製するときは、Watson サービスのすべての構成が新規エージェントにコピーされます。 ボイス・エージェントを複製するには、ボイス・エージェントのオプションのリストから**「エージェントの複製 (Clone Agent)」**をクリックします。 ボイス・エージェントに固有の名前と電話番号を指定して、必要に応じて構成オプションを変更し、変更内容を保存します。

## ボイス・エージェントの削除
{: #delete_va}

ボイス・エージェントを削除して電話番号を解放できます。 1 つの電話番号を複数のボイス・エージェントに指定することはできません。 ある電話番号を別のボイス・エージェントで使用するには、まずその電話番号を使用しているボイス・エージェントを削除する必要があります。

ボイス・エージェントを削除するには、ボイス・エージェントのオプションのリストから**「エージェントの削除 (Delete Agent)」**をクリックし、変更内容を保存します。 ボイス・エージェントがボイス・エージェントのリストから削除されます。

## ボイス・エージェントの構成
{: #configure_va}

### 拡張オプションの構成
{: #config-advanced}

ボイス・エージェントを作成または複製するときに、**「詳細の表示 (Show advanced)」**をクリックすると、以下の拡張構成オプションを表示できます。

* **{{site.data.keyword.conversationshort}} 失敗応答メッセージ (オプション) ({{site.data.keyword.conversationshort}} failure reply message (optional))**: 通話が {{site.data.keyword.conversationshort}} に接続できない場合にメッセージ受信者に送信されるデフォルトの応答メッセージ。
* **転送失敗応答メッセージ (オプション)(Transfer failure reply message (optional))**: 通話中転送が失敗した場合に発信者に対して流されるデフォルトの応答メッセージ。
* **{{site.data.keyword.iva_short}} から仮のリンギング応答を送信する (Send provisional ringing response from {{site.data.keyword.iva_short}})**: {{site.data.keyword.iva_short}} が着信を処理する間に `180 リンギング`応答を送信します。 デフォルトでは有効です。
* **転送時に発信者を保留にする (Put caller on hold on transfer)**: 転送時に発信者を保留にします。 デフォルトでは有効です。
* **転送が失敗したときに通話を切断する (Disconnect call on transfer failure)**: 通話中転送が失敗した場合に通話を切断するかどうかを指定します。  デフォルトでは有効です。 この設定を無効にした場合に通話中転送が失敗すると、{{site.data.keyword.iva_short}} が会話のターンを開始します。 その後、ダイアログでの構成に応じて、{{site.data.keyword.conversationshort}} は通話を切断することも、別の宛先に転送することもできます。
* **ネットワーク・イベント時に {{site.data.keyword.conversationshort}} に通知する (Notify {{site.data.keyword.conversationshort}} on network events)**: このオプションを有効にした場合、ネットワーク・エラーが検出されると、{{site.data.keyword.iva_short}} は "vgwNetworkWarningMessage" というテキストで {{site.data.keyword.conversationshort}} へのターンを開始します。 `vgwNetworkWarnings` 状態変数には、現在のターンで発生したネットワーク・イベントのリストが入ります。 このオプションを無効にした場合、現在のターンで発生したネットワーク・イベントのリストは、次のターン・イベントで `vgwNetworkWarnings` 状態変数に入れて送信されます。 デフォルトでは有効です。

### 複数の Watson サービス・ロケーションの追加
{: #add_location}

_標準_ アカウントまたは_プレミアム_・アカウントをお持ちの場合は、異なるロケーションの複数の Watson サービスにボイス・エージェントを接続して、サービスを冗長化することができます。 _トライアル_・アカウントと_ライト_・アカウントは、{{site.data.keyword.iva_short}} サービス・インスタンスが作成されている場所にのみ接続できます。 2 番目の場所は、2 番目のボイス・エージェントではありません。 災害復旧用のバックアップとしてのみ機能します。

ボイス・エージェントは、Watson サービス・インスタンスを地理的な距離の順序で使用します。 例えば、ボイス・エージェントを米国東部地域で作成し、{{site.data.keyword.conversationshort}} サービスは米国南部とオーストラリアのシドニーにあるとします。 この場合、ボイス・エージェントは、{{site.data.keyword.conversationshort}} 米国南部地域を使用します。米国南部の方がシドニーより地理的に米国東部に近いからです。 複数の地域の Watson サービスに接続しているなら、あるロケーションで Watson サービスがオフラインになっても、ボイス・エージェントは予備のサービスを使用できます。

ボイス・エージェント構成に Watson サービス・ロケーションをいつでも追加できます。 ボイス・エージェントの作成時に複数のサービス・ロケーション・インスタンスを接続する方法については、[ボイス・エージェントの作成](#creating)を参照してください。

既存のボイス・エージェントに Watson サービス・ロケーションを追加するには、構成するボイス・エージェントの**「エージェントの編集 (Edit agent)」**をクリックします。 接続する {{site.data.keyword.conversationshort}}、{{site.data.keyword.texttospeechshort}}、または {{site.data.keyword.speechtotextshort}} インスタンスにおいて**「ロケーション 1 (Location 1)」**または**「ロケーション 2 (Location 2)」**を選択し、構成情報を追加します。 自分のワークスペースまたは他のワークスペースの Watson サービス・インスタンスを使用できます。 [他の {{site.data.keyword.Bluemix_notm}} ワークスペースのサービス・インスタンスの使用](#other_services)を参照してください。

**注**: サービスを冗長化するには、異なるロケーションごとに異なるサービス地域で Watson サービス・インスタンスを使用する必要があります。

**「ロケーションの有効化 (Enable location)」**ボックスを使用して、ロケーションを有効または無効にすることができます。 **「ロケーション 1 (Location 1)」**はデフォルトで有効になっており、**「ロケーション 2 (Location 2)」**はデフォルトで無効になっています。 Watson サービスごとに、少なくとも 1 つのロケーションが有効でなければなりません。

### 他の {{site.data.keyword.Bluemix_notm}} ワークスペースのサービス・インスタンスの使用
{: #other_service}

他の {{site.data.keyword.Bluemix_short}} アカウントのワークスペースに属する {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、または {{site.data.keyword.speechtotextshort}} のサービス・インスタンスを使用するようボイス・エージェントを構成することができます。 ボイス・エージェントを他のサービス・インスタンスに接続するには、サービス・インスタンスのユーザー名とパスワードの資格情報か、API キーを使用します。

1. **「サービス・タイプ (Service type)」**と**「地域 (Region)」**を選択します。

1. **「ユーザー名とパスワード (User name and password)」**または**「API キー (API key)」**を選択し、サービス資格情報を入力します。
  これらの値を見つけるには、構成するサービス・インスタンスに移動し、**「サービスの選択」**、**「資格情報の表示」**の順に選択します。

  * **ユーザー名とパスワード (User name and password)**: **「URL」**、**「ユーザー名 (User name)」**、および**「パスワード (Password)」**の各フィールドで、{{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、または {{site.data.keyword.texttospeechshort}} のサービス・インスタンスの資格情報を構成します。
  * **API キー (API key)**: **「URL」**および**「API キー (API key)」**の各フィールドで、{{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、または {{site.data.keyword.texttospeechshort}} のサービス・インスタンスの資格情報を構成します。

  資格情報は {{site.data.keyword.Bluemix_notm}} のユーザー名とパスワードではなく、特定のサービス・インスタンスの暗号化された資格情報です。
  {:tip}

1. サービス・インスタンス情報を入力します。

  * **{{site.data.keyword.conversationshort}}:****「ワークスペース ID (Workspace ID)」**フィールドに、ボイス・エージェントで使用するワークスペースの ID を入力します。 ワークスペース ID を見つけるには、ツールを起動し、統合するワークスペースで「アクション」アイコン (**&vellip;**) をクリックし、**「詳細を表示」**をクリックします。

  * **{{site.data.keyword.speechtotextshort}}:****「モデル」**フィールドで、サービスの音声の言語と形式を選択します。 {{site.data.keyword.iva_short}} では、狭周波数帯域モデルのみがサポートされています。

  * **{{site.data.keyword.texttospeechshort}}:****「音声」**フィールドで、サービスが使用する言語と音声を選択します。 サービスの音声を指定する必要があります。

**注:** ボイス・エージェントが機能するためには、{{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、および {{site.data.keyword.texttospeechshort}} で同じ言語を構成する必要があります。 [サポートされている言語](about.html#supported-languages)を参照してください。

### ボイス・エージェントの {{site.data.keyword.conversationshort}} の構成
{: #conversation_va}

{{site.data.keyword.conversationshort}} サービス・インスタンスを構成する代わりに、サービス・オーケストレーション・エンジン (SOE) または Watson {{site.data.keyword.virtualagentshort}} に接続することができます。

* **サービス・オーケストレーション・エンジン**: {{site.data.keyword.conversationshort}} ワークスペースまたは {{site.data.keyword.virtualagentshort}} に [サービス・オーケストレーション・エンジン (SOE)](about.html#arch-soe) を使用して接続します。 SOE はサービスとの間で送受信されるメッセージを代行受信し、サード・パーティー API を使用して変更できるようにします。

  **「URL」**フィールドに、SOE ワークスペースへの完全な URL を入力します (`https://iva-soesample.myorg.net/SOE/myWorkspace` など)。 SOE が認証を要求する場合 (推奨)、ユーザー名とパスワードをそれぞれのフィールドに入力します。

* **Watson {{site.data.keyword.virtualagentshort}}**: {{site.data.keyword.conversationshort}} ワークスペースではなく {{site.data.keyword.virtualagentshort}} チャットボットに接続します。 [{{site.data.keyword.virtualagentshort}}](../virtual-agent/getting-started.html#getting-started) は {{site.data.keyword.conversationshort}} サービス上にビルドされますが、事前にトレーニングされた機能を提供するので、機械学習の経験がゼロでも始められます。

  **「URL」**フィールドに、{{site.data.keyword.virtualagentshort}} の URL 資格情報を入力します (`https://api.ibm.com/virtualagent/run/api` など)。 **「クライアント ID」**フィールドと**「クライアント秘密鍵」**フィールドに認証鍵を入力します。これらは API 呼び出しの `X-IBM-Client-Id` ヘッダー・フィールドと `X-IBM-Client-Secret` ヘッダー・フィールドにマップされます。 **「ボット ID (Bot ID)」**フィールドに、このボイス・エージェントで使用するボットの ID を入力します。 これらの値を見つける方法について詳しくは、{{site.data.keyword.virtualagentshort}} 資料の[エージェントの公開](../virtual-agent/publish.html)を参照してください。
