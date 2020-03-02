---

copyright:
  years: 2019, 2020
lastupdated: "2020-02-17"

keywords: enable, disable, manage, outbound calling

subcollection: "voice-agent"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}

# Enabling outbound calling
{: #enable-outbound-calling}

When enabled, {{site.data.keyword.iva_full}} allows customers to initiate outbound calls from {{site.data.keyword.conversationshort}}.
{: #shortdesc}

## Enabling/disabling outbound calling
{: #enable-outbound}

To enable or disable outbound calling:

1. Go to the _Instance_ tab on the _Manage_ dashboard.

1. Under the **Outbound calling** section, click the **Manage** icon.

1. Click the checkbox next to _Enable outbound calling_ to enable or disable outbound calling.

1. Click the checkbox next to _Secure trunking_ to enable or disable secure trunking.

1. Specify a _Peer IP address_. A peer IP address is the IP address of the SIP termination endpoint.

   For example, in Twilio this would correspond to a Signaling IP address.

   - From the Twilio website, go to the Elastic SIP Trunking dashboard.

   - Select **Networking Info** from the navigation bar. Here you will see a list of Signaling IPs. Use one of these IP addresses as the peer IP address.

1. Whitelist the IP address

   For example, in Twilio, if you do not specify a credential, then you must add an IP address to the IP `ACCESS CONTROL LISTS`.

   - Configure one of the _Authentication types_. The IP address to use here would be the voice agent outbound calling interface IP address. See [Networking Information](/docs/services/voice-agent?topic=voice-agent-networking_info).
