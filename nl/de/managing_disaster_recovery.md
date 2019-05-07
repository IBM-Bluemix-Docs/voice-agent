---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Mehrere Servicestandorte konfigurieren
{: #disaster-recovery}

Sie können den Sprachagenten aus Gründen der Serviceredundanz mit mehreren Services an verschiedenen Standorten verbinden. Beim zweiten Standort handelt es sich nicht um einen zweiten Sprachagenten; er fungiert lediglich als Backup.
{: shortdesc}

Wenn Sie einen _Lite_-Plan für Ihre Voice Agent-Instanz verwenden, können Sie Ihren SIP-Trunk mit nur einem einzigen Endpunkt verbinden, an dem Ihre Voice Agent-Instanz erstellt wird. Da der _Lite_-Plan Verbindungen zu nur einem einzigen Standort bereitstellt, können Sie Redundanzen für die verbundenen Services bereitstellen, aber nicht für Ihren Sprachagenten. Falls an dem Standort Ihres Sprachagenten eine Serviceunterbrechung auftritt, können Anrufe nicht an einen sekundären Standort geleitet werden.
{: tip}

## Redundante Services hinzufügen
{: #add_redundant}

Sie können Ihrer Sprachagentenkonfiguration jederzeit einen Servicestandort von Watson oder anderen Anbietern hinzufügen, indem Sie Ihren Sprachagenten bearbeiten.

1. Wenn Sie einen redundanten Service zu einem vorhandenen Sprachagenten hinzufügen möchten, navigieren Sie in Ihrem Dashboard _Verwalten_ zur Registerkarte _Sprachagenten_. Klicken Sie auf die Option **Agenten bearbeiten** für den Sprachagenten, den Sie konfigurieren möchten.

1. Wählen Sie **Standort 1** oder **Standort 2** für den {{site.data.keyword.conversationshort}}-, den {{site.data.keyword.texttospeechshort}}- oder den {{site.data.keyword.speechtotextshort}}-Service aus, den Sie verbinden möchten, und fügen Sie Ihre Konfigurationsinformationen hinzu. Sie können Serviceinstanzen anderer Anbieter oder Watson-Serviceinstanzen in Ihrem Arbeitsbereich oder in anderen Arbeitsbereichen verwenden. Informationen hierzu finden Sie in [Serviceinstanzen in anderen {{site.data.keyword.Bluemix_notm}}-Arbeitsbereichen verwenden](/docs/services/voice-agent?topic=voice-agent-other_service).

**Denken Sie daran**: Zum Zweck der Serviceredundanz müssen Sie Watson-Serviceinstanzen in verschiedenen Serviceregionen für verschiedene Standorte verwenden.

Sie können einen Standort über das Feld **Standort aktivieren** aktivieren oder inaktivieren. **Standort 1** ist standardmäßig aktiviert, **Standort 2** ist standardmäßig inaktiviert. Für jeden Watson-Service muss mindestens ein Standort aktiviert sein.

## Mehrere Watson-Servicestandorte hinzufügen
{: #add_location}

Der Sprachagent verwendet die Watson-Serviceinstanzen in der Reihenfolge der jeweiligen geografischen Distanz. Beispiel: Sie können einen Sprachagenten in der Region 'Washington DC' und die {{site.data.keyword.conversationshort}}-Services in den Regionen 'Dallas' und 'Sydney, Australien' erstellen. Der Sprachagent verwendet die {{site.data.keyword.conversationshort}}-Region 'Dallas', da diese geografisch näher an 'Washington DC' liegt als 'Sydney, Australien'. Wenn Sie Verbindungen zu Watson-Services in mehreren Regionen einrichten und ein Watson-Service an einem Standort offline ist, kann der Sprachagent den redundanten Service verwenden.
