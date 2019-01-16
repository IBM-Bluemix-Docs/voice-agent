---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# サービスの作成

{{site.data.keyword.iva_full}} サービス・インスタンスは、{{site.data.keyword.Bluemix_short}} カタログまたは {{site.data.keyword.Bluemix_notm}} `ibmcloud` コマンドを使用して作成できます。
{: shortdesc}


## カタログからのサービス作成
{: #catalog_create}

1. [{{site.data.keyword.iva_short}}カタログ・ページ](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)に移動します。

   カタログ・ページにはサービスと価格プランに関する情報があります。 **サービス名**の値は変更可能です。

2. [_「管理」_ダッシュボードで**「作成」**をクリックしてボイス・エージェントを作成](managing_create.html#config_instance)します。

## コマンド・ラインからのサービスの作成
{: #command_create}

1. [{{site.data.keyword.Bluemix_notm}} CLI をインストールします](../cli/index.html#overview)。

2. [`ibmcloud` コマンド](../cli/idt/commands.html#idt-cli)を実行して、_ライト_・プランで Voice Agent サービス・インスタンスを作成します。

   ```
   ibmcloud service create VoiceAgent _Lite_ "My Voice Agent Service"
   ```
   {: codeblock}
