---

copyright:
  years: 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Information security and data privacy
{: #infosec}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions.
{: shortdesc}

## Information handling and configuration options
{: #configure_infosec}

{{site.data.keyword.iva_short}} does not store, collect, or process data received from customers. Instead, the data is routed to different services for processing. During conversation, users might share information that contains Protected Health Information (PHI), personally identifiable information (PII), or PCI Data Security Standard (PCI DSS) data. See [Architecture](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window} to learn more about the conversation flow and architecture of {{site.data.keyword.iva_short}}.

Consider the following features when you configure your voice agent instance to support data privacy and secure handling.

### Call transfer
{:  #calltransfer_infosec}

When adding call transfer capabilities to your voice agent, you provide a phone number when you configure the transfer target SIP URI. Users should not provide a personal phone number for this transfer target.

See [Setting up call transfer](/docs/services/voice-agent?topic=voice-agent-call-transfer) to learn about configuring your SIP Trunk and SIP URI for call transfer.

### Event forwarding
{: #infosec_event_forwarding}

You can configure your voice agent to forward reporting events to a {{site.data.keyword.cloudantfull}} database instance. These reporting events can include PII, PHI, and PCI DSS data about your callers in the form of transcriptions, conversation turn events, and call detail records (CDR) events. Call data and reporting events are not stored, processed, or collected within {{site.data.keyword.iva_short}}, and users should configure their external {{site.data.keyword.cloudant_short_notm}} services appropriately. **By default, event forwarding is disabled.**

See [Enabling event forwarding](/docs/services/voice-agent?topic=voice-agent-event_forwarding) to configure your voice agents to forward reporting events.

See [**{{site.data.keyword.cloudant_short_notm}}: Security**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window} for more information about data privacy and information security for {{site.data.keyword.cloudant_short_notm}}.

### Text to Speech caching
{: #tts_caching}

To converse with customers, {{site.data.keyword.conversationshort}} crafts responses as text, which are passed to the {{site.data.keyword.texttospeechshort}} service and spoken aloud in {{site.data.keyword.iva_short}}. The responses that {{site.data.keyword.conversationshort}} creates might contain sensitive information. To prevent the {{site.data.keyword.iva_short}} from caching responses received from the {{site.data.keyword.texttospeechshort}} service that contain personal data, you can enable the `vgwActExcludeFromTTSCache` action command to exclude utterances that contain certain types of information from being cached. See [Programming voice agents using the API](/docs/services/voice-agent?topic=voice-agent-api#action-sequences).

### Secure connections
{: #secure_trunking}

{{site.data.keyword.iva_short}} is based in {{site.data.keyword.Bluemix_notm}} and integrates with SIP Trunks that users configure. Since SIP Trunks are external and connect to {{site.data.keyword.iva_short}}, you can enable secure connections between your SIP Trunks and {{site.data.keyword.iva_short}} by using Secure Real Time Transport Protocol (SRTP) and encryption by using secure sip (sips), which relies on Transport Layer Security (TLS). See [Securing connections](/docs/services/voice-agent?topic=voice-agent-securing).

### Service orchestration engine (SOE) configuration
{: #SOE_config}

You can use a Service Orchestration Engine (SOE) to process information passing between {{site.data.keyword.iva_short}} and {{site.data.keyword.conversationshort}} to customize conversation with callers. To maintain secure connections, ensure that you configure your SOE by using a secure URL, `https`, and user authentication.

See [Configuring {{site.data.keyword.conversationshort}} for your voice agent](/docs/services/voice-agent?topic=voice-agent-conversation_va#conversation_va) and [Architecture with a service orchestration engine](/docs/services/voice-agent?topic=voice-agent-about#arch-soe).

## Services related to {{site.data.keyword.iva_short}}
{: #related_services}

{{site.data.keyword.iva_short}} orchestrates different {{site.data.keyword.Bluemix_notm}} services to coordinate communication between end users and cloud based cognitive services. {{site.data.keyword.iva_short}} itself does not store, collect or process data in a manner that violates end user rights. However, depending on how you configure the related services, these integrated services might collect Protected Health Information (PHI), personally identifiable information (PII), or PCI Data Security Standard (PCI DSS) data that users share during conversation. To learn about {{site.data.keyword.iva_short}} architecture and conversation flow, see [Architecture](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}.

See the following resources to find considerations for each service and {{site.data.keyword.Bluemix_notm}}.

  * [**{{site.data.keyword.Bluemix_short}}: Security compliance**](/docs/overview?topic=overview-security#security)
  * [**{{site.data.keyword.conversationfull}}: Information security**](/docs/services/conversation?topic=services/conversation-information-security){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}: Information security**](/docs/services/text-to-speech?topic=text-to-speech-information-security){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}: Information security**](/docs/services/speech-to-text?topic=speech-to-text-information-security){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: Security**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}
