---

copyright:
  years: 2018, 2019
lastupdated: "2019-10-30"

keywords: security, privacy, data, governance, secure connections, information security

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

IBM is committed to providing our clients and partners with innovative data privacy, security, and governance solutions.
{: shortdesc}

## Information handling and configuration options
{: #configure_infosec}

To operate the service and optimize the user experience, {{site.data.keyword.iva_short}} collects and stores a minimal set of Personal Information (PI) which is handled in accordance with our [Data Processing Addendum (DPA)](https://www.ibm.com/support/customer/csol/terms/){: new_window} and [DPA Exhibit](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=00C4CE004FA711E7AA10752A2F494A7C){: new_window}. {{site.data.keyword.iva_short}} does not store, collect, or process data that is part of any voice or SMS conversations. Instead, the data is routed to different services for processing. During conversation, users might share information that contains Protected Health Information (PHI), personally identifiable information (PII), or PCI Data Security Standard (PCI DSS) data. See [Architecture](/docs/voice-agent?topic=voice-agent-about#architecture){: new_window} to learn more about the conversation flow and architecture of {{site.data.keyword.iva_short}}.

Consider the following features when you configure your agent instance to support data privacy and secure handling.

### Call transfer
{:  #calltransfer_infosec}

When you add call transfer capabilities to your agent, you provide a phone number when you configure the transfer target SIP URI. Users should not provide a personal phone number for this transfer target.

See [Setting up call transfer](/docs/voice-agent?topic=voice-agent-call-transfer) to learn about configuring your SIP Trunk and SIP URI for call transfer.

### Event forwarding
{: #infosec_event_forwarding}

You can configure your agent to forward reporting events to a {{site.data.keyword.cloudantfull}} database instance. These reporting events can include PII, PHI, and PCI DSS data about your callers in the form of transcriptions, conversation turn events, and call detail records (CDR) events. Call data, SMS data, and reporting events are not stored, processed, or collected within {{site.data.keyword.iva_short}}, and users should configure their external {{site.data.keyword.cloudant_short_notm}} services appropriately. **By default, event forwarding is disabled.**

See [Enabling event forwarding](/docs/voice-agent?topic=voice-agent-event_forwarding) to configure your agents to forward reporting events.

See [**{{site.data.keyword.cloudant_short_notm}}: Security**](/docs/Cloudant/offerings?topic=cloudant-security#security){: new_window} for more information about data privacy and information security for {{site.data.keyword.cloudant_short_notm}}.

### Text to Speech caching
{: #tts_caching}

To converse with customers, {{site.data.keyword.conversationshort}} crafts text responses, which are passed to the {{site.data.keyword.texttospeechshort}} service and spoken aloud in {{site.data.keyword.iva_short}}. The responses that {{site.data.keyword.conversationshort}} creates might contain sensitive information. To prevent the {{site.data.keyword.iva_short}} from caching responses received from the {{site.data.keyword.texttospeechshort}} service that contain personal data, you can enable the `vgwActExcludeFromTTSCache` action command to exclude utterances that contain certain types of information from being cached. See [Programming voice agents by using the API](/docs/voice-agent?topic=voice-agent-api#action-sequences).

After your Agent instance is deleted, the TTS cache is cleared in 24 hours. This value is referred to as the `TTS cache timeout value`.

### Secure connections
{: #secure_trunking}

{{site.data.keyword.iva_short}} is based in {{site.data.keyword.Bluemix_notm}} and integrates with SIP Trunks that users configure. Since SIP Trunks are external and connect to {{site.data.keyword.iva_short}}, you can enable secure connections between your SIP Trunks and {{site.data.keyword.iva_short}} by using Secure Real Time Transport Protocol (SRTP) and encryption by using secure sip (sips), which relies on Transport Layer Security (TLS). See [Securing connections](/docs/voice-agent?topic=voice-agent-securing).

By default, SMS data is encrypted with TLS. See [Voice Gateway: Data Processing](https://www.ibm.com/support/knowledgecenter/en/SS4U29/gdpr_considerations.html#GDPR_dataProcessing){: new_window} for more information.

### Service orchestration engine (SOE) configuration
{: #SOE_config}

You can use a Service Orchestration Engine (SOE) to process information that is passing between {{site.data.keyword.iva_short}} and {{site.data.keyword.conversationshort}} to customize conversation with callers. To maintain secure connections, ensure that you configure your SOE by using a secure URL, `https`, and user authentication.

See [Configuring {{site.data.keyword.conversationshort}} for your agent](/docs/voice-agent?topic=voice-agent-conversation_va#conversation_va) and [Architecture with a service orchestration engine](/docs/voice-agent?topic=voice-agent-about#arch-soe).

### SIP Authentication
{: #info_sip_auth}

When connecting SIP endpoints to a voice agent, you can add an additional level of protection by enabling SIP authentication. This feature ensures that only SIP endpoints that have the authorized service credential can initiate a call with a password-protected voice agent.

SIP digest authentication is supported for both inbound and outbound calls. For more information about how to configure your voice agent, see [SIP Authentication](/docs/voice-agent?topic=voice-agent-sip_auth).

## SMS/MMS Support
{: #SMS_MMS}

### Data handling
{: #data_handling}

{{site.data.keyword.iva_short}} does not store, collect, or process SMS data. MMS images are stored outside of our service and are handled by the service provider. Customers must refer to the security and privacy agreement of their SMS provider. {{site.data.keyword.iva_short}}  handles only textual links to the images that are embedded in the SMS messages.

When a service orchestration engine or {{site.data.keyword.conversationshort}} sends an MMS message to the user (with or without an SMS text message), one or more publicly accessible media URLs are sent to Twilio. Twilio does not support non-public URLs. Users should avoid sending sensitive or personal information through MMS.

{{site.data.keyword.iva_short}} masks caller IDs in the message logs to avoid collecting this type of personally identifiable information.

### Authentication
{: #authentication}

Inbound SMS messages are secured with the service provider by using [IAM authentication](/docs/voice-agent?topic=voice-agent-iam#sms_access){: new_window}.

## Services related to {{site.data.keyword.iva_short}}
{: #related_services}

{{site.data.keyword.iva_short}} orchestrates different {{site.data.keyword.Bluemix_notm}} services to coordinate communication between users and cloud based cognitive services. {{site.data.keyword.iva_short}} itself does not store, collect, or process data in a manner that violates user rights. However, depending on how you configure the related services, these integrated services might collect Protected Health Information (PHI), personally identifiable information (PII), or PCI Data Security Standard (PCI DSS) data that users share during conversation. To learn about {{site.data.keyword.iva_short}} architecture and conversation flow, see [Architecture](/docs/voice-agent?topic=voice-agent-about#architecture){: new_window}.

See the following resources to find considerations for each service and {{site.data.keyword.Bluemix_notm}}.

  * [**{{site.data.keyword.Bluemix_short}}: Security compliance**](/docs/overview?topic=overview-security#security)
  * [**{{site.data.keyword.conversationfull}}: Information security**](/docs/assistant?topic=assistant-information-security#information-security){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}: Information security**](/docs/text-to-speech?topic=text-to-speech-information-security){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}: Information security**](/docs/speech-to-text?topic=speech-to-text-information-security){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: Security**](/docs/Cloudant/offerings?topic=cloudant-security#security){: new_window}
