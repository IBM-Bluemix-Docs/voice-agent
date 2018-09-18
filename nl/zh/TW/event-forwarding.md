---

copyright:
  years: 2018
lastupdated: "2018-08-24"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 啟用語音代理程式的事件轉遞
{: #event_forwarding}

您可以啟用事件轉遞，使用 {{site.data.keyword.cloudantfull}} 資料庫服務來收集 {{site.data.keyword.iva_full}} 中語音代理程式所處理通話的相關資訊。
{: shortdesc}

您可能想要收集及分析來自 {{site.data.keyword.iva_short}} 的通話資料，以改善交談對來電者的自然程度。您建立的每一個語音代理程式都可以將事件報告轉遞至您管理的指定 {{site.data.keyword.cloudant_short_notm}}。報告的事件包括通話詳細記錄 (CDR) 事件、轉錄事件及回合事件報告。您可以在[報告事件](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}中進一步瞭解您可轉遞的事件類型。

分析來自這些事件的資料可協助您調整對話、修正目的，以及改善整體來電者體驗。

當您建立或編輯語音代理程式時，也可以選擇啟用事件轉遞。如需建立及編輯語音代理程式的詳細資料，請參閱[管理語音代理程式](managing.html)。您需要提供 {{site.data.keyword.cloudant_short_notm}} 帳戶資訊（包括帳戶名稱及密碼），才能啟用事件轉遞。

**重要事項：**CDR、轉錄及回合事件包括使用者的資訊，而這些資訊可能包含「受保護健康資訊 (PHI)」、個人識別資訊 (PII) 或「PCI 資料安全標準 (PCI DSS)」資料。若要防止公開個人資訊，您必須確保 {{site.data.keyword.cloudant_short_notm}} 實例適當地保護使用者在交談中或交談期間分享的機密資訊。請參閱[資訊安全及資料隱私：事件轉遞](infosec.html#event_forwarding)和 [{{site.data.keyword.cloudant_short_notm}}：安全](../Cloudant/offerings/security.html#security)。


## 啟用事件轉遞
{: #enable-event-forwarding}

在 {{site.data.keyword.Bluemix_short}} 的_管理_ 儀表板中建立或編輯語音代理程式時，可以啟用事件轉遞。

1. 在**事件轉遞**區段中，於 {{site.data.keyword.texttospeechshort}} 的配置區段之後，選取**啟用事件轉遞**。

1. 選取**我的 {{site.data.keyword.cloudant_short_notm}} 服務實例**或**其他 {{site.data.keyword.cloudant_short_notm}} 服務實例**。
  * 如果您使用**我的 {{site.data.keyword.cloudant_short_notm}} 服務實例**，請從清單中選取 **{{site.data.keyword.cloudant_short_notm}} 帳戶**名稱及使用者名稱。
  * 如果您使用**其他 {{site.data.keyword.cloudant_short_notm}} 服務實例**，請輸入帳戶的 {{site.data.keyword.cloudant_short_notm}} 使用者名稱及密碼，或是 API 金鑰。

1. 針對您要轉遞的每一種事件類型，選取**啟用**，然後選擇您要轉遞事件的資料庫。
  * 通話詳細記錄 (CDR) 事件
  * 轉錄事件
  * 回合事件

1. 檢視資料庫，以確保正確地轉遞事件報告。

## 相關鏈結
* [IBM Voice Gateway：報告事件](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
* [資訊安全及資料隱私](infosec.html)
* [{{site.data.keyword.cloudant_short_notm}}：安全](../Cloudant/offerings/security.html#security)
