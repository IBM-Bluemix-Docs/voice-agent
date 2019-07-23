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


# 连接到 SMS 提供者
{: #connect-sms}

您可以从以下列表中选择 SMS 提供者，用于与 {{site.data.keyword.iva_full}} 集成。
{: #shortdesc}

* [Twilio](#twilio-setup)

## 生成 API 密钥并设置凭证
{: #sms_access}

仅为帐户中已处于活动状态的角色创建凭证。对于 SMS 和语音 + SMS 代理程序，您必须已分配*写入者*或*管理者*角色。请参阅[步骤 9 的邀请用户并分配初始访问权](/docs/services/voice-agent?topic=voice-agent-iam#step1)。

1. 在 {{site.data.keyword.iva_short}} 实例的*仪表板*上，单击**新建凭证 (+)**。 
2. 在弹出的新对话框中，输入**名称**，并在**角色**下拉菜单下，选择*写入者*或*管理者*。 
    - **注：**对于任何与 SMS 相关的功能，您**_必须_**选择*写入者*或*管理者*角色。 
3. 单击**添加**。
4. 在新创建的凭证旁，单击**查看凭证**。请记录 JSON 脚本中 `APIKEY` 的值，以在[配置 Twilio 以使用 SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup) 中使用。

## 配置 Twilio 以使用 SMS
{: #twilio-setup}

1. 访问 Twilio 电话号码，在[此处](https://www.twilio.com/console/phone-numbers/)可以找到，然后选择为 _SMS_ 或_语音 + SMS_ 代理程序分配的电话号码。 

1. 向下滚动到**消息传递**部分。在_配置方式_字段中，从下拉菜单中选择**Webhook、TwiML Bins、函数、Studio 或代理**。

1. 在_消息来源_字段中，从下拉菜单中选择 **Webhook**。

1. 在 **Webhook** 旁边的空 URL 字段中，遵循代理所在区域的指示信息。 

    - 如果创建的代理程序位于华盛顿区域，请在字段中写入 `https://apikey:YOUR_API_KEY@sms-east.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv`。
    - 如果创建的代理程序位于达拉斯区域，请在字段中写入 `https://apikey:YOUR_API_KEY@sms-south.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv`。
    - 请将上述 URL 中的 `YOUR_API_KEY` 替换为先前创建的凭证的 `APIKEY`。请参阅[生成 API 密钥并设置凭证](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_access)。 

1. 单击**保存**。 
