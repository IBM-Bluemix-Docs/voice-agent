---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Setting up call transfer
{: #call-transfer}

You can set up call transfer so that if a caller requests to speak to a live agent during a conversation, the voice agent automatically transfers the call.
{: shortdesc}

## About call transfer
{: #about-ct}

By enabling call transfer, if a caller requests to speak with a live agent during conversation, the voice agent will redirect the call. {{site.data.keyword.iva_short}} uses a SIP REFER to direct the call back to your SIP trunk provider to handle, and does not anchor transferred phone calls.

You can enable call transfer by setting a termination URI or tel URI in your SIP provider configuration. Then, you define the transfer target on an API action in a dialog node of your {{site.data.keyword.conversationshort}} instance. Your transfer target is a SIP URI that contains the termination URI and phone number or a tel URI with phone number. For more information about supported actions and customizing your voice agents, see [Programming voice agents using the API](/docs/services/voice-agent?topic=voice-agent-api).

## Step 1: Setting up the termination URI
{: #termination-setup}

If you are using a tel URI instead of a termination URI for your SIP URI configuration, you can use the tel URI, such as `tel:+18889990000`, for your `transferTarget`. You need a termination URI for your `transferTarget` if you are using a SIP URI.
{: tip}

### Setting up a termination URI in NetFoundry
{: #termination-netfoundry}

Make note of the phone number in your [NetFoundry account![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson.netfoundry.io/watson-login){: new_window} that you want to transfer to. Later, you can specify this phone number and the termination URI as the transfer target in your {{site.data.keyword.conversationshort}} dialog. Do not use a personal phone number.

Copy the following NetFoundry termination URI to use in the transfer target.

```
dal.watson-va.netfoundry.net
```
{: codeblock}

You do not need to manually configure the termination URI in your NetFoundry account when [Configuring {{site.data.keyword.conversationshort}} for call transfer](#conversation-setup).

### Setting up a termination URI in Twilio
{: #termination-Twilio}

1. In your Twilio account, navigate to the _Elastic SIP Trunking_ dashboard and select **Trunks**.

1. Choose the trunk that you want to add call transfer to by either selecting an existing trunk or creating a new one by clicking the **+** icon.

  * If you create a new trunk, you need to configure the _SIP Trunk URI_ in the **Origination** dashboard.  For more information, see [Connecting a SIP trunk](/docs/services/voice-agent?topic=voice-agent-connect).

1. Select **Termination** on your navigation bar and enter a name for your termination URI.

  * Termination URI names must be unique. Twilio automatically checks the name that you choose for availability. See [SIP Trunk termination settings ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window} for more detail about the Twilio services.

1. Select **General** on your navigation bar to view the _General settings_. Under the **Call Transfer (SIP REFER)** heading, toggle the setting to **Enabled** and select **Allow Call Transfers to the PSTN via your Trunk.**

1. Click **Save** to finish configuring your termination URI and enabling call transfer.

1. Make note of the phone number and termination URI that you want to transfer to. Make sure that the phone number is not a personal phone number. You can use the phone number and termination URI to specify the transfer target in your {{site.data.keyword.conversationshort}} dialog.


## Step 2: Configuring {{site.data.keyword.conversationshort}} for call transfer
{: #conversation-setup}

To learn more about working in the {{site.data.keyword.conversationshort}} service, see [About {{site.data.keyword.conversationshort}}](/docs/services/assistant?topic=assistant-index#indext).

1. In your {{site.data.keyword.Bluemix_notm}} dashboard, select the {{site.data.keyword.conversationshort}} instance that your voice agent uses.

1. From the _Getting started_ dashboard, click the **Launch tool** button.

1. Click **Getting Started** on the skill that you want to edit.

1. Click **Add intent** and enter a name for the intent, such as _Transfer_.

  You can enter more detailed information, or return later to edit and refine the intent.

1. After you create your call transfer intent, select the _Dialog_ tab.

1. Click **Add node** and enter a name for the node, such as _Call Transfer_.

1. In the _If the bot recognizes:_ section, type **Call transfer intent** to find the intent you made.

1. For the _Then respond with:_ section, click the **&vellip;** icon and select **Open JSON editor**. Copy and paste the following code snippet to replace the code in the field.

  * If you use a tel URI, replace the SIP URI in the `transferTarget` with your tel URI. For example,  `"transferTarget":"tel:+18889990000"`.

  * **NOTE**: Make sure the `transferTarget` URI starts with a `+`.

  ```json
  {
      "output": {
          "text": {
              "values": [ "Please hold on while I connect you with a live agent." ],
              "selection_policy": "sequential"
          },
          "vgwAction": {
              "command": "vgwActTransfer",
              "parameters": {
                  "transferTarget": "sip:+18889990000\\@dal.watson-va.netfoundry.net"
              }
          }
      }
  }
  ```
  {: codeblock}

1. Check that the phone number in your `transferTarget` termination URI or tel URI correctly matches the phone number in your SIP trunk.

**Remember**: The SIP URI of the transfer target includes a telephone number and the termination URI that you created. Do not use a personal telephone number in your transfer target. For example, if the telephone number is `18889990000` and your termination URI is `mysiptrunk.pstn.twilio.com`, the full SIP URI is `sip:+18889990000\\@mysiptrunk.pstn.twilio.com`. If you use Netfoundry, and have a telephone number of `18889990000`, the full SIP URI is `sip:+18889990000\\@dal.watson-va.netfoundry.net`.

**NOTE**: Make sure the `transferTarget` URI starts with a `+` and may include up to 256 characters.

## Next steps
{: #Next}

Test your voice agent by calling its associated phone number, and use the key terms that you identified in your intent. If your voice agent redirects you, then it worked!

Now you can refine and configure the **Transfer** intent and dialog to respond to key terms and phrases of your choice.
