---

copyright:

  years: 2019

lastupdated: "2019-06-06"
subcollection: "voice-agent"

keywords: Voice Agent IAM, Voice Agent user access, get started with IAM, IAM tutorial, IAM quick start, user access, SMS IAM, SMS user access

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}

# IAM und Benutzerzugriff konfigurieren
{: #iam}

Dieses Lernprogramm soll Ihnen bei der raschen Einrichtung und Ausführung von IBM Cloud Identity and Access Management (IAM) helfen; hierzu laden Sie Benutzer zu Ihrem Konto ein und weisen diesen Benutzern den Cloud IAM-Zugriff für eine {{site.data.keyword.iva_short}}-Instanz zu.
{:shortdesc}

## Vorbereitende Schritte
{: #iam-before-you-begin}

Falls Sie IAM noch nicht verwendet haben, können Sie sich in der folgenden Dokumentation genauer über die Funktionen, Konzepte und Komponenten des Zugriffsmanagementsystems informieren.

* Der Abschnitt [IBM Cloud Identity and Access Management](/docs/iam?topic=iam-iamoverview) bietet eine Kurzübersicht über die Aufgabe von IAM bei IBM, über die verfügbaren Funktionen sowie Links zu verfügbaren CLI- und API-Dokumenten.
* Im Abschnitt [IAM-Konzepte](/docs/iam?topic=iam-iamconcepts) werden die allgemeinen Konzepte in IAM vorgestellt, die Ihnen zum Einstieg ein Verständnis für die unterschiedlichen Komponenten vermitteln.
* Im Abschnitt [IAM-Zugriff](/docs/iam?topic=iam-userroles) wird detaillierter erläutert, wie das Zugriffsmanagement durch Verwendung von Zugriffsrichtlinien funktioniert.

Das vorliegende Handbuch deckt die meisten gängigen Szenarios für das Hinzufügen und Zuweisen des Zugriffs zu Benutzern ab. Für Benutzerzugriff und Rollen gibt es viele weitere Optionen und Konfigurationen. Detailliertere Informationen können Sie über die obigen Links aufrufen. 

## Schritt 1. Benutzer einladen und Anfangszugriff zuweisen
{: #step1}

Sie können einen oder mehrere Benutzer einladen und in der Einladung eine Richtlinie für den Anfangszugriff angeben. Falls Sie in einer einzigen Einladung mehrere Benutzer einladen, wird jedem Benutzer derselbe Zugriff zugewiesen. Im Abschnitt **Zugriff** auf der Seite **Benutzer einladen** werden nur die Benutzerrollen angezeigt, die Sie zuordnen dürfen.

Der Kontoeigner kann Cloud IAM-Rollen für eingeladene Benutzer im Abschnitt **Services** zuweisen. Als Kontoeigner können Sie den Zugriff auf Folgendes ermöglichen:
* Alle Ressourcen in einer Ressourcengruppe
* Alle Ressourcen für einen bestimmten Service in einer Ressourcengruppe 
* Alle für IAM aktivierten Services im Konto
* Einzelne Ressource im Konto
* Kontoverwaltungsservices

Gehen Sie zum Zuweisen von Cloud IAM-Rollen für Benutzer in Ihrem Konto wie nachfolgend beschrieben vor.

1. Navigieren Sie zu **Verwalten** &gt; **Zugriff (IAM)** und wählen Sie **Benutzer** aus.
2. Klicken Sie auf **Benutzer einladen**.
3. Geben Sie die E-Mail-Adressen der Benutzer an, die Sie einladen möchten.
4. Erweitern Sie im Abschnitt **Zugriff** die Option **Services**.
5. Wählen Sie aus, ob der Zugriff auf eine **Ressource**, auf Ressourcen innerhalb einer **Ressourcengruppe** oder auf **Kontoverwaltungsservices** zugewiesen werden soll.
6. Befolgen Sie abhängig von Ihrer Auswahl die Bedienerführungen zum Angeben des gewünschten Zugriffs. Falls Sie die Option _Ressourcengruppe_ ausgewählt haben, können Sie dem Benutzer den Zugriff zum Anzeigen, Bearbeiten oder Verwalten des Zugriffs auf die Ressourcengruppe auch dadurch erteilen, indem Sie eine Rolle für den Zugriff auf die Ressourcengruppe auswählen.
7. Wählen Sie im Eingabefeld **Services** den Eintrag *{{site.data.keyword.iva_short}}* im Dropdown-Menü aus oder geben Sie ihn im Feld ein und drücken Sie die Eingabetaste. 
8. Wählen Sie die entsprechende **Region** und die **Serviceinstanz**aus.
9. Wählen Sie im Abschnitt **Rollen auswählen** eine der Optionen *Manager*, *Schreibberechtigter* oder *Leseberechtigter* aus. Falls Ihre {{site.data.keyword.iva_short}}-*Serviceinstanz* SMS verwendet, **müssen** Sie neben allen anderen Rollen, die Sie erteilen wollen, die Rolle *Schreibberechtigter* oder *Manager* auswählen.
    - Weitere Informationen zu **Rollen** finden Sie unter [Servicezugriffsrollen](/docs/iam?topic=iam-userroles#service_access_roles).
10. Wenn Sie eine entsprechende Berechtigung besitzen, können Sie in der Einladung auch den Cloud Foundry- oder Infrastrukturzugriff zuweisen.
11. Klicken Sie auf **Benutzer einladen**.

Weitere Informationen enthält der Abschnitt [Benutzer einladen und Zugriff zuweisen](/docs/iam?topic=iam-iamuserinv#iamuserinv).

## Schritt 2. Zugriffsgruppen erstellen
{: #step2}

Den Prozess für das Zuweisen des Zugriffs zu Benutzern in Ihrem Konto können Sie durch die Erstellung von Zugriffsgruppen optimieren. Mithilfe von Zugriffsgruppen können Sie Benutzer und Service-IDs organisieren, denen Sie anschließend ohne großen Aufwand einen Zugriff zuweisen, indem Sie für die gesamte Gruppe eine einzige Richtlinie definieren.

### Gruppen konfigurieren
{: #group_setup}

Führen Sie zum Erstellen einer Zugriffsgruppe die folgenden Schritte aus.

1. Klicken Sie in der Menüleiste auf **Verwalten** &gt; **Zugriff (IAM)** und wählen Sie **Zugriffsgruppen**aus.
2. Klicken Sie auf **Erstellen**.
3. Geben Sie einen Namen für Ihre Gruppe ein. Das Hinzufügen einer Beschreibung ist optional.
4. Klicken Sie auf **Erstellen**.

Setzen Sie anschließend die Konfiguration der Gruppe fort, indem Sie Benutzer oder Service-IDs hinzufügen.

1. Sie werden auf die Seite für die neu erstellte Zugriffsgruppe geführt. Diese Gruppe wird auch in der Liste _Gruppe_ auf der Seite **Zugriffsgruppen** in der Menüleiste angezeigt.
2. Klicken Sie auf **Benutzer hinzufügen**.
3. Wählen Sie die Benutzer, die Sie hinzufügen wollen, in der Liste aus und klicken Sie auf **Zu Gruppe hinzufügen**.
4. Klicken Sie auf **Service-IDs**, um Service-IDs zu der Gruppe hinzuzufügen.
5. Wählen Sie die IDs, die Sie hinzufügen wollen, in der Liste aus und klicken Sie auf **Zu Gruppe hinzufügen**.

### Zugriff zu Ihren Gruppen zuweisen
{: #group_access}

Nachdem Sie Ihre Gruppen erstellt haben, können Sie den Zugriff auf alle Entitäten innerhalb der Gruppe durch eine einzige oder durch mehrere Richtlinien zuweisen.

1. Klicken Sie in der Menüleiste auf **Verwalten** &gt; **Zugriff (IAM)** und wählen Sie **Zugriffsgruppen**aus.
2. Wählen Sie die Gruppe aus, der Sie den Zugriff zuweisen wollen.
3. Klicken Sie auf der Registerkarte **Zugriffsrichtlinien** auf **Zugriff zuweisen**, um eine Zugriffsrichtlinie einzurichten. Wiederholen Sie diesen Vorgang bei Bedarf, um weitere Zugriffe zuzuweisen.

Indem Sie Benutzer in Zugriffsgruppen organisieren, können Sie einer Gruppe von Benutzern den Zugriff auf eine einzige Richtlinie zuweisen, was die Gesamtzahl der Richtlinien verringert, die Sie verwalten müssen.
{: tip}


## Schritt 3. Zugriff für vorhandene Benutzer verwalten
{: #user_access_manage}

Im folgenden Abschnitt ist detailliert beschrieben, wie Sie den Zugriff für Benutzer und Gruppen verwalten und bearbeiten, die Sie bereits in Ihrem Konto konfiguriert haben.

### Neuen Zugriff zuweisen
{: #new_access}

Führen Sie die folgenden Schritte aus, um eine neue Zugriffsrichtlinie zuzuweisen:

1. Klicken Sie in der Menüleiste auf **Verwalten** &gt; **Zugriff (IAM)** und wählen Sie **Benutzer**aus.
2. Wählen Sie den Namen des Benutzers aus, dem Sie den Zugriff zuweisen möchten.
3. Klicken Sie auf **Zugriffsrichtlinien**.
4. Klicken Sie auf **Zugriff zuweisen**.
5. Wählen Sie aus, wie der Zugriff zugewiesen werden soll:
    * Wählen Sie die Option **Zugriff in einer Ressourcengruppe zuweisen** aus, um den Zugriff entweder auf alle Ressourcen in einer Gruppe oder auf Ressourcen zuzuweisen, die für einen bestimmten Service in einer Gruppe bestimmt sind. Sie können Benutzern auch die Berechtigung erteilen, den Zugriff auf die Ressourcengruppe anzuzeigen, zu bearbeiten oder zu verwalten, indem Sie ihnen eine Benutzerrolle für die Ressourcengruppe zuweisen. Wählen Sie die Option **Kein Zugriff** aus, wenn Sie einem Benutzer lediglich den Zugriff auf die angegebene Ressource und nicht auf die Ressourcengruppe erteilen wollen.
    * Wählen Sie die Option **Zugriff auf Ressourcen zuweisen** aus, um den Zugriff auf alle für IAM aktivierten Ressourcen im gesamten Konto, auf alle Ressourcen eines bestimmten Service im gesamten Konto, auf eine einzelne Instanz oder auf eine einzelne Ressource in einer bestimmten Serviceinstanz zuzuweisen.
    * Wählen Sie die Option **Zugriff auf Kontoverwaltungsservices zuweisen** aus, um den Zugriff auf alle Kontoverwaltungsservices oder auf nur einen Kontoverwaltungsservice zuzuweisen.
5. Wählen Sie eine beliebige Kombination von Rollen aus, um den Geltungsbereich des Zugriffs zu definieren. Weitere Informationen finden Sie unter [Cloud IAM-Rollen](/docs/iam?topic=iam-userroles#iamusermanrol).
6. Klicken Sie auf **Zuweisen**.


### Vorhandenen Zugriff bearbeiten
{: #editing_access}

Sie können einen vorhandenen Zugriff aktualisieren, indem Sie die zugewiesenen Rollen für einen Benutzer bearbeiten.

1. Klicken Sie in der Menüleiste auf **Verwalten** &gt; **Zugriff (IAM)** und wählen Sie **Benutzer**aus.
2. Wählen Sie den Namen des Benutzers aus, dessen Zugriff Sie bearbeiten möchten.
3. Klicken Sie auf **Zugriffsrichtlinien**.
4. Klicken Sie in der Zeile für die Richtlinie, die Sie bearbeiten möchten, auf **Bearbeiten** im Menü **Aktionen**![Symbol für Aktionsliste](../icons/action-menu-icon.svg) .
4. Bearbeiten Sie die Richtlinie, indem Sie die zugewiesenen Rollen aktualisieren.
5. Klicken Sie auf **Speichern**.

Sie können den Zugriff für einen Benutzer entfernen, indem Sie auf die Option **Entfernen** im Menü **Aktionen**![Symbol für Aktionsliste](../icons/action-menu-icon.svg) für die Richtlinie klicken, die Sie entfernen möchten.

## Schritt 4. Zugriff auf SMS-Agenten oder auf Agenten für SMS + Sprache zuweisen (optional)
{: #sms_access}

Falls der Agent, dem Sie Zugriff zuweisen, ein Agent für **SMS** oder für **Sprache + SMS** ist, erstellen Sie einen *neuen Berechtigungsnachweis*.

### Neuen Berechtigungsnachweis erstellen
{: #new_cred}

Sie können Berechtigungsnachweise nur für Rollen erstellen, die bereits in Ihrem Konto aktiv sind. Für SMS-Agenten sowie Agenten für Sprache + SMS muss Ihnen die Rolle *Schreibberechtigter* oder *Manager* zugewiesen sein. Weitere Informationen enthält [Schritt 9 unter 'Benutzer einladen und Anfangszugriffsberechtigungen zuweisen'](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. Klicken Sie im *Dashboard* Ihrer {{site.data.keyword.iva_short}}-Instanz auf **Neuer Berechtigungsnachweis (+)**. 
2. Geben Sie im aufgerufenen Dialogfeld 'Neu' einen **Namen** ein und wählen Sie im Dropdown-Menü **Rolle** die Option *Schreibberechtigter* oder *Manager* aus. 
    - **HINWEIS:** Sie **_müssen_** für jede SMS-bezogene Funktionalität die Rolle *Schreibberechtigter* oder die Rolle *Manager* auswählen. 
3. Klicken Sie auf die Schaltfläche **Hinzufügen**.

## Fehlerbehebung
{: #troubleshoot}

Auf der Seite **Serviceberechtigungsnachweise** wird bei dem Versuch, einen *neuen Berechtigungsnachweis* zu erstellen, möglicherweise die folgende Fehlernachricht angezeigt:
> Sie besitzen nicht die erforderliche Berechtigung für das Zuweisen der Rolle 'Schreibberechtigter'. Wenden Sie sich an den Kontoeigner. Ihr Zugriff muss aktualisiert werden.

Befolgen Sie in diesem Fall die Anweisungen, mit denen Sie sich selbst den Zugriff *Schreibberechtigter* oder *Manager* zuweisen können, was eine **Voraussetzung** für SMS-bezogene Funktionen ist. Lesen Sie [Schritt 9 unter 'Zugriff zuweisen'](/docs/services/voice-agent?topic=voice-agent-iam#step1) und fahren Sie dann mit dem Abschnitt [Neuen Berechtigungsnachweis erstellen](/docs/services/voice-agent?topic=voice-agent-iam#new_cred) fort.

## Nächste Schritte
{: #next}

Über die Möglichkeiten von Cloud IAM können Sie sich ausgehend von der Liste [Cloud IAM-Funktionen](/docs/iam?topic=iam-iamoverview#features) informieren.
