---

copyright:
  years: 2018
lastupdated: "2018-11-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 機密保護とデータ・プライバシー
{: #infosec}

IBM は、お客様とパートナーへの革新的なデータ・プライバシー、セキュリティー、ガバナンスのソリューションの提供にコミットしています。
{: shortdesc}

## 情報処理と構成オプション
{: #configure_infosec}

{{site.data.keyword.iva_short}} は、顧客から受け取るデータの保管、収集、処理を行いません。 代わりに、データは別のサービスにルーティングされて処理されます。 ユーザーは会話中に、保護医療情報 (PHI)、個人情報 (PII)、または PCI データ・セキュリティー基準 (PCI DSS) のデータが含まれている情報を共有することもあります。 {{site.data.keyword.iva_short}} の会話フローとアーキテクチャーの詳細は、[アーキテクチャー](about.html#architecture){: new_window}を参照してください。

データ・プライバシーと保護の処理をサポートするようにボイス・エージェント・インスタンスを構成する際には、以下の機能を考慮してください。

### 通話中転送
{:  #calltransfer_infosec}

通話中転送機能をボイス・エージェントに追加する際には、転送ターゲット SIP URI の構成時に電話番号を指定します。 ユーザーは、この転送ターゲットに個人の電話番号を指定しないでください。

通話中転送用に SIP トランクと SIP URI を構成することについては、[通話中転送のセットアップ](call-transfer.html)を参照してください。

### イベント転送
{: #event_forwarding}

{{site.data.keyword.cloudantfull}} データベース・インスタンスにレポート作成イベントを転送するように、ボイス・エージェントを構成できます。 これらのレポート作成イベントには、発信者に関する PII、PHI、PCI DSS データを、転写、会話のターン・イベント、発着信詳細記録 (CDR) イベントの形式で組み込むことができます。 発信データやレポート作成イベントは {{site.data.keyword.iva_short}} 内で保管されたり、処理されたり、収集されたりしないので、ユーザーは外部 {{site.data.keyword.cloudant_short_notm}} サービスを適切に構成する必要があります。 **デフォルトでは、イベント転送は無効になっています。**

レポート作成イベントを転送するようにボイス・エージェントを構成するには、[イベント転送の有効化](event-forwarding.html)を参照してください。

{{site.data.keyword.cloudant_short_notm}} に関するデータ・プライバシーと機密保護の詳細については、[**{{site.data.keyword.cloudant_short_notm}}: セキュリティー**](../Cloudant/offerings/security.html#security){: new_window}を参照してください。

### Text to Speech キャッシング
{: #tts_caching}

{{site.data.keyword.conversationshort}} は、顧客と対話するために、応答をテキストとして作成します。このテキストは {{site.data.keyword.texttospeechshort}} サービスに渡され、{{site.data.keyword.iva_short}} で発話されます。 {{site.data.keyword.conversationshort}} が作成する応答には、機密情報が含まれている場合があります。 {{site.data.keyword.iva_short}} が、個人データが含まれる応答を {{site.data.keyword.texttospeechshort}} サービスから受け取った場合にキャッシュに入れないようにするには、`vgwActExcludeFromTTSCache` アクション・コマンドを有効にして、特定のタイプの情報が含まれる発話をキャッシュに入れることから除外できます。 [API を使用したボイス・エージェントのプログラミング](api.html#action-sequences)を参照してください。

### セキュア接続
{: #secure_trunking}

{{site.data.keyword.iva_short}} は、{{site.data.keyword.Bluemix_notm}} に基づいており、ユーザーが構成する SIP トランクと統合します。 SIP トランクは外付けで、{{site.data.keyword.iva_short}} に接続するので、Secure Real Time Transport Protocol (SRTP) を使用して SIP トランクと {{site.data.keyword.iva_short}} の間のセキュア接続を有効にしたり、Transport Layer Security (TLS) に依存する Secure SIP (SIPS) を使用して暗号化を有効にしたりできます。 [接続の保護](secure-trunking.html)を参照してください。

### サービス・オーケストレーション・エンジン (SOE) の構成
{: #SOE_config}

サービス・オーケストレーション・エンジン (SOE) を使用して、{{site.data.keyword.iva_short}} と {{site.data.keyword.conversationshort}} の間で渡される情報を処理し、発信者との会話をカスタマイズできます。 セキュア接続を保守するには、セキュア URL の `https` とユーザー認証を使用して SOE を構成していることを確認してください。

[ボイス・エージェントの {{site.data.keyword.conversationshort}} の構成](managing_SOE.html#conversation_va)と、[サービス・オーケストレーション・エンジンを使用するアーキテクチャー](about.html#arch-soe)を参照してください。

## {{site.data.keyword.iva_short}} に関連したサービス
{: #related_services}

{{site.data.keyword.iva_short}} は様々な {{site.data.keyword.Bluemix_notm}} サービスを編成して、エンド・ユーザーとクラウド・ベースのコグニティブ・サービスとの間の通信を調整します。 {{site.data.keyword.iva_short}} 自体は、エンド・ユーザーの権限に違反するような方法でデータの保管、収集、処理を行いません。 しかし、関連したサービスの構成方法によっては、
これらの統合されたサービスが、ユーザーが会話中に共有する保護医療情報 (PHI)、個人情報 (PII)、または PCI データ・セキュリティー基準 (PCI DSS) のデータを収集することもできます。 {{site.data.keyword.iva_short}} のアーキテクチャーと会話フローの詳細については、[アーキテクチャー](about.html#architecture){: new_window}を参照してください。

各サービスと {{site.data.keyword.Bluemix_notm}} に関する考慮事項については、以下のリソースを参照してください。

  * [**{{site.data.keyword.Bluemix_short}}: セキュリティー・コンプライアンス**](../security/compliance.html)
  * [**{{site.data.keyword.conversationfull}}: Information security**](../conversation/information-security.html){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}: Information security**](../text-to-speech/information-security.html){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}: Information security**](../speech-to-text/information-security.html){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: セキュリティー**](../Cloudant/offerings/security.html#security){: new_window}
