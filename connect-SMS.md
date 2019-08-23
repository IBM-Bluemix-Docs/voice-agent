---

copyright:
  years: 2019
lastupdated: "2019-06-21"

keywords: SMS, SMS provider, SMS agent

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Connecting to SMS Providers
{: #connect-sms}

You can choose the SMS provider that you use to integrate with {{site.data.keyword.iva_full}} from the following list.
{: #shortdesc}

* [Twilio](#twilio-setup)

## Generating an API key and Setting Credentials
{: #sms_access}

You can create credentials only for roles that are already active in your account. For SMS and Voice + SMS agents, you must have either the *Writer* or *Manager* role assigned. See [Step 9 of Invite users and assign initial access](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. On the *Dashboard* of your {{site.data.keyword.iva_short}} instance, click **New Credential (+)**. 
2. In the new dialog box that pops up, enter a **Name**, and under the **Role** menu, select *Writer* or *Manager*. 
    - **NOTE:** For any SMS-related functions, you **_must_** select either the *Writer* or *Manager* role. 
3. Click **Add**.
4. Next to your newly created credentials, click **View credentials**. Make note of the value for `APIKEY` in the JSON script for use in [Configuring Twilio for SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

## Configuring Twilio for SMS
{: #twilio-setup}

1. Access your Twilio phone numbers, found [here](https://www.twilio.com/console/phone-numbers/) and select the phone number that is assigned to your _SMS_ or _Voice + SMS_ agent. 

1. Scroll down to the **Messaging** section. In the _CONFIGURE WITH_ field, select **Webhooks, TwiML Bins, Functions, Studio, or Proxy** from the dropdown menu.

1. In the _A MESSAGE COMES IN_ field, select **Webhook** from the dropdown menu.

1. In the empty URL field next to **Webhook**, follow the instructions based on the region of your agent. 

    - If the agent you created is based in the Washington region, write `https://apikey:YOUR_API_KEY@sms-east.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` in the field.
    - If the agent you created is based in the Dallas region, write `https://apikey:YOUR_API_KEY@sms-south.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` in the field.
    - Replace `YOUR_API_KEY` in the preceding URL with the `APIKEY` from the credential you created earlier. See [Generating an API key and Setting Credentials](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_access). 

1. Click **Save**. 