---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 他の {{site.data.keyword.Bluemix_notm}} ワークスペースのサービス・インスタンスの使用
{: #other_service}

他の {{site.data.keyword.Bluemix_short}} アカウントのワークスペースに属する {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、または {{site.data.keyword.speechtotextshort}} のサービス・インスタンスを使用するようにボイス・エージェントを構成できます。
{: shortdesc}

ボイス・エージェントを他のサービス・インスタンスに接続するには、サービス・インスタンスのユーザー名とパスワードの資格情報か、API キーを使用します。

1. _「管理」_ダッシュボードの_「音声エージェント」_タブで、**「ボイス・エージェントの新規作成 (Create a new voice agent)」**を選択するか、編集するボイス・エージェントを選択します。

1. {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、または {{site.data.keyword.speechtotextshort}} で、**「サービス・タイプ」**に**「その他のサービス・インスタンス (Other service instance)」**を選択してから、**「地域」**を選択します。

1. **「ユーザー名とパスワード (User name and password)」**または**「API キー (API key)」**を選択し、サービス資格情報を入力します。
  これらの値を見つけるには、構成するサービス・インスタンスに移動し、**「サービスの選択」**、**「資格情報の表示」**の順に選択します。

  * **ユーザー名とパスワード (User name and password)**: **「URL」**、**「ユーザー名 (User name)」**、および**「パスワード (Password)」**の各フィールドで、{{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、または {{site.data.keyword.texttospeechshort}} のサービス・インスタンスの資格情報を構成します。
  * **API キー (API key)**: **「URL」**および**「API キー (API key)」**の各フィールドで、{{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、または {{site.data.keyword.texttospeechshort}} のサービス・インスタンスの資格情報を構成します。

  資格情報は {{site.data.keyword.Bluemix_notm}} のユーザー名とパスワードではなく、特定のサービス・インスタンスの暗号化された資格情報です。
  {:tip}

1. サービス・インスタンス情報を入力します。

  * **{{site.data.keyword.conversationshort}}:****「ワークスペース ID (Workspace ID)」**フィールドに、ボイス・エージェントで使用するワークスペースの ID を入力します。 ワークスペース ID を見つけるには、ツールを起動し、統合するワークスペースで「アクション」アイコン (**&vellip;**) をクリックし、**「詳細を表示」**をクリックします。
  * **{{site.data.keyword.speechtotextshort}}:** **「モデル・タイプの選択 (Select model type)」**では、** 「狭帯域 (Narrowband)」**、**「ブロードバンド (Broadband)」**、または**「狭帯域とブロードバンドの両方 (Both narrowband and broadband)」**を選択してから、言語の**「モデル」**を選択します。
  * **{{site.data.keyword.texttospeechshort}}:****「音声」**フィールドで、サービスが使用する言語と音声を選択します。 サービスの音声を指定する必要があります。

**注:** ボイス・エージェントが機能するためには、{{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}}、および {{site.data.keyword.texttospeechshort}} で同じ言語を構成する必要があります。 [サポートされている言語](about.html#supported-languages)を参照してください。
