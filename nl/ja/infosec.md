---

copyright:
  years: 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"

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

サービスを運用してユーザー・エクスペリエンスを最適化する目的で、{{site.data.keyword.iva_short}} は最小限の個人情報 (PI) を収集して保管し、[データ処理補足契約書 (DPA)](https://www.ibm.com/support/customer/csol/terms/){: new_window} および [DPA 別表](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=00C4CE004FA711E7AA10752A2F494A7C){: new_window}に従ってそれを取り扱います。{{site.data.keyword.iva_short}} は、音声や SMS の会話に含まれるデータを保管、収集、処理することはありません。代わりに、データは別のサービスにルーティングされて処理されます。 ユーザーは会話中に、保護医療情報 (PHI)、個人情報 (PII)、または PCI データ・セキュリティー基準 (PCI DSS) のデータが含まれている情報を共有することもあります。 {{site.data.keyword.iva_short}} の会話フローとアーキテクチャーの詳細は、[アーキテクチャー](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}を参照してください。

データ・プライバシーと保護の処理をサポートするようにボイス・エージェント・インスタンスを構成する際には、以下の機能を考慮してください。

### 通話中転送
{:  #calltransfer_infosec}

通話中転送機能をボイス・エージェントに追加する際には、転送ターゲット SIP URI の構成時に電話番号を指定します。 ユーザーは、この転送ターゲットに個人の電話番号を指定しないでください。

通話中転送用に SIP トランクと SIP URI を構成することについては、[通話中転送のセットアップ](/docs/services/voice-agent?topic=voice-agent-call-transfer)を参照してください。

### イベント転送
{: #infosec_event_forwarding}

{{site.data.keyword.cloudantfull}} データベース・インスタンスにレポート作成イベントを転送するように、ボイス・エージェントを構成できます。 これらのレポート作成イベントには、発信者に関する PII、PHI、PCI DSS データを、転写、会話のターン・イベント、発着信詳細記録 (CDR) イベントの形式で組み込むことができます。 通話データ、SMS データ、レポート作成イベントは {{site.data.keyword.iva_short}} 内で保管されたり、処理されたり、収集されたりしないので、ユーザーは外部 {{site.data.keyword.cloudant_short_notm}} サービスを適切に構成する必要があります。**デフォルトでは、イベント転送は無効になっています。**

レポート作成イベントを転送するようにボイス・エージェントを構成するには、[イベント転送の有効化](/docs/services/voice-agent?topic=voice-agent-event_forwarding)を参照してください。

{{site.data.keyword.cloudant_short_notm}} に関するデータ・プライバシーと機密保護の詳細については、[**{{site.data.keyword.cloudant_short_notm}}: セキュリティー**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}を参照してください。

### Text to Speech キャッシング
{: #tts_caching}

{{site.data.keyword.conversationshort}} は、顧客と対話するために、応答をテキストとして作成します。このテキストは {{site.data.keyword.texttospeechshort}} サービスに渡され、{{site.data.keyword.iva_short}} で発話されます。 {{site.data.keyword.conversationshort}} が作成する応答には、機密情報が含まれている場合があります。 {{site.data.keyword.iva_short}} が、個人データが含まれる応答を {{site.data.keyword.texttospeechshort}} サービスから受け取った場合にキャッシュに入れないようにするには、`vgwActExcludeFromTTSCache` アクション・コマンドを有効にして、特定のタイプの情報が含まれる発話をキャッシュに入れることから除外できます。 [API を使用したボイス・エージェントのプログラミング](/docs/services/voice-agent?topic=voice-agent-api#action-sequences)を参照してください。

Voice Agent インスタンスが削除されると、TTS キャッシュが 24 時間で消去されます。これを `TTS キャッシュ・タイムアウト値`といいます。

### セキュア接続
{: #secure_trunking}

{{site.data.keyword.iva_short}} は、{{site.data.keyword.Bluemix_notm}} に基づいており、ユーザーが構成する SIP トランクと統合します。 SIP トランクは外付けで、{{site.data.keyword.iva_short}} に接続するので、Secure Real Time Transport Protocol (SRTP) を使用して SIP トランクと {{site.data.keyword.iva_short}} の間のセキュア接続を有効にしたり、Transport Layer Security (TLS) に依存する Secure SIP (SIPS) を使用して暗号化を有効にしたりできます。 [接続の保護](/docs/services/voice-agent?topic=voice-agent-securing)を参照してください。

デフォルトで、SMS データは TLS で暗号化されます。詳細については、[Voice Gateway: データ処理](https://www.ibm.com/support/knowledgecenter/en/SS4U29/gdpr_considerations.html#GDPR_dataProcessing){: new_window}を参照してください。

### サービス・オーケストレーション・エンジン (SOE) の構成
{: #SOE_config}

サービス・オーケストレーション・エンジン (SOE) を使用して、{{site.data.keyword.iva_short}} と {{site.data.keyword.conversationshort}} の間で渡される情報を処理し、発信者との会話をカスタマイズできます。 セキュア接続を保守するには、セキュア URL の `https` とユーザー認証を使用して SOE を構成していることを確認してください。

[ボイス・エージェントの {{site.data.keyword.conversationshort}} の構成](/docs/services/voice-agent?topic=voice-agent-conversation_va#conversation_va)と、[サービス・オーケストレーション・エンジンを使用するアーキテクチャー](/docs/services/voice-agent?topic=voice-agent-about#arch-soe)を参照してください。

## SMS/MMS サポート
{: #SMS_MMS}

### データの取り扱い
{: #data_handling}

{{site.data.keyword.iva_short}} が SMS データを保管、収集、処理することはありません。MMS イメージは本サービスの外部で保管され、サービス・プロバイダーによって取り扱われます。お客様ご自身で SMS プロバイダーのセキュリティー/プライバシー合意事項を確認していただく必要があります。{{site.data.keyword.iva_short}} は、SMS メッセージに組み込まれるテキスト形式のイメージ・リンクだけを取り扱います。

サービス・オーケストレーション・エンジンまたは {{site.data.keyword.conversationshort}} が MMS メッセージをユーザー (SMS テキスト・メッセージの有無はかかわらない) に送信すると、1 つ以上の公的にアクセス可能なメディア URL が Twilio に送信されます。Twilio は、非パブリック URL をサポートしません。ユーザーは MMS を通して機密情報や個人情報を送らないよう注意する必要があります。

{{site.data.keyword.iva_short}} はメッセージ・ログで発信者 ID をマスクすることにより、このような個人を識別できる情報の収集を防止します。

### 認証
{: #authentication}

インバウンド SMS メッセージは、[IAM 認証](/docs/services/voice-agent?topic=voice-agent-iam#sms_access){: new_window}を使用してサービス・プロバイダーで機密保護されます。

## {{site.data.keyword.iva_short}} に関連したサービス
{: #related_services}

{{site.data.keyword.iva_short}} は様々な {{site.data.keyword.Bluemix_notm}} サービスを編成して、エンド・ユーザーとクラウド・ベースのコグニティブ・サービスとの間の通信を調整します。 {{site.data.keyword.iva_short}} 自体は、エンド・ユーザーの権限に違反するような方法でデータの保管、収集、処理を行いません。 しかし、関連したサービスの構成方法によっては、これらの統合されたサービスが、ユーザーが会話中に共有する保護医療情報 (PHI)、個人情報 (PII)、または PCI データ・セキュリティー基準 (PCI DSS) のデータを収集する場合もあります。 {{site.data.keyword.iva_short}} のアーキテクチャーと会話フローの詳細については、[アーキテクチャー](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}を参照してください。

各サービスと {{site.data.keyword.Bluemix_notm}} に関する考慮事項については、以下のリソースを参照してください。

  * [**{{site.data.keyword.Bluemix_short}}: セキュリティー・コンプライアンス**](/docs/overview?topic=overview-security#security)
  * [**{{site.data.keyword.conversationfull}}: Information security**](/docs/services/assistant?topic=assistant-information-security#information-security){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}: Information security**](/docs/services/text-to-speech?topic=text-to-speech-information-security){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}: Information security**](/docs/services/speech-to-text?topic=speech-to-text-information-security){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: セキュリティー**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}
