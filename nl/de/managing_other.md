---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Serviceinstanzen in anderen {{site.data.keyword.Bluemix_notm}}-Arbeitsbereichen verwenden
{: #other_service}

Sie können Ihren Sprachagenten für die Verwendung von {{site.data.keyword.conversationshort}}-, {{site.data.keyword.speechtotextshort}}- oder {{site.data.keyword.speechtotextshort}}-Serviceinstanzen, die zu Arbeitsbereichen in anderen {{site.data.keyword.Bluemix_short}}-Konten gehören, konfigurieren.
{: shortdesc}

Für die Verbindung Ihres Sprachagenten mit anderen Serviceinstanzen können Sie entweder den Benutzernamen und die Kennwortberechtigungsnachweise oder einen API-Schlüssel für Ihre Serviceinstanzen verwenden.

1. Wählen Sie auf der Registerkarte _Sprachagenten_ im Dashboard _Verwalten_ die Option **Neuen Sprachagenten erstellen** oder einen Sprachagenten aus, den Sie bearbeiten möchten.

1. Wählen Sie in {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} oder {{site.data.keyword.speechtotextshort}} die Option **Weitere Serviceinstanz** für Ihren **Servicetyp** und anschließend die Option **Region** aus.

1. Wählen Sie entweder **Benutzername und Kennwort** oder **API-Schlüssel** aus und geben Sie Ihre Serviceberechtigungsnachweise ein.
  Zum Suchen dieser Werte wechseln Sie zu der Serviceinstanz, die Sie konfigurieren möchten, und wählen **Serviceberechtigungsnachweise** und danach **Berechtigungsnachweise anzeigen** aus.

  * **Benutzername und Kennwort**: Konfigurieren Sie in den Feldern **URL**, **Benutzername** und **Kennwort** die Berechtigungsnachweise für Ihre {{site.data.keyword.conversationshort}}-, {{site.data.keyword.speechtotextshort}}- oder {{site.data.keyword.texttospeechshort}}-Serviceinstanz.
  * **API-Schlüssel**: Konfigurieren Sie in den Feldern **URL** und **API-Schlüssel** die Berechtigungsnachweise für Ihre {{site.data.keyword.conversationshort}}-, {{site.data.keyword.speechtotextshort}}- oder {{site.data.keyword.texttospeechshort}}-Serviceinstanz.

  Die Berechtigungsnachweise sind nicht Ihr {{site.data.keyword.Bluemix_notm}}-Benutzername und -Kennwort, sondern verschlüsselte Berechtigungsnachweise für die jeweilige Serviceinstanz.
  {:tip}

1. Geben Sie die Serviceinstanzinformationen ein.

  * **{{site.data.keyword.conversationshort}}:** Im Feld **Arbeitsbereich-ID** geben Sie die ID des Arbeitsbereichs ein, den Sie mit Ihrem Sprachagenten verwenden möchten. Zum Suchen der Arbeitsbereich-ID starten Sie das Tool und den Arbeitsbereich, den Sie integrieren möchten, klicken auf das Symbol 'Aktionen' (**&vellip;**) und wählen **Details anzeigen** aus.
  * **{{site.data.keyword.speechtotextshort}}:** Wählen Sie bei **Modelltyp auswählen** die Option **Schmalband**, **Breitband** oder **Schmal- und Breitband** sowie das Sprachmodell aus.
  * **{{site.data.keyword.texttospeechshort}}:** Wählen Sie im Feld **Sprachunterstützung** die Sprache und die Sprachunterstützung aus, die Ihr Service verwendet. Für Ihren Service müssen Sie eine Sprachunterstützung angeben.

**Bitte beachten:** Damit Ihr Sprachagent funktioniert, müssen Sie {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} und {{site.data.keyword.texttospeechshort}} für dieselbe Sprache konfigurieren. Weitere Informationen finden Sie in [Unterstützte Sprachen](about.html#supported-languages).
