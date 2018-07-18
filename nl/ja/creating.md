---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# サービスの作成

{: shortdesc}
{{site.data.keyword.Bluemix_short}} カタログまたは {{site.data.keyword.Bluemix_notm}} `ibmcloud` コマンドを使用して {{site.data.keyword.iva_full}} サービス・インスタンスを作成できます。

## カタログからのサービス作成
{: #catalog_create}

1. [{{site.data.keyword.iva_short}}カタログ・ページ](https://console.bluemix.net/catalog/services/voice-agent-with-watson)に移動します。

   カタログ・ページにはサービスと価格プランに関する情報があります。 **サービス名**の値は変更可能です。

2. **「作成」**をクリックします。

## コマンド・ラインからのサービスの作成
{: #command_create}

1. [{{site.data.keyword.Bluemix_notm}} CLI をインストールします](../../cli/reference/bluemix_cli/get_started.html)。

2. [`ibmcloud` コマンド](../../cli/reference/bluemix_cli/bx_cli.html#bluemix_cli)を実行して、_トライアル_・プランで VoiceAgent サービス・インスタンスを作成します。

   ```
   ibmcloud service create VoiceAgent _Trial_ "My Voice Agent Service"
   ```
   {: codeblock}

## 次のステップ
{: #next}

_管理_ダッシュボードからボイス・エージェントを作成します。 [ボイス・エージェントの管理](managing.html)を参照してください。
