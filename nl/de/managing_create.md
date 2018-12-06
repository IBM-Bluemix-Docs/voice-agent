---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Sprachagenten über das Dashboard _Verwalten_ erstellen
{: #config_instance}

Nachdem Sie Ihren {{site.data.keyword.iva_full}}-Service erstellt haben, können Sie einzelne Sprachagenten über das Dashboard _Verwalten_ erstellen.
{: shortdesc}


## Sprachagenten erstellen
{: #create_instance}

Wenn Sie einen Sprachagenten erstellen, sucht {{site.data.keyword.iva_short}} automatisch nach allen verfügbaren Watson-Serviceinstanzen, die Sie verwenden können. Ist ein Service nicht verfügbar, können Sie ihn wahlweise mit dem Sprachagenten erstellen oder eine Verbindung zu Services in einem anderen {{site.data.keyword.Bluemix_short}}-Kontoarbeitsbereich herstellen. Es ist auch möglich, eine Verbindung zwischen Ihrem Sprachagenten und einer Service-Orchestrierungsengine-, einer Google Speech to Text- oder einer Google Text to Speech-Instanz herzustellen.

1. Navigieren Sie zur Registerkarte _Sprachagenten_ auf dem Dashboard _Verwalten_ und klicken Sie auf **Sprachagenten erstellen**.

1. In **Name** geben Sie einen eindeutigen Namen für Ihren Sprachagenten an. Beispiel: `Kundendienst - Nordamerika`.

1. Als **Telefonnummer** fügen Sie die Nummer von Ihrem SIP-Trunk, einschließlich Landes- und Ortsvorwahl, hinzu. Für eine 800-er Nummer in den Vereinigten Staaten z. B. geben Sie die Nummer mit `18883334444` an. Die Telefonnummer darf Leerzeichen und die Zeichen `+ ( ) -` enthalten.

1. Optional beschreiben Sie Ihren Sprachagenten.

1. Wenn Sie die Anrufübergabe aktivieren möchten, geben Sie den Beendigungs-URI für das **Übergabestandardziel** ein. Informationen zum Konfigurieren eines Beendigungs-URI finden Sie im Abschnitt zum [Einrichten einer Anrufübergabe](call-transfer.html). Verwenden Sie keine persönliche Telefonnummer für das Übergabeziel.

1. Konfigurieren Sie die Verbindungen zu Ihren Watson-Serviceinstanzen. Sie können Verbindungen zu mehreren Watson-Serviceinstanzen herstellen, indem Sie sowohl für **Standort 1** als auch für **Standort 2** Verbindungen konfigurieren. Wenn Verbindungen zu mehreren Serviceinstanzen vorhanden sind, kann der Sprachagent bei einem Ausfall zu einer alternativen Serviceinstanz wechseln. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](managing_disaster_recovery.html#add_location).

1. Konfigurieren Sie unter **{{site.data.keyword.conversationshort}}** die Verbindung zur {{site.data.keyword.conversationshort}}-Serviceinstanz, indem Sie auf **Standort 1** oder **Standort 2** klicken und den ausgewählten Standort aktivieren. Sie können {{site.data.keyword.conversationshort}}-Instanzen in {{site.data.keyword.Bluemix_notm}}-Konten verwenden, deren Eigner Sie sind oder deren Eigner ein anderer Benutzer ist. Sie können auch zu jeder dieser Optionen eine Verbindung über eine Service-Orchestrierungsengine herstellen.

   * Wenn Sie in der Region 'Dallas' oder 'Washington DC' einen Sprachagenten erstellen und nicht über eine {{site.data.keyword.conversationshort}}-Serviceinstanz verfügen, können Sie über das Menü **Serviceinstanz** eine Serviceinstanz erstellen.
   * Alternativ können Sie Verbindungen zu anderen Quellen eines {{site.data.keyword.conversationshort}}-Dialogs oder zu einer SOE herstellen, indem Sie den [**Servicetyp**](managing_other.html#other_service) ändern.
   * Wenn Sie mehrere Servicestandorte konfigurieren möchten, klicken Sie auf die Option für den anderen Standort und wählen Sie **Standort aktivieren** aus, um die Verbindung zur anderen {{site.data.keyword.conversationshort}}-Instanz zu konfigurieren. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](managing_disaster_recovery.html#add_location).

1. Überprüfen Sie unter **{{site.data.keyword.speechtotextshort}}** die Standardkonfiguration für die {{site.data.keyword.speechtotextshort}}-Serviceinstanz, indem Sie **Standort 1** oder **Standort 2** auswählen und diesen Standort aktivieren. Sie können Ihre Konfiguration wie folgt anpassen.
   * Wenn Sie eine Verbindung zwischen Ihrem Sprachagenten und einer vorhandenen Instanz als **Servicetyp** herstellen möchten, wählen Sie **Eigene Speech-to-Text-Instanz** aus. Wählen Sie anschließend bei **Modelltyp auswählen** die Option **Schmalband**, **Breitband** oder **Schmal- und Breitband** sowie das Sprachmodell aus.
   * Wenn Sie in der Region 'Dallas' oder 'Washington DC' einen Sprachagenten erstellen und nicht über eine {{site.data.keyword.speechtotextshort}}-Serviceinstanz verfügen, können Sie über das Menü **Serviceinstanz** eine Serviceinstanz erstellen.
   * Wählen Sie als **Servicetyp** entweder eine [{{site.data.keyword.speechtotextshort}}-Instanz in einem anderen {{site.data.keyword.Bluemix_notm}}-Arbeitsbereich](managing_other.html) oder einen [Speech-to-Text-Service eines anderen Anbieters](managing_third_party.html) aus, z. B. Google Cloud Speech-to-Text.
   * Wenn Sie mehrere Servicestandorte konfigurieren möchten, klicken Sie auf die Option für den anderen Standort und wählen Sie **Standort aktivieren** aus, um die Verbindung zur anderen {{site.data.keyword.speechtotextshort}}-Instanz zu konfigurieren. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](managing_disaster_recovery.html).

1. Überprüfen Sie unter **{{site.data.keyword.texttospeechshort}}** die Standardkonfiguration für die {{site.data.keyword.texttospeechshort}}-Serviceinstanz, indem Sie auf **Standort 1** oder **Standort 2** klicken und diesen Standort aktivieren. Sie können Ihre Konfiguration wie folgt anpassen.
   * Wenn Sie in der Region 'Dallas' oder 'Washington DC' einen Sprachagenten erstellen und nicht über eine {{site.data.keyword.texttospeechshort}}-Serviceinstanz verfügen, können Sie über das Menü **Serviceinstanz** eine Serviceinstanz erstellen.
   * Wählen Sie als **Servicetyp** entweder eine [{{site.data.keyword.texttospeechshort}}-Instanz in einem anderen {{site.data.keyword.Bluemix_notm}}-Arbeitsbereich](managing_other.html) oder einen [Text-to-Speech-Service eines anderen Anbieters](managing_third_party.html) aus, z. B. Google Cloud Text-to-Speech.
   * Wenn Sie mehrere Servicestandorte konfigurieren möchten, klicken Sie auf die Option für den anderen Standort und wählen Sie **Standort aktivieren** aus, um die Verbindung zur anderen {{site.data.keyword.texttospeechshort}}-Instanz zu konfigurieren. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](managing_disaster_recovery.html).

1. Sie können auch die Ereignisweiterleitung aktivieren, um Informationen zu den von Ihren Sprachagenten verarbeiteten Anrufen in {{site.data.keyword.cloudantfull}} zu erfassen. Informationen hierzu finden Sie in [Ereignisweiterleitung für Sprachagenten aktivieren](event-forwarding.html). Weitere Konfigurationsoptionen finden Sie in [Sprachagenten konfigurieren](managing.html#configure_va).

1. Klicken Sie auf **Sprachagenten erstellen**, um Ihren Sprachagenten und eventuell neue Services zu erstellen.

Nach dem Erstellen des Sprachagenten testen Sie Ihren Sprachagenten, indem Sie eine Telefonnummer anrufen. Details zu Ihrem Telefonanruf können Sie über das Dashboard _Nutzung_ anzeigen.  
