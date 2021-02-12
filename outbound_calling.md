---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-30"

keywords: initiate, outbound calling

subcollection: "voice-agent"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}

# Initiating an outbound call
{: #init-outbound}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances. Existing instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

To make a new outbound call, make an HTTP POST request to the following endpoint:

```
https://apikey:<your_apikey>@{gateway}:443/vgw/outboundCalls/<<your-agent-number>>/startOutboundCall`
```

where `{gateway}` is either `gateway.voiceagent.cloud.ibm.com` (US South), `gateway-wdc.voiceagent.cloud.ibm.com` (US East), `gateway-fra04.voiceagent.cloud.ibm.com` or `gateway-fra05.voiceagent.cloud.ibm.com` (Frankfurt).

## Initiating an outbound call via cURL commands
{: #init-outbound-curl}

You can perform REST API operations by using the cURL command. Use the following request format:

`curl -X <HTTP request> -u 'apikey:<your_apikey>' --header 'Content-Type: application/json' --header 'Accept: application/json' -d <JSON data>`

HTTP Basic authentication is used to authorize a REST request. The username is `apikey` and `<your_apikey>` is a valid API key for your service instance. (To find the API key, go to the dashboard page for your service instance and click **Service credentials**.
{: note}

## Data for outbound call
{: #outbound-data}

Provide data in JSON format:

| Field Name             | Description      | 
|:-------------------|:-----------------|
| to |	A SIP or `tel` URI to be called. |
| from |	Optional. A calling party SIP or `tel` URI. |
| context |	Optional. A name/value pair of state variables to be forwarded to Watson Assistant when a call starts. |
| tenantConfig |	Optional. Configuration settings to be used for the call. |
| route |	Optional. A comma-separated list of SIP `Route` headers to be added to an outbound call. |
| statusWebhook |	Optional. A webhook to be used for asynchronous HTTP callbacks. Voice Gateway will use a webhook for sending notifications about the life cycle of the call. |
| statusWebhookUsername |	Optional. A username to be used for authentication when sending notifications to a webhook. |
| statusWebhookPassword |	Optional. A password to be used for authentication when sending notifications to a webhook. |
{: caption="Table 1. Actions that generate events" caption-side="top"}

An example cURL command would be:

```
curl -X POST -u 'apikey:<your_apikey>' --header 'Content-Type: application/json' --header 'Accept: application/json' \
   -d '{ "from": "sip:+<<your-agent-number>>@myTwilio.pstn.twilio.com",
         "to": "sip:+<<your-cell-number>>@myTwilio.pstn.twilio.com"}'  'https://gateway.voiceagent.cloud.ibm.com:443/vgw/outboundCalls/<<your-agent-number>>/startOutboundCall'
```

## SIP Authentication for outbound calling
{: #outbound-sip-auth}

{{site.data.keyword.iva_full}} supports SIP authentication for outbound calling. In order to provide credentials, add the following JSON object to the `tenantConfig`:

```
"config" : {
    "outboundCalls": {  
        "sipAuth": {  "username": "<<configured-username>>", "password": "<<configured-password>>" }
    }
}
```

The username and password here are the credentials that will be used with SIP providers and other external clients. It is not to be confused with the `apikey` credentials that are used to initiate a REST API call.

For example, in Twilio this would correspond to a credential defined in the _Authentication_ section under **Termination** from your _Elastic SIP Trunking_ dashboard.

  - In your Twilio account, navigate to the _Elastic SIP Trunking_ dashboard and select **Trunks**.
  
  - Choose the trunk that you want to configure and go to the **Termination** dashboard. In the _Authentication_ section you can configure a credential in the **Credentials List**.

  - If you do not specify a credential, then **you must** add an IP address to the **IP ACCESS CONTROL LISTS**. In other words, you must configure one of the _Authentication_ types. The IP address to use here would be the Voice agent outbound calling interface IP address. See [Networking Information](/docs/voice-agent?topic=voice-agent-networking_info).
  

An example cURL command would be:

```
curl -X POST -u 'apikey:<your_apikey>' --header 'Content-Type: application/json' --header 'Accept: application/json' \
   -d '{ "from": "sip:+<<your-twilio-number>>@myTwilio.pstn.twilio.com",
         "to": "sip:+<<your-cell-number>>@myTwilio.pstn.twilio.com",
         "tenantConfig": { 
            "config" : {
               "outboundCalls": {  
                  "sipAuth": {  "username": "<<configured-username>>", "password": "<<configured-password>>" }
               }
            }
         }
      }' 'https://gateway.voiceagent.cloud.ibm.com:443/vgw/outboundCalls/<<your-agent-number>>/startOutboundCall'
```

## More information

For the API documentation for outbound calling, see [IBM Voice Agent API Documentation](https://cloud.ibm.com/apidocs/voice-agent/outbound-api).

For more information, visit [IBM Voice Gateway Outbound Calling ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS4U29/apioutboundcalls.html).
