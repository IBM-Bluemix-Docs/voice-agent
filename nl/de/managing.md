---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Serviceinstanzen und Sprachagenten verwalten
{: #managing}

Mithilfe des Dashboards _Verwalten_ können Sie Ihre Serviceinstanzkonfigurationen ändern und einzelne Sprachagenten erstellen, bearbeiten, klonen, konfigurieren oder entfernen. Sie können über mehrere Sprachagenten in Ihrer Serviceinstanz verfügen und jeder dieser Sprachagenten kann bis zu 1000 eindeutige Nummern und Beschreibungen umfassen. Jeder Sprachagent muss jedoch über einen eindeutigen Namen und mindestens eine Telefonnummer verfügen.

* **HINWEIS**: Eine einzige {{site.data.keyword.iva_full}}-Serviceinstanz kann bis zu 150 Sprachagenten haben.
{: shortdesc}

## Zum eigenen Voice Agent-Service-Dashboard navigieren
{: #navigate_manage}

Sie finden das Dashboard _Verwalten_ im Dashboard Ihres {{site.data.keyword.iva_short}}-Service.

1. Rufen Sie die [Ressourcenliste Ihres {{site.data.keyword.Bluemix_notm}}-Kontos](https://cloud.ibm.com/resources) auf.

1. Wählen Sie in der Liste der **Services** die **Voice Agent**-Serviceinstanz aus, um das Service-Dashboard auf der Registerkarte _Verwalten_ zu öffnen.

## Voice Agent-Zusammenfassung
{: #agent_summary}

Wenn Sie bereits über einen vorhandenen Sprachagenten verfügen, können Sie eine Zusammenfassung aller Nummern, Beschreibungen und Konfigurationseinstellungen für den Agenten anzeigen. Klicken Sie zum Anzeigen der Zusammenfassung links vom **Namen** des Sprachagenten auf die Pfeilschaltfläche für die Dropdown-Liste. Die Zusammenfassung wird dann erweitert.

Der Sprachagent kann zwar mehrere Nummern enthalten, doch in der Zusammenfassung für den Agenten ist nur die **Primärnummer** für die Anzeige ausgewählt. Standardmäßig handelt es sich dabei um die erste Nummer, die zum Sprachagenten hinzugefügt wurde, und dient nur der Anzeige, ohne eine Funktion zu erfüllen. Wenn eine andere Nummer des Sprachagenten angezeigt werden soll, lesen Sie die Informationen in [Mehrere Nummern verwalten](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

In der Zusammenfassung für den Sprachagenten können Sie alle Nummern anzeigen lassen. Erweitern Sie dazu die Zusammenfassung der Konfiguration und klicken Sie dann auf die Schaltfläche **Nummern anzeigen**. In einem neuen Dialogfeld namens **Verwalten** wird eine Liste aller Nummern angezeigt. Weitere Informationen zum Arbeiten mit dem Dialogfenster **Verwalten** finden Sie auf der Seite [Mehrere Nummern verwalten](/docs/services/voice-agent?topic=voice-agent-multi_num). 

## Maximale Anzahl gleichzeitiger Verbindungen für Ihre Serviceinstanz bearbeiten
{: #edit_service}

In allen Plänen sind zwei gleichzeitige Verbindungen kostenfrei enthalten. Wenn Sie den _Standardplan_ oder den _Premiumplan_ verwenden, können Sie die [maximale Anzahl gleichzeitiger Verbindungen gegenüber den Standardeinstellungen ändern](/docs/services/voice-agent?topic=voice-agent-edit_concurrency), und zwar über die Registerkarte _Instanzen_.

## Sprachagenten erstellen
{: #create_va}

[Erstellen Sie einen neuen Sprachagenten](/docs/services/voice-agent?topic=voice-agent-config_instance), und zwar über die Registerkarte _Sprachagenten_ im Dashboard _Verwalten_.

## Sprachagenten bearbeiten
{: #edit_va}

Sie können vorhandene Sprachagenten ändern, indem Sie sie auf der Registerkarte _Sprachagenten_ im Dashboard _Verwalten_ bearbeiten. Zum Bearbeiten eines Sprachagenten klicken Sie in der Liste der Optionen für den Sprachagenten auf **Agenten bearbeiten**. Ändern Sie die Konfiguration und speichern Sie die Änderungen.

## Sprachagenten klonen
{: #clone_va}

Wenn Sie einen Sprachagenten klonen, werden die gesamten Konfigurationen für die Watson-Services auf den neuen Agenten kopiert. Zum Klonen eines Sprachagenten klicken Sie in der Liste der Optionen für den Sprachagenten auf **Agenten klonen**. Geben Sie Ihrem Sprachagenten einen eindeutigen Namen und eine eindeutige Telefonnummer, ändern Sie alle Konfigurationsoptionen nach Bedarf und speichern Sie die Änderungen.

## Sprachagenten löschen
{: #delete_va}

Das Löschen eines Sprachagenten kann sinnvoll sein, um eine Telefonnummer freizugeben. Für eine einzelne Telefonnummer können Sie nur jeweils einen Sprachagenten haben. Um eine Telefonnummer für einen anderen Sprachagenten zu verwenden, müssen Sie zuerst einen eventuell vorhandenen Sprachagenten löschen, der diese Telefonnummer verwendet.

Zum Löschen eines Sprachagenten rufen Sie die Registerkarte _Sprachagenten_ auf, klicken Sie in der Liste der Optionen für den Sprachagenten auf **Agenten löschen** und speichern Sie die Änderungen. Der Sprachagent wird aus der Liste der Sprachagenten entfernt.

## Sprachagenten nach Nummer oder Beschreibung suchen
{: #search}

Sie können anhand der in einem Agenten gespeicherten Nummern oder Beschreibungen nach Sprachagenten suchen.

Geben Sie in der Suchleiste (_Suchen_) eine Nummer oder eine Beschreibung ein. Die Suchergebnisse werden während der Eingabe automatisch aktualisiert.  

## Sprachagenten konfigurieren
{: #configure_va}

Beim Erstellen, Klonen oder Bearbeiten eines Sprachagenten können Sie Änderungen an den Konfigurationseinstellungen für Ihren Sprachagenten sowie an den Verbindungen zu zugehörigen Services vornehmen.

* **[Mehrere Telefonnummern konfigurieren](/docs/services/voice-agent?topic=voice-agent-multi_num):** Sie können Ihren Sprachagenten so konfigurieren, dass er mehrere Telefonnummern einbezieht.
* **[Mehrere Servicestandorte konfigurieren](/docs/services/voice-agent?topic=voice-agent-disaster-recovery):** Schließen Sie zur Unterstützung der Serviceredundanz mehrere Servicestandorte für Ihre verbundenen Services ein.
* **[Verbindung zu Sprach- und Textservices anderer Anbieter herstellen](/docs/services/voice-agent?topic=voice-agent-third-party):** Anstatt {{site.data.keyword.texttospeechshort}} oder {{site.data.keyword.speechtotextshort}} zu verwenden, können Sie eine Verbindung zwischen Ihrem Sprachagenten und APIs anderer Anbieter herstellen, z. B. Google Cloud Speech-to-Text.
* **[Services in anderen {{site.data.keyword.Bluemix_notm}}-Arbeitsbereichen verwenden](/docs/services/voice-agent?topic=voice-agent-other_service):** Sie können Ihren Sprachagenten für die Verwendung von {{site.data.keyword.conversationshort}}-, {{site.data.keyword.speechtotextshort}}- oder {{site.data.keyword.speechtotextshort}}-Serviceinstanzen konfigurieren, die zu Arbeitsbereichen in anderen {{site.data.keyword.Bluemix_short}}-Konten gehören.
* **[Watson Assistant mit einer Service-Orchestrierungsengine (SOE) konfigurieren](/docs/services/voice-agent?topic=voice-agent-conversation_va):** Sie können mithilfe einer Service-Orchestrierungsengine eine Verbindung zu einem {{site.data.keyword.conversationshort}}-Skill herstellen. Eine SOE fängt Nachrichten zum und vom Service ab, sodass Sie sie mithilfe von APIs von Drittanbietern modifizieren können.
* **[Ereignisweiterleitung für Sprachagenten aktivieren](/docs/services/voice-agent?topic=voice-agent-event_forwarding):** Möglicherweise möchten Sie Anrufdaten von {{site.data.keyword.iva_short}} erfassen und analysieren, um die Natürlichkeit des Dialogs für den Anrufer zu verbessern. Jeder Sprachagent, den Sie erstellen, kann Berichte an eine angegebene {{site.data.keyword.cloudant_short_notm}} weiterleiten, die Sie verwalten.

## Erweiterte Optionen für den Sprachagenten konfigurieren
{: #config-advanced}

Beim Erstellen oder Klonen eines Sprachagenten können Sie auf **Erweiterte Optionen anzeigen** klicken, um die folgenden erweiterten Konfigurationsoptionen aufzurufen.

* **Zeitlimitüberschreitung beim Lesen des Dialogs (optional)**: Diese Option legt (in Sekunden) fest, wie lange Voice Agent auf eine Antwort des Watson Assistant wartet. Bei Überschreitung des angegebenen Zeitraums versucht Voice Agent erneut, Kontakt zu Watson Assistant aufzunehmen. Kann der Service weiterhin nicht erreicht werden, schlägt der Anruf fehl. Standardmäßig ist ein Zeitraum von 5 Sekunden festgelegt.
* **Antwortnachricht bei {{site.data.keyword.conversationshort}}-Fehler (optional)**: Die Standardantwortnachricht, die an den Nachrichtenempfänger gesendet wird, falls der Anruf nicht mit {{site.data.keyword.conversationshort}} verbunden werden kann. Es können bis zu 1024 Zeichen eingegeben werden.
* **Antwortnachricht bei Anrufübergabefehler (optional)**: Die Standardantwortnachricht, die an den Anrufer gestreamt wird, falls die Anrufübergabe fehlschlägt. Es können bis zu 1024 Zeichen eingegeben werden.
* **Angepasster SIP-Einladungsheader (optional)**: Gibt den angepassten SIP-Header an, der aus eingehenden SIP INVITE-Anforderungen extrahiert werden soll. Es können bis zu 1024 Zeichen eingegeben werden.
* **Vorläufige Antwort mit dem Statuscode 'Ringing' von {{site.data.keyword.iva_short}}** senden: Sendet eine Antwort mit dem Statuscode `180 - Ringing`, während {{site.data.keyword.iva_short}} einen eingehenden Anruf verarbeitet. Standardmäßig aktiviert.
* **Anruf während der Übergabe in die Warteschleife legen**: Legt den Anruf während der Übergabe in die Warteschleife. Standardmäßig aktiviert.
* **Anruf bei fehlgeschlagener Übergabe unterbrechen**: Bestimmt, ob der Anruf bei einer fehlgeschlagenen Anrufübergabe unterbrochen werden soll.  Standardmäßig aktiviert. Wenn die Einstellung inaktiviert ist und eine Anrufübergabe fehlschlägt, initiiert {{site.data.keyword.iva_short}} einen Dialogwechsel. Dann kann {{site.data.keyword.conversationshort}} den Anruf entweder unterbrechen oder an ein anderes Ziel übergeben, abhängig von der Dialogkonfiguration.
* **{{site.data.keyword.conversationshort}} bei Netzereignissen benachrichtigen**: Wenn diese Option aktiviert ist und ein Netzfehler festgestellt wird, initiiert {{site.data.keyword.iva_short}} einen Wechsel zum {{site.data.keyword.conversationshort}}-Service mit dem Text "vgwNetworkWarningMessage". Die Statusvariable `vgwNetworkWarnings` enthält eine Liste der Netzereignisse, die während des aktuellen Dialogwechsels aufgetreten sind. Wenn diese Option inaktiviert ist, wird eine Liste der Netzereignisse, die während des aktuellen Dialogwechsels aufgetreten sind, in der Statusvariablen `vgwNetworkWarning` des nächsten Wechselereignisses gesendet. Standardmäßig aktiviert.
