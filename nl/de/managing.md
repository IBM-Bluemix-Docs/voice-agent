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


# Sprachagenten verwalten
{: #managing}

Das Erstellen, Bearbeiten, Klonen, Konfigurieren und Entfernen von Sprachagenten erfolgt im Dashboard _Verwalten_. Sie können über mehrere Sprachagenten verfügen, jedoch muss jeder einen eindeutigen Namen und eine eindeutige Telefonnummer besitzen.
{: shortdesc}

<!-- Title should be task oriented and descriptive-->

## Sprachagenten erstellen
{: #config_instance}

Wenn Sie einen Sprachagenten erstellen, sucht {{site.data.keyword.iva_short}} automatisch nach allen verfügbaren Watson-Serviceinstanzen, die Sie verwenden können. Ist ein Service nicht verfügbar, können Sie ihn wahlweise mit dem Sprachagenten erstellen oder eine Verbindung zu Services in einem anderen {{site.data.keyword.Bluemix_short}}-Kontoarbeitsbereich herstellen.

1. Klicken Sie auf **Sprachagenten erstellen**.

1. In **Name** geben Sie einen eindeutigen Namen für Ihren Sprachagenten an. Beispiel: `Kundendienst - Nordamerika`.

1. Als **Telefonnummer** fügen Sie die Nummer von Ihrem SIP-Trunk, einschließlich Landes- und Ortsvorwahl, hinzu. Für eine 800-er Nummer in den Vereinigten Staaten z. B. geben Sie die Nummer mit `18883334444` an. Die Telefonnummer darf Leerzeichen und die Zeichen `+ ( ) -` enthalten.

1. Optional beschreiben Sie Ihren Sprachagenten.

1. Wenn Sie die Anrufübergabe aktivieren möchten, können Sie einen Beendigungs-URI für das **Übergabeziel** konfigurieren. Weitere Informationen finden Sie in [Anrufübergabe einrichten](call-transfer.html). Verwenden Sie keine persönliche Telefonnummer für das Übergabeziel.

1. Konfigurieren Sie die Verbindungen zu Ihren Watson-Serviceinstanzen. Sie können Verbindungen zu mehreren Watson-Serviceinstanzen herstellen, indem Sie sowohl für **Standort 1** als auch für **Standort 2** Verbindungen konfigurieren. Wenn Verbindungen zu mehreren Serviceinstanzen vorhanden sind, kann der Sprachagent bei einem Ausfall zu einer alternativen Serviceinstanz wechseln. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](#add_location).

    **Wichtig**: Bei Instanzen des Typs _Trial_ und _Lite_ ist eine Verbindung nur zu dem Standort möglich, an dem die {{site.data.keyword.iva_short}}-Serviceinstanz erstellt wurde. Beim zweiten Standort handelt es sich nicht um einen zweiten Sprachagenten. Er dient nur als Sicherung für Disaster-Recovery-Situationen.

1. Konfigurieren Sie unter **{{site.data.keyword.conversationshort}}** die Verbindung zur {{site.data.keyword.conversationshort}}-Serviceinstanz, indem Sie auf **Standort 1 aktivieren** oder **Standort 2 aktivieren** klicken. Sie können {{site.data.keyword.conversationshort}}-Instanzen oder {{site.data.keyword.virtualagentfull}}-Instanzen in {{site.data.keyword.Bluemix_notm}}-Konten verwenden, deren Eigner Sie sind oder deren Eigner ein anderer Benutzer ist. Sie können auch zu jeder dieser Optionen eine Verbindung über eine Service-Orchestrierungsengine herstellen.

    * Wenn Sie in der Region 'USA (Süden)' oder 'USA (Osten)' einen Sprachagenten erstellen und nicht über eine {{site.data.keyword.conversationshort}}-Serviceinstanz verfügen, können Sie über das Menü **Serviceinstanz** eine Serviceinstanz erstellen.
    * Alternativ können Sie Verbindungen zu anderen Quellen eines {{site.data.keyword.conversationshort}}-Dialogs herstellen, indem Sie den [**Servicetyp**](#other_service) ändern.
    * Wenn Sie mehrere Servicestandorte konfigurieren möchten, klicken Sie auf die Option für den anderen Standort und wählen Sie **Standort aktivieren** aus, um die Verbindung zur anderen {{site.data.keyword.conversationshort}}-Instanz zu konfigurieren. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](#add_location).

1. Überprüfen Sie unter **{{site.data.keyword.speechtotextshort}}** die Standardkonfiguration für die {{site.data.keyword.speechtotextshort}}-Serviceinstanz, indem Sie auf **Standort 1 aktivieren** oder **Standort 2 aktivieren** klicken. Sie können die Konfiguration wie folgt anpassen: 
    * Wenn Sie in der Region 'USA (Süden)' oder 'USA (Osten)' einen Sprachagenten erstellen und nicht über eine {{site.data.keyword.speechtotextshort}}-Serviceinstanz verfügen, können Sie über das Menü **Serviceinstanz** eine Serviceinstanz erstellen.
    * Wählen Sie den [**Servicetyp**](#other_service) aus, um Ihren Sprachagenten mit einer {{site.data.keyword.speechtotextshort}}-Instanz in einem anderen {{site.data.keyword.Bluemix_notm}} zu verbinden. 
    * Wenn Sie mehrere Servicestandorte konfigurieren möchten, klicken Sie auf die Option für den anderen Standort und wählen Sie **Standort aktivieren** aus, um die Verbindung zur anderen {{site.data.keyword.speechtotextshort}}-Instanz zu konfigurieren. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](#add_location).
    * **Wichtig:** {{site.data.keyword.iva_short}} unterstützt nur Narrowband-Modelle. 

1. Überprüfen Sie unter **{{site.data.keyword.texttospeechshort}}** die Standardkonfiguration für die {{site.data.keyword.texttospeechshort}}-Serviceinstanz, indem Sie auf **Standort 1 aktivieren** oder **Standort 2 aktivieren** klicken.  
    * Wenn Sie in der Region 'USA (Süden)' oder 'USA (Osten)' einen Sprachagenten erstellen und nicht über eine {{site.data.keyword.texttospeechshort}}-Serviceinstanz verfügen, können Sie über das Menü **Serviceinstanz** eine Serviceinstanz erstellen. 
    * Sie können Ihren Sprachagenten auch mit einer {{site.data.keyword.texttospeechshort}}-Instanz in einem anderen {{site.data.keyword.Bluemix_notm}}-Kontobereich verbinden, indem Sie den [**Servicetyp**](#other_service) ändern. 
    * Wenn Sie mehrere Servicestandorte konfigurieren möchten, klicken Sie auf die Option für den anderen Standort und wählen Sie **Standort aktivieren** aus, um die Verbindung zur anderen {{site.data.keyword.texttospeechshort}}-Instanz zu konfigurieren. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](#add_location).

1. Sie können auch die Ereignisweiterleitung aktivieren, um Informationen zu den von Ihren Sprachagenten verarbeiteten Anrufen in {{site.data.keyword.cloudantfull}} zu erfassen. Informationen hierzu finden Sie in [Ereignisweiterleitung für Sprachagenten aktivieren](event-forwarding.html). Weitere Konfigurationsoptionen finden Sie in [Sprachagenten konfigurieren](#configure_va).

1. Klicken Sie auf **Sprachagenten erstellen**, um Ihren Sprachagenten und eventuell neue Services zu erstellen.

Nach dem Erstellen des Sprachagenten testen Sie Ihren Sprachagenten, indem Sie eine Telefonnummer anrufen. Details zu Ihrem Telefonanruf können Sie über das Dashboard _Nutzung_ anzeigen.  

## Maximalwert für gleichzeitige Verbindungen bearbeiten
{: #edit_concurrency}

Wenn Sie den _Standardplan_ verwenden, können Sie die maximale Anzahl gleichzeitiger Verbindungen gegenüber den Standardeinstellungen ändern. In allen Plänen sind zwei gleichzeitige Verbindungen kostenfrei enthalten. Weitere Informationen finden Sie in [Preisstrukturpläne](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

Im Dashboard _Verwalten_ wird die maximale Anzahl gleichzeitiger Verbindungen, die im Rahmen Ihres aufgeführten Plans zulässig sind, im Feld **Maximale Anzahl gleichzeitiger Verbindungen** angezeigt. Darüber hinaus wird die maximale Anzahl gleichzeitiger Verbindungen, die von Ihren Sprachagenten im laufenden Monat genutzt wurden, im Feld _Genutzte maximale Anzahl gleichzeitiger Verbindungen_ angezeigt.

Wenn Sie die maximale Anzahl gleichzeitiger Verbindungen in Ihrem Plan ändern möchten, klicken Sie auf das Symbol **Bearbeiten**. Wählen Sie im Fenster _Maximale Anzahl gleichzeitiger Verbindungen bearbeiten_ die gewünschte maximale Anzahl gleichzeitiger Verbindungen aus und klicken Sie auf **Speichern**. Der Mindestwert für die Anzahl gleichzeitiger Anrufe, der im Self-Service-Verfahren festgelegt werden kann, ist 10, der Höchstwert 50. Wenn Sie mehr als 50 gleichzeitige Verbindungen für den Sprachagenten benötigen, lesen Sie die Informationen in [Unterstützung für Netzkonfiguration anfordern](connect-SIP.html#request-setup).

### Preisinformationen für gleichzeitige Verbindungen
{: #concurrent-charge}

  * In den Plänen des Typs _Lite_, _Trial_ und _Standard_ sind 2 gebührenfreie gleichzeitige Verbindungen enthalten.
  * _Premium_-Pläne werden pro Instanz angepasst.
  * In einem Plan des Typs _Standard_ ist eine Mindestkapazität von 10 gleichzeitigen Verbindungen verfügbar.
  * Die Nutzung gleichzeitiger Verbindungen wird anteilmäßig pro Monat umgelegt. Wenn Sie mehr als 2 gleichzeitige Verbindungen an einem Tag nutzen, werden Gebühren auf der Basis einer Tagesrate berechnet.
  * Bei der Verwendung eines _Standard_- oder _Premium_-Plans können Sie eine größere Kapazität für gleichzeitige Verbindungen kaufen.
  * Für die maximale Kapazität gleichzeitiger Verbindungen, die Sie an einem Tag nutzen, werden Gebühren auf der Basis einer Tagesrate berechnet. Beispiel: Der Plan unterstützt 2 kostenfreie gleichzeitige Verbindungen und Sie legen einen Maximalwert von 12 Verbindungen fest. Wenn Sie nur 5 an einem Tag nutzen, werden Gebühren für 3 berechnet.

Weitere Informationen zu Plänen, Raten und Features finden Sie in [Preisstrukturpläne](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

## Sprachagenten bearbeiten
{: #edit_va}

Durch Bearbeiten können Sie Änderungen an vorhandenen Sprachagenten vornehmen. Zum Bearbeiten eines Sprachagenten klicken Sie in der Liste der Optionen für den Sprachagenten auf **Agenten bearbeiten**. Ändern Sie die Konfiguration und speichern Sie die Änderungen.

## Sprachagenten klonen
{: #clone_va}

Wenn Sie einen Sprachagenten klonen, werden die gesamten Konfigurationen für die Watson-Services auf den neuen Agenten kopiert. Zum Klonen eines Sprachagenten klicken Sie in der Liste der Optionen für den Sprachagenten auf **Agenten klonen**. Geben Sie Ihrem Sprachagenten einen eindeutigen Namen und eine eindeutige Telefonnummer, ändern Sie alle Konfigurationsoptionen nach Bedarf und speichern Sie die Änderungen.

## Sprachagenten löschen
{: #delete_va}

Das Löschen eines Sprachagenten kann sinnvoll sein, um eine Telefonnummer freizugeben. Für eine einzelne Telefonnummer können Sie nur jeweils einen Sprachagenten haben. Um eine Telefonnummer für einen anderen Sprachagenten zu verwenden, müssen Sie zuerst einen eventuell vorhandenen Sprachagenten löschen, der diese Telefonnummer verwendet.

Zum Löschen eines Sprachagenten klicken Sie in der Liste der Optionen für den Sprachagenten auf **Agenten löschen**. Der Sprachagent wird aus der Liste der Sprachagenten entfernt.

## Sprachagenten konfigurieren
{: #configure_va}

### Erweiterte Optionen konfigurieren
{: #config-advanced}

Beim Erstellen oder Klonen eines Sprachagenten können Sie auf **Erweiterte Optionen anzeigen** klicken, um die folgenden erweiterten Konfigurationsoptionen aufzurufen.

* **Antwortnachricht bei {{site.data.keyword.conversationshort}}-Fehler (optional)**: Die Standardantwortnachricht, die an den Nachrichtenempfänger gesendet wird, falls der Anruf nicht mit {{site.data.keyword.conversationshort}} verbunden werden kann.
* **Antwortnachricht bei Anrufübergabefehler (optional)**: Die Standardantwortnachricht, die an den Anrufer gestreamt wird, falls die Anrufübergabe fehlschlägt.
* **Angepasster SIP INVITE-Header (optional)**: Gibt den angepassten SIP-Header an, der aus eingehenden SIP INVITE-Anforderungen extrahiert werden soll.
* **Vorläufige Antwort mit dem Statuscode 'Ringing' von {{site.data.keyword.iva_short}}** senden: Sendet eine Antwort mit dem Statuscode `180 - Ringing`, während {{site.data.keyword.iva_short}} einen eingehenden Anruf verarbeitet. Standardmäßig aktiviert.
* **Anruf während der Übergabe in die Warteschleife legen**: Legt den Anruf während der Übergabe in die Warteschleife. Standardmäßig aktiviert.
* **Anruf bei fehlgeschlagener Übergabe unterbrechen**: Bestimmt, ob der Anruf bei einer fehlgeschlagenen Anrufübergabe unterbrochen werden soll.  Standardmäßig aktiviert. Wenn die Einstellung inaktiviert ist und eine Anrufübergabe fehlschlägt, initiiert {{site.data.keyword.iva_short}} einen Dialogwechsel. Dann kann {{site.data.keyword.conversationshort}} den Anruf entweder unterbrechen oder an ein anderes Ziel übergeben, abhängig von der Dialogkonfiguration.
* **{{site.data.keyword.conversationshort}} bei Netzereignissen benachrichtigen**: Wenn diese Option aktiviert ist und ein Netzfehler festgestellt wird, initiiert {{site.data.keyword.iva_short}} einen Wechsel zum {{site.data.keyword.conversationshort}}-Service mit dem Text "vgwNetworkWarningMessage". Die Statusvariable `vgwNetworkWarnings` enthält eine Liste der Netzereignisse, die während des aktuellen Dialogwechsels aufgetreten sind. Wenn diese Option inaktiviert ist, wird eine Liste der Netzereignisse, die während des aktuellen Dialogwechsels aufgetreten sind, in der Statusvariablen `vgwNetworkWarning` des nächsten Wechselereignisses gesendet. Standardmäßig aktiviert.

### Mehrere Watson-Servicestandorte hinzufügen
{: #add_location}

Wenn Sie über eine _Standard_- oder _Premium_-Instanz verfügen, können Sie den Sprachagenten aus Gründen der Serviceredundanz mit mehreren Watson-Services an verschiedenen Standorten verbinden. Mit _Trial_- und _Lite_-Instanzen kann nur eine Verbindung zu dem Standort hergestellt werden, an dem die {{site.data.keyword.iva_short}}-Serviceinstanz erstellt wurde. Beim zweiten Standort handelt es sich nicht um einen zweiten Sprachagenten. Er dient nur als Sicherung für Disaster-Recovery-Situationen.

Der Sprachagent verwendet die Watson-Serviceinstanzen in der Reihenfolge der jeweiligen geografischen Distanz. Beispiel: Sie können einen Sprachagenten in der Region 'USA (Osten)' und die {{site.data.keyword.conversationshort}}-Services in den Regionen 'USA (Süden)' und 'Sydney, Australien' erstellen. Der Sprachagent verwendet die {{site.data.keyword.conversationshort}}-Region 'USA (Süden)', da diese geografisch näher an 'USA (Osten)' liegt als 'Sydney, Australien'. Wenn Sie Verbindungen zu Watson-Services in mehreren Regionen einrichten und ein Watson-Service an einem Standort offline ist, kann der Sprachagent den redundanten Service verwenden.

Sie können einen Watson-Servicestandort zu jedem beliebigen Zeitpunkt zur Konfiguration Ihres Sprachagenten hinzufügen. Informationen zur Herstellung von Verbindungen zu Serviceinstanzen an mehreren Standorten beim Erstellen des Sprachagenten finden Sie in [Sprachagenten erstellen](#creating).

Wenn Sie einen Watson-Servicestandort zu einem vorhandenen Sprachagenten hinzufügen möchten, klicken Sie auf die Option **Agenten bearbeiten** für den Sprachagenten, den Sie konfigurieren möchten. Wählen Sie **Standort 1** oder **Standort 2** für die {{site.data.keyword.conversationshort}}-, {{site.data.keyword.texttospeechshort}}- oder {{site.data.keyword.speechtotextshort}}-Instanz aus, die Sie verbinden möchten, und fügen Sie Ihre Konfigurationsinformationen hinzu. Sie können Watson-Serviceinstanzen in Ihrem Arbeitsbereich oder in anderen Arbeitsbereichen verwenden. Informationen hierzu finden Sie in [Serviceinstanzen in anderen {{site.data.keyword.Bluemix_notm}}-Arbeitsbereichen verwenden](#other_services).

**Denken Sie daran**: Zum Zweck der Serviceredundanz müssen Sie Watson-Serviceinstanzen in verschiedenen Serviceregionen für verschiedene Standorte verwenden.

Sie können einen Standort über das Feld **Standort aktivieren** aktivieren oder inaktivieren. **Standort 1** ist standardmäßig aktiviert, **Standort 2** ist standardmäßig inaktiviert. Für jeden Watson-Service muss mindestens ein Standort aktiviert sein.

### Serviceinstanzen in anderen {{site.data.keyword.Bluemix_notm}}-Arbeitsbereichen verwenden
{: #other_service}

Sie können Ihren Sprachagenten für die Verwendung von {{site.data.keyword.conversationshort}}-, {{site.data.keyword.speechtotextshort}}- oder {{site.data.keyword.speechtotextshort}}-Serviceinstanzen, die zu Arbeitsbereichen in anderen {{site.data.keyword.Bluemix_short}}-Konten gehören, konfigurieren. Für die Verbindung Ihres Sprachagenten mit anderen Serviceinstanzen können Sie entweder den Benutzernamen und die Kennwortberechtigungsnachweise oder einen API-Schlüssel für Ihre Serviceinstanzen verwenden.

1. Wählen Sie den **Servicetyp** und die **Region** aus.

1. Wählen Sie entweder **Benutzername und Kennwort** oder **API-Schlüssel** aus und geben Sie Ihre Serviceberechtigungsnachweise ein.
  Zum Suchen dieser Werte wechseln Sie zu der Serviceinstanz, die Sie konfigurieren möchten, und wählen **Serviceberechtigungsnachweise** und danach **Berechtigungsnachweise anzeigen** aus.

  * **Benutzername und Kennwort**: Konfigurieren Sie in den Feldern **URL**, **Benutzername** und **Kennwort** die Berechtigungsnachweise für Ihre {{site.data.keyword.conversationshort}}-, {{site.data.keyword.speechtotextshort}}- oder {{site.data.keyword.texttospeechshort}}-Serviceinstanz.
  * **API-Schlüssel**: Konfigurieren Sie in den Feldern **URL** und **API-Schlüssel** die Berechtigungsnachweise für Ihre {{site.data.keyword.conversationshort}}-, {{site.data.keyword.speechtotextshort}}- oder {{site.data.keyword.texttospeechshort}}-Serviceinstanz.

  Die Berechtigungsnachweise sind nicht Ihr {{site.data.keyword.Bluemix_notm}}-Benutzername und -Kennwort, sondern verschlüsselte Berechtigungsnachweise für die jeweilige Serviceinstanz.
  {:tip}

1. Geben Sie die Serviceinstanzinformationen ein.

  * **{{site.data.keyword.conversationshort}}:** Im Feld **Arbeitsbereich-ID** geben Sie die ID des Arbeitsbereichs ein, den Sie mit Ihrem Sprachagenten verwenden möchten. Zum Suchen der Arbeitsbereich-ID starten Sie das Tool und den Arbeitsbereich, den Sie integrieren möchten, klicken auf das Symbol 'Aktionen' (**&vellip;**) und wählen **Details anzeigen** aus.
  * **{{site.data.keyword.speechtotextshort}}:** Im Feld **Modell** geben Sie die Sprache für die Sprachausgabe und das Format für Ihren Service an. {{site.data.keyword.iva_short}} unterstützt nur Narrowband-Modelle.
  * **{{site.data.keyword.texttospeechshort}}:** Wählen Sie im Feld **Sprachunterstützung** die Sprache und die Sprachunterstützung aus, die Ihr Service verwendet. Für Ihren Service müssen Sie eine Sprachunterstützung angeben.

**Bitte beachten:** Damit Ihr Sprachagent funktioniert, müssen Sie {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} und {{site.data.keyword.texttospeechshort}} für dieselbe Sprache konfigurieren. Weitere Informationen finden Sie in [Unterstützte Sprachen](about.html#supported-languages).

### {{site.data.keyword.conversationshort}} für Ihren Sprachagenten konfigurieren
{: #conversation_va}

Als Alternative zum Konfigurieren einer {{site.data.keyword.conversationshort}}-Serviceinstanz können Sie eine Verbindung zu einer Service-Orchestrierungsengine (SOE) oder zu Watson {{site.data.keyword.virtualagentshort}} herstellen.

* **Service-Orchestrierungsengine**: Stellen Sie eine Verbindung zu einem {{site.data.keyword.conversationshort}}-Arbeitsbereich oder zu {{site.data.keyword.virtualagentshort}} über eine [Service-Orchestrierungsengine (SOE)](about.html#arch-soe) her. Eine SOE fängt Nachrichten zum und vom Service ab, sodass Sie sie mithilfe von APIs von Drittanbietern modifizieren können.

  Geben Sie im Feld **URL** die vollständige URL zu Ihrem SOE-Arbeitsbereich ein, z. B. `https://iva-soesample.myorg.net/SOE/myWorkspace`. Wenn die SOE Ihre Authentifizierung anfordert (empfohlen), geben Sie in den Benutzernamen und Kennwort in den entsprechenden Feldern an.

  **Wichtig**: Aus Gründen der Datensicherheit müssen Sie sicherstellen, dass Sie für Ihren SOE-Arbeitsbereich eine sichere URL verwenden. Verwenden Sie `https:` anstelle von `http:` sowie obligatorische Authentifizierung. Weitere Informationen zu Sicherheitsaspekten finden Sie unter [Informationssicherheit und Datenschutz](infosec.html). 

* **Watson {{site.data.keyword.virtualagentshort}}**: Stellen Sie eine Verbindung zu einem {{site.data.keyword.virtualagentshort}}-Chatbot statt zu einem {{site.data.keyword.conversationshort}}-Arbeitsbereich her. [{{site.data.keyword.virtualagentshort}}](../virtual-agent/getting-started.html#getting-started) ist auf dem {{site.data.keyword.conversationshort}}-Service aufgebaut, bietet aber vortrainierte Funktionen, sodass Sie ohne jegliche Erfahrung mit maschinellem Lernen gleich einsteigen können.

  Geben Sie im Feld **URL** den URL-Berechtigungsnachweis für {{site.data.keyword.virtualagentshort}} an, z. B. `https://api.ibm.com/virtualagent/run/api`. Geben Sie in den Feldern **Client-ID** und **Geheimer Clientschlüssel** die Authentifizierungsschlüssel ein, die den Headerfeldern `X-IBM-Client-Id` und `X-IBM-Client-Secret` für API-Anrufe zugeordnet sind. Im Feld **Bot-ID** geben Sie die ID für den Bot ein, der für diesen Sprachagenten verwendet werden soll. Weitere Informationen dazu, wie man diese Werte sucht, finden Sie unter [Agenten veröffentlichen](../virtual-agent/publish.html) in der {{site.data.keyword.virtualagentshort}}-Dokumentation.
