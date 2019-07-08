---

copyright:
  years: 2019
lastupdated: "2019-06-24"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Creating an SMS-enabled voice agent
{: #sms_voice_config_instance}

After you have created your {{site.data.keyword.iva_full}} service, you can create individual voice agents with SMS functionality, or voice agents with only SMS capabilities, from the _Manage_ dashboard. You can configure your {{site.data.keyword.iva_full}} to receive inbound voice calls and respond with SMS outbound messages, depending on the voice command received by the user. To configure, add a node and intent in your {{site.data.keyword.conversationshort}} service.
{: shortdesc}


1. Go to the _Voice agents_ tab on the _Manage_ dashboard, and click **Create a Voice Agent**.

1. For **Agent Type**, select _Voice + SMS_.

1. Follow the instructions in [creating a voice agent](/docs/services/voice-agent?topic=voice-agent-config_instance).

1. Check the **Initiate conversation from inbound messages** box to allow users to begin an SMS session with your SMS agent.

1. Check **Notify on session timeout** to have your SMS agent send an SMS message to the user, alerting them that the agent has not received a response in some time and will now timeout. 

   - See [Advanced Options](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) for more information on the **Advanced Options** available for your SMS agent, such as setting a custom time for the session to time out.

1. Follow instructions in [creating an SMS agent](/docs/services/voice-agent?topic=voice-agent-sms_config_instance) to create an SMS agent.

1. _**NOTE:**_ For an agent to have both Voice and SMS integration, such as receiving Voice input and sending back an SMS outbound message for a reply, you **must** use a one of your **voice** numbers for the **SMS** agent.

### Configuring Watson Assistant for Voice and SMS integration
{: #sms_outbound}

1. In your {{site.data.keyword.Bluemix_notm}} dashboard, select the {{site.data.keyword.conversationshort}} instance that your voice agent uses.

1. Create an **outbound SMS intent** from the dashboard.

1. Add an **outbound SMS node** from the dashboard.

1. In the _If assistant recognizes:_ section, select the **outbound SMS intent** attribute that you previously created.

1. Add the response to the node. Copy and paste the following code snippet to replace the code in the field.

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

To learn more about working in the {{site.data.keyword.conversationshort}} service, see [About {{site.data.keyword.conversationshort}}](/docs/services/assistant?topic=assistant-index#indext).