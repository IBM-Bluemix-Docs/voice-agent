---

copyright:
  years: 2019, 2020
lastupdated: "2020-07-28"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:tip: .tip}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:pre: .pre}
{:screen: .screen}

# Release notes
{: #release-notes}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances. Existing instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}


Stay up-to-date with new features and updates that are available for {{site.data.keyword.iva_full}}.
{: shortdesc}

## July 2020

- **Updated:  Voice Gateway driver is updated to version 1.0.6**

## March 2020

- **Updated:  Voice Gateway driver is updated to version 1.0.5**

## December 2019

- **Updated:  Voice Gateway driver is updated to version 1.0.4**

## November 2019

- **Added:  Support for SIP Authentication** New as of:  _2019-11-26_

  - {{site.data.keyword.iva_full}} now supports the ability to enable SIP Authentication. For more information, see [SIP Authentication](/docs/voice-agent?topic=voice-agent-sip_auth)

- **Added:  Support for outbound calls** New as of:  _2019-11-26_

  - {{site.data.keyword.iva_full}} now supports the ability to make outbound calls using REST API. For more information, see [Enabling outbound calling](/docs/voice-agent?topic=voice-agent-enable-outbound-calling) and [Initiating an outbound call](/docs/voice-agent?topic=voice-agent-init-outbound)

- **Updated:  Voice Gateway driver is updated to version 1.0.3**

## September 2019

- **Added:  Speech To Text advanced configuration options** New as of:  _2019-09-19_

  - You can now configure custom language models and custom acoustic models for {{site.data.keyword.iva_full}} by using the Speech To Text advanced configuration options. For more information, see [Step 12 of Creating an Agent](/docs/voice-agent?topic=voice-agent-config_instance#config_instance).

- **Updated:  Voice Gateway driver is updated to version 1.0.2.4**

## July 2019

- **Updated:  User interface updated for SMS-enabled voice agents**
  
  - **Voice + SMS** agents now support stand-alone **SMS** functionality under the same phone number that is used for integrated **Voice + SMS** service. For more information, see [Creating an SMS-enabled voice agent with SMS-only capabilities](/docs/voice-agent?topic=voice-agent-sms_voice_config_instance#sms_voice_inbound)

- **Updated:  Voice Gateway driver is updated to version 1.0.2.1**

## June 2019

- **Added:  Support for SMS Messaging** New as of:  _2019-06-24_

  - {{site.data.keyword.iva_full}} now supports SMS functionality as either a **Voice + SMS** agent or a stand-alone **SMS** agent. For more information, see [Creating an SMS-enabled voice agent](/docs/voice-agent?topic=voice-agent-sms_voice_config_instance) to create a **Voice + SMS** agent, or [Creating an SMS agent](/docs/voice-agent?topic=voice-agent-sms_config_instance) to create a stand-alone **SMS** agent.

- **Updated:  Voice Gateway driver is updated to version 1.0.1.**

## March 2019

- **Added:  Support for multiple phone numbers within a single agent.** New as of:  _2019-03-19_

  - {{site.data.keyword.iva_full}} now supports the ability to configure multiple phone numbers within a single agent. This allows multiple phone numbers to be easily mapped to the same dialog. See [Managing Multiple Numbers](/docs/voice-agent?topic=voice-agent-multi_num#multi_num).

- **Updated:  Voice Gateway driver is updated to version 1.0.0.8d.**

## January 2019

- **Added:  Support for non-standard phone numbers.** New as of: _2019-01-31_

  - {{site.data.keyword.iva_full}} now supports both traditional phone numbers as well as unique numeric identifiers for agents. See [Step 3 of Creating an Agent](/docs/voice-agent?topic=voice-agent-config_instance#create_instance).

- **Updated:  Voice Gateway driver is updated to version 1.0.0.8b.**
