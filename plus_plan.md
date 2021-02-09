---

copyright:
  years: 2019
lastupdated: "2019-08-12"

keywords: plus plan, premium plan, Watson
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

# Using a Plus plan
{: #plus_plan}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances, and access to free instances will be removed. Existing paid instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

The {{site.data.keyword.iva_full}} Plus plan is for customers who require more {{site.data.keyword.iva_short}} capacity than what is provided by the Standard plan. The Plus plan includes:
- Real-time phone calls with {{site.data.keyword.conversationshort}}
- Support for sending and receiving SMS messages during voice calls
- Up to 50 simultaneous phone calls (more by request)
- SIP connectivity for voice calls
- Unified billing with Watson services

The {{site.data.keyword.iva_full}} Plus plan cannot be provisioned through {{site.data.keyword.Bluemix_short}}. It must be purchased through an IBM sales representative.

## Watson services
{: #plus_watson_services}
The {{site.data.keyword.iva_full}} Plus plan simplifies pricing by bundling {{site.data.keyword.iva_short}} with the Watson services it depends on under a single price. For more information, see [Creating a voice agent](/docs/voice-agent?topic=voice-agent-config_instance).

To avoid extra charges, select a {{site.data.keyword.conversationshort}} Plus or Premium plan for use with your {{site.data.keyword.iva_short}} Plus plan. If you do not use a {{site.data.keyword.conversationshort}} Plus or Premium plan, you incur extra charges based on the number of API calls.

## Using an SOE
{: #plus_soe}
To use an SOE as part of the Plus plan, the SOE must pass the `user_id` attribute in the `context` object from {{site.data.keyword.iva_short}} to {{site.data.keyword.conversationshort}}.

**V1:**
```
{
  "alternateIntents": false,
  "input": {
    "text": ""
  },
  "context": {
    "vgwSessionID": "DQqrG1-j3A",
    "metadata": {
      "user_id": "xxxxxx"
    }
  }
}
```
**V2:**
```
{
  "input": {
    "options": {
      "return_context": true
    },
    "text": ""
  },
  "context": {
    "skills": {
      "main skill": {
        "user_defined": {
          "vgwSessionID": "hcK492niTn"
        }
      }
    },
    "global": {
      "system": {
        "user_id": "xxxxxx"
      }
    }
  }
}
```

## SMS interaction
{: #plus_sms}
SMS messages are bundled as part of the Plus plan. SMS messages can be sent and received as part of a voice call at no additional cost. For more information on SMS integration, see [Creating an SMS-enabled voice agent](/docs/voice-agent?topic=voice-agent-sms_voice_config_instanc).

Currently, SMS functionality is limited under the Plus plan:
- **SMS** type agents are not available.
- **Voice + SMS** type agents are available, but do not support an SMS-only {{site.data.keyword.conversationshort}}
- SMS sessions must be initiated through {{site.data.keyword.conversationshort}}. SMS sessions cannot be initiated through the API or an inbound SMS message.
