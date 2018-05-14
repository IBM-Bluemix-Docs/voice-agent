---

copyright:
  years: 2018
lastupdated: "2018-05-14"

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

By enabling call transfer, if a caller requests to speak with a live agent during conversation, the voice agent will redirect the call. You can enable call transfer setting a termination URI in your SIP provider configuration, and then defining the transfer target on an API action in a dialog node of your {{site.data.keyword.conversationshort}} instance. See [Programming voice agents using the API](api.html) for more detailed information about supported actions and customizing your voice agents.

## Step 1: Setting up the termination URI
{: #termination-setup}

### Setting up a termination URI in Twilio
{: #termination-Twilio}

1. In your Twilio account, navigate to the _Elastic SIP Trunking_ dashboard and select **Trunks**.

1. Choose the trunk that you want to add call transfer to by either selecting an existing trunk or creating a new one by clicking the **+** icon.

  * If you create a new trunk, you need to configure the _SIP Trunk URI_ in the **Origination** dashboard.  For more information, see [Set up a SIP trunk](getting-started.html#step2).

1. Select **Termination** on your navigation bar and enter a name for your termination URI.

  * Termination URI names must be unique. Twilio automatically checks the name you choose for availability. See [SIP Trunk termination settings](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination) for more detail about the Twilio services.

1. In the _Authentication_ section, click the **+** icon to add a voice agent IP address to the Access Control IP list.

  Add both of the following IP addresses:
   * 169.60.154.134 (US-South service region)
   * 169.61.86.179 (US-East service region)

1. Click **Save** to finish configuring your termination URI.

Make note of the phone number and termination URI that you want to transfer to so that you can specify them as the transfer target in your {{site.data.keyword.conversationshort}} dialog.


## Step 2: Configuring {{site.data.keyword.conversationshort}} for call transfer
{: #conversation-setup}

To learn more about working in the {{site.data.keyword.conversationshort}} service, see [About {{site.data.keyword.conversationshort}}](../../conversation/index.html#about).

1. In your {{site.data.keyword.Bluemix_notm}} dashboard, select the {{site.data.keyword.conversationshort}} instance that your voice agent uses.

1. From the _Getting started_ dashboard, click the **Launch tool** button.

1. Click **Getting Started** on the workspace that you want to edit.

1. Click **Add intent** and enter a name for the intent, such as _Transfer_.

  You can enter more detailed information, or return later to edit and refine the intent.

1. After you have created your call transfer intent, select the _Dialog_ tab.

1. Click **Add node** and enter a name for the node, such as _Call Transfer_.

1. In the _If the bot recognizes:_ section, type **Call transfer intent** to find the intent you made.

1. For the _Then respond with:_ section, click the **&vellip;** icon and select **Open JSON editor**. Copy and paste the following code snippet to replace what is currently in the field:

  ```json
{
 "output": {
   "text": {
     "values": [
       "Please hold on while I connect you with a live agent."
     ],
     "selection_policy": "sequential"
   },
   "vgwAction": {
     "command": "vgwActTransfer",
     "parameters": {
       "transferTarget": "sip:18889990000\\@mysiptrunk.pstn.twilio.com"
     }
   }
 }
}
  ```
{: codeblock}

**Note**: The SIP URI of the transfer target includes a telephone number and the termination URI that you created. For example, if the telephone number is `18889990000` and your termination URI is `mysiptrunk.pstn.twilio.com`, the full SIP URI is `sip:18889990000\\@mysiptrunk.pstn.twilio.com`.

## Next steps
{: #Next}

Test your voice agent by calling its associated phone number and use the key terms that you identified in your intent. If your voice agent redirects you, then it worked!

Now you can refine and configure the **Transfer** intent and dialog to respond to key terms and phrases of your choice.
