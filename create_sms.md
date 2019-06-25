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


# Creating an SMS agent
{: #sms_config_instance}

After you have created your {{site.data.keyword.iva_full}} service, you can create individual sms agents from the _Manage_ dashboard.
{: shortdesc}

1. Go to the _Voice agents_ tab on the _Manage_ dashboard, and click **Create a Voice Agent**.

1. For **Agent Type**, select _SMS_.

1. Follow steps 3 through 6 in [creating a voice agent](https://test.cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-config_instance).

1. Under **SMS Provider**, enter the user name, password and API URL for your SMS provider. For example, if using _Twilio_, the username is your **Account SID**, the password is your **Auth Token** and your SMS provider is `https://api.twilio.com`

1. Under **Conversation**, configure the connection to your {{site.data.keyword.conversationshort}} service instance. You can use {{site.data.keyword.conversationshort}} service instances in {{site.data.keyword.Bluemix_notm}} accounts that you or someone else owns. You can also connect to any of these options through a service orchestration engine (SOE).

   * If you are creating an SMS agent in either the Dallas or Washington DC region and do not have a {{site.data.keyword.conversationshort}} service instance, you can create one in the **Service instance** menu.
   * Alternatively, you can connect to other sources of a {{site.data.keyword.conversationshort}} dialog or to connect with a SOE by changing the [**Service type**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service).
   * If you want to configure multiple service locations, click the other location option and select **Enable location** to configure the connection to your other {{site.data.keyword.conversationshort}} instance. For more information, see [Adding multiple Watson service locations](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).

1. You can also choose to enable event forwarding to collect information about calls that are handled by your voice agents in a {{site.data.keyword.cloudantfull}}. For more information, see [Enabling event forwarding for voice agents](/docs/services/voice-agent?topic=voice-agent-event_forwarding). For more configuration options, see [Configuring a voice agent](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1.  Click **Create voice agent** to create your SMS agent and any new services.

1. Follow [the instructions](/docs/services/voice-agent?topic=voice-agent-connect-sms) to connect to an SMS provider.

After you create the SMS agent, test your SMS agent by texting its phone number. You can view details about your interaction on the _Usage_ dashboard. See [Viewing Usage and Logs](/docs/services/voice-agent?topic=voice-agent-logging).

To enable SMS messaging between customers and a voice agent during a voice call, the SMS number must match the voice number.
{: tip}

Before you create an SMS agent or add SMS functionality to your voice agent, you **must** have the proper credentials set up and generate an API key to program to your SMS number. For more information, see [Generating API Key and Setting Credentials](/docs/services/voice-agent?topic=voice-agent-connect-sms#sms_access).

You **must** also configure your SIP trunk for SMS functionality. See your provider's instructions, for example, Twilio. If you do not have a Twilio phone number, see [Creating a Twilio SIP trunk](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup).

Once you have a Twilio number, you will need to configure it for SMS functionality. For more information, see [Configuring Twilio for SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

If you have trouble creating credentials, contact your service instance administrator to grant you *Manager* or *Writer* access.
{: tip}

## Advanced Options for SMS Agents
{: #sms_advanced}

Click **Show Advanced** after the **Phone Number** field.

1. Set an optional **Conversation read timeout** value. This is the time in seconds that the SMS Gateway waits for a response from Watson Assistant. If the time is exceeded, SMS Gateway reattempts to contact Watson Assistant. If the service still cannot be reached, the SMS/MMS message fails. Set to 30 seconds by default.

2. Set an optional **Session Timeout**. This is the time in seconds after which the session expires if SMS Gateway does not receive a response from the user.

3. Set a **Conversation failure reply message**. This is the default response message that is sent if Watson Assistant cannot be reached. By default, it is set to `We're sorry, but we can't respond to your message.`.

### Configuring the SMS Agent for Terminating the Session
{: #sms_terminate}

The {{site.data.keyword.iva_full}} SMS agent terminates a session based on the value for the session timeout, which is configurable and set to 30 seconds by default. 

You can also add a node to your {{site.data.keyword.conversationshort}} service to respond to an end session command from the user. 

1. In your {{site.data.keyword.Bluemix_notm}} dashboard, select the {{site.data.keyword.conversationshort}} instance that your voice agent uses.

1. From the _Getting started_ dashboard, click **Launch tool**.

1. Click **Getting Started** on the skill that you want to edit.

1. Click **Add intent** and enter a name for the intent, such as _Terminate SMS_. Alternatively, you can modify an existing intent that you already use for the voice agent, such as _End the call_.

  You can enter more detailed information, or return later to edit and refine the intent.

1. After you create your outbound messaging intent, select the _Dialog_ tab.

1. Click **Add node** and enter a name for the node, such as _Terminate SMS Text_.

1. In the _If the bot recognizes:_ section, type **Terminate SMS Text intent**, or the existing intent name you had, to find the intent you made.

1. For the _Then respond with:_ section, click the **&vellip;** icon and select **Open JSON editor**. Copy and paste the following code snippet to replace the code in the field.

    ```json
        {
            "output": {
                 "text": {
                    "values": [
                        "Thank you for using the service. Goodbye!"
                    ],
                    "selection_policy”: “sequential"
                },
                "smsAction": {
                    "command": "terminateSession"
                }
            }
        }
    ```
    {: codeblock}


1. Change the `values` field in the preceding code snippet to be your customized termination message to the user. 

After you create the voice agent, test your voice agent by calling or texting its phone number based on its type. You can view details about your interaction on the _Usage_ dashboard. See [Viewing Usage and Logs](/docs/services/voice-agent?topic=voice-agent-logging).