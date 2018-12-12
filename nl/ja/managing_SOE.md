---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# {{site.data.keyword.conversationshort}} にサービス・オーケストレーション・エンジンを構成する
{: #conversation_va}

{{site.data.keyword.conversationshort}} サービス・インスタンスを構成する代わりに、サービス・オーケストレーション・エンジン (SOE) に接続することができます。
{: shortdesc}

[サービス・オーケストレーション・エンジン (SOE)](about.html#arch-soe) を経由して {{site.data.keyword.conversationshort}} ワークスペースに接続することができます。SOE はサービスとの間で送受信されるメッセージを代行受信し、サード・パーティー API を使用して変更できるようにします。

## SOE への接続の構成
{: #how-to}

1. ボイス・エージェントの_「管理」_ページの_「音声エージェント」_タブの、{{site.data.keyword.conversationshort}} 構成セクションにナビゲートします。

1. **「サービス・タイプ」**として**「サービス・オーケストレーション・エンジン」**を選択します。

1. **「サービス・タイプ」**の**「地域」**を選択します。

1. **「URL」**フィールドに、SOE ワークスペースの完全な URL を入力します (`https://iva-soesample.myorg.net/SOE/myWorkspace` など)。

  **重要**: データ・セキュリティーの場合、`http:` ではなく `https:` を使用して、SOE ワークスペースにセキュア URL を使用していることを確認してください。また、認証が必要です。 セキュリティーに関する考慮事項の詳細については、[機密保護とデータ・プライバシー](infosec.html)を参照してください。

1. **オプション** SOE が認証を要求する場合 (推奨)、ユーザー名とパスワードをそれぞれのフィールドに入力します。
