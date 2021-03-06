---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-08"

keywords: state variables, action tags, api reference, DTMF

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

# Action tags and state variables in the API
{: #api-reference}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances. Existing instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}


Use the reference materials to find action tags or state variables. Action tags initiate actions that your agent takes during a conversation session. State variables define agent characteristics that persist throughout the conversation unless otherwise changed.
{: shortdesc}

See [Programming agents using the API](/docs/voice-agent?topic=voice-agent-api) for code examples and examples of how to set states and initiate action sequences.

Because {{site.data.keyword.iva_full}} is based on IBM Voice Gateway, the API works the same way. If you're familiar with Voice Gateway, you can use the same actions and state variables in your {{site.data.keyword.conversationshort}} dialogs with {{site.data.keyword.iva_short}}. See [Action tags and state variables in the Voice Gateway API](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html).
{: tip}

## Action commands and attributes
{: #actions-and-attributes}

The following table lists the actions that you can specify in the {{site.data.keyword.conversationshort}} dialog and any attributes that you can define for each action.

| Action Command | Description | Attributes |
| ----- | ----- | ----- |
| `vgwActPlayText`| Plays an utterance that is converted to speech by the {{site.data.keyword.texttospeechshort}} service. | `text`: A list of utterances to play. Optional. <p>For example:<br><code>"text": [<br/>&nbsp;&nbsp;&nbsp;"Hello. How can I help you today?"<br/>&nbsp;&nbsp;&nbsp;]</code><p> By default, the action plays a list of utterances that are configured in the `output.text` field. <br><br>`errAudioURL`: A URL to an audio file that is played if the agent cannot contact the {{site.data.keyword.texttospeechshort}} service to complete the action. The audio file must be in WAV format.|
| `vgwActPlayUrl` | Plays an audio file as soon as the included text is played back, such as for playing music on hold (MOH) or common one-time utterances. If no text is included, the audio is played immediately. The file must be single channel (mono), PCM-encoded, and have a 8,000 Hz sampling rate with 16 bits per sample. | `url`: The URL to play. Required.<br><br> `playURLInLoop`: Optionally set to `Yes` or `No` to indicate whether to play the URL in a loop. The default value is `No`.|
| `vgwActHangup` | Hangs up the call. | No attributes. |
| `vgwActSetSTTConfig` | Applies a set of parameters for the agent to pass to the Watson {{site.data.keyword.speechtotextshort}} service. The {{site.data.keyword.conversationshort}} service dynamically defines the parameters based on the call. | Attributes are transparently passed as JSON properties to the {{site.data.keyword.speechtotextshort}} service. |
| `vgwActSetTTSConfig` | Applies a set of parameters for the agent to pass to the Watson {{site.data.keyword.texttospeechshort}} service. The {{site.data.keyword.conversationshort}} service dynamically defines the parameters based on the call. |  Attributes are transparently passed as JSON properties to the {{site.data.keyword.texttospeechshort}} service.  |
| `vgwActSetConversationConfig` | Applies a set of parameters for the agent to define a {{site.data.keyword.conversationshort}} workspace. The {{site.data.keyword.conversationshort}} service dynamically defines the parameters based on the call. | `url`: The `url` credential for the {{site.data.keyword.conversationshort}} service API.<br><br>`workspaceID`: {{site.data.keyword.conversationshort}} workspace ID<br><br>`username`: The `username` credential for the {{site.data.keyword.conversationshort}} service, up to 64 characters.<br><br>`password`: The `password` credential for the {{site.data.keyword.conversationshort}} service, up to 256 characters. |
| `vgwActCollectDtmf` | Instructs the agent to collect dual-tone multi-frequency signaling (DTMF) input. | One of the following attributes must be defined. <br> `dtmfTermKey`: The DTMF termination key, which signals the end of DTMF input. For example, "`#`". <br><br> `dtmfCount`: The number of DTMF digits to collect.<br><br> When either of these conditions is met, the agent stops collecting DTMF input. |
| `vgwActPauseDTMF` | Disables DTMF input. All DTMF input is ignored until it is reenabled by the `vgwActUnPauseDTMF` action. | No attributes. |
| `vgwActUnPauseDTMF` | Enables the DTMF input that was disabled by the `vgwActPauseDTMF` action. | No attributes. |
| `vgwActExcludeFromTTSCache` | Instructs the agent to not cache the response from the {{site.data.keyword.texttospeechshort}} service. For example, responses that contain sensitive PHI, PII, and PCI DSS data or dynamic information such as customer names or birth dates should be excluded. <br/>This action tag must be set on the {{site.data.keyword.conversationshort}} dialog node for each utterance that you do not want to cache. | No attributes. |
| `vgwActPauseSTT` | Pauses speech-to-text processing until it is reenabled by the `vgwActUnPauseSTT` action. If recording is enabled and speech-to-text processing is paused, the audio from the caller is not captured. | No attributes. |
| `vgwActUnPauseSTT` | Resumes speech-to-text processing that was previously paused by the `vgwActPauseSTT` action. | No attributes. |
| `vgwActEnableSpeechBargeIn` | Enables speech barge-in so that callers can interrupt playback from the agent by speaking. | No attributes. |
| `vgwActDisableSpeechBargeIn` | Disables speech barge-in so that playback from the agent is not interrupted when callers speak. | No attributes. |
| `vgwActEnableDTMFBargeIn`| Enables DTMF barge-in so that callers can interrupt playback from the agent by pressing a key. | No attributes. |
| `vgwActDisableDTMFBargeIn` | Disables DTMF barge-in so that playback from the agent is not interrupted when callers press keys. | No attributes. |
| `vgwActForceNoInputTurn` | Forces a new turn in the conversation without waiting for input from the caller. | No attributes. |
{: caption="Table 1. Actions that you can initiate from the {{site.data.keyword.conversationshort}} service" caption-side="top"}

## State variables set in the {{site.data.keyword.conversationshort}} dialog
{: #state-variables-conv}

You can set the following state variables within the {{site.data.keyword.conversationshort}} dialog to modify your agent's behavior.

| State Variable Name | Expected Value | Description |
| -------------- | ------ | ----------- |
| `vgwByeCustomHeader` | User defined | Defines a custom header in an outgoing SIP BYE message. The custom header value is defined by the `vgwByeCustomHeaderVal` state variables.  |
| `vgwByeCustomHeaderVal` | User defined | Defines the value of a custom header in an outgoing SIP BYE message. The custom header is defined by the `vgwByeCustomHeader` state variables. |
| `vgwPostResponseTimeoutCount` | Time in milliseconds | The amount of time to wait for a new utterance after the response is played back to the caller. If this value is exceeded, the {{site.data.keyword.conversationshort}} receives a text update with the word "vgwPostResponseTimeout" to indicate that a timeout occurred.|
| `vgwConversationFailedMessage` | Text string | Message streamed to the caller if the {{site.data.keyword.conversationshort}} service fails. Configure your {{site.data.keyword.conversationshort}} dialog to set this variable on the first turn. |
| `vgwSessionInactivityTimeout` | Time in minutes <br/><br/>Default: `2` | The inactivity timeout interval. The timeout interval value specifies in minutes how long the agent allows a session to be inactive. When the timeout expires, the agent ends the session. |
| `vgwErrAudioURL` | User defined | A URL to an audio file that is played if the {{site.data.keyword.texttospeechshort}} service cannot be contacted when the agent attempts to play back a response. The audio file must be in WAV format. |
{: caption="Table 2. Variables set by the {{site.data.keyword.conversationshort}} service" caption-side="top"}

## State variables set by the agent
{: #state-variables-iva}

| State Variable Name | Expected Value | Description |
| -------------- | ----- | ----------- |
| `vgwSessionID`   | User defined <br/><br/> Default: `Call-ID` | A custom session ID header that is pulled from the SIP INVITE request. The value represents the global session ID that is used in all the agent audit logs related to the session. |
| `vgwSIPCallID` | SIP `Call-ID` | The SIP call ID associated with the call. |
| `vgwSIPRequestURI` | SIP `Request-URI` | The SIP request URI that started the call. |
| `vgwSIPToURI` | SIP `To` URI | The SIP `To` URI associated with the call. |
| `vgwSIPFromURI` | SIP `From` URI | The SIP `From` URI associated with the call. |
| `vgwBargeInOccurred` | `Yes` / `No` | Indicates whether or not barge-in occurred. |
| `vgwHangUp` | `Yes` / `No` | Indicates whether the conversation was ended. |
| `vgwHangupReason` | String | When a hang up is initiated either by the caller or because of an error, this variable is sent to the {{site.data.keyword.conversationshort}} service to indicate why the call was disconnected. The text in the message request that is sent to the {{site.data.keyword.conversationshort}} service also includes "vgwHangUp". |
| `vgwConversationResponseTimeout` | Time in seconds<br/><br/>Default: `5`  | The time in seconds that the agent waits for a response from the {{site.data.keyword.conversationshort}} service. If the time is exceeded, the agent reattempts to contact the {{site.data.keyword.conversationshort}} service. If the service still cannot be reached, the call fails. |
| `vgwSTTResponse` | JSON object | The final response from the {{site.data.keyword.speechtotextshort}} service in JSON format, including the transcript and confidence score for the preferred hypothesis and any alternatives. <p>For example, the following format matches exactly the format that is received from the {{site.data.keyword.speechtotextshort}} service:</p><p><code>{<br/>&nbsp;&nbsp;"result_index": 0,<br/>&nbsp;&nbsp;"warnings": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;"Unknown arguments: continuous."<br/>&nbsp;&nbsp;],<br/>&nbsp;&nbsp;"results": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"final": true,<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"alternatives": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello world",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.758<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello wooled",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.358<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;]<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}.</code></p> |
| `vgwIsDTMF` | `Yes` / `No` | Indicates whether the input to the {{site.data.keyword.conversationshort}} service is dual-tone multi-frequency signaling (DTMF). |
{: caption="Table 3. Variables set by the agent" caption-side="top"}
