---

copyright:
  years: 2019
lastupdated: "2019-06-17"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 定價常見問題
{: #faq-pricing}

## 使用 {{site.data.keyword.iva_short}} 標準服務的價格是多少？
{: #faq-pricing-zero}
{: faq}

 如需相關資訊，請參閱[定價頁面](https://cloud.ibm.com/catalog/services/voice-agent-with-watson){: external}。

## 何謂「每分鐘定價」？
{: #faq-pricing-one}
{: faq}

價格係基於您傳送至服務的音訊數量（分鐘數）。價格並非取決於服務處理音訊所需的時間。


## 每次呼叫 API 時，您是否計算到最近的分鐘數？
{: #faq-pricing-two}
{: faq}

{{site.data.keyword.IBM_notm}} 不計算服務接收到最近分鐘的每個 API 呼叫的音訊長度。反之，{{site.data.keyword.IBM_notm}} 會彙總該月的用量，然後計算到月底的最近分鐘。每次通話的持續時間都會四捨五入到下一分鐘。例如，如果第一次通話為 3.1 秒，第二次通話為 25.9 秒，{{site.data.keyword.IBM_notm}} 會將第一次通話計算為 4 秒，將第二次通話計算為 26 秒。然後，總音訊的持續時間計算為一分鐘。


## 如何計算並行連線，並應用在哪裡？
{: #faq-pricing-three}
{: faq}

並行連線僅應用於語音通話（非 SMS）。並行連線計算為同時定義在服務實例中的任何電話號碼的連線數。實際使用的每日並行連線數上限根據每月費用按比例計費。

## 並行連線數上限的定義是什麼？如何進行變更？

{: #faq-pricing-four}
{: faq}

並行連線數上限是任何時候都容許的最大連線數，它是計費的連線數上限。您可以在[儀表板](https://cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-edit_concurrency)中定義及變更並行連線數上限。標準方案的最大並行容量為 50 個連線，如果需要更多，您可以開立支援問題單。

## 如何對入埠和出埠 SMS/MMS 訊息進行計費？

{: #faq-pricing-five}
{: faq}

在向使用者傳送回應之前，不會對入埠訊息進行計費。當出埠訊息透過 Voice Gateway 傳送給使用者或作為對入埠訊息的回應時，即會建立一個階段作業。如果適用，將對回應的出埠和入埠訊息進行計費。
出埠和入埠訊息都會收費，直到階段作業逾時。階段作業逾時後，即會捨棄交談上下文。預設階段作業逾時為 3600 秒，使用者可以在儀表板上設定階段作業逾時的持續時間。
