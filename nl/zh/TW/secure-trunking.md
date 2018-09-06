---

copyright:
  years: 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# 保護連線安全
{: #securing}

您可以針對 SIP 幹線啟用「安全即時傳輸通訊協定 (SRTP)」以及使用「傳輸層安全 (TLS)」進行加密，來保護使用 {{site.data.keyword.iva_full}} 所進行之連線的安全。

## 在 Twilio 中設定 SRTP
{: #SRTP}

**附註：**如果您啟用 SRTP，則也會加密 SIP 訊息。您不需要分別啟用 SRTP 及 SIP 訊息加密。

1. 在 Twilio 帳戶中，導覽至_彈性 SIP 幹線_ 儀表板，然後選取**幹線**。

1. 選擇您要使用 SRTP 保護其安全的幹線，方法是選取現有幹線，或按一下 **+** 圖示來建立新的幹線。

  * 如果您建立新幹線，則需要在**起源**儀表板中配置 _SIP 幹線 URI_。如需相關資訊，請參閱[連接 SIP 幹線](connect-SIP.html)。

1. 在_一般_ 儀表板上，尋找_保護幹線安全_ 區段。按一下**已停用**，以將安全幹線設定變更為**已啟用**，然後儲存變更。

## 在 Twilio 中使用 TLS 僅啟用 SIP 訊息的加密
{: #TLS}

如果您想要只在 {{site.data.keyword.iva_short}} 中加密 SIP 訊息，而不使用 SRTP，則可以在 Twilio 中選取可使用「傳輸層安全 (TLS)」的 URI 端點。

1. 在 Twilio 帳戶中，導覽至_彈性 SIP 幹線_ 儀表板，然後選取**幹線**。

1. 選擇要新增通話轉接的幹線，方法是選取現有幹線，或按一下 **+** 圖示來建立新的幹線。

1. 從功能表中選取**起源**，然後輸入下列安全起源 URI（一次一個）。藉由包含多個主機名稱或 IP 位址，如果第一個主機端點失敗或無法運作，則您的 SIP 幹線提供者會將通話導向至下一個列出的主機名稱。

```
sip:us-south.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}

或

```
sip:us-east.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}
