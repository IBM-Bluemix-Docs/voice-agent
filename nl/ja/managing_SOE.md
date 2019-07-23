---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"
subcollection: "voice-agent"


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

[サービス・オーケストレーション・エンジン (SOE)](/docs/services/voice-agent?topic=voice-agent-about#arch-soe) を経由して {{site.data.keyword.conversationshort}} ワークスペースに接続することができます。 SOE はサービスとの間で送受信されるメッセージを代行受信し、サード・パーティー API を使用して変更できるようにします。

## SOE への接続の構成
{: #how-to-SEO}

1. ボイス・エージェントの_「管理」_ページの_「音声エージェント」_タブの、{{site.data.keyword.conversationshort}} 構成セクションにナビゲートします。

1. **「サービス・タイプ」**として**「サービス・オーケストレーション・エンジン」**を選択します。

1. **「サービス・タイプ」**の**「地域」**を選択します。

1. **「URL」**フィールドに、SOE ワークスペースの完全な URL (`https://iva-soesample.myorg.net/SOE/myWorkspace` など)を入力します。 URL には最大 256 文字まで入力できます。

  **重要**: データ・セキュリティーの場合、`http:` ではなく `https:` を使用して、SOE ワークスペースにセキュア URL を使用していることを確認してください。また、認証が必要です。 セキュリティーに関する考慮事項の詳細については、[機密保護とデータ・プライバシー](/docs/services/voice-agent?topic=voice-agent-infosec)を参照してください。

1. **オプション** SOE が認証を要求する場合 (推奨)、ユーザー名とパスワードをそれぞれのフィールドに入力します。それぞれ、最大 64 文字、256 文字まで入力できます。
