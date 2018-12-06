---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# _「管理」_ダッシュボードからボイス・エージェントを作成する
{: #config_instance}

{{site.data.keyword.iva_full}} サービスを作成したら、_「管理」_ダッシュボードからボイス・エージェントを個々に作成できます。
{: shortdesc}


## ボイス・エージェントの作成
{: #create_instance}

ボイス・エージェントの作成時に、{{site.data.keyword.iva_short}} は使用可能な Watson サービス・インスタンスを自動的に検索します。 使用可能なサービスがない場合は、ボイス・エージェントと同時に作成するか、別の {{site.data.keyword.Bluemix_short}} アカウント・スペースのサービスに接続するかを選択できます。サービス・オーケストレーション・エンジン、Google Speech to Text、または Google Text to Speech インスタンスにボイス・エージェントを接続することもできます。

1. _「管理」_ダッシュボードの_「音声エージェント」_タブに移動して、**「音声エージェントの作成」**をクリックします。

1. **「名前」**に、ボイス・エージェントの固有の名前を指定します。 例えば、`Customer Support - North America` などと指定します。

1. **「電話番号 (Phone number)」**に、SIP トランクから取得した、国別コードと市外局番を含む番号を追加します。 例えば、米国の着信課金用電話番号 (800 ナンバー)の場合は、`18883334444` と指定します。 電話番号にはスペースや `+ ( ) -` の文字を含めることができます。

1. オプションで、ボイス・エージェントの説明を入力します。

1. 通話中転送を有効にする場合は、**「転送する場合のデフォルトの宛先」**に終端 URI を入力します。終端 URI のセットアップ方法については、[通話中転送のセットアップ](call-transfer.html)を参照してください。転送ターゲットに個人の電話番号を使用しないでください。

1. Watson サービス・インスタンスへの接続を構成します。 **「ロケーション 1 (Location 1)」**と**「ロケーション 2 (Location 2)」**の両方に接続を構成して、複数の Watson サービス・インスタンスに接続することができます。複数のサービス・インスタンスに接続できるので、障害発生時には、ボイス・エージェントを別のサービス・インスタンスに切り替えることができます。 [複数の Watson サービス・ロケーションの追加](managing_disaster_recovery.html#add_location)を参照してください。

1. **{{site.data.keyword.conversationshort}}** の下で、**「場所 1」**または**「場所 2」**をクリックし、選択したロケーションを有効にして、{{site.data.keyword.conversationshort}} サービス・インスタンスへの接続を構成します。自分または他の人が所有する {{site.data.keyword.Bluemix_notm}} アカウントの {{site.data.keyword.conversationshort}} インスタンスを使用できます。サービス・オーケストレーション・エンジンを使用してこれらのオプションのいずれかに接続することもできます。

   * ダラスまたはワシントン DC の地域にボイス・エージェントを作成する場合は、{{site.data.keyword.conversationshort}} サービス・インスタンスがなければ、**「サービス・インスタンス」**メニューから作成できます。
   * また、[**「サービス・タイプ」**](managing_other.html#other_service)を変更して {{site.data.keyword.conversationshort}} ダイアログの他のソースに接続したり SOE を使用して接続したりすることもできます。
   * 複数のサービス・ロケーションを構成する場合は、他のロケーション・オプションをクリックし、**「ロケーションの有効化 (Enable location)」**を選択して、他の {{site.data.keyword.conversationshort}} インスタンスへの接続を構成します。 [複数の Watson サービス・ロケーションの追加](managing_disaster_recovery.html#add_location)を参照してください。

1. **{{site.data.keyword.speechtotextshort}}** の下で、**「場所 1」**または**「場所 2」**を選択し、そのロケーションを有効にして、{{site.data.keyword.speechtotextshort}} サービス・インスタンスのデフォルト構成を確認します。以下のオプションを使用して、構成をカスタマイズできます。
   * **「サービス・タイプ」**として既存のインスタンスにボイス・エージェントを接続するには、**「自分の Speech to Text インスタンス」**を選択します。次に、**「モデル・タイプの選択 (Select model type)」**で**「狭帯域 (Narrowband)」**、**「ブロードバンド (Broadband)」**、または**「狭帯域とブロードバンドの両方 (Both narrowband and broadband)」**を選択してから、言語の**「モデル」**を選択します。
   * ダラスまたはワシントン DC の地域にボイス・エージェントを作成する場合は、{{site.data.keyword.speechtotextshort}} サービス・インスタンスがなければ、**「サービス・インスタンス」**メニューから作成できます。
   * **「サービス・タイプ」**では、[他の {{site.data.keyword.Bluemix_notm}} ワークスペースの {{site.data.keyword.speechtotextshort}} インスタンス](managing_other.html)を選択することも、Google Cloud Speech-to-Text などの[サード・パーティーの音声認識サービス](managing_third_party.html)を選択することもできます。
   * 複数のサービス・ロケーションを構成する場合は、他のロケーション・オプションをクリックし、**「ロケーションの有効化 (Enable location)」**を選択して、他の {{site.data.keyword.speechtotextshort}} インスタンスへの接続を構成します。 [複数の Watson サービス・ロケーションの追加](managing_disaster_recovery.html)を参照してください。

1. **{{site.data.keyword.texttospeechshort}}** の下で、**「場所 1」**または**「場所 2」**をクリックし、そのロケーションを有効にして、{{site.data.keyword.texttospeechshort}} サービス・インスタンスのデフォルト構成を確認します。以下のオプションを使用して、構成をカスタマイズできます。
   * ダラスまたはワシントン DC の地域にボイス・エージェントを作成する場合は、{{site.data.keyword.texttospeechshort}} サービス・インスタンスがなければ、**「サービス・インスタンス」**メニューから作成できます。
   * **「サービス・タイプ」**では、[他の {{site.data.keyword.Bluemix_notm}} ワークスペースの {{site.data.keyword.texttospeechshort}} インスタンス](managing_other.html)を選択することも、Google Cloud Text-to-Speech などの[サード・パーティーの音声合成サービス](managing_third_party.html)を選択することもできます。
   * 複数のサービス・ロケーションを構成する場合は、他のロケーション・オプションをクリックし、**「ロケーションの有効化 (Enable location)」**を選択して、他の {{site.data.keyword.texttospeechshort}} インスタンスへの接続を構成します。 [複数の Watson サービス・ロケーションの追加](managing_disaster_recovery.html)を参照してください。

1. イベント転送を有効にして、ボイス・エージェントが処理した通話に関する情報を、{{site.data.keyword.cloudantfull}} で収集することもできます。 [ボイス・エージェントのイベント転送の有効化](event-forwarding.html)を参照してください。 他の構成オプションについては、[ボイス・エージェントの構成](managing.html#configure_va)を参照してください。

1. **「ボイス・エージェントの作成 (Create voice agent)」**をクリックして、ボイス・エージェントと新しいサービスを作成します。

ボイス・エージェントを作成した後、その電話番号を呼び出してボイス・エージェントをテストします。 _「使用 (Usage)」_ダッシュボードで電話通話に関する詳細を表示できます。  
