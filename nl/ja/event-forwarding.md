---

copyright:
  years: 2018
lastupdated: "2018-08-16"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# ボイス・エージェントのイベント転送の有効化
{: #event_forwarding}

イベント転送を有効化し、{{site.data.keyword.cloudantfull}} データベース・サービスを使用して、{{site.data.keyword.iva_full}} でボイス・エージェントによって処理された通話に関する情報を収集することができます。
{: shortdesc}

発信者に会話がより自然に感じられるようにするために、{{site.data.keyword.iva_short}} から発信データを収集して分析することができます。 作成する各ボイス・エージェントは、管理対象の指定された {{site.data.keyword.cloudant_short_notm}} にイベント・レポートを転送することができます。 レポートされるイベントには、発着信詳細記録 (CDR) イベント、転写イベント、およびターン・イベントのレポートが含まれます。 転送可能なイベントの種類について詳しくは、[イベントのレポート作成](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}を参照してください。

これらのイベントのデータを分析することは、ダイアログの調整、意図の絞り込み、および全体的な発信者体験の改善に役立ちます。

ボイス・エージェントを作成または編集するとき、イベント転送の有効化も選択することができます。 ボイス・エージェントの作成および編集の詳細については、[ボイス・エージェントの管理](managing.html)を参照してください。 イベント転送を有効化するには、{{site.data.keyword.cloudant_short_notm}} アカウント情報 (アカウント名とパスワードを含む) を提供する必要があります。

**重要:** CDR イベント、転写イベント、およびターン・イベントにはユーザーからの情報が取り込まれますが、それには保護医療情報 (PHI)、個人情報 (PII)、または PCI データ・セキュリティー基準 (PCI DSS) のデータが含まれている可能性があります。 個人情報の漏えいを防ぐため、会話内および会話中にユーザーどうしがやりとりする機密情報が {{site.data.keyword.cloudant_short_notm}} インスタンスで適切に保護されるようにする必要があります。


## イベント転送の有効化
{: #enable-event-forwarding}

{{site.data.keyword.Bluemix_short}} の_管理_ダッシュボードでボイス・エージェントを作成または編集するときに、イベント転送を有効化することができます。

1. {{site.data.keyword.texttospeechshort}} の構成セクションの後にある**「Event forwarding (イベント転送)」**セクションで、**「Enable event forwarding (イベント転送を有効化する)」**を選択します。

1. **「マイ {{site.data.keyword.cloudant_short_notm}} サービス・インスタンス」**または**「その他の {{site.data.keyword.cloudant_short_notm}} サービス・インスタンス」**のいずれかを選択します。
  * **「マイ {{site.data.keyword.cloudant_short_notm}} サービス・インスタンス」**を使用する場合は、リストから **{{site.data.keyword.cloudant_short_notm}} アカウント**名とユーザー名を選択します。
  * **「その他の {{site.data.keyword.cloudant_short_notm}} サービス・インスタンス」**を使用する場合は、アカウントの {{site.data.keyword.cloudant_short_notm}} ユーザー名とパスワード、または API キーを入力します。

1. 転送する各イベント・タイプについて**「Enable (有効化)」**を選択してから、イベントを転送する宛先のデータベースを選択します。
  * 発着信詳細記録 (CDR) イベント
  * 転写イベント
  * ターン・イベント

1. データベースを表示して、イベント・レポートが正しく転送されていることを確認します。

## 関連リンク
* [IBM Voice Gateway: イベントのレポート作成](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
