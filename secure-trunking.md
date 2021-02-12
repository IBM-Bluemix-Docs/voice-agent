---

copyright:
  years: 2018
lastupdated: "2018-06-14"

keywords: Secure Real Time Transport Protocol, SRTP, trunking, SIP trunk, SIP messages

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:deprecated: .deprecated}
{:external: target="_blank" .external}


# Securing connections
{: #securing}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances. Existing instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

You can enable Secure Real Time Transport Protocol (SRTP) and encryption by using Transport Layer Security (TLS) for your SIP trunks to secure connections that are made with {{site.data.keyword.iva_full}}.

## Setting up SRTP in Twilio
{: #SRTP}

**Note:** If you enable SRTP, SIP messages are also encrypted. You do not have to enable SRTP and SIP message encryption separately.

1. In your Twilio account, navigate to the _Elastic SIP Trunking_ dashboard and select **Trunks**.

1. Choose the trunk that you want to secure with SRTP by either selecting an existing trunk or creating a new one by clicking the **+** icon.

  * If you create a new trunk, you need to configure the _SIP Trunk URI_ in the **Origination** dashboard.  For more information, see [Connecting a SIP trunk](/docs/voice-agent?topic=voice-agent-connect).

1. On the _General_ dashboard, find the _Secure Trunking_ section. Click **Disabled** to change the secure trunking setting to **Enabled**, and save your changes.

## Enabling encryption for only SIP messages by using TLS in Twilio
{: #TLS}

If you want to encrypt only SIP messages in {{site.data.keyword.iva_short}} without SRTP, you can select a URI endpoint that uses Transport Layer Security (TLS) in Twilio.

1. In your Twilio account, navigate to the _Elastic SIP Trunking_ dashboard and select **Trunks**.

1. Choose the trunk that you want to add call transfer to by either selecting an existing trunk or creating a new one by clicking the **+** icon.

1. Select **Origination** from the menu and enter the following secure origination URIs, one at a time. By including multiple hostnames or IP addresses, if the first host endpoint fails or is out of service, your SIP trunk provider directs calls to the next listed hostname.

```
sip:us-south.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}

Or

```
sip:us-east.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}
