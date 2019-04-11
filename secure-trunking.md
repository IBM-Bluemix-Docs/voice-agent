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


# Securing connections
{: #securing}

You can enable Secure Real Time Transport Protocol (SRTP) and encryption by using Transport Layer Security (TLS) for your SIP trunks to secure connections that are made with {{site.data.keyword.iva_full}}.

## Setting up SRTP in Twilio
{: #SRTP}

**Note:** If you enable SRTP, SIP messages are also encrypted. You do not have to enable SRTP and SIP message encryption separately.

1. In your Twilio account, navigate to the _Elastic SIP Trunking_ dashboard and select **Trunks**.

1. Choose the trunk that you want to secure with SRTP by either selecting an existing trunk or creating a new one by clicking the **+** icon.

  * If you create a new trunk, you need to configure the _SIP Trunk URI_ in the **Origination** dashboard.  For more information, see [Connecting a SIP trunk](/docs/services/voice-agent?topic=voice-agent-connect).

1. On the _General_ dashboard, find the _Secure Trunking_ section. Click **Disabled** to change the secure trunking setting to **Enabled**, and save your changes.

## Enabling encryption for only SIP messages by using TLS in Twilio
{: #TLS}

If you want to encrypt only SIP messages in {{site.data.keyword.iva_short}} without SRTP, you can select a URI endpoint that uses Transport Layer Security (TLS) in Twilio.

1. In your Twilio account, navigate to the _Elastic SIP Trunking_ dashboard and select **Trunks**.

1. Choose the trunk that you want to add call transfer to by either selecting an existing trunk or creating a new one by clicking the **+** icon.

1. Select **Origination** from the menu and enter the following secure origination URIs, one at a time. By including multiple host names or IP addresses, if the first host endpoint fails or is out of service, your SIP trunk provider directs calls to the next listed host name.

```
sip:us-south.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}

Or

```
sip:us-east.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}
