---

copyright:
  years: 2019
lastupdated: "2019-06-21"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# SMS プロバイダーへの接続
{: #connect-sms}

以下のリストから、{{site.data.keyword.iva_full}} との統合に使用する SMS プロバイダーを選択できます。
{: #shortdesc}

* [Twilio](#twilio-setup)

## API キーの生成と資格情報の設定
{: #sms_access}

ご使用のアカウントで既にアクティブになっている役割に関してのみ、資格情報を作成できます。SMS エージェントおよびボイス + SMS エージェントの場合、*ライター*または*マネージャー (管理者)* の役割が割り当てられている必要があります。[「ユーザーを招待し、初期アクセス権限を割り当てる」のステップ 9](/docs/services/voice-agent?topic=voice-agent-iam#step1) を参照してください。

1. {{site.data.keyword.iva_short}} インスタンスの*ダッシュボード*で、**「新規資格情報 (+)」**をクリックします。 
2. 新規作成のダイアログ・ボックスが開いたら、**名前**を入力し、**「役割」**ドロップダウン・メニューで*「ライター」*または*「管理者」*を選択します。 
    - **注:** SMS 関連の機能を利用するには、*「ライター」*または*「管理者」*のいずれかの役割を選択する**_必要があります_**。 
3. **「追加」**をクリックします。
4. 新規作成された資格情報の横にある**「資格情報の表示」**をクリックします。[Twilio for SMS の構成](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup)で使用する目的で、JSON スクリプト内の `APIKEY` の値を書き留めます。

## Twilio for SMS の構成
{: #twilio-setup}

1. [ここ](https://www.twilio.com/console/phone-numbers/)にある Twilio 電話番号にアクセスして、_SMS_ エージェントまたは _ボイス + SMS_ エージェントに割り当てられた電話番号を選択します。 

1. **「メッセージング」**セクションまでスクロールダウンします。_「CONFIGURE WITH (次を使用して構成)」_フィールドで、ドロップダウン・メニューから **Webhooks、TwiML Bins、Functions、Studio、または Proxy** を選択します。

1. _「A MESSAGE COMES IN (受信されるメッセージの形式)」_フィールドで、ドロップダウン・メニューから **Webhook** を選択します。

1. **Webhook** の横にある空の URL フィールドで、エージェントの地域 (リージョン) に基づく指示に従います。 

    - 作成したエージェントが Washington 地域に基づいている場合は、フィールドに `https://apikey:YOUR_API_KEY@sms-east.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` と指定します。
    - 作成したエージェントが Dallas 地域に基づいている場合は、フィールドに `https://apikey:YOUR_API_KEY@sms-south.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` と指定します。
    - 上記の URL の `YOUR_API_KEY` を、既に作成した資格情報の `APIKEY` に置き換えます。[API キーの生成と資格情報の設定](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_access)を参照してください。 

1. **「保存」**をクリックします。 
