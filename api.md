---

copyright:
  years: 2017, 2020
lastupdated: "2020-03-13"

keywords: Programming voice agents, api, editing JSON

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Programming agents by using the API
{: #api}

You can control the behavior of your agent by defining action tags and state variables from within the {{site.data.keyword.conversationfull}} service. Action tags initiate actions that your agent takes during a conversation session, and state variables define agent characteristics that persist throughout the conversation unless otherwise changed.
{: shortdesc}

Because {{site.data.keyword.iva_full}} is based on IBM Voice Gateway, the API works the same way. If you're familiar with Voice Gateway and SMS Gateway, you can use the same actions and state variables in your {{site.data.keyword.conversationshort}} dialogs with {{site.data.keyword.iva_short}}. See [Action tags and state variables in the Voice Gateway API](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html) and [API for SMS Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/sms_api.html), respectively.
{: tip}

**Note:** By default, Watson Assistant service instances that are not part of Premium plans log requests and their results to improve the service for future users. To prevent IBM usage of data in this way, see [Data collection](https://cloud.ibm.com/apidocs/assistant/assistant-v2#data-collection) in the Watson Assistant API reference.

**Note:** Services which process data outside of IBM Voice Gateway require the ability to remove a customer's data from that service. For more information on labeling and deleting data in {{site.data.keyword.conversationshort}}, see: [Labeling and deleting data in the {{site.data.keyword.conversationshort}} service](https://cloud.ibm.com/docs/assistant?topic=assistant-information-security#information-security-gdpr-wa){: new_window}

## Editing JSON in the dialog response
{: #json-editor}

Both actions and states are defined in a dialog node response in JSON format. To edit the JSON code, open the JSON editor.

1. From the {{site.data.keyword.Bluemix_short}} dashboard, select your {{site.data.keyword.conversationshort}} service instance.
1. Launch the {{site.data.keyword.conversationshort}} tool.
1. Click the skill that contains the dialog you want to edit.
1. Go to the **Dialog** tab, and select the node where you want to set an action or state.
1. In the response, click the ![Advanced response](../conversation/images/kabob.png) icon, and select **Open JSON editor**.

Within the JSON editor, you can define actions on the `output` property and states on the `context` property as described in the following sections.

## Initiating actions
{: #defining-actions}

To initiate actions in the agent during a call, you can define action tags on a {{site.data.keyword.conversationshort}} dialog node in JSON format on the `output` property. You can define either a single action on the `vgwAction` tag or a sequence of actions on the `vgwActionSequence` tag. Each action consists of a `command` property, followed by an optional `parameter` property to define attributes for commands that require them.

### Single actions
{: #single-actions}

To perform a single action, define the action in the `vgwAction` tag with any necessary parameter attributes. In the `text` block in the `output` property, you can optionally include an utterance that the agent plays after the action is performed.

The following single action on the `vgwAction` tag tells the agent to hang up the call when the node response is triggered. Because the `vgwActHangup` command has no parameters, none are defined.
```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActHangup"
    }
  }
}
```
{: codeblock}

The following action tells the agent to collect dual-tone multi-frequency signaling (DTMF) input and to play the defined text to the caller.

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActCollectDtmf",
      "parameters": {
        "dtmfTermKey": "#"
      }
    },
    "text": {
      "values": [
        "Enter your phone number."
      ]
    }
  }
}
```
{: codeblock}

### Action sequences
{: #action-sequences}

To perform one or more actions on a single conversation turn, you can define a sequence of actions within the `vgwActionSequence` tag as a JSON list. The actions are performed in the order that you define them.

Unlike single actions, for the agent to play an utterance when it is using the `vgwActionSequence` tag, the list of actions must contain the `vgwActPlayText` action. In contrast to the `vgwAction` tag, an utterance in the `output.text` field is not automatically played.
{: tip}

In the following more complex example, the defined actions on the `vgwActionSequence` tag tell the agent to disable speech-to-text processing and collect DTMF input as it plays an utterance.

```json
{
  "output": {
    "vgwActionSequence": [
      {
        "command": "vgwActPauseSTT"
      },
      {
        "command": "vgwActCollectDtmf",
        "parameters": {
          "dtmfTermKey": "#"
        }
      },
      {
        "command": "vgwActPlayText",
        "parameters": {
          "text": [
            "Enter your social security number."
          ]
        }
      }
    ]
  }
}

```
{: codeblock}

## Setting states
{: #setting-states}

To indicate a change of state that remains between conversation turns, the agent exchanges state variables with the configured {{site.data.keyword.conversationfull}} service. These state variables are defined on a {{site.data.keyword.conversationshort}} dialog node as [context variables](/docs/assistant?topic=assistant-dialog-build#dialog-build) in JSON format.

For example, you can define following state variable to set the message that is streamed to the caller if the connection to the {{site.data.keyword.conversationshort}} service fails.

```json
{
  "context": {
    "vgwConversationFailedMessage": "Sorry, we're unable to connect you to our help line. Please try again later."
  }
}
```
{: codeblock}

The agent assumes that the {{site.data.keyword.conversationshort}} service is stateless and that all state is maintained at the agent between exchanges with the {{site.data.keyword.conversationshort}} service. For each conversation turn within a call, the state is passed to the {{site.data.keyword.conversationshort}} service and received back from the service in the `context` section of the REST messages.

## Configure STT Customization
{: #stt-customization}

You can configure and customize the Assitant in your {{site.data.keyword.conversationshort}} service to dynamically set the Speech-to-Text interactions during a call. Set up this configuration by using the Voice Gateway actions. See [Dynamically configuring Watson services](https://www.ibm.com/support/knowledgecenter/SS4U29/dynamicspeech.html) for more information. 
