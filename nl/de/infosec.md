---

copyright:
  years: 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Informationssicherheit und Datenschutz
{: #infosec}

IBM hat sich das Ziel gesetzt, unseren Kunden und Partnern innovative Datenschutz-, Sicherheits- und Governance-Lösungen bereitzustellen.
{: shortdesc}

## Informationsverarbeitung und Konfigurationsoptionen
{: #configure_infosec}

Zum Betrieb des Service und zur Optimierung der Funktionalität für den Benutzer erfasst und speichert {{site.data.keyword.iva_short}} in minimalem Umfang personenbezogene Daten, die in Übereinstimmung mit dem IBM [Data Processing Addendum (DPA)](https://www.ibm.com/support/customer/csol/terms/){: new_window} und dem [Datenblatt zu Datenverarbeitung und Datenschutz](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=00C4CE004FA711E7AA10752A2F494A7C){: new_window} behandelt werden. {{site.data.keyword.iva_short}} speichert, erfasst oder verarbeitet keine Daten, die Teil eines Sprach- oder SMS-Dialogs sind. Die Daten werden stattdessen zur Verarbeitung an verschiedene Services weitergeleitet. Bei einer Unterhaltung geben Benutzer möglicherweise Informationen preis, die geschützte Gesundheitsinformationen (Protected Health Information, PHI), persönlich identifizierbare Daten (Personally Identifiable Information, PII) oder Zahlungskarteninformationen (Payment Card Industry Data Security Standard, PCI DSS) enthalten. Weitere Informationen zum Dialogablauf und zur Architektur von {{site.data.keyword.iva_short}} finden Sie unter [Architektur](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}.

Wenn Sie Ihre Instanz des Sprachagenten konfigurieren, sollten Sie die folgenden Funktionen berücksichtigen, um den Datenschutz und die sichere Verarbeitung zu unterstützen.

### Anrufübergabe
{:  #calltransfer_infosec}

Wenn Sie die Funktionalität für die Anrufübergabe zu Ihrem Sprachagenten hinzufügen, geben Sie bei der Konfiguration des SIP-URI für das Übergabeziel eine Telefonnummer an. Benutzer sollten für dieses Übergabeziel keine persönliche Telefonnummer angeben.

Im Thema [Anrufübergabe einrichten](/docs/services/voice-agent?topic=voice-agent-call-transfer) finden Sie Informationen zur Konfiguration des SIP-Trunks und des SIP-URI für die Anrufübergabe.

### Ereignisweiterleitung
{: #infosec_event_forwarding}

Sie können den Sprachagenten so konfigurieren, dass er Berichterstellungsereignisse an eine {{site.data.keyword.cloudantfull}}-Datenbankinstanz weiterleitet. Diese Berichterstellungsereignisse können PII-, PHI- und PCI DSS-Daten zu den Anrufern in Form von Transkriptionen, Dialogwechselereignissen und CDR-Ereignissen (CDR - Call Detail Records - Datensätze mit Anrufdetails) enthalten. Anrufdaten, SMS-Daten und Berichterstellungsereignisse werden in {{site.data.keyword.iva_short}} nicht gespeichert, verarbeitet oder erfasst und Benutzer sollten die externen {{site.data.keyword.cloudant_short_notm}}-Services entsprechend konfigurieren. **Die Ereignisweiterleitung ist standardmäßig inaktiviert.**

Unter [Ereignisweiterleitung aktivieren](/docs/services/voice-agent?topic=voice-agent-event_forwarding) finden Sie Informationen dazu, wie Sprachagenten für die Weiterleitung von Berichterstellungsereignissen konfiguriert werden.

Unter [**{{site.data.keyword.cloudant_short_notm}}: Sicherheit**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window} finden Sie weitere Informationen zum Datenschutz und zur Informationssicherheit für {{site.data.keyword.cloudant_short_notm}}.

### Zwischenspeicherung bei Text to Speech
{: #tts_caching}

Um sich mit Kunden zu unterhalten, generiert {{site.data.keyword.conversationshort}} Antworten in Textform, die an den {{site.data.keyword.texttospeechshort}}-Service weitergeleitet und in {{site.data.keyword.iva_short}} als Sprachausgabe ausgegeben werden. Die Antworten, die {{site.data.keyword.conversationshort}} erstellt, können möglicherweise schutzwürdige Informationen enthalten. Um zu verhindern, dass {{site.data.keyword.iva_short}} Antworten zwischenspeichert, die vom {{site.data.keyword.texttospeechshort}}-Service empfangen wurden und die persönliche Daten enthalten, können Sie den Aktionsbefehl `vgwActExcludeFromTTSCache` aktivieren, mit dem Äußerungen, die bestimmte Informationstypen enthalten, von der Zwischenspeicherung ausgeschlossen werden. Weitere Informationen finden Sie unter [Sprachagenten mithilfe der API programmieren](/docs/services/voice-agent?topic=voice-agent-api#action-sequences).

Nachdem Ihre Voice Agent-Instanz gelöscht wurde, wird der TTS-Cache in 24 Stunden gelöscht. Dies wird als `TTS-Cachezeitlimit` bezeichnet.

### Sichere Verbindungen
{: #secure_trunking}

{{site.data.keyword.iva_short}} basiert auf {{site.data.keyword.Bluemix_notm}} und ist mit SIP-Trunks integriert, die von Benutzern konfiguriert werden. Da SIP-Trunks extern sind und eine Verbindung mit {{site.data.keyword.iva_short}} herstellen, können Sie sichere Verbindungen zwischen den SIP-Trunks und {{site.data.keyword.iva_short}} aktivieren, indem Sie SRTP (Secure Real Time Transport Protocol) verwenden. Außerdem können Sie die Verschlüsselung mithilfe von Secure SIP (SIPS) auf der Basis von Transport Layer Security (TLS) aktivieren. Weitere Informationen finden Sie in [Verbindungen schützen](/docs/services/voice-agent?topic=voice-agent-securing).

SMS-Daten werden standardmäßig mit TLS verschlüsselt. Weitere Informationen finden Sie auf der Seite [Hinweise zur Umsetzung der DSGVO für IBM Voice Gateway und SMS Gateway](https://www.ibm.com/support/knowledgecenter/en/SS4U29/gdpr_considerations.html#GDPR_dataProcessing){: new_window}.

### Konfiguration der Service-Orchestrierungsengine (SOE)
{: #SOE_config}

Sie können eine Service-Orchestrierungsengine (SOE) verwenden, um die zwischen {{site.data.keyword.iva_short}} und {{site.data.keyword.conversationshort}} ausgetauschten Informationen zu verarbeiten und um die Unterhaltung mit Anrufern anzupassen. Um sichere Verbindungen zu verwenden, sollten Sie sicherstellen, dass Sie die SOE mit einer sicheren URL (`https`) und mit Benutzerauthentifizierung konfigurieren.

Weitere Informationen finden Sie in [{{site.data.keyword.conversationshort}} für den Sprachagenten konfigurieren](/docs/services/voice-agent?topic=voice-agent-conversation_va#conversation_va) und [Architektur mit einer Service-Orchestrierungsengine](/docs/services/voice-agent?topic=voice-agent-about#arch-soe).

## SMS/MMS-Unterstützung
{: #SMS_MMS}

### Datenverarbeitung
{: #data_handling}

{{site.data.keyword.iva_short}} speichert, erfasst oder verarbeitet keine SMS-Daten. MMS-Bilder werden außerhalb des IBM Service gespeichert und durch den Service-Provider verarbeitet. Kunden müssen sich hierüber in der Sicherheits-/Datenschutzvereinbarung ihres SMS-Providers informieren. {{site.data.keyword.iva_short}} verarbeitet nur Textlinks zu den Bildern, die in die SMS-Nachrichten integriert sind.

Wenn eine Service-Orchestrierungs-Engine oder {{site.data.keyword.conversationshort}} eine MMS-Nachricht (mit oder ohne SMS-Textnachricht) an den Benutzer sendet, werden eine oder mehrere öffentlich zugängliche Medien-URLs an Twilio gesendet. Twilio unterstützt keine nicht öffentlichen URLs. Benutzer sollten keine vertraulichen oder personenbezogenen Daten per MMS senden.

{{site.data.keyword.iva_short}} maskiert Anrufer-IDs in den Nachrichtenprotokollen, um eine Erfassung solcher personenbezogenen Daten zu verhindern.

### Authentifizierung
{: #authentication}

Eingehende SMS-Nachrichten werden vom Service-Provider durch den Einsatz der [IAM-Authentifizierung](/docs/services/voice-agent?topic=voice-agent-iam#sms_access){: new_window} geschützt.

## Services mit Bezug auf {{site.data.keyword.iva_short}}
{: #related_services}

{{site.data.keyword.iva_short}} orchestriert eine Reihe von {{site.data.keyword.Bluemix_notm}}-Services, um die Kommunikation zwischen Endbenutzern und cloudbasierten kognitiven Services zu koordinieren. {{site.data.keyword.iva_short}} selbst speichert, erfasst oder verarbeitet keine Daten auf eine Weise, die die Rechte der Endbenutzer verletzen würde. Anhängig von der Konfiguration der zugehörigen Services erfassen diese integrierten Services möglicherweise geschützte Gesundheitsinformationen (Protected Health Information, PHI), persönlich identifizierbare Daten (Personally Identifiable Information, PII) oder Zahlungskarteninformationen (Payment Card Industry Data Security Standard, PCI DSS), die von Benutzern bei einer Unterhaltung preisgegeben werden. Weitere Informationen zur Architektur und zum Dialogablauf in {{site.data.keyword.iva_short}} finden Sie unter [Architektur](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}.

In den folgenden Ressourcen finden Sie weitere Hinweise zu den einzelnen Services und zu {{site.data.keyword.Bluemix_notm}}.

  * [**{{site.data.keyword.Bluemix_short}}: Einhaltung der Sicherheitsrichtlinie**](/docs/overview?topic=overview-security#security)
  * [**{{site.data.keyword.conversationfull}}: Informationssicherheit**](/docs/services/assistant?topic=assistant-information-security#information-security){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}: Informationssicherheit**](/docs/services/text-to-speech?topic=text-to-speech-information-security){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}: Informationssicherheit**](/docs/services/speech-to-text?topic=speech-to-text-information-security){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: Sicherheit**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}
