---

copyright:
  years: 2019, 2020
lastupdated: "2020-02-28"

keywords: networking ip address
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

# Networking Information
{: #networking_info}

{{site.data.keyword.iva_full_notm}} is deprecated. As of 1 March 2021, you can't create new instances. Existing instances are supported until 31 December 2021. Any instance that still exists on that date will be deactivated. For more information, see the deprecation announcement [blog post](https://community.ibm.com/community/user/watsonapps/blogs/mitch-mason1/2021/02/08/announcing-voice-agent-with-watson-deprecation){: external}. You can use {{site.data.keyword.conversationfull}} integrations to enable voice and SMS interaction with your cognitive assistant. See the migration instructions for the {{site.data.keyword.conversationshort}} [phone integration](/docs/assistant?topic=assistant-deploy-phone#deploy-phone-migrate-from-va){: external} and [SMS with Twilio integration](/docs/assistant?topic=assistant-deploy-sms#deploy-sms-migrate-from-va){: external}.
{: deprecated}

## Voice agent endpoint IP addresses
{: #ip-address}

    | Dallas (US South)       | Washington DC (US East) |
    | ----------------------- | ----------------------- |
    | 169.61.56.226           | 169.62.26.42            |

    | Frankfurt 4             | Frankfurt 5             |
    | ----------------------- | ----------------------- |
    | 161.156.70.250          | 149.81.130.34           |

## Voice agent outbound calling interface IP addresses
{: #outbound-ip-address}

    | Dallas (US South)       | Washington DC (US East) |
    | ----------------------- | ----------------------- |
    | 169.59.10.204           | 169.61.70.83            |

    | Frankfurt 4             | Frankfurt 5             |
    | ----------------------- | ----------------------- |
    | 161.156.70.251          | 149.81.130.35           |

## Voice agent Vyatta IP addresses
{: #vyatta-ip-address}

    | Dallas (US South)       | Washington DC (US East) |
    | ----------------------- | ----------------------- |
    | 169.60.155.11           | 169.61.102.99           |
    | 169.60.155.13           | 169.61.102.101          |
    | ----------------------- | ----------------------- |
    | Subnet                  | Subnet                  |
    | ----------------------- | ----------------------- |
    | 169.60.155.8/29         | 169.61.102.96/29        |

    | Frankfurt 4             | Frankfurt 5             |
    | ----------------------- | ----------------------- |
    | 161.156.121.115         | 149.81.78.106           |
    | 161.156.121.118         | 149.81.78.109           |
    | ----------------------- | ----------------------- |
    | Subnet                  | Subnet                  |
    | ----------------------- | ----------------------- |
    | 161.156.121.112/29      | 149.81.78.104/29        |
