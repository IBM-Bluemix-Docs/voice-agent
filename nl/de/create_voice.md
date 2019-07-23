---

copyright:
  years: 2019
lastupdated: "2019-06-24"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Sprachagenten erstellen
{: #config_instance}

Nachdem Sie Ihren {{site.data.keyword.iva_full}}-Service erstellt haben, können Sie einzelne Sprachagenten über das Dashboard _Verwalten_ erstellen.
{: shortdesc}

Wenn Sie einen Sprachagenten erstellen, sucht {{site.data.keyword.iva_short}} automatisch nach allen verfügbaren Watson-Serviceinstanzen, die Sie verwenden können. Falls keine Serviceinstanz verfügbar ist, können Sie sie zusammen mit dem Sprachagenten erstellen oder eine Verbindung zu Services in einem anderen {{site.data.keyword.Bluemix_short}}-Konto herstellen. Es ist auch möglich, eine Verbindung zwischen Ihrem Sprachagenten und einer Service-Orchestrierungsengine-, einer Google Speech to Text- oder einer Google Text to Speech-Instanz herzustellen.

1. Navigieren Sie zur Registerkarte _Sprachagenten_ auf dem Dashboard _Verwalten_ und klicken Sie auf **Sprachagenten erstellen**.

1. Wählen Sie bei **Agententyp** die Einstellung _Sprache_ aus.

1. In **Name** geben Sie einen eindeutigen Namen für Ihren Sprachagenten an. Beispiel: `Kundendienst - Nordamerika`. Der Name kann aus bis zu 64 Zeichen bestehen.

1. Als **Telefonnummer** fügen Sie die Nummer von Ihrem SIP-Trunk, einschließlich Landes- und Ortsvorwahl, hinzu. Für eine 800-er Nummer in den Vereinigten Staaten z. B. geben Sie die Nummer mit `18883334444` an. Die Telefonnummer kann maximal 30 Zeichen umfassen, einschließlich Leerzeichen und sowie die Zeichen + ().

1. Standardmäßig wird diese Telefonnummer als **Primärnummer** für den Service festgelegt. Dabei handelt es sich einfach um die erste Nummer, die Ihnen angezeigt wird, wenn eine Liste von Nummern vorhandne ist. Die Primärnummer dient nur Anzeigezwecken. Informationen dazu, wie Sie die primäre Nummer ändern, finden Sie in [Primäre Nummer festlegen](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

1. Geben Sie optional eine maximal 256 Zeichen lange Beschreibung für Ihren Sprachagenten ein.

1. Sie können auch mehrere Nummern zu einem Sprachagenten hinzufügen, indem Sie neben **Telefonnummer** auf **Verwalten** klicken. Informationen zum Einrichten und Zuordnen mehrerer Rufnummern finden Sie in [Mehrere Telefonnummern in einer Voice Agent-Instanz konfigurieren](/docs/services/voice-agent?topic=voice-agent-multi_num). Im Dialogfenster **Verwalten** können Sie die Nummern auch bearbeiten und Beschreibungen für die einzelnen Nummern hinzufügen.
    
1. Wenn Sie alternativ die Nummern bearbeiten möchten, klicken Sie auf das grau abgeblendete Feld für die **Telefonnummer** oder klicken Sie auf **Verwalten**. Weitere Informationen finden Sie in [Nummer und/oder Beschreibung für mehrere Nummern bearbeiten](/docs/services/voice-agent?topic=voice-agent-multi_num#edit_num).
    
1. Geben Sie zum Aktivieren der Anrufübergabe den Beendigungs-URI für das **Standardübergabeziel** ein. Informationen zum Konfigurieren eines Beendigungs-URI finden Sie im Abschnitt zum [Einrichten einer Anrufübergabe](/docs/services/voice-agent?topic=voice-agent-call-transfer). Verwenden Sie keine persönliche Telefonnummer für das Übergabeziel. Der Beendigungs-URI für das **Standardübergabeziel** kann bis zu 256 Zeichen enthalten.
    
1. Konfigurieren Sie die Verbindungen zu Ihren Instanzen des Watson-Service. Sie können Verbindungen zu mehreren Watson-Serviceinstanzen herstellen, indem Sie sowohl für **Standort 1** als auch für **Standort 2** Verbindungen konfigurieren. Wenn Verbindungen zu mehreren Serviceinstanzen vorhanden sind, kann der Sprachagent bei einem Ausfall zu einer alternativen Serviceinstanz wechseln. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).
    
1. Konfigurieren Sie unter **Dialog** die Verbindung zu Ihrer {{site.data.keyword.conversationshort}}-Serviceinstanz, indem Sie auf **Standort 1** oder **Standort 2** klicken und den ausgewählten Standort aktivieren. Sie können {{site.data.keyword.conversationshort}}-Serviceinstanzen in {{site.data.keyword.Bluemix_notm}}-Konten verwenden, deren Eigner Sie sind oder deren Eigner ein anderer Benutzer ist. Sie können auch zu jeder dieser Optionen eine Verbindung über eine Service-Orchestrierungsengine herstellen.
    
   * Wenn Sie in der Region 'Dallas' oder 'Washington DC' einen Sprachagenten erstellen und nicht über eine {{site.data.keyword.conversationshort}}-Serviceinstanz verfügen, können Sie über das Menü **Serviceinstanz** eine Serviceinstanz erstellen.
   * Alternativ können Sie Verbindungen zu anderen Quellen eines {{site.data.keyword.conversationshort}}-Dialogs oder zu einer SOE herstellen, indem Sie den [**Servicetyp**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service) ändern.
   * Wenn Sie mehrere Servicestandorte konfigurieren möchten, klicken Sie auf die Option **Anderer Standort** und wählen Sie **Standort aktivieren** aus, um die Verbindung zur anderen {{site.data.keyword.conversationshort}}-Instanz zu konfigurieren. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).
    
1. Überprüfen Sie unter **{{site.data.keyword.speechtotextshort}}** die Standardkonfiguration für die {{site.data.keyword.speechtotextshort}}-Serviceinstanz, indem Sie **Standort 1** oder **Standort 2** auswählen und diesen Standort aktivieren. Sie können Ihre Konfiguration wie folgt anpassen.
   * Wenn Sie eine Verbindung zwischen Ihrem Sprachagenten und einer vorhandenen Instanz als **Servicetyp** herstellen möchten, wählen Sie **Eigene Speech-to-Text-Instanz** aus. Wählen Sie anschließend bei **Modelltyp auswählen** die Option **Schmalband**, **Breitband** oder **Schmal- und Breitband** sowie das Sprachmodell aus.
   * Wenn Sie in der Region 'Dallas' oder 'Washington DC' einen Sprachagenten erstellen und nicht über eine {{site.data.keyword.speechtotextshort}}-Serviceinstanz verfügen, können Sie über das Menü **Serviceinstanz** eine Serviceinstanz erstellen.
   * Wählen Sie als **Servicetyp** entweder eine [a {{site.data.keyword.speechtotextshort}}-Instanz in einem anderen {{site.data.keyword.Bluemix_notm}}-Workspace](/docs/services/voice-agent?topic=voice-agent-other_service) oder einen [Speech-to-Text-Service eines anderen Anbieters](/docs/services/voice-agent?topic=voice-agent-third-party#third-party) aus, wie z. B. Google Cloud Speech-to-Text.
   * Wenn Sie mehrere Servicestandorte konfigurieren möchten, klicken Sie auf die Option für den anderen Standort und wählen Sie **Standort aktivieren** aus, um die Verbindung zur anderen {{site.data.keyword.speechtotextshort}}-Instanz zu konfigurieren. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](/docs/services/voice-agent?topic=voice-agent-disaster-recovery).
    
1. Überprüfen Sie unter **{{site.data.keyword.texttospeechshort}}** die Standardkonfiguration für die {{site.data.keyword.texttospeechshort}}-Serviceinstanz, indem Sie auf **Standort 1** oder **Standort 2** klicken und diesen Standort aktivieren. Sie können Ihre Konfiguration wie folgt anpassen.
   * Wenn Sie in der Region 'Dallas' oder 'Washington DC' einen Sprachagenten erstellen und nicht über eine {{site.data.keyword.texttospeechshort}}-Serviceinstanz verfügen, können Sie über das Menü **Serviceinstanz** eine Serviceinstanz erstellen.
   * Wählen Sie als **Servicetyp** entweder eine [{{site.data.keyword.texttospeechshort}}-Instanz in einem anderen {{site.data.keyword.Bluemix_notm}}-Arbeitsbereich](/docs/services/voice-agent?topic=voice-agent-other_service) oder einen [Text-to-Speech-Service eines anderen Anbieters](/docs/services/voice-agent?topic=voice-agent-third-party) aus, z. B. Google Cloud Text-to-Speech.
   * Wenn Sie mehrere Servicestandorte konfigurieren möchten, klicken Sie auf die Option für den anderen Standort und wählen Sie **Standort aktivieren** aus, um die Verbindung zur anderen {{site.data.keyword.texttospeechshort}}-Instanz zu konfigurieren. Weitere Informationen finden Sie in [Mehrere Watson-Servicestandorte hinzufügen](/docs/services/voice-agent?topic=voice-agent-disaster-recovery).
      
1. Sie können auch die Ereignisweiterleitung aktivieren, um Informationen zu den von Ihren Sprachagenten verarbeiteten Anrufen in {{site.data.keyword.cloudantfull}} zu erfassen. Informationen hierzu finden Sie in [Ereignisweiterleitung für Sprachagenten aktivieren](/docs/services/voice-agent?topic=voice-agent-event_forwarding). Weitere Konfigurationsoptionen finden Sie in [Sprachagenten konfigurieren](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1. Klicken Sie auf **Sprachagenten erstellen**, um Ihren Sprachagenten und eventuell neue Services zu erstellen.

Nach dem Erstellen des Sprachagenten testen Sie Ihren Sprachagenten, indem Sie eine Telefonnummer anrufen. Details zu Ihrer Interaktion können Sie über das Dashboard _Nutzung_ anzeigen. Weitere Informationen enthält der Abschnitt [Nutzung und Protokolle anzeigen](/docs/services/voice-agent?topic=voice-agent-logging).   
