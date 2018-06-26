---

copyright:
  years: 2018
lastupdated: "2018-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Connecting a SIP trunk
{: #connect}

You can choose the SIP trunk provider that you use to integrate with {{site.data.keyword.iva_full}} from the following list.
{: #shortdesc}

* [NetFoundry](#NetFoundry-setup)
* [Twilio](#twilio-setup)
* [AT&T and other providers](#att-other)
* [Peering with {{site.data.keyword.iva_short}}](#peering)
* [Requesting assisted setup](#request-setup)

## Creating a NetFoundry SIP trunk and phone number
{: #NetFoundry-setup}

**Note:** Creating an account requires a credit card, which is periodically charged based on your use. If you already have a NetFoundry account, you can use the existing account.

1. Create an account on the [NetFoundry![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson.netfoundry.io/watson-login){: new_window} website.

1. Go to the _Watson account_ main page.

1. Select a region that you want the number to be from.

  **Note:** Check Netfoundry website for available regions. New regions are added continuously.

1. Click **Purchase** and follow the on-screen instructions to complete the purchase.

1. Once the payment successfully processes, your SIP trunk phone number is displayed in your account.

You need this phone number to set up your voice agent and configure call transfer, including the country and area codes. See [Creating and connecting your voice agent](getting-started.html#step3).


## Creating a Twilio SIP trunk
{: #twilio-setup}

**Note:** Creating a [Twilio account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.twilio.com/try-twilio){: new_window} requires a credit card, which is periodically charged based on your use of the SIP trunk that you configure. If you already have a Twilio account, you can use the existing account.

  1. Create a Twilio account on the [Twilio website ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.twilio.com/try-twilio){: new_window}.

  1. Create a SIP trunk with your Twilio account.

  1. From the Twilio website, go to the Elastic SIP Trunking dashboard.

  1. Select **Trunks** from the navigation bar and create a SIP trunk. If you already have a SIP trunk, click the **+** icon. In the resulting dialog box, enter a name for your SIP trunk and click **Create**.

  1. From the Elastic SIP Trunks page, select your SIP trunk.

  1. Select **Origination** from the navigation bar for your SIP trunk and configure the origination SIP URI. You can include multiple host names to prevent service failures by selecting the **+** icon.

  The IP address or the host name is the value that you noted on the _Getting Started_ dashboard of your {{site.data.keyword.iva_short}} service instance. When you configure the origination URI, it must be in SIP URI format, such as `sip:us-south.voiceagent.cloud.ibm.com/`. By including multiple host names or IP addresses, if the first host endpoint fails or is out of service, your SIP trunk provider directs calls to the next listed host name.

  1. Select **Numbers** from the navigation bar for your SIP trunk. Then, create a phone number and assign it to your SIP trunk.

  On the Numbers page, click **Buy a Number** or, if you already have a number, click the **+** icon. A panel displays where you can provision a new phone number in your region. Assign the number to the SIP trunk you created by going back to the SIP trunk and clicking the Number icon.

  You need this phone number to set up your voice agent, including the country and area codes. See [Creating and connecting your voice agent](getting-started.html#step3).


## Connecting with AT&T and other providers
{: #att-other}

{{site.data.keyword.iva_short}} supports connections with AT&T&reg; and other SIP trunking providers. However, these connections are not self-service setup, and require extra assistance. See [Requesting assisted setup](#request-setup).

## Peering with {{site.data.keyword.iva_short}}
{: #peering}

{{site.data.keyword.iva_short}} supports peer connections, such as an IPSec tunnel. However, these connections are not self-service setup, and require extra assistance. See [Requesting assisted setup](#request-setup).

## Requesting assisted setup
{: #request-setup}

You can request assisted network setup to connect with AT&T or other SIP trunking providers, peer with {{site.data.keyword.iva_short}}, or to request more than 50 concurrent connections by using the following process.

1. Open a new [{{site.data.keyword.Bluemix_notm}} support ticket](https://console.bluemix.net/unifiedsupport/tickets/add)

1. Select **Technical** for **Ticket Type**.

1. Choose **Cloud Foundry** for **Select a resource context**.

1. For **Technical area of support**, choose **Application Services**.

1. Choose the **Region**, **Organization**, and **Space** for your {{site.data.keyword.iva_short}} instance.

1. Select your {{site.data.keyword.iva_short}} service instance for **Associated resource**.

1. Choose **Severity 4 - Minimal Impact** for **Severity**

1. For **Subject**, enter `{{site.data.keyword.iva_short}} assisted network setup`.

1. In the **Brief description** section, describe how you intend to connect to your {{site.data.keyword.iva_short}} service or to request more than 50 concurrent connections for your voice agent. You can connect by using either a SIP trunking provider or a Peer connection, such as an IPSec tunnel. In your ticket, you can attach a network diagram that describes your network topology in a PDF or image format. You can also attach any white papers that describe the service capabilities that you want in detail.
