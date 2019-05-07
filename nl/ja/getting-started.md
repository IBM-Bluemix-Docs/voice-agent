---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

keywords: voice agent, creating a SIP trunk, creating and connecting your voice agent,

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 入門チュートリアル
{: #getting-started}
{{site.data.keyword.iva_full}} は、編成された Watson サービスを Session Initiation Protocol (SIP) を使用して電話ネットワークと統合するのに役立ちます。 このチュートリアルでは、コグニティブ・ボイス・エージェントをセットアップして、任意の電話から通話できるようにする方法について説明します。
{: shortdesc}

この [{{site.data.keyword.iva_full_notm}} チュートリアル ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/) で、ボイス・エージェントを初めて作成する方法のデモをご覧ください。
{: tip}

支援が必要な場合、Slack で [IBM Cloud テクノロジー ![外部リンクのアイコン](../../icons/launch-glyph.svg "外部リンクのアイコン")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) チーム内の `#ibmvoicegateway` チャネルの下を確認してください
{: tip}

## 始めに
{: #prereqs}

[{{site.data.keyword.Bluemix_short}}](https://cloud.ibm.com/) で、新しいアカウントを作成するか、既存のアカウントにログインします。

## ステップ 1: {{site.data.keyword.Bluemix_notm}} での {{site.data.keyword.iva_short}} サービス・インスタンスの作成
{: #step1}

[{{site.data.keyword.iva_short}}カタログ・ページ](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)で、サービス情報を確認して、**「作成」**をクリックします。

サービスを作成した後、_「開始 (Getting started)」_ダッシュボードに示されているボイス・エージェント・エンドポイントをメモします。 SIP トランクを構成するために、このエンドポイントの SIP URI が必要になります。

## ステップ 2: 発信を {{site.data.keyword.iva_short}} に転送するための SIP トランクの作成
{: #step2}

1. 以下に示すサポート対象のいずれかのプロバイダーから、SIP トランクを作成します。 そして、電話番号を SIP トランクに関連付けます。

  * [NetFoundry](/docs/services/voice-agent?topic=voice-agent-connect#NetFoundry-setup)
  * [Twilio](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup)
  * [AT&T やその他の SIP トランキング・プロバイダー](/docs/services/voice-agent?topic=voice-agent-connect#att-other)
  * [{{site.data.keyword.iva_short}} とのピアリング](/docs/services/voice-agent?topic=voice-agent-connect#peering)

## ステップ 3: ボイス・エージェントの作成と接続
{: #step3}

1. {{site.data.keyword.iva_short}} ダッシュボードの_「管理」_ダッシュボードに移動して、**「Create a Voice Agent (ボイス・エージェントの作成)」**をクリックします。

2. ボイス・エージェントの基本設定を入力します。
  * **名前:** ボイス・エージェントの固有の名前。例: `お客様サポート`
  * **電話番号:** SIP トランクに関連付けた (国別コードと市外局番を含む) 完全な電話番号。 例えば、米国の 800 ナンバーの場合は、電話番号を 18883334444 と指定します。 電話番号にはスペースや + ( ) - の文字を含めることができます。
  * **説明:** 用途の説明 (任意)
  * **デフォルトの転送ターゲット:** 呼び出しを転送できるオプションの終端 URI。

3. ボイス・エージェント用に {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、および {{site.data.keyword.texttospeechshort}} のサービス・インスタンスを作成します。 次のいずれかの方法で、ボイス・エージェントを作成することができます。
  * **「Create a voice agent (ボイス・エージェントの作成)」**をクリックして、1 つのステップですべてのサービスとボイス・エージェントをデフォルト構成で作成します。
  * または、各サービス名をクリックしてサービスを自分で作成します。 その後 {{site.data.keyword.iva_short}} に戻り、ボイス・エージェントを別途作成します。

   {{site.data.keyword.conversationshort}} サービス・インスタンスを手動で作成した場合は、ダイアログを追加して、ボイス・エージェントをテストできるようにしてください。  迅速に開始するには、GitHub の [サンプル会話 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) を複製し、スキルとしてその[サンプルをインポート](/docs/conversation?topic=services/conversation-configuring-a-watson-assistant-workspace#creating-workspaces)します。

   1. GitHub のサンプル会話のページで、`1` 行目をクリックし、**「... > Copy line (行のコピー)」**を選択します。 コピーしたテキストをファイルに貼り付け、それを `voice-gateway-conversation-en.json` などの JSON ファイルとして保存します。
   2. {{site.data.keyword.conversationshort}} ツールを起動します。 _「Skills」_ページで、![ワークスペースのインポート](../conversation/images/workspace_import.png) アイコンをクリックして JSON ファイルをインポートします。

  または、[独自のダイアログを作成](/docs/services/assistant?topic=assistant-getting-started#getting-started-build-dialog)して、実稼働環境をシミュレートすることもできます。 この場合、作成するダイアログには、少なくとも `conversation_start` 条件を含むノードと、デフォルト応答を含むノードが含まれている必要があります。


## 次のステップ
{: #next-steps}

ボイス・エージェントに関連付けられた電話番号を呼び出して、ボイス・エージェントをテストします。 応答が聞こえたなら、ボイス・エージェントはアクティブです。

応答が聞こえない場合は、_「Usage (使用)」_ダッシュボードで通話ログとボイス・エージェントの使用を調査することができます。 [使用状況と通話ログの表示](/docs/services/voice-agent?topic=voice-agent-logging)を参照してください。

_「Manage (管理)」_ダッシュボードから、ボイス・エージェントの設定を編集したり、ボイス・エージェントを作成または削除したり、複数の Watson サービス・ロケーションをボイス・エージェントに追加したりすることができます。 詳しくは、[ボイス・エージェントの管理](/docs/services/voice-agent?topic=voice-agent-managing)を参照してください。

さらに、Twilio アカウントからの SIP 接続の保護など、詳細設定を構成することもできます。 [接続の保護](/docs/services/voice-agent?topic=voice-agent-securing)を参照してください。
