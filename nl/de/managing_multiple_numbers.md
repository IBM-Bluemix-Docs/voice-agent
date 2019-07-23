---

copyright:
  years: 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Mehrere Telefonnummern für einen _einzigen Agenten_ konfigurieren
{: #multi_num}

[comment]: # (Nachdem Sie Ihre {{site.data.keyword.iva_full}}-Serviceinstanz erstellt haben: )

Sie können mehrere Telefonnummern zu einem einzigen Agenten hinzufügen, sodass sich die Konfiguration des Agenten auf alle ihm zugeordneten Nummern auswirkt. Auf der Dashboardseite _Serviceinstanz verwalten_ wird die **primäre Nummer** angezeigt, die dem Agenten zugeordnet ist. Weitere Informationen enthält [Primäre Nummer festlegen](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

Sie können auf das Dialogfenster **Verwalten** zugreifen, indem Sie auf der Seite _Sprachagenten erstellen_ oder der Seite _Sprachagenten bearbeiten_ neben **Telefonnummer** auf **Verwalten** klicken.

  * _**HINWEIS:**_ Pro Agentenkonfiguration gilt ein Grenzwert von maximal 1000 eindeutigen Nummern.
{: shortdesc}


## Neue Nummer hinzufügen
{: #add_num}

1. Klicken Sie auf der Seite _Sprachagenten erstellen_ oder der Seite _Sprachagenten bearbeiten_ neben **Telefonnummer** auf **Verwalten**, damit das Dialogfenster **Verwalten** geöffnet wird.

1. Klicken Sie im Dialogfenster **Verwalten** in der rechten oberen Ecke auf das Symbol für "Nummer hinzufügen". Es wird ein neuer leerer Eintrag in der Liste erstellt.

1. {: #format_num} Fügen Sie als **Telefonnummer** die Nummer von Ihrem SIP-Trunk einschließlich Landes- und Ortsvorwahl hinzu. Für eine 800-er Nummer in den Vereinigten Staaten geben Sie dann zum Beispiel 18883334444 als Nummer an. Die Telefonnummer kann Leerzeichen sowie die Zeichen + (Pluszeichen), ( ) und Bindestrich/Minuszeichen (-) enthalten und darf aus 30 Zeichen bestehen.  

  * _**HINWEIS:**_ Pro Sprachagentenkonfiguration gilt ein Grenzwert von maximal 1000 eindeutigen Nummern.

1. Im Feld **Beschreibung** können Sie wahlweise eine Beschreibung für Ihre Telefonnummer eingeben, die maximal 64 Zeichen lang sein darf.

1. Klicken Sie auf das "Häkchen"-Symbol, um die Nummer in der Liste zu speichern, oder klicken Sie auf das Symbol "X", um die Hinzufügung abzubrechen.

1. Ganz oben wird eine Meldung vom Typ "Erfolg!" zusammen mit einem Eintrag in der Liste mit der neuen Nummer angezeigt. Andernfalls wird eine Fehlermeldung mit einer Beschreibung angezeigt.

1. Die Nummer ist mit einem **grünen** Häkchen unter der Spalte "Status" in der Liste versehen, was angibt, dass die Nummer frei von Fehler ist.

1. Klicken Sie auf **Fertig**, um die Nummer zu speichern und gegenüber dem Agenten zu bestätigen.

## Nummer und/oder Beschreibung bearbeiten
{: #edit_num}

1. Klicken Sie auf der Seite _Sprachagenten erstellen_ oder der Seite _Sprachagenten bearbeiten_ neben **Telefonnummer** auf **Verwalten**. Alternativ dazu können Sie, sofern Voice Agent bereits mehrere Nummern enthält, einfach auf das grau abgeblendete Feld für **Telefonnummer** klicken, um das Dialogfenster **Verwalten** zu öffnen.

1. Heben Sie den Telefonnummereintrag, den Sie bearbeiten möchten, hervor und klicken Sie auf die Optionsliste, die auf der rechten Seite der Liste durch **drei Punkte** dargestellt wird.

1. Wählen Sie in dem Dropdown-Menü, das jetzt angezeigt wird, die Option **Bearbeiten** aus.

1. Sie können nun die **Telefonnummer** und/oder **Beschreibung** bearbeiten und ändern.

1. Klicken Sie auf das "Häkchen"-Symbol, um die Aktualisierung zu bestätigen, oder klicken Sie auf das Symbol "X", um die Aktualisierung zu verwerfen.

1. Ganz oben wird eine Meldung vom Typ "Erfolg!" zusammen mit dem Eintrag in der Liste, der aktualisiert wird, angezeigt. Andernfalls wird eine Fehlermeldung mit einer Beschreibung angezeigt.

1. Klicken Sie auf **Fertig**, um die Änderungen im Agenten zu speichern.

## Nummern löschen
{: #delete_num}

1. Klicken Sie auf der Seite _Sprachagenten erstellen_ oder der Seite _Sprachagenten bearbeiten_ neben **Telefonnummer** auf **Verwalten**.

1. Wählen Sie neben allen Nummern, die Sie löschen möchten, das zugehörige weiße Kästchen aus. Um _alle_ Nummern auszuwählen, wählen Sie einfach das weiße Kästchen neben dem Header **Telefonnummer** aus.

1. Klicken Sie im Dialogfenster **Verwalten** nahe der rechten oberen Ecke auf das Symbol für "Element löschen".

1. Ganz oben wird eine Meldung vom Typ "Erfolg!" angezeigt und die ausgewählten Einträge werden aus der Liste entfernt. Andernfalls wird eine Fehlermeldung mit einer Beschreibung angezeigt.

1. Wenn Sie eine einzelne Zahl löschen möchten, können Sie anstelle des Kontrollkästchens wahlweise den zu löschenden Nummerneintrag hervorheben und auf die Optionsliste klicken, die auf der rechten Seite der Liste durch **drei Punkte** dargestellt wird.

1. Wählen Sie in dem Dropdown-Menü, das jetzt angezeigt wird, die Option **Löschen** aus.

1. Ganz oben wird eine Meldung vom Typ "Erfolg!" angezeigt und der hervorgehobenen Eintrag wird aus der Liste entfernt. Andernfalls wird eine Fehlermeldung mit einer Beschreibung angezeigt.

1. Klicken Sie auf **Fertig**, um den Löschvorgang für die Nummer aus dem Agenten zu bestätigen und zu speichern.

## Nummern importieren
{: #import_num}

Es ist möglich, eine Liste von Nummern auf einmal auf den Agenten hochzuladen. Bei dieser Liste _muss_ es sich um eine Datei vom Typ **.csv** handeln. Die Datei kann bis zu 1000 eindeutige **Telefonnummern** enthalten, wobei jede Telefonnummer in einer eigenen Zeile stehen muss und für jede Nummer eine optionale **Beschreibung** vorhanden sein kann.

  * _**HINWEIS:**_ Durch das Hochladen von Nummern aus einer CSV-Datei werden _ALLE_ aktuellen Nummern im Agenten ersetzt. Die Nummern aus der CSV-Datei werden _nicht_ an die Nummernliste angehängt.

  * Die Nummern in der CSV-Datei _müssen_ dem gleichen Format entsprechen wie beim Hinzufügen einer Nummer über das Dashboard und müssen außerdem eindeutig sein. Weitere Informationen enthält [Format von Nummern](/docs/services/voice-agent?topic=voice-agent-multi_num#format_num).

1. Klicken Sie auf der Seite _Sprachagenten erstellen_ oder der Seite _Sprachagenten bearbeiten_ neben **Telefonnummer** auf **Verwalten**.

1. Klicken Sie im Dialogfenster **Verwalten** nahe der rechten oberen Ecke auf das Symbol für "CSV-Datei hochladen".

1. Es wird ein Fenster angezeigt, in dem Sie bestätigen können, dass alle vorhandenen Nummern in der Liste durch die Nummern aus der CSV-Datei ersetzt werden. Klicken Sie auf **OK**, um den Vorgang zu bestätigen und fortzufahren.

1. Navigieren Sie in dem neuen Fenster zu der CSV-Datei, wählen Sie sie aus und klicken Sie auf **Öffnen**.

1. Ganz oben wird eine Meldung vom Typ "Erfolg!" angezeigt und es werden alle neuen Nummern zu der Liste hinzugefügt. Andernfalls wird eine Fehlermeldung mit einer Beschreibung angezeigt und neben jeder Nummer, bei der ein Problem aufgetreten ist, wird eine Fehlernachricht angezeigt.

1. Die einzelnen importierten Nummern werden mit einem **grünen** Häkchen in der Spalte _Status_ in der Liste versehen, was angibt, dass die Nummer frei von Fehlern ist. Andernfalls wird ein spezifischer Fehler in der Spalte _Status_ angezeigt.

1. Klicken Sie auf **Fertig**, um die Hinzufügung der Nummer(n) zum Agenten zu bestätigen und zu speichern.

## Nummern exportieren
{: #export_num}

Es ist möglich, eine Liste von Nummern und ihre Beschreibungen vom Agenten in eine **CSV**-Datei zu exportieren und auf Ihren Computer herunterzuladen. Auf diese Weise können Sie die Nummern und/oder Beschreibungen nach Bedarf oder Wunsch ändern und wieder in den Agenten hochladen. Weitere Informationen finden Sie in [Nummern importieren](/docs/services/voice-agent?topic=voice-agent-multi_num#import_num).

1. Klicken Sie auf der Seite _Sprachagenten erstellen_ oder der Seite _Sprachagenten bearbeiten_ neben **Telefonnummer** auf **Verwalten**.

1. Klicken Sie im Dialogfenster **Verwalten** nahe der rechten oberen Ecke auf das Symbol für "CSV-Datei herunterladen".

1. Es wird eine CSV-Datei mit allen im Agenten gespeicherten Nummern auf Ihren Computer heruntergeladen.

1. Zum Verlassen des Dialogfensters **Verwalten** können Sie auf **Fertig** klicken.

## Primäre Nummer festlegen
{: #primary_num}

Die _primäre Nummer_ dient nur der Anzeige und hat keine Funktion. Standardmäßig wird die erste Nummer, die zum Agenten hinzugefügt wird, als **primäre Nummer** bezeichnet, d. h. als die Nummer, die auf der Seite _Serviceinstanz verwalten_ des Dashboards angezeigt wird. In einem Voice Agent muss mindestens eine **primäre Nummer** vorhanden sein.

Sie können die Bezeichnung **Primäre Nummer** in Voice Agent in jede gewünschte Nummer ändern.

1. Klicken Sie auf der Seite _Sprachagenten erstellen_ oder der Seite _Sprachagenten bearbeiten_ neben **Telefonnummer** auf **Verwalten**.

1. Heben Sie den Telefonnummereintrag, den Sie bearbeiten möchten, hervor und klicken Sie auf die Optionsliste, die auf der rechten Seite der Liste durch **drei Punkte** dargestellt wird.

1. Wählen Sie in dem Dropdown-Menü, das jetzt angezeigt wird, die Option **Als primäre festlegen** aus.

1. Ganz oben wird eine Meldung vom Typ "Erfolg!" angezeigt. Für den von Ihnen gewählten Eintrag wird unter der Spalte _Status_ die Bezeichnung **Primäre** angezeigt. Andernfalls wird eine Fehlermeldung mit einer Beschreibung angezeigt.

1. Klicken Sie auf **Fertig**, um die Änderungen im Agenten zu speichern.

## Telefonnummern sortieren und in ihnen navigieren
{: #sort_num}

Sie können die Liste der Nummern wahlweise auf- oder absteigend nach _Telefonnummer_ oder nach _Beschreibung_ sortieren. Standardmäßig wird die Telefonnummernliste aufsteigend nach der **Telefonnummer** sortiert.

1. Klicken Sie auf den Header **Telefonnummer**, um die Nummern in der Liste numerisch zu sortieren.

1. Klicken Sie auf den Header **Beschreibung**, um die Nummern in der Liste alphabetisch nach ihrer _Beschreibung_ zu sortieren.  

Sie können auch die Anzahl der angezeigten Nummern pro Seite aus mehreren Optionen in der Liste auswählen. Es können 5, 10 oder 30 Nummern pro Seite angezeigt werden. Sie können auch zu verschiedenen Seiten mit Nummern navigieren.

1. Klicken Sie auf die Zahl neben **Elemente pro Seite**, um auszuwählen, wie viele Nummerneinträge in der Liste angezeigt werden. Standardmäßig werden 5 Einträge pro Seite angezeigt.

1. Klicken Sie zum Navigieren zwischen den einzelnen Seiten über dem Header **Status** auf den _Rechtspfeil_ oder den _Linkspfeil_.

1. Alternativ können Sie auch auf die Zahl zwischen den Pfeilen klicken, um manuell eine Seite auszuwählen, zu der Sie navigieren möchten.

1. Klicken Sie auf **Fertig**, um die Änderungen im Agenten zu speichern.

## Änderungen speichern
{: #save_changes}

Wenn Sie in Voice Agent Änderungen an der Nummernliste vornehmen möchten, _müssen_ Sie die Änderungen im Dialogfeld **Verwalten** speichern und die Änderungen anschließend auf der Seite _Voice Agent bearbeiten_ speichern.

1. Klicken Sie auf der Seite _Sprachagenten erstellen_ oder der Seite _Sprachagenten bearbeiten_ neben **Telefonnummer** auf **Verwalten**.

1. Führen Sie nach Bedarf Änderungen an den Nummern in der Liste durch.

1. Klicken Sie auf **Fertig**, um die Änderungen im Agenten zu speichern.

1. Sie gelangen zurück zur Seite _Voice Agent bearbeiten_. Klicken Sie dort in der rechten oberen Ecke auf **Änderungen speichern**, um alle Ihre Änderungen anzuwenden.

* _**HINWEIS:**_ Sie _müssen_ sowohl im Dialogfenster **Verwalten** auf **Fertig** _als auch_ auf der Seite _Voice Agent bearbeiten_ auf **Änderungen speichern** klicken, um Ihre Änderungen zu speichern. Andernfalls werden die Änderungen verworfen.

## Nach Nummern oder Beschreibung suchen
{: #search_num}

Sie können nach gespeicherten Nummern suchen, indem Sie nach der Nummer oder der Beschreibung suchen.

1. Klicken Sie auf der Seite _Sprachagenten erstellen_ oder der Seite _Sprachagenten bearbeiten_ neben **Telefonnummer** auf **Verwalten**.

1. Geben Sie in der Suchleiste (_Suchen_) eine Nummer oder eine Beschreibung ein, nach der in der Liste gesucht werden soll. Die Suchergebnisse werden während der Eingabe automatisch aktualisiert.

1. Klicken Sie auf **Fertig**, um die Änderungen im Agenten zu speichern.
