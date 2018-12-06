---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 使用其他 {{site.data.keyword.Bluemix_notm}} 工作區中的服務實例
{: #other_service}

您可以將語音代理程式配置成使用 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.speechtotextshort}} 服務實例，而這些服務實例屬於其他 {{site.data.keyword.Bluemix_short}} 帳戶中的工作區。
{: shortdesc}

若要將語音代理程式連接至其他服務實例，您可以使用服務實例的使用者名稱及密碼認證或 API 金鑰。

1. 在_管理_ 儀表板上的_語音代理程式_ 標籤，選取**建立新的語音代理程式**或您要編輯的語音代理程式。

1. 在 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.speechtotextshort}}中，針對您的**服務類型**選取**其他服務實例**，然後選取**地區**。

1. 選擇**使用者名稱及密碼**或 **API 金鑰**，然後輸入服務認證。若要尋找這些值，請移至您要配置的服務實例，選取**服務認證**，然後選取**檢視認證**。

  * **使用者名稱及密碼**：在 **URL**、**使用者名稱**及**密碼**欄位中，配置 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.texttospeechshort}} 服務實例的認證。
  * **API 金鑰**：在 **URL** 及 **API 金鑰**欄位中，配置 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.texttospeechshort}} 服務實例的認證。

  認證不是您的 {{site.data.keyword.Bluemix_notm}} 使用者名稱及密碼，而是特定服務實例的加密認證。
{:tip}

1. 輸入服務實例資訊。

  * **{{site.data.keyword.conversationshort}}：**在**工作區 ID** 欄位中，輸入您要與語音代理程式搭配使用的工作區 ID。若要尋找工作區 ID，請啟動工具，並在您要整合的工作區上，按一下「動作」圖示 (**&vellip;**)，然後選取**檢視詳細資料**。
  * **{{site.data.keyword.speechtotextshort}}：**針對**選取模型類型**，選擇**窄頻**、**寬頻**或**窄頻與寬頻**，然後選取語言**模型**。
  * **{{site.data.keyword.texttospeechshort}}：**在**語音**欄位中，選取服務所使用的語言及語音。您必須指定服務的語音。

**請記住：**為了讓您的語音代理程式運作，您必須配置相同語言的 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 及 {{site.data.keyword.texttospeechshort}}。請參閱[支援的語言](about.html#supported-languages)。
