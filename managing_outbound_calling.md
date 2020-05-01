---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-30"

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

   If you enable secure trunking, the equivalent setting must be configured in your SIP provider.

   For example, in Twilio go to the Elastic SIP Trunking dashboard. Select your Trunk and under General Settings, you would enable **Secure Trunking**.

1. Specify a _Peer IP address_. A peer IP address is the IP address of the SIP termination endpoint.

   For example, in Twilio this would correspond to a Signaling IP address.

   - From the Twilio website, go to the Elastic SIP Trunking dashboard.

   - Select **Networking Info** from the navigation bar. Here you will see a list of Signaling IPs. Use one of these IP addresses as the peer IP address.

1. Whitelist the IP address

   Your trunk termination point must have at least one authentication scheme (`IP Access Control Lists` and/or `Credential Lists`).

   For example, in Twilio, go to the Elastic SIP Trunking dashboard. Select your Trunk and go to **Termination** from the navigation bar.

   - Under the **Authentication** section, configure one of the _Authentication types_. For `IP ACCESS CONTROL LISTS`, the IP address to use here would be the voice agent outbound calling interface IP address. See [Networking Information](/docs/voice-agent?topic=voice-agent-networking_info).
