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

# {{site.data.keyword.conversationshort}} mit einer Service-Orchestrierungsengine konfigurieren
{: #conversation_va}

Als Alternative zum Konfigurieren einer {{site.data.keyword.conversationshort}}-Serviceinstanz können Sie eine Verbindung zu einer Service-Orchestrierungsengine (SOE) herstellen.
{: shortdesc}

Sie können mithilfe einer [Service-Orchestrierungsengine (SOE)](about.html#arch-soe) eine Verbindung zu einem {{site.data.keyword.conversationshort}}-Arbeitsbereich herstellen. Eine SOE fängt Nachrichten zum und vom Service ab, sodass Sie sie mithilfe von APIs von Drittanbietern modifizieren können.

## Verbindung zu einer SOE konfigurieren
{: #how-to}

1. Navigieren Sie auf der Registerkarte _Sprachagent_ auf der Seite _Verwalten_ für Ihren Sprachagenten zum Abschnitt für die {{site.data.keyword.conversationshort}}-Konfiguration.

1. Wählen Sie **Service-Orchestrierungsengine** als Ihren **Servicetyp** aus.

1. Wählen Sie die **Region** für Ihren **Servicetyp** aus.

1. Geben Sie im Feld **URL** die vollständige URL zu Ihrem SOE-Arbeitsbereich ein, z. B. `https://iva-soesample.myorg.net/SOE/myWorkspace`.

  **Wichtig**: Aus Gründen der Datensicherheit müssen Sie sicherstellen, dass Sie für Ihren SOE-Arbeitsbereich eine sichere URL verwenden. Verwenden Sie `https:` anstelle von `http:` sowie obligatorische Authentifizierung. Weitere Informationen zu Sicherheitsaspekten finden Sie unter [Informationssicherheit und Datenschutz](infosec.html).

1. **Optional** Wenn die SOE Ihre Authentifizierung anfordert (empfohlen), geben Sie in den Benutzernamen und Kennwort in den entsprechenden Feldern an.
