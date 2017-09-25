---

copyright:
  years: 2017
lastupdated: "2017-09-22"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Limitations
{: #limitations}

The experimental release of {{site.data.keyword.iva_full}} has the following limitations.
{: shortdesc}

* Only connections to the public switched telephone network (PSTN) are supported.
* Only Twilio&reg; SIP trunks are supported, which results in limitations such as:
  * The SIPS URI scheme is not supported.
  * Secure Real-time Transport Protocol (SRTP) encryption is not supported.
  * Call transfer is not supported.
  * API actions and state variables that are related to these features are not supported.
* All voice agent configuration must be specified in the {{site.data.keyword.conversationshort}} service using the API.
