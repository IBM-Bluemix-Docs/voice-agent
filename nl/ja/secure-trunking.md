---

copyright:
  years: 2018
lastupdated: "2018-06-14"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 接続の保護
{: #securing}

Secure Real Time Transport Protocol (SRTP) を有効にしたり、SIP トランクに Transport Layer Security (TLS) を使用して暗号化を有効にしたりして、{{site.data.keyword.iva_full}} で確立される接続を保護することができます。

## Twilio で SRTP をセットアップする
{: #SRTP}

**注:** SRTP を有効にした場合、SIP メッセージも暗号化されます。 SRTP と SIP のメッセージ暗号化を別々に有効化する必要はありません。

1. Twilio アカウントで、_「弾力的な SIP トランクの接続 (Elastic SIP Trunking)」_ダッシュボードにナビゲートして**「トランク (Trunks)」**を選択します。

1. 既存のトランクを選択するか、**「+」**アイコンをクリックして新規トランクを作成し、SRTP を使用して保護するトランクを選択します。

  * 新しいトランクを作成する場合、**「起点 (Origination)」**ダッシュボードで_「SIP トランク URI (SIP Trunk URI)」_を構成する必要があります。  詳しくは、[SIP トランクの接続](/docs/services/voice-agent?topic=voice-agent-connect)を参照してください。

1. _「一般」_ダッシュボードで、_「トランキングの保護 (Secure Trunking)」_セクションを見つけます。 **「無効」**をクリックして、トランキングの保護設定を**「有効」**に変更し、変更内容を保存します。

## Twilio で TLS を使用して SIP メッセージの暗号化のみを有効にする
{: #TLS}

SRTP を使用せずに {{site.data.keyword.iva_short}} の SIP メッセージのみを暗号化する場合は、Twilio で Transport Layer Security (TLS) を使用する URI エンドポイントを選択します。

1. Twilio アカウントで、_「弾力的な SIP トランクの接続 (Elastic SIP Trunking)」_ダッシュボードにナビゲートして**「トランク (Trunks)」**を選択します。

1. 既存のトランクを選択するか**「+」**アイコンをクリックして新規作成することにより、通話中転送を追加するトランクを選択します。

1. メニューから**「起点 (Origination)」**を選択し、以下のセキュアな起点 URI を一度に 1 つずつ入力します。 複数のホスト名または IP アドレスを指定しておくと、最初のホスト・エンドポイントで障害が発生したり、サービス休止になったりした場合、SIP トランク・プロバイダーはリストの次のホスト名に通話を切り替えます。

```
sip:us-south.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}

または

```
sip:us-east.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}
