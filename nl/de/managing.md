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


# Serviceinstanzen und Sprachagenten verwalten
{: #managing}

Mithilfe des Dashboards _Verwalten_ können Sie Ihre Serviceinstanzkonfigurationen ändern und einzelne Sprachagenten erstellen, bearbeiten, klonen, konfigurieren oder entfernen. Sie können über mehrere Sprachagenten in Ihrer Serviceinstanz verfügen, jedoch muss jeder einen eindeutigen Namen und eine eindeutige Telefonnummer besitzen.
{: shortdesc}

## Zum eigenen Voice Agent-Service-Dashboard navigieren
{: #navigate_manage}

Sie finden das Dashboard _Verwalten_ im Dashboard Ihres {{site.data.keyword.Bluemix_notm}}-Kontos.

1. Rufen Sie das [Dashboard Ihres {{site.data.keyword.Bluemix_notm}}-Kontos](https://console.bluemix.net/dashboard/apps) auf.

1. Wählen Sie in der Liste der **Services** die **Voice Agent**-Serviceinstanz aus, um das Service-Dashboard auf der Registerkarte _Verwalten_ zu öffnen.

## Maximale Anzahl gleichzeitiger Verbindungen für Ihre Serviceinstanz bearbeiten
{: #edit_service}

In allen Plänen sind zwei gleichzeitige Verbindungen kostenfrei enthalten. Wenn Sie den _Standardplan_ oder den _Premiumplan_ verwenden, können Sie die [maximale Anzahl gleichzeitiger Verbindungen gegenüber den Standardeinstellungen ändern](managing_concurrency.html), und zwar über die Registerkarte _Instanzen_.


## Sprachagenten erstellen
{: #create_va}

[Erstellen Sie einen neuen Sprachagenten](managing_create.html), und zwar über die Registerkarte _Sprachagenten_ im Dashboard _Verwalten_.

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

## Sprachagenten konfigurieren
{: #configure_va}

Beim Erstellen, Klonen oder Bearbeiten eines Sprachagenten können Sie Änderungen an den Konfigurationseinstellungen für Ihren Sprachagenten sowie an den Verbindungen zu zugehörigen Services vornehmen.

* **[Mehrere Servicestandorte konfigurieren](managing_disaster_recovery.html):** Schließen Sie zur Unterstützung der Serviceredundanz mehrere Servicestandorte für Ihre verbundenen Services ein.
* **[Verbindung zu Sprach- und Textservices anderer Anbieter herstellen](managing_third_party.html):** Anstatt {{site.data.keyword.texttospeechshort}} oder {{site.data.keyword.speechtotextshort}} zu verwenden, können Sie eine Verbindung zwischen Ihrem Sprachagenten und APIs anderer Anbieter herstellen, z. B. Google Cloud Speech-to-Text.
* **[Services in anderen {{site.data.keyword.Bluemix_notm}}-Arbeitsbereichen verwenden](managing_other.html):** Sie können Ihren Sprachagenten für die Verwendung von {{site.data.keyword.conversationshort}}-, {{site.data.keyword.speechtotextshort}}- oder {{site.data.keyword.speechtotextshort}}-Serviceinstanzen konfigurieren, die zu Arbeitsbereichen in anderen {{site.data.keyword.Bluemix_short}}-Konten gehören.
* **[Watson Assistant mit einer Service-Orchestrierungsengine (SOE) konfigurieren](managing_SOE.html):** Sie können mithilfe einer Service-Orchestrierungsengine eine Verbindung zu einem {{site.data.keyword.conversationshort}}-Arbeitsbereich herstellen. Eine SOE fängt Nachrichten zum und vom Service ab, sodass Sie sie mithilfe von APIs von Drittanbietern modifizieren können.
* **[Ereignisweiterleitung für Sprachagenten aktivieren](event-forwarding.html):** Möglicherweise möchten Sie Anrufdaten von {{site.data.keyword.iva_short}} erfassen und analysieren, um die Natürlichkeit des Dialogs für den Anrufer zu verbessern. Jeder Sprachagent, den Sie erstellen, kann Berichte an eine angegebene {{site.data.keyword.cloudant_short_notm}} weiterleiten, die Sie verwalten.

## Erweiterte Optionen für den Sprachagenten konfigurieren
{: #config-advanced}

Beim Erstellen oder Klonen eines Sprachagenten können Sie auf **Erweiterte Optionen anzeigen** klicken, um die folgenden erweiterten Konfigurationsoptionen aufzurufen.

* **Antwortnachricht bei {{site.data.keyword.conversationshort}}-Fehler (optional)**: Die Standardantwortnachricht, die an den Nachrichtenempfänger gesendet wird, falls der Anruf nicht mit {{site.data.keyword.conversationshort}} verbunden werden kann.
* **Antwortnachricht bei Anrufübergabefehler (optional)**: Die Standardantwortnachricht, die an den Anrufer gestreamt wird, falls die Anrufübergabe fehlschlägt.
* **Angepasster SIP INVITE-Header (optional)**: Gibt den angepassten SIP-Header an, der aus eingehenden SIP INVITE-Anforderungen extrahiert werden soll.
* **Vorläufige Antwort mit dem Statuscode 'Ringing' von {{site.data.keyword.iva_short}}** senden: Sendet eine Antwort mit dem Statuscode `180 - Ringing`, während {{site.data.keyword.iva_short}} einen eingehenden Anruf verarbeitet. Standardmäßig aktiviert.
* **Anruf während der Übergabe in die Warteschleife legen**: Legt den Anruf während der Übergabe in die Warteschleife. Standardmäßig aktiviert.
* **Anruf bei fehlgeschlagener Übergabe unterbrechen**: Bestimmt, ob der Anruf bei einer fehlgeschlagenen Anrufübergabe unterbrochen werden soll.  Standardmäßig aktiviert. Wenn die Einstellung inaktiviert ist und eine Anrufübergabe fehlschlägt, initiiert {{site.data.keyword.iva_short}} einen Dialogwechsel. Dann kann {{site.data.keyword.conversationshort}} den Anruf entweder unterbrechen oder an ein anderes Ziel übergeben, abhängig von der Dialogkonfiguration.
* **{{site.data.keyword.conversationshort}} bei Netzereignissen benachrichtigen**: Wenn diese Option aktiviert ist und ein Netzfehler festgestellt wird, initiiert {{site.data.keyword.iva_short}} einen Wechsel zum {{site.data.keyword.conversationshort}}-Service mit dem Text "vgwNetworkWarningMessage". Die Statusvariable `vgwNetworkWarnings` enthält eine Liste der Netzereignisse, die während des aktuellen Dialogwechsels aufgetreten sind. Wenn diese Option inaktiviert ist, wird eine Liste der Netzereignisse, die während des aktuellen Dialogwechsels aufgetreten sind, in der Statusvariablen `vgwNetworkWarning` des nächsten Wechselereignisses gesendet. Standardmäßig aktiviert.
