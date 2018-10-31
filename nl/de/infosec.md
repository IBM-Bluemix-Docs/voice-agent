---

copyright:
  years: 2018
lastupdated: "2018-08-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Informationssicherheit und Datenschutz
{: #infosec}

IBM hat sich das Ziel gesetzt, unseren Kunden und Partnern innovative Datenschutz- Sicherheits- und Governance-Lösungen bereitzustellen.
{: shortdesc}

## Informationsverarbeitung und Konfigurationsoption
{: #configure_infosec}

{{site.data.keyword.iva_short}} speichert, erfasst oder verarbeitet keine von Kunden empfangene Daten. Die Daten werden stattdessen zur Verarbeitung an verschiedene Services weitergeleitet. Bei einer Unterhaltung geben Benutzer möglicherweise Informationen preis, die geschützte Gesundheitsinformationen (Protected Health Information, PHI), persönlich identifizierbare Daten (Personally Identifiable Information, PII) oder Zahlungskarteninformationen (Payment Card Industry Data Security Standard, PCI DSS) enthalten. Weitere Informationen zum Dialogablauf und zur Architektur von {{site.data.keyword.iva_short}} finden Sie unter [Architektur](about.html#architecture){: new_window}.

Wenn Sie Ihre Instanz des Sprachagenten konfigurieren, sollten Sie die folgenden Funktionen berücksichtigen, um den Datenschutz und die sichere Verarbeitung zu unterstützen.

### Anrufübergabe
{:  #calltransfer_infosec}

Wenn Sie die Funktionalität für die Anrufübergabe zu Ihrem Sprachagenten hinzufügen, geben Sie bei der Konfiguration des SIP-URI für das Übergabeziel eine Telefonnummer an. Benutzer sollten für dieses Übergabeziel keine persönliche Telefonnummer angeben.

Im Thema [Anrufübergabe einrichten](call-transfer.html) finden Sie Informationen zur Konfiguration des SIP-Trunks und des SIP-URI für die Anrufübergabe.

### Ereignisweiterleitung
{: #event_forwarding}

Sie können den Sprachagenten so konfigurieren, dass er Berichterstellungsereignisse an eine {{site.data.keyword.cloudantfull}}-Datenbankinstanz weiterleitet. Diese Berichterstellungsereignisse können PII-, PHI- und PCI DSS-Daten zu den Anrufern in Form von Transkriptionen, Dialogwechselereignissen und CDR-Ereignissen (CDR - Call Detail Records - Datensätze mit Anrufdetails) enthalten. Anrufdaten und Berichterstellungsereignisse werden in {{site.data.keyword.iva_short}} nicht gespeichert, verarbeitet oder erfasst und Benutzer sollten die externen {{site.data.keyword.cloudant_short_notm}}-Services entsprechend konfigurieren. **Die Ereignisweiterleitung ist standardmäßig inaktiviert.**

Unter [Ereignisweiterleitung aktivieren](event-forwarding.html) finden Sie Informationen dazu, wie Sprachagenten für die Weiterleitung von Berichterstellungsereignissen konfiguriert werden.

Unter [**{{site.data.keyword.cloudant_short_notm}}: Sicherheit**](../Cloudant/offerings/security.html#security){: #new_window} finden Sie weitere Informationen zum Datenschutz und zur Informationssicherheit für {{site.data.keyword.cloudant_short_notm}}.

### Zwischenspeicherung bei Text to Speech
{: #tts_caching}

Um sich mit Kunden zu unterhalten, generiert {{site.data.keyword.conversationshort}} Antworten in Textform, die an den {{site.data.keyword.texttospeechshort}}-Service weitergeleitet und in {{site.data.keyword.iva_short}} als Sprachausgabe ausgegeben werden. Die Antworten, die {{site.data.keyword.conversationshort}} erstellt, können möglicherweise schutzwürdige Informationen enthalten. Um zu verhindern, dass {{site.data.keyword.iva_short}} Antworten zwischenspeichert, die vom {{site.data.keyword.texttospeechshort}}-Service empfangen wurden und die persönliche Daten enthalten, können Sie den Aktionsbefehl `vgwActExcludeFromTTSCache` aktivieren, mit dem Äußerungen, die bestimmte Informationstypen enthalten, von der Zwischenspeicherung ausgeschlossen werden. Weitere Informationen finden Sie unter [Sprachagenten mithilfe der API programmieren](api.html#action-sequencess).

### Sichere Verbindungen
{: #secure_trunking}

{{site.data.keyword.iva_short}} basiert auf {{site.data.keyword.Bluemix_notm}} und ist mit SIP-Trunks integriert, die von Benutzern konfiguriert werden. Da SIP-Trunks extern sind und eine Verbindung mit {{site.data.keyword.iva_short}} herstellen, können Sie sichere Verbindungen zwischen den SIP-Trunks und {{site.data.keyword.iva_short}} aktivieren, indem Sie SRTP (Secure Real Time Transport Protocol) verwenden. Außerdem können Sie die Verschlüsselung mithilfe von Secure SIP (SIPS) auf der Basis von Transport Layer Security (TLS) aktivieren. Weitere Informationen finden Sie unter [Verbindungen schützen](secure-trunking.html).

### Konfiguration der Service-Orchestrierungsengine (SOE)
{: #SOE_config}

Sie können eine Service-Orchestrierungsengine (SOE) verwenden, um die zwischen {{site.data.keyword.iva_short}} und {{site.data.keyword.conversationshort}} ausgetauschten Informationen zu verarbeiten und um die Unterhaltung mit Anrufern anzupassen. Um sichere Verbindungen zu verwenden, sollten Sie sicherstellen, dass Sie die SOE mit einer sicheren URL (`https`) und mit Benutzerauthentifizierung konfigurieren.

Weitere Informationen finden Sie unter [{{site.data.keyword.conversationshort}}  für Ihren Sprachagenten konfigurieren](managing.html#conversation_va) und [Architektur mit einer Service-Orchestrierungsengine](about.html#arch-soe).

## Services mit Bezug auf {{site.data.keyword.iva_short}}
{: #related_services}

{{site.data.keyword.iva_short}} orchestriert eine Reihe von {{site.data.keyword.Bluemix_notm}}-Services, um die Kommunikation zwischen Endbenutzern und cloudbasierten kognitiven Services zu koordinieren. {{site.data.keyword.iva_short}} selbst speichert, erfasst oder verarbeitet keine Daten auf eine Weise, die die Rechte der Endbenutzer verletzen würde. Anhängig von der Konfiguration der zugehörigen Services erfassen diese integrierten Services möglicherweise geschützte Gesundheitsinformationen (Protected Health Information, PHI), persönlich identifizierbare Daten (Personally Identifiable Information, PII) oder Zahlungskarteninformationen (Payment Card Industry Data Security Standard, PCI DSS), die von Benutzern bei einer Unterhaltung preisgegeben werden. Weitere Informationen zur Architektur und zum Dialogablauf in {{site.data.keyword.iva_short}} finden Sie unter [Architektur](about.html#architecture){: new_window}.

In den folgenden Ressourcen finden Sie weitere Hinweise zu den einzelnen Services und zu {{site.data.keyword.Bluemix_notm}}.

  * [**{{site.data.keyword.Bluemix_short}}: Einhaltung der Sicherheitsrichtlinie**](../../security/compliance.html)
  * [**{{site.data.keyword.conversationfull}}: Informationssicherheit**](../conversation/information-security.html){: #new_window}
  * [**{{site.data.keyword.texttospeechfull}}: Informationssicherheit**](../text-to-speech/information-security.html){: #new_window}
  * [**{{site.data.keyword.speechtotextfull}}: Informationssicherheit**](../speech-to-text/information-security.html){: #new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: Sicherheit**](../Cloudant/offerings/security.html#security){: #new_window}
