---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 配置多個服務位置
{: #disaster-recovery}

您可以將語音代理程式連接至不同位置中的多個服務，以進行服務備援。您的第二個位置不是第二個語音代理程式，它只會充當備份。
{: shortdesc}

如果您的語音代理程式實例使用_精簡_ 方案，則只能將 SIP 幹線連接至一個端點，也就是建立語音代理程式實例的端點。由於_精簡_ 方案只提供一個位置的連線，您可以為連線服務提供備援，但無法為語音代理程式提供備援。如果在語音代理程式位置發生服務中斷，通話無法導向第二個位置。
{: tip}

## 新增備援服務
{: #add_redundant}

您隨時可以藉由編輯語音代理程式，將 Watson 或協力廠商服務位置新增至語音代理程式配置。

1. 若要將備援服務新增至現有的語音代理程式，請導覽至_管理_ 儀表板上的_語音代理程式_ 標籤。針對您要配置的語音代理程式按一下**編輯代理程式**。

1. 針對您要連接的 {{site.data.keyword.conversationshort}}、{{site.data.keyword.texttospeechshort}} 或 {{site.data.keyword.speechtotextshort}} 服務選擇**位置 1** 或**位置 2**，然後新增配置資訊。您可以在您的工作區或其他工作區中使用協力廠商服務或 Watson 服務實例。請參閱[使用其他 {{site.data.keyword.Bluemix_notm}} 工作區中的服務實例](managing_other.html)。

**請記住**：針對服務備援，您必須在不同位置之不同服務地區中使用 Watson 服務實例。

您可以使用**啟用位置**方框來啟用或停用位置。依預設會啟用**位置 1**，而依預設會停用**位置 2**。必須為每一個 Watson 服務啟用至少一個位置。

## 新增多個 Watson 服務位置
{: #add_location}

您的語音代理程式會依地理距離的順序來使用 Watson 服務實例。例如，您可以在「華盛頓特區」地區建立語音代理程式，以及在「達拉斯」及「澳洲雪梨」建立您的 {{site.data.keyword.conversationshort}} 服務。您的語音代理程式會使用 {{site.data.keyword.conversationshort}}「達拉斯」地區，因為「達拉斯」在地理位置上比起「雪梨」更接近「華盛頓特區」。藉由連接至多個地區中的 Watson 服務，如果 Watson 服務在某個位置離線，則語音代理程式可以使用備用服務。
