---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Programming voice agents using the API
{: #api}

You can control the behavior of your voice agent by defining action tags and state variables from within the {{site.data.keyword.conversationfull}} service. Action tags initiate actions that your voice agent takes during a conversation session, and state variables define voice agent characteristics that persist throughout the conversation unless otherwise changed.
{: shortdesc}

Because {{site.data.keyword.iva_full}} is based on IBM Voice Gateway, the API works the same way. If you're familiar with Voice Gateway, you can use the same actions and state variables in your {{site.data.keyword.conversationshort}} dialogs with {{site.data.keyword.iva_short}}. See [Action tags and state variables in the Voice Gateway API](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html).
{: tip}

## Editing JSON in the dialog response
{: #json-editor}

Both actions and states are defined in a dialog node response in JSON format. To edit the JSON code, open the JSON editor.

1. From the {{site.data.keyword.Bluemix_short}} dashboard, select your {{site.data.keyword.conversationshort}} service instance.
1. Launch the {{site.data.keyword.conversationshort}} tool.
1. Click the workspace that contains the dialog you want to edit.
1. Go to the **Dialog** tab, and select the node where you want to set an action or state.
1. In the response, click the ![Advanced response](../conversation/images/kabob.png) icon, and select **Open JSON editor**.

Within the JSON editor, you can define actions on the `output` property and states on the `context` property as described in the following sections.

## Initiating actions
{: #defining-actions}

To initiate actions in the voice agent during a call, you can define action tags on a {{site.data.keyword.conversationshort}} dialog node in JSON format on the `output` property. You can define either a single action on the `vgwAction` tag or a sequence of actions on the `vgwActionSequence` tag. Each action consists of a `command` property, followed by an optional `parameter` property to define attributes for commands that require them.

### Single actions
{: #single-actions}

To perform a single action, define the action in the `vgwAction` tag with any necessary parameter attributes. In the `text` block in the `output` property, you can optionally include an utterance that the voice agent plays after the action is performed.

The following single action on the `vgwAction` tag tells the voice agent to hang up the call when the node response is triggered. Because the `vgwActHangup` command has no parameters, none are defined.
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

The following action tells the voice agent to collect dual-tone multi-frequency signaling (DTMF) input and to play the defined text to the caller.

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

Unlike single actions, for the voice agent to play an utterance when using the `vgwActionSequence` tag, the list of actions must contain the `vgwActPlayText` action. In contrast to the `vgwAction` tag, an utterance in the `output.text` field is not automatically played.
{: tip}

In the following more complex example, the defined actions on the `vgwActionSequence` tag tell the voice agent to disable speech-to-text processing and collect DTMF input as it plays an utterance.

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


### Action commands and attributes
{: #actions-and-attributes}

The following table lists the actions that you can specify in the {{site.data.keyword.conversationshort}} dialog and any attributes that you can define for each action.

| Action command | Description | Attributes |
| ----- | ----- | ----- |
| `vgwActPlayText`| Plays an utterance that is converted to speech by the {{site.data.keyword.texttospeechshort}} service. | <ul><li>`text`: A list of utterances to play. Optional. <p>For example:<br/><code>"text": [<br/>&nbsp;&nbsp;&nbsp;"Hello. How can I help you today?"<br/>&nbsp;&nbsp;&nbsp;]</code><p> By default, the action plays a list of utterances that are configured in the `output.text` field. </li><li>`errAudioURL`: A URL to an audio file that is played if the voice agent cannot contact the {{site.data.keyword.texttospeechshort}} service to complete the action. The audio file must be in WAV format.</li></ul>|
| `vgwActPlayUrl` | Plays an audio file as soon as the included text is played back, such as for playing music on hold (MOH) or common one-time utterances. If no text is included, the audio is played immediately. The file must be single channel (mono), PCM-encoded, and have a 8,000 Hz sampling rate with 16 bits per sample. | <ul><li>`url`: The URL to play. Required.</li><li> `playURLInLoop`: Optionally set to `Yes` or `No` to indicate whether to play the URL in a loop. The default value is `No`.</li></ul> |
| `vgwActHangup` | Hangs up the call. | No attributes. |
| `vgwActSetSTTConfig` | Applies a set of parameters for the voice agent to pass to the Watson {{site.data.keyword.speechtotextshort}} service. The {{site.data.keyword.conversationshort}} service dynamically defines the parameters based on the call. | Attributes are transparently passed as JSON properties to the {{site.data.keyword.speechtotextshort}} service. |
| `vgwActSetTTSConfig` | Applies a set of parameters for the voice agent to pass to the Watson {{site.data.keyword.texttospeechshort}} service. The {{site.data.keyword.conversationshort}} service dynamically defines the parameters based on the call. |  Attributes are transparently passed as JSON properties to the {{site.data.keyword.texttospeechshort}} service.  |
| `vgwActSetConversationConfig` | Applies a set of parameters for the voice agent to define a {{site.data.keyword.conversationshort}} workspace. The {{site.data.keyword.conversationshort}} service dynamically defines the parameters based on the call. | <ul><li>`url`: The `url` credential for the {{site.data.keyword.conversationshort}} service API.</li><li>`workspaceID`: {{site.data.keyword.conversationshort}} workspace ID</li><li>`username`: The `username` credential for the {{site.data.keyword.conversationshort}} service.</li><li>`password`: The `password` credential for the {{site.data.keyword.conversationshort}} service.</li></ul> |
| `vgwActCollectDtmf` | Instructs the voice agent to collect dual-tone multi-frequency signaling (DTMF) input. | One of the following attributes must be defined. <ul><li> `dtmfTermKey`: The DTMF termination key, which signals the end of DTMF input. For example, "`#`". </li><li> `dtmfCount`: The number of DTMF digits to collect.</li></ul> When either of these conditions is met, the voice agent stops collecting DTMF input. |
| `vgwActPauseDTMF` | Disables DTMF input. All DTMF input is ignored until it is reenabled by the `vgwActUnPauseDTMF` action. | No attributes. |
| `vgwActUnPauseDTMF` | Enables the DTMF input that was disabled by the `vgwActPauseDTMF` action. | No attributes. |
| `vgwActExcludeFromTTSCache` | Instructs the voice agent to not cache the response from the {{site.data.keyword.texttospeechshort}} service. For example, responses that contain sensitive PHI, PII, and PCI DSS data or dynamic information such as customer names or birth dates should be excluded. <br/>This action tag must be set on the {{site.data.keyword.conversationshort}} dialog node for each utterance that you do not want to cache. | No attributes. |
| `vgwActPauseSTT` | Pauses speech-to-text processing until it is reenabled by the `vgwActUnPauseSTT` action. If recording is enabled and speech-to-text processing is paused, the audio from the caller is not captured. | No attributes. |
| `vgwActUnPauseSTT` | Resumes speech-to-text processing that was previously paused by the `vgwActPauseSTT` action. | No attributes. |
| `vgwActEnableSpeechBargeIn` | Enables speech barge-in so that callers can interrupt playback from the voice agent by speaking. | No attributes. |
| `vgwActDisableSpeechBargeIn` | Disables speech barge-in so that playback from the voice agent is not interrupted when callers speak. | No attributes. |
| `vgwActEnableDTMFBargeIn`| Enables DTMF barge-in so that callers can interrupt playback from the voice agent by pressing a key. | No attributes. |
| `vgwActDisableDTMFBargeIn` | Disables DTMF barge-in so that playback from the voice agent is not interrupted when callers press keys. | No attributes. |
| `vgwActForceNoInputTurn` | Forces a new turn in the conversation without waiting for input from the caller. | No attributes. |
{: caption="Table 1. Actions that you can initiate from the {{site.data.keyword.conversationshort}} service" caption-side="top"}

## Setting states
{: #setting-states}

To indicate a change of state that remains between conversation turns, the voice agent exchanges state variables with the configured {{site.data.keyword.conversationfull}} service. These state variables are defined on a {{site.data.keyword.conversationshort}} dialog node as [context variables](https://console.bluemix.net/docs/services/conversation/dialog-build.html#context) in JSON format.

For example, you can define following state variable to set the message that is streamed to the caller if the connection to the  {{site.data.keyword.conversationshort}} service fails.

```json
{
  "context": {
    "vgwConversationFailedMessage": "Sorry, we're unable to connect you to our help line. Please try again later."
  }
}
```
{: codeblock}

The voice agent assumes that the {{site.data.keyword.conversationshort}} service is stateless and that all state is maintained at the voice agent between exchanges with the {{site.data.keyword.conversationshort}} service. For each conversation turn within a call, the state is passed to the {{site.data.keyword.conversationshort}} service and received back from the service in the `context` section of the REST messages.

### State variables set in the {{site.data.keyword.conversationshort}} dialog
{: #state-variables-conv}

You can set the following state variables within the {{site.data.keyword.conversationshort}} dialog to modify your voice agent's behavior.

| State variable name | Expected value | Description |
| -------------- | ------ | ----------- |
| `vgwByeCustomHeader` | User defined | Defines a custom header in an outgoing SIP BYE message. The custom header value is defined by the `vgwByeCustomHeaderVal` state variables.  |
| `vgwByeCustomHeaderVal` | User defined | Defines the value of a custom header in an outgoing SIP BYE message. The custom header is defined by the `vgwByeCustomHeader` state variables. |
| `vgwPostResponseTimeoutCount` | Time in milliseconds | The amount of time to wait for a new utterance after the response is played back to the caller. If this value is exceeded, the {{site.data.keyword.conversationshort}} receives a text update with the word "vgwPostResponseTimeout" to indicate that a timeout occurred.|
| `vgwConversationFailedMessage` | Text string | Message streamed to the caller if the {{site.data.keyword.conversationshort}} service fails. Configure your {{site.data.keyword.conversationshort}} dialog to set this variable on the first turn. |
| `vgwSessionInactivityTimeout` | Time in minutes <br/><br/>Default: `2` | The inactivity timeout interval. The timeout interval value specifies in minutes how long the voice agent allows a session to be inactive. When the timeout expires, the voice agent ends the session. |
| `vgwErrAudioURL` | User defined | A URL to an audio file that is played if the {{site.data.keyword.texttospeechshort}} service cannot be contacted when the voice agent attempts to play back a response. The audio file must be in WAV format. |
{: caption="Table 2. Variables set by the {{site.data.keyword.conversationshort}} service" caption-side="top"}

### State variables set by the voice agent
{: #state-variables-iva}

| State variable name | Expected value | Description |
| -------------- | ----- | ----------- |
| `vgwSessionID`   | User defined <br/><br/> Default: `Call-ID` | A custom session ID header that is pulled from the SIP INVITE request. The value represents the global session ID that is used in all the voice agent audit logs related to the session. |
| `vgwSIPCallID` | SIP `Call-ID` | The SIP call ID associated with the call. |
| `vgwSIPRequestURI` | SIP `Request-URI` | The SIP request URI that started the call. |
| `vgwSIPToURI` | SIP `To` URI | The SIP `To` URI associated with the call. |
| `vgwSIPFromURI` | SIP `From` URI | The SIP `From` URI associated with the call. |
| `vgwBargeInOccurred` | `Yes` / `No` | Indicates whether or not barge-in occurred. |
| `vgwHangUp` | `Yes` / `No` | Indicates whether the conversation was ended. |
| `vgwHangupReason` | String | When a hang up is initiated either by the caller or because of an error, this variable is sent to the {{site.data.keyword.conversationshort}} service to indicate why the call was disconnected. The text in the message request that is sent to the {{site.data.keyword.conversationshort}} service also includes "vgwHangUp". |
| `vgwConversationResponseTimeout` | Time in seconds<br/><br/>Default: `5`  | The time in seconds that the voice agent waits for a response from the {{site.data.keyword.conversationshort}} service. If the time is exceeded, the voice agent reattempts to contact the {{site.data.keyword.conversationshort}} service. If the service still cannot be reached, the call fails. |
| `vgwSTTResponse` | JSON object | The final response from the {{site.data.keyword.speechtotextshort}} service in JSON format, including the transcript and confidence score for the preferred hypothesis and any alternatives. <p>For example, the following format matches exactly the format that is received from the {{site.data.keyword.speechtotextshort}} service:</p><p><code>{<br/>&nbsp;&nbsp;"result_index": 0,<br/>&nbsp;&nbsp;"warnings": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;"Unknown arguments: continuous."<br/>&nbsp;&nbsp;],<br/>&nbsp;&nbsp;"results": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"final": true,<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"alternatives": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello world",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.758<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello wooled",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.358<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;]<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}.</code></p> |
| `vgwIsDTMF` | `Yes` / `No` | Indicates whether the input to the {{site.data.keyword.conversationshort}} service is dual-tone multi-frequency signaling (DTMF). |
{: caption="Table 3. Variables set by the voice agent" caption-side="top"}
