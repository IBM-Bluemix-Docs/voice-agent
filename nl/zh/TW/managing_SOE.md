---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 使用服務編排引擎配置 {{site.data.keyword.conversationshort}}
{: #conversation_va}

除了配置 {{site.data.keyword.conversationshort}} 服務實例之外，您還可以連接至服務編排引擎 (SOE)。
{: shortdesc}

您可以透過[服務編排引擎 (SOE)](about.html#arch-soe)連接至 {{site.data.keyword.conversationshort}} 工作區。SOE 會將訊息截取至服務並從中截取訊息，讓您可以使用協力廠商 API 進行修改。

## 配置 SOE 的連線
{: #how-to}

1. 在語音代理程式的_管理_ 頁面上的_語音代理程式_ 標籤，導覽至 {{site.data.keyword.conversationshort}} 配置區段。

1. 選擇**服務編排引擎**作為您的**服務類型**。

1. 針對**服務類型**，選取**地區**。

1. 在 **URL** 欄位中，輸入 SOE 工作區的完整 URL（例如 `https://iva-soesample.myorg.net/SOE/myWorkspace`）。

  **重要事項**：為了資料安全，請確定針對 SOE 工作區使用安全的 URL，方法是使用 `https:` 而不要使用 `http:`，並且要求鑑別。若要進一步瞭解安全考量，請參閱[資訊安全及資料隱私](infosec.html)。

1. **選用**：如果您的 SOE 需要鑑別（建議），則請在個別欄位中輸入使用者名稱及密碼。
