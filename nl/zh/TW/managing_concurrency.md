---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 編輯並行連線數上限
{: #edit_concurrency}

如果您使用_標準_ 或_超值_ 方案，則可以從預設值變更並行連線數上限。
{: shortdesc}

在所有方案中，您都會免費收到 2 個並行連線。如需相關資訊，請參閱[定價方案](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)。在_管理_ 儀表板上，您可以看到**並行連線數上限**中列出之方案中所容許的並行連線數上限。您也可以在**使用的並行連線數上限**中看到語音代理程式在現行月份期間所使用的並行連線數上限。

1. 移至_管理_ 儀表板上的_實例_ 標籤，以編輯您方案中的並行連線數上限。

1. 如果您要變更方案中的並行連線數上限，請按一下**編輯**圖示。

1. 在_編輯並行連線數上限_ 中，輸入並行連線數上限，然後按一下**儲存**。

您可設定的並行連線數下限是 10，而上限是 50。如果對於語音代理程式您需要超過 50 個的並行連線，請參閱[要求設定輔助網路](/docs/services/voice-agent?topic=voice-agent-connect#request-setup).

## 並行連線計價資訊
{: #concurrent-charge}

  * _精簡_ 及_標準_ 方案包括 2 個免費的並行連線。
  * _超值_ 方案是依實例來自訂。
  * 在_標準_ 方案中，您的容量下限至少有 10 個並行連線。
  * 並行連線使用是按月依比例分配。如果您使用超過 2 個的並行連線，則會對您按日計費。例如，因為您的方案支援 2 個免費的並行連線，所以您最多可以設定 12 個連線。如果您一天只使用 5 個，只會對 3 個計費。
  * 如果您有_標準_ 或_超值_ 方案，則可以購買更大的並行連線容量。
  * 您一天使用的並行連線若達到並行連線容量上限，則會對您按日計費。

如需方案、費用及功能的相關資訊，請參閱[定價方案](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)。
