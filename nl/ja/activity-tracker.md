---

copyright:
  years: 2018
lastupdated: "2018-10-30"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# アクティビティー・トラッカー・イベント
{: #activity-tracker}

{{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、ユーザーおよびアプリケーションが {{site.data.keyword.Bluemix}} の {{site.data.keyword.iva_full}} サービスとどのように相互作用するかをトラックします。 {: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} サービスは、{{site.data.keyword.Bluemix_notm}} でサービスの状態を変更するユーザー開始アクティビティーを記録します。 詳細については、[{{site.data.keyword.cloudaccesstrailshort}}](../cloud-activity-tracker/index.html#getting-started-with-cla) を参照してください。

## イベントのリスト
{: #event-List}

次のテーブルに、イベントを生成するアクションを示します。

|アクション| 説明 |
| --- | ---- |
| `エージェントの作成: POST /config/submitconfig` | 新しいボイス・エージェントの作成 |
| `エージェントの更新: POST /config/submitconfig` | ボイス・エージェントの更新 |
| `並行性の更新: POST /config/updatemax` | 最大呼び出し並行性の更新 |
| `エージェントの削除: POST /config/submitconfig` | ボイス・エージェントの削除 |
{: caption="表 1. イベントを生成するアクション" caption-side="top"}

## アクティビティー・イベントの表示場所
{: #view-event}

{{site.data.keyword.cloudaccesstrailshort}} イベントは、イベントが生成される {{site.data.keyword.Bluemix_notm}} リージョンで使用可能な {{site.data.keyword.cloudaccesstrailshort}} アカウント・ドメインで使用できます。

## イベントのフィルター
{: #filter_events}

### ボイス・エージェント ID によるフィルター
{: #filter_id}

特定のボイス・エージェントのアクティビティー・イベントのリストをインスタンス ID でフィルターできます。

1. {{site.data.keyword.cloudaccesstrailshort}} の**「管理」**ページに移動します。
2. **「検索フィールド」**で `target.name_str` と入力し、**「検索」**フィールドでボイス・エージェント・インスタンス ID をストリングとして入力します。 ボイス・エージェント・インスタンス ID がパーセントでエンコードされていることと、ワイルドカード検索 _*_ を使用していることを確認します。

例えば、ボイス・エージェント・インスタンス ID `serviceInstanceId=crn%3A...` を検索するには以下のようにします。

  * **検索フィールド**: `target.name_str`
  * **検索**: `"*crn%3A...*"`

### アクション・イベントによるフィルター
{: #filter_action}

特定のアクション・イベントのアクティビティー・イベントのリストもフィルターできます。

1. {{site.data.keyword.cloudaccesstrailshort}} の**「管理」**ページに移動し、各フィールドごとに以下の構成値を入力します。

  * **ログの表示**: `Space logs`
  * **検索フィールド**: `action_str`
  * **検索**: `"action string"`

## 拡張フィルターの作成
{: #advanced_filters}

`AND` または `OR` を使用して検索語を**「検索」**フィールドで結合することによって、拡張フィルターを作成することもできます。

例えば、特定のボイス・エージェント・インスタンス ID および特定のアクションでフィルターします。

* **ログの表示**: `Space logs`
* **検索フィールド**: `target.name_str`
* **検索**: `"*crn%3A...*" AND action_str:"action string"`

**重要**: ボイス・エージェント・インスタンス id がパーセントでエンコードされていることと、ワイルドカード検索 _*_ を使用していることを確認します。
