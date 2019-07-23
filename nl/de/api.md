---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-01"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Sprachagenten mithilfe der API programmieren
{: #api}

Das Verhalten Ihres Sprachagenten kann durch Definieren von Aktionstags und Statusvariablen im {{site.data.keyword.conversationfull}}-Service gesteuert werden. Aktionstags initiieren Aktionen, die Ihr Sprachagent während einer Dialogsitzung unternimmt; Statusvariablen definieren Eigenschaften des Sprachagenten, die während des ganzen Dialogs bestehen bleiben, sofern sie nicht geändert werden.
{: shortdesc}

Da {{site.data.keyword.iva_full}} auf IBM Voice Gateway basiert, funktioniert die API auf gleiche Weise. Wenn Sie mit Voice Gateway und SMS Gateway vertraut sind, können Sie in Ihren {{site.data.keyword.conversationshort}}-Dialogen mit {{site.data.keyword.iva_short}} die gleichen Aktionen und Statusvariablen verwenden. Unter [Aktionstags und Statusvariablen in der Voice Gateway-API](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html) bzw. [API für SMS Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/sms_api.html) finden Sie weitere Informationen.
{: tip}

## JSON in der Dialogantwort bearbeiten
{: #json-editor}

Sowohl Aktionen als auch Status werden in einer Dialogknotenantwort im JSON-Format definiert. Zum Bearbeiten des JSON-Codes öffnen Sie den JSON-Editor.

1. Wählen Sie im {{site.data.keyword.Bluemix_short}}-Dashboard Ihre {{site.data.keyword.conversationshort}}-Serviceinstanz aus.
1. Starten Sie das {{site.data.keyword.conversationshort}}-Tool.
1. Klicken Sie auf den Skill, der den zu bearbeitenden Dialog enthält.
1. Wechseln Sie zur Registerkarte **Dialog** und wählen Sie den Knoten aus, an dem Sie eine Aktion oder einen Status festlegen möchten.
1. Klicken Sie in der Antwort auf das Symbol ![Erweiterte Antwort](../conversation/images/kabob.png) und wählen Sie **JSON-Editor öffnen**.

Im JSON-Editor können Sie Aktionen für die Eigenschaft `output` und die Status für die Eigenschaft `context` definieren, wie in den folgenden Abschnitten beschrieben.

## Aktionen initiieren
{: #defining-actions}

Um während eines Anrufs Aktionen im Sprachagenten zu initiieren, können Sie in der Eigenschaft `output` im JSON-Format Aktionstags für einen {{site.data.keyword.conversationshort}}-Dialogknoten definieren. Sie können entweder eine Einzelaktion im Tag `vgwAction` oder eine Aktionssequenz im Tag `vgwActionSequence` definieren. Jede Aktion setzt sich aus einer Eigenschaft `command`, gefolgt von einer optionalen Eigenschaft `parameter`, zusammen, um Attribute für Befehle zu definieren, die sie benötigen.

### Einzelaktionen
{: #single-actions}

Um eine Einzelaktion durchzuführen, definieren Sie die Aktion im Tag `vgwAction` zusammen mit allen notwendigen Parameterattributen. Im `text`-Block der Eigenschaft `output` können Sie optional eine Äußerung einschließen, die der Sprachagent nach Ausführung der Aktion abspielt.

Die folgende Einzelaktion im Tag `vgwAction` fordert den Sprachagenten auf, den Anruf zu beenden, sobald die Knotenantwort ausgelöst wird. Da der Befehl `vgwActHangup` über keine Parameter verfügt, sind keine definiert.
```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActHangup"
    }
  }
}
```
{: codeblock}

Die folgende Aktion weist den Sprachagenten an, DTMF-Eingaben (Dual-Tone Multi-Frequency Signaling) zu erfassen und den definierten Text für den Anrufer abzuspielen.

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActCollectDtmf",
      "parameters": {
        "dtmfTermKey": "#"
      }
    },
    "text": {
      "values": [
        "Geben Sie Ihre Telefonnummer ein."
      ]
    }
  }
}
```
{: codeblock}

### Aktionssequenzen
{: #action-sequences}

Um eine oder mehr Aktionen für einen einzelnen Dialogwechsel auszuführen, können Sie im Tag `vgwActionSequence` eine Sequenz von Aktionen als JSON-Liste definieren. Die Aktionen werden in der Reihenfolge ausgeführt, wie Sie sie definieren.

Anders als bei Einzelaktionen muss die Aktionsliste die Aktion `vgwActPlayText` enthalten, wenn der Sprachagent unter Verwendung des Tags `vgwActionSequence` eine Äußerung abspielen soll. Anders als beim Tag `vgwAction` wird eine Äußerung im Feld `output.text` nicht automatisch abgespielt.
{: tip}

Im folgenden, etwas komplexeren Beispiel fordern die im Tag `vgwActionSequence` definierten Aktionen den Sprachagenten auf, die Sprache-Text-Verarbeitung zu inaktivieren und DTMF-Eingaben zu erfassen, während der die Äußerung abspielt.

```json
{
  "output": {
    "vgwActionSequence": [
      {
        "command": "vgwActPauseSTT"
      },
      {
        "command": "vgwActCollectDtmf",
        "parameters": {
          "dtmfTermKey": "#"
        }
      },
      {
        "command": "vgwActPlayText",
        "parameters": {
          "text": [
            "Geben Sie Ihre Sozialversicherungsnummer ein."
          ]
        }
      }
    ]
  }
}

```
{: codeblock}

## Status festlegen
{: #setting-states}

Um eine Änderung des Status anzugeben, der zwischen den Dialogwechseln verbleibt, tauscht der Sprachagent mit dem konfigurierten {{site.data.keyword.conversationfull}}-Service Statusvariablen aus. Diese Statusvariablen werden in einem {{site.data.keyword.conversationshort}}-Dialogknoten als [Kontextvariablen](/docs/services/assistant?topic=assistant-dialog-build#dialog-build) im JSON-Format definiert.

Sie können z. B. die folgende Statusvariable definieren, um die Nachricht festzulegen, die an den Anrufer gestreamt wird, wenn die Verbindung zum {{site.data.keyword.conversationshort}}-Service fehlschlägt.

```json
{
  "context": {
    "vgwConversationFailedMessage": "Ich kann leider keine Verbindung zu unserer Hotline herstellen. Bitte versuchen Sie es später noch einmal."
  }
}
```
{: codeblock}

Der Sprachagent geht davon aus, dass der {{site.data.keyword.conversationshort}}-Service statusunabhängig ist und dass alle Status beim Sprachagenten zwischen den Austauschvorgängen mit dem {{site.data.keyword.conversationshort}}-Service beibehalten werden. Der Status für jeden Dialogwechsel innerhalb eines Anrufs wird an den {{site.data.keyword.conversationshort}}-Service geleitet und im Abschnitt `context` der REST-Nachrichten vom Service zurückerhalten.
