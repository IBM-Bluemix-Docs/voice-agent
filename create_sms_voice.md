---

copyright:
  years: 2019
lastupdated: "2019-06-24"

keywords: SMS, SMS-enabled, create

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
{:note: .note}

# Creating an SMS-enabled voice agent
{: #sms_voice_config_instance}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances, and access to free instances will be removed. Existing paid instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

After you create your {{site.data.keyword.iva_full}} service, you can create individual voice agents with SMS functions from the _Manage_ dashboard. You can configure your {{site.data.keyword.iva_full}} to receive inbound voice calls and respond with SMS outbound messages, depending on what type of response the user requests. To configure, add a node and intent in your {{site.data.keyword.conversationshort}} service.
{: shortdesc}


1. Go to the _Agents_ tab on the _Manage_ dashboard, and click **Create an Agent**.

1. For **Agent Type**, select _Voice + SMS_.

1. Follow the instructions in [Creating a voice agent](/docs/voice-agent?topic=voice-agent-config_instance).

1. Complete the **SMS Provider** section.

1. _**NOTE:**_ The Advanced SMS features section is not required to enable basic Voice and SMS integration, such as the capability to reply to an inbound voice message with an outbound SMS message. This section provides extra SMS functions. For more information, see [Creating an SMS-enabled voice agent with SMS-only capabilities](/docs/voice-agent?topic=voice-agent-sms_voice_config_instance#sms_voice_inbound).

### Configuring Watson Assistant for Voice and SMS integration
{: #sms_outbound}

1. In your {{site.data.keyword.Bluemix_notm}} dashboard, select the {{site.data.keyword.conversationshort}} instance that your agent uses.

1. Create an **outbound SMS intent** from the dashboard.

1. Add an **outbound SMS node** from the dashboard.

1. In the _If assistant recognizes:_ section, select the **outbound SMS intent** attribute that you previously created.

1. Find the outbound SMS intent that was created in the previous step. Add the response to the node. Copy and paste the following code snippet to replace the code in the field.

    ```json
        {
            "output": {
                "text": {
                "values": [
                    "Okay. I will send you a text message now."
                ],
                "selection_policy": "sequential"
                },
                "vgwActionSequence": [
                {
                    "command": "vgwActSendSMS",
                    "parameters": {
                    "message": "This is a test message from Watson Assistant"
                    }
                },
                {
                    "command": "vgwActPlayText"
                }
                ]
            }
        }
    ```
    {: codeblock}

1. Call your agent and trigger the node to receive a text message on the phone that you are calling from. 

To learn more about working in the {{site.data.keyword.conversationshort}} service, see [About {{site.data.keyword.conversationshort}}](/docs/assistant?topic=assistant-index).

## Creating an SMS-enabled voice agent with SMS-only capabilities
{: #sms_voice_inbound}

These settings enable stand-alone SMS-only sessions, which are not initiated through a voice call, under the same number that is used for integrated Voice+SMS service. This section allows for a separate {{site.data.keyword.conversationshort}} and {{site.data.keyword.cloudant_short_notm}} to be used for SMS-only sessions. NOTE: These settings do not apply to SMS sessions initiated through voice calls.

1. Enable **Allow SMS only conversation**.

1. Enable **Initiate conversation from inbound messages** if you want sessions to be initiated from inbound messages. If this option is not enabled, these settings apply only when a session is initiated by using the REST API.

1. Follow instructions in [Creating an SMS agent](/docs/voice-agent?topic=voice-agent-sms_config_instance) to create an SMS agent.


If an outbound text message is triggered from a node within Watson Assistant, the SMS Gateway endpoint region must be the same region as the Voice Agent endpoint region (SIP URI). The regions must be the same because of the pipe between Voice Gateway and SMS Gateway.
{: note}

