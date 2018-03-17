---

copyright:
  years: 2017, 2018
lastupdated: "2017-09-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Troubleshooting and support
{: #troubleshooting}

Having trouble with {{site.data.keyword.iva_full}}? Review the troubleshooting tips for common problems, and reach out to the community with any questions.
{: shortdesc}

## Getting help
{: #help}

If you need help, join our developer community by posting your questions or comments to any of the following places, which are all actively monitored:
* Post on the [dwAnswers forum ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/topics/voice-agent/) with the `voice-agent` tag
* Post on [StackOverflow ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://stackoverflow.com/questions/tagged/voice-agent){: new_window} with the `voice-agent` tag
* Find us on Slack in the [IBM Cloud Technology ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) team under the `#ibmvoicegateway` channel

## Troubleshooting tips
{: #troubleshooting-tips}

### Why don't I get a response on the phone when I call my voice agent?

Your call likely didn't connect to the services. This problem occurs when the {{site.data.keyword.iva_short}} service instance isn't set up correctly. Check the following voice agent settings:

* Verify that the phone number on the voice agent _Manage_ dashboard is the same phone number from Twilio.

   **Note:** Phone numbers from Twilio include a country code such as `+1`. Include the country and area code when you specify the phone number on the voice agent _Manage_ dashboard; for example: `18884253968`.
* Verify that the Watson service credentials, URLs, and the {{site.data.keyword.conversationshort}} workspace ID are all valid.
* Verify that the dialog in your {{site.data.keyword.conversationshort}} workspace was created correctly.
  * You can import the [sample conversation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) from GitHub for a pre-built workspace. See [Step 3 in *Getting started tutorial*](getting-started.html#step3) for details on how to save the sample conversation as a JSON file and then import the file as a workspace in the {{site.data.keyword.conversationshort}} tool.
  * If you created your own {{site.data.keyword.conversationshort}} dialog, verify that the dialog at minimum contains a node with the `conversation_start` condition and node with a default response. For detailed instructions, see [Building a dialog](../conversation/dialog-build.html) in the {{site.data.keyword.conversationshort}} documentation.
* See whether your phone call is listed on the voice agent _Usage_ dashboard. If you see an item for your phone call, then your voice agent connected to the Watson service.

### Why can't I specify a phone number when I create a voice agent?

See if the phone number you specified is used by an existing voice agent. You can have only one voice agent for a phone number. You can provision another phone number from Twilio and use it to create another voice agent. Or [delete the existing voice agent on the _Manage_ dashboard](managing.html#delete_instance) to free up the phone number and then create a new voice agent.
