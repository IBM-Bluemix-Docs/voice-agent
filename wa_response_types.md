---

copyright:
  years: 2020
lastupdated: "2020-06-12"

keywords: Programming voice agents, watson assistant, response types

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Handling various {{site.data.keyword.conversationshort}} response types
{: #wa_response_types}


{{site.data.keyword.conversationfull}} supports various [response types](https://cloud.ibm.com/docs/assistant?topic=assistant-api-dialog-responses).

The {{site.data.keyword.iva_full}} supports the following response types:
 * `text`
 * `image`
 * `option`
 * `suggestion`

Each response type is specified using a different set of JSON properties. The properties included for each response will vary depending upon a response type.

`image`, `option`, and `suggestion` response types are available in {{site.data.keyword.vgw_short}} 1.0.6 and later.


## Response type `text`
{: #wa_response_type_text}

The `text` response type is used for ordinary text responses.

```json
{
  "output": {
    "generic": [
      {
        "response_type": "text",
        "text": "OK, you want to fly to Boston next Monday."
      }
    ]
  }
}
```
{:codeblock}

## Response type `image`
{: #wa_response_type_image}

The `image` response type instructs the client to display an image.

```json
{
  "output": {
    "generic":[
      {
        "response_type": "image",
        "source": "http://example.com/image.jpg"
      }
    ]
  }
}
```
{:codeblock}


The `image` response type can be used when SMS integration is enabled.

In the following example, the text message is sent to the user over the voice channel, while the image is sent over the SMS channel:

```json
{
  "output": {
    "generic": [
      {
        "response_type": "text",
        "text": "This is a test message."
      },
      {
        "response_type": "image",
        "source": "<url>"
      }
    ]
  }
}
```
{:codeblock}

This is equivalent to the following action sequence:

```json
{
  "output": {
    "vgwActionSequence": [
      {
        "command": "vgwActPlayText",
        "parameters": {
          "text": [
            "This is a test message."
          ]
        }
      },
      {
        "command": "vgwActSendSMS",
        "parameters": {
          "mediaURL": "http://example.com/image.jpg"
        }
      }
    ]
  }
}
```
{:codeblock}

If SMS integration is not enabled, the `image` response type is ignored in the {{site.data.keyword.iva_short}}.


## Response type `suggestion`
{: #wa_response_type_suggestion}


The `suggestion` response type is used by the disambiguation feature to suggest possible matches when it isn�t clear what the user wants to do. 
When disambiguation is enabled, your assistant asks the user for help when more than one dialog node can respond to the user's input. Instead of guessing which node to process, your assistant lists the top node options, and asks the user to pick the right one. (For more details about the disambiguation feature, see the Watson Assistant [documentation](https://cloud.ibm.com/docs/assistant?topic=assistant-dialog-runtime#dialog-runtime-disambiguation).)

Possible matching dialog nodes are listed using a `suggestion` response:

```json
{
  "output": {
    "generic": [
      {
        "response_type": "suggestion",
        "title": "Please choose one of the following options:",
        "suggestions": [
          {
            "label": "I'd like to order a drink.",
            "value": {
              "intents": [
                {
                  "intent": "order_drink",
                  "confidence": 0.7330395221710206
                }
              ],
              "entities": [],
              "input": {
                "suggestion_id": "576aba3c-85b9-411a-8032-28af2ba95b13",
                "text": "I want to place an order"
              }
            },
            "output": {
              "text": [
                "I'll get you a drink."
              ],
              "generic": [
                {
                  "response_type": "text",
                  "text": "I'll get you a drink."
                }
              ],
              "nodes_visited_details": [
                {
                  "dialog_node": "node_1_1547675028546",
                  "title": "order drink",
                  "user_label": "I'd like to order a drink.",
                  "conditions": "#order_drink"
                }
              ]
            },
            "source_dialog_node": "root"
          },
          {
            "label": "I need a drink refill.",
            "value": {
              "intents": [
                {
                  "intent": "refill_drink",
                  "confidence": 0.2529746770858765
                }
              ],
              "entities": [],
              "input": {
                "suggestion_id": "6583b547-53ff-4e7b-97c6-4d062270abcd",
                "text": "I need a drink refill"
              }
            },
            "output": {
              "text": [
                "I'll get you a refill."
              ],
              "generic": [
                {
                  "response_type": "text",
                  "text": "I'll get you a refill."
                }
              ],
              "nodes_visited_details": [
                {
                  "dialog_node": "node_2_1547675097178",
                  "title": "refill drink",
                  "user_label": "I need a drink refill.",
                  "conditions": "#refill_drink"
                }
              ]
            },
            "source_dialog_node": "root"
          }
        ]
      }
    ]
  }
}
```
{:codeblock}

Each suggestion includes a label that can be played to the user and a value specifying the input that should be sent back to the assistant if the user chooses the corresponding suggestion. By default, {{site.data.keyword.iva_short}} adds a number to the text specified in a `label`. Options are numbered sequentially and played to the user in the order in which they appear in the list. The user can use DTMFs or say the respective number to choose one of the available options. The list of options is introduced using the text specified by the `title` attribute of the `suggestion` response.

You can configure the text that will be prepended to each label using the `vgwActSetDisambiguationConfig` action. In the `prefixText` attribute, use `%s` to represent the number corresponding to the option; this is replaced with the actual number at run time.

**Note:** If a configuration is specified using the `vgwActSetDisambiguationConfig` action, the same settings are used each time disambiguation is triggered. It is recommended to specify this action in a root node.

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActSetDisambiguationConfig",
      "parameters": {
        "prefixText": "Press or say %s for.",
        "matchWord": ["one","two", "three","four","five"],
        "disableSpeech" : true
      }
    }
  }
}
```
{:codeblock}

For example, if label is configured as follows:

```
"label": "I'd like to order a drink."
```
By default, the {{site.data.keyword.iva_short}} will play to the user:

```
1. I'd like to order a drink.
```
If `prefixText` is set to `Press or say %s for`, {{site.data.keyword.iva_short}} will play to the user:

```
Press or say 1 for "I'd like to order a drink."
```

Voice Agent uses STT to match user utterances to the options in the list. By default, Voice Agent attempts to match the English words that correspond to the options (for example, `two` matches the second option). In other languages, the user must specify on the first conversation turn which match words to use in the preferred language. You can configure the match words to use using the `matchWord` attribute of the `vgwActSetDisambiguationConfig` action, specifying one match word per option. For example, if there are three options in the list, and the `matchWord` attribute is set to `["first", "middle", and "last"]`, the word "first" will match the first option in the list, the word "middle" will match the second option in the list, and so on.

By default, either voice or DTMF can be used to choose an option. You can use the `disableSpeech` attribute to disable voice and accept only DTMF for choosing one of the options in the list.

## Response type `option`
{: #wa_response_type_option}

The `option` response type allows the user to select from a list of options, and then send input back to the assistant based on the selected option:

```json
{
  "output": {
    "generic": [
      {
        "response_type": "option",
        "title": "Available options",
        "description": "Please select one of the following options:",
        "preference": "button",
        "options": [
          {
            "label": "Option 1",
            "value": {
              "input": {
                "text": "option 1"
              }
            }
          },
          {
            "label": "Option 2",
            "value": {
              "input": {
                "text": "option 2"
              }
            }
          }
        ]
      }
    ]
  }
}
```
{:codeblock}

The {{site.data.keyword.iva_short}} uses the same numbering approach as for a `suggestion` response. As in a `suggestion` response, you can change the default text that will be prepended to each `label` using the `vgwActSetOptionsConfig` action.

As with the `suggestion` response, the text specified by the `title` attribute is played first, followed by the text specified by the `label` attributes.

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActSetOptionsConfig",
      "parameters": {
        "prefixText": "Press or say %s for.",
        "matchWord": ["one","two", "three","four","five"],
        "disableSpeech" : true
      }
    }
  }
}
```
{:codeblock}

When the `vgwActSetOptionsConfig` is specified, the same settings are used for all `option` responses.
