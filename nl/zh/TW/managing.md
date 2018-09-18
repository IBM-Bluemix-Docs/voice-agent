---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-29"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 管理語音代理程式
{: #managing}

您可以在_管理_ 儀表板上建立、編輯、複製、配置及移除語音代理程式。您可以有多個語音代理程式，但每一個語音代理程式都必須要有唯一名稱及電話號碼。
{: shortdesc}

<!-- Title should be task oriented and descriptive-->

## 建立語音代理程式
{: #config_instance}

當您建立語音代理程式時，{{site.data.keyword.iva_short}} 會自動搜尋您可使用的任何可用 Watson 服務實例。如果服務無法使用，您可以選擇將其與語音代理程式一起建立，或連接至不同 {{site.data.keyword.Bluemix_short}} 帳戶空間中的服務。

1. 按一下**建立語音代理程式**。

1. 在**名稱**中，指定語音代理程式的唯一名稱。例如，`Customer Support - North America`。

1. 在**電話號碼**中，新增來自 SIP 幹線的號碼（包括國碼及區域碼）。例如，若為美國 800 號碼，請將電話號碼指定為 `18883334444`。電話號碼可以有空格及 `+ ( ) -` 字元。

1. 選擇性地說明您的語音代理程式。

1. 如果您想要啟用通話轉接，可以為您的**轉接目標**配置終止 URI。請參閱[設定通話轉接](call-transfer.html)。請不要在轉接目標使用個人電話號碼。

1. 配置與 Watson 服務實例的連線。您可以配置**位置 1** 及**位置 2** 的連線，以連接至多個 Watson 服務實例。具有與多個服務實例的連線可讓語音代理程式在運作中斷時切換至替代服務實例。請參閱[新增多個 Watson 服務位置](#add_location)。

    **重要事項**：_試用_ 及_精簡_ 實例只能直接連接至您建立 {{site.data.keyword.iva_short}} 服務實例的位置。您的第二個位置不是第二個語音代理程式。它只會充當災難回復的備份。

1. 在 **{{site.data.keyword.conversationshort}}** 下，按一下**啟用位置 1** 或**啟用位置 2** 以配置與 {{site.data.keyword.conversationshort}} 服務實例的連線。在您或其他人擁有的 {{site.data.keyword.Bluemix_notm}} 帳戶中，您可以使用 {{site.data.keyword.conversationshort}} 實例或 {{site.data.keyword.virtualagentfull}} 實例。您也可以透過服務編排引擎，連接至其中任何選項。

    * 如果您在「美國南部」或「美國東部」地區中建立語音代理程式，但沒有 {{site.data.keyword.conversationshort}} 服務實例，則可以在**服務實例**功能表中建立服務實例。
    * 或者，您也可以藉由變更[**服務類型**](#other_service)，以連接至 {{site.data.keyword.conversationshort}} 對話的其他來源。
    * 如果您要配置多個服務位置，請按一下另一個位置選項，然後選取**啟用位置**以配置與其他 {{site.data.keyword.conversationshort}} 實例的連線。請參閱[新增多個 Watson 服務位置](#add_location)。

1. 在 **{{site.data.keyword.speechtotextshort}}** 下，按一下**啟用位置 1** 或**啟用位置 2** 以檢閱 {{site.data.keyword.speechtotextshort}} 服務實例的預設配置。您可以使用下列各項來自訂配置。
    * 如果您在「美國南部」或「美國東部」地區中建立語音代理程式，但沒有 {{site.data.keyword.speechtotextshort}} 服務實例，則可以從**服務實例**功能表建立服務實例。
    * 選擇[**服務類型**](#other_service)，將語音代理程式連接至不同 {{site.data.keyword.Bluemix_notm}} 中的 {{site.data.keyword.speechtotextshort}} 實例。
    * 如果您要配置多個服務位置，請按一下另一個位置選項，然後選取**啟用位置**以配置與其他 {{site.data.keyword.speechtotextshort}} 實例的連線。請參閱[新增多個 Watson 服務位置](#add_location)。
    * **請記住**：{{site.data.keyword.iva_short}} 僅支援窄頻模型。

1. 在 **{{site.data.keyword.texttospeechshort}}** 下，按一下**啟用位置 1** 或**啟用位置 2** 以檢閱 {{site.data.keyword.texttospeechshort}} 服務實例的預設配置。 
    * 如果您在「美國南部」或「美國東部」地區中建立語音代理程式，但沒有 {{site.data.keyword.texttospeechshort}} 服務實例，則可以從**服務實例**功能表建立服務實例。 
    * 您也可以藉由變更[**服務類型**](#other_service)，來將語音代理程式連接至不同 {{site.data.keyword.Bluemix_notm}} 帳戶空間中的 {{site.data.keyword.texttospeechshort}} 實例。
    * 如果您要配置多個服務位置，請按一下另一個位置選項，然後選取**啟用位置**以配置與其他 {{site.data.keyword.texttospeechshort}} 實例的連線。請參閱[新增多個 Watson 服務位置](#add_location)。

1. 您也可以選擇啟用事件轉遞，收集 {{site.data.keyword.cloudantfull}} 中語音代理程式所處理通話的相關資訊。請參閱[啟用語音代理程式的事件轉遞](event-forwarding.html)。如需其他配置選項，請參閱[配置語音代理程式](#configure_va)。

1. 按一下**建立語音代理程式**，以建立您的語音代理程式及任何新服務。

建立語音代理程式之後，即可藉由與其電話號碼通話來測試語音代理程式。您可以在_用量_ 儀表板上，檢視通話的詳細資料。  

## 編輯並行連線數上限
{: #edit_concurrency}

如果您使用_標準_ 方案，則可以從預設值變更並行連線數上限。在所有方案中，您都會免費收到 2 個並行連線。如需相關資訊，請參閱[定價方案](https://console.bluemix.net/catalog/services/voice-agent-with-watson)。

在_管理_ 儀表板上，您可以看到**並行連線數上限**中列出之方案中所容許的並行連線數上限。您也可以在**使用的並行連線數上限**中看到語音代理程式在現行月份期間所使用的並行連線數上限。

如果您要變更方案中的並行連線數上限，請按一下**編輯**圖示。在_編輯並行連線數上限_ 視窗中，選擇並行連線數上限，然後按一下**儲存**。您可設定的並行連線數下限是 10，而上限是 50。如果對於語音代理程式您需要超過 50 個的並行連線，請參閱[要求設定輔助網路](connect-SIP.html#request-setup).

### 並行連線計價資訊
{: #concurrent-charge}

  * _精簡_、_試用_ 及_標準_ 方案包括 2 個免費的並行連線。
  * _超值_ 方案是依實例來自訂。
  * 在_標準_ 方案中，您的容量下限至少有 10 個並行連線。
  * 並行連線使用是按月依比例分配。如果您使用超過 2 個的並行連線，則會對您按日計費。
  * 如果您有_標準_ 或_超值_ 方案，則可以購買更大的並行連線容量。
  * 您一天使用的並行連線若達到並行連線容量上限，則會對您按日計費。例如，因為您的方案支援 2 個免費的並行連線，所以您最多可以設定 12 個連線。如果您一天只使用 5 個，只會對 3 個計費。

如需方案、費用及功能的相關資訊，請參閱[定價方案](https://console.bluemix.net/catalog/services/voice-agent-with-watson)。

## 編輯語音代理程式
{: #edit_va}

您可以編輯現有語音代理程式，以對其進行變更。若要編輯語音代理程式，請從語音代理程式的選項清單中按一下**編輯代理程式**。變更配置，然後儲存變更。

## 複製語音代理程式
{: #clone_va}

當您複製語音代理程式時，會將 Watson 服務的所有配置都複製至新的代理程式。若要複製語音代理程式，請從語音代理程式的選項清單中按一下**複製代理程式**。為您的語音代理程式提供唯一的名稱及電話號碼，並視需要變更任何配置選項，然後儲存變更。

## 刪除語音代理程式
{: #delete_va}

您可能想要刪除語音代理程式，以釋放電話號碼。一個電話號碼只能有一個語音代理程式。若要將電話號碼用於不同的語音代理程式，您必須先刪除任何使用此電話號碼的語音代理程式。

若要刪除語音代理程式，請從語音代理程式的選項清單中按一下**刪除代理程式**，然後儲存變更。即會從語音代理程式清單中移除語音代理程式。

## 配置語音代理程式
{: #configure_va}

### 配置進階選項
{: #config-advanced}

建立或複製語音代理程式時，您可以按一下**顯示進階**，來檢視下列進階配置選項。

* **{{site.data.keyword.conversationshort}} 失敗回覆訊息（選用）**：通話無法連接至 {{site.data.keyword.conversationshort}} 時，要傳送給訊息接收者的預設回覆訊息。
* **轉接失敗回覆訊息（選用）**：通話轉接失敗時，要串流給來電者的預設回覆訊息。
* **自訂 SIP INVITE 標頭（選用）**：指定要從送入的 SIP INVITE 要求擷取的自訂 SIP 標頭。
* **從 {{site.data.keyword.iva_short}} 傳送暫時鈴聲回應**：當 {{site.data.keyword.iva_short}} 處理送入的通話時，傳送 `180 ringing` 回應。預設為啟用。
* **轉接時保留通話**：在轉接期間讓來電者進入保留狀態。預設為啟用。
* **轉接失敗時中斷通話**決定通話轉接失敗時，是否中斷通話。預設為啟用。如果設定為已停用且通話轉接失敗，則 {{site.data.keyword.iva_short}} 會起始一個回合的交談。然後，{{site.data.keyword.conversationshort}} 可以中斷通話，或將它轉接至對話中所配置的不同目的地。
* **發生網路事件時通知 {{site.data.keyword.conversationshort}}**：啟用且偵測到錯誤時，{{site.data.keyword.iva_short}} 會以文字 "vgwNetworkWarningMessage" 對 {{site.data.keyword.conversationshort}} 服務起始一個回合。`vgwNetworkWarnings` 狀態變數包含在現行回合期間發生之網路事件的清單。如果已停用，則在現行回合期間發生之網路事件的清單，會以 `vgwNetworkWarning` 狀態變數中的下一回合事件進行傳送。預設為啟用。

### 新增多個 Watson 服務位置
{: #add_location}

如果您有_標準_ 或_超值_ 實例，則以將語音代理程式連接至不同位置中的多個 Watson 服務，以進行服務備援。_試用_ 及_精簡_ 實例只能直接連接至您建立 {{site.data.keyword.iva_short}} 服務實例的位置。您的第二個位置不是第二個語音代理程式。它只會充當災難回復的備份。

您的語音代理程式會依地理距離的順序來使用 Watson 服務實例。例如，您可以在「美國東部」地區建立語音代理程式，以及在「美國南部」及「澳洲雪梨」建立您的 {{site.data.keyword.conversationshort}} 服務。您的語音代理程式會使用 {{site.data.keyword.conversationshort}}「美國南部」地區，因為「美國南部」在地理位置上較接近「美國東部」，而不是雪梨。藉由連接至多個地區中的 Watson 服務，如果 Watson 服務在某個位置離線，則語音代理程式可以使用備用服務。

您隨時可以將 Watson 服務位置新增至語音代理程式配置。如需在您建立語音代理程式時連接多個服務位置實例的相關資訊，請參閱[建立語音代理程式](#creating)。

若要將 Watson 服務位置新增至現有語音代理程式，請針對您要配置的語音代理程式按一下**編輯代理程式**。針對您要連接的 {{site.data.keyword.conversationshort}}、{{site.data.keyword.texttospeechshort}} 或 {{site.data.keyword.speechtotextshort}} 實例選擇**位置 1** 或**位置 2**，然後新增配置資訊。您可以在您的工作區或其他工作區中使用 Watson 服務實例。請參閱[使用其他 {{site.data.keyword.Bluemix_notm}} 工作區中的服務實例](#other_services)。

**請記住**：針對服務備援，您必須在不同位置之不同服務地區中使用 Watson 服務實例。

您可以使用**啟用位置**方框來啟用或停用位置。依預設會啟用**位置 1**，而依預設會停用**位置 2**。必須為每一個 Watson 服務啟用至少一個位置。

### 使用其他 {{site.data.keyword.Bluemix_notm}} 工作區中的服務實例
{: #other_service}

您可以將語音代理程式配置成使用 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.speechtotextshort}} 服務實例，而這些服務實例屬於其他 {{site.data.keyword.Bluemix_short}} 帳戶中的工作區。若要將語音代理程式連接至其他服務實例，您可以使用服務實例的使用者名稱及密碼認證或 API 金鑰。

1. 選取**服務類型**及**地區**。

1. 選擇**使用者名稱及密碼**或 **API 金鑰**，然後輸入服務認證。若要尋找這些值，請移至您要配置的服務實例，選取**服務認證**，然後選取**檢視認證**。

  * **使用者名稱及密碼**：在 **URL**、**使用者名稱**及**密碼**欄位中，配置 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.texttospeechshort}} 服務實例的認證。
  * **API 金鑰**：在 **URL** 及 **API 金鑰**欄位中，配置 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 或 {{site.data.keyword.texttospeechshort}} 服務實例的認證。

  認證不是您的 {{site.data.keyword.Bluemix_notm}} 使用者名稱及密碼，而是特定服務實例的加密認證。
{:tip}

1. 輸入服務實例資訊。

  * **{{site.data.keyword.conversationshort}}：**在**工作區 ID** 欄位中，輸入您要與語音代理程式搭配使用的工作區 ID。若要尋找工作區 ID，請啟動工具，並在您要整合的工作區上，按一下「動作」圖示 (**&vellip;**)，然後選取**檢視詳細資料**。
  * **{{site.data.keyword.speechtotextshort}}：**在**模型**欄位中，選取服務的語音語言及格式。{{site.data.keyword.iva_short}} 僅支援窄頻模型。
  * **{{site.data.keyword.texttospeechshort}}：**在**語音**欄位中，選取服務所使用的語言及語音。您必須指定服務的語音。

**請記住：**為了讓您的語音代理程式運作，您必須配置相同語言的 {{site.data.keyword.conversationshort}}、{{site.data.keyword.speechtotextshort}} 及 {{site.data.keyword.texttospeechshort}}。請參閱[支援的語言](about.html#supported-languages)。

### 為語音代理程式配置 {{site.data.keyword.conversationshort}}
{: #conversation_va}

作為配置 {{site.data.keyword.conversationshort}} 服務實例的替代方案，您可以連接至服務編排引擎 (SOE) 或 Watson {{site.data.keyword.virtualagentshort}}。

* **服務編排引擎**：透過[服務編排引擎 (SOE)](about.html#arch-soe) 連接至 {{site.data.keyword.conversationshort}} 工作區或 {{site.data.keyword.virtualagentshort}}。SOE 會將訊息截取至服務並從中截取訊息，讓您可以使用協力廠商 API 進行修改。

  在 **URL** 欄位中，輸入 SOE 工作區的完整 URL（例如 `https://iva-soesample.myorg.net/SOE/myWorkspace`）。如果您的 SOE 需要鑑別（建議），則請在個別欄位中輸入使用者名稱及密碼。

  **重要事項**：為了資料安全，請確定針對 SOE 工作區使用安全的 URL，方法是使用 `https:` 而不要使用 `http:`，並且要求鑑別。若要進一步瞭解安全考量，請參閱[資訊安全及資料隱私](infosec.html)。

* **Watson {{site.data.keyword.virtualagentshort}}**：連接至 {{site.data.keyword.virtualagentshort}} 聊天機器人，而不是 {{site.data.keyword.conversationshort}} 工作區。[{{site.data.keyword.virtualagentshort}}](../virtual-agent/getting-started.html#getting-started) 是以 {{site.data.keyword.conversationshort}} 服務為建置基礎，但提供預先訓練的功能，以讓您開始使用零機器學習體驗。

  在 **URL** 欄位中，輸入 {{site.data.keyword.virtualagentshort}} 的 URL 認證（例如 `https://api.ibm.com/virtualagent/run/api`）。在**用戶端 ID** 及**用戶端密碼**欄位中，輸入鑑別金鑰，以對映至 API 呼叫的 `X-IBM-Client-Id` 及 `X-IBM-Client-Secret` 標頭欄位。在**機器人 ID** 欄位中，輸入用於此語音代理程式之機器人的 ID。如需如何尋找這些值的相關資訊，請參閱 {{site.data.keyword.virtualagentshort}} 文件中的[發佈代理程式](../virtual-agent/publish.html)。
