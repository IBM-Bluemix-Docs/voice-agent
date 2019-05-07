---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 配置多个服务位置
{: #disaster-recovery}

您可以将语音代理程序连接到不同位置的多个服务来实现服务冗余。第二个位置并不是第二个语音代理程序，而只是用作备份。
{: shortdesc}

如果对您的语音代理程序实例使用_轻量_套餐，那么只能将您的 SIP 中继连接到一个端点，即您在其上创建了语音代理程序实例的端点。_轻量_套餐仅提供与一个位置的连接，因此只能为您所连接的服务提供冗余，而不能为您的语音代理程序提供冗余。如果您的语音代理程序位置发生服务中断，那么无法将呼叫定向到辅助位置。
{: tip}

## 添加冗余服务
{: #add_redundant}

您可以通过编辑语音代理程序，随时向语音代理程序配置中添加 Watson 或第三方服务位置。

1. 要向现有语音代理程序添加冗余服务，请导航到_管理_仪表板上的_语音代理程序_选项卡。针对要配置的语音代理程序，单击**编辑代理程序**。

1. 针对要连接的 {{site.data.keyword.conversationshort}}、{{site.data.keyword.texttospeechshort}} 或 {{site.data.keyword.speechtotextshort}} 服务，选择**位置 1** 或**位置 2**，然后添加您的配置信息。您可以使用您的工作空间或其他工作空间中的第三方服务或 Watson 服务实例。请参阅[使用其他 {{site.data.keyword.Bluemix_notm}} 工作空间中的服务实例](/docs/services/voice-agent?topic=voice-agent-other_service)。

**请记住**：对于服务冗余，您必须在不同服务地区的不同位置使用 Watson 服务实例。

您可以通过使用**启用位置**框启用或禁用位置。**位置 1** 在缺省情况下已启用，**位置 2** 在缺省情况下已禁用。对于每个 Watson 服务必须启用至少一个位置。

## 添加多个 Watson 服务位置
{: #add_location}

语音代理程序按地理位置的远近使用 Watson 服务实例。例如，您可以在华盛顿区域创建语音代理程序，而在达拉斯和澳大利亚的悉尼创建 {{site.data.keyword.conversationshort}} 服务。您的语音代理程序会使用 {{site.data.keyword.conversationshort}} 达拉斯区域，因为达拉斯在地理上比悉尼更靠近华盛顿。在多个地区连接 Watson 服务时，如果一个位置的 Watson 服务脱机，您的语音代理程序可以使用冗余服务。
