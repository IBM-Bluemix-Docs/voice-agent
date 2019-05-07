---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Maximalwert für gleichzeitige Verbindungen bearbeiten
{: #edit_concurrency}

Wenn Sie den _Standardplan_ oder den _Premiumplan_ verwenden, können Sie die maximale Anzahl gleichzeitiger Verbindungen gegenüber den Standardeinstellungen ändern.
{: shortdesc}

In allen Plänen sind zwei gleichzeitige Verbindungen kostenfrei enthalten. Weitere Informationen finden Sie in [Preisstrukturpläne](https://cloud.ibm.com/catalog/services/voice-agent-with-watson). Im Dashboard _Verwalten_ wird die maximale Anzahl gleichzeitiger Verbindungen, die im Rahmen Ihres aufgeführten Plans zulässig sind, im Feld **Maximale Anzahl gleichzeitiger Verbindungen** angezeigt. Darüber hinaus wird die maximale Anzahl gleichzeitiger Verbindungen, die von Ihren Sprachagenten im laufenden Monat genutzt wurden, im Feld _Genutzte maximale Anzahl gleichzeitiger Verbindungen_ angezeigt.

1. Rufen Sie die Registerkarte _Instanzen_ in Ihrem Dashboard _Verwalten_ auf, um die maximale Anzahl gleichzeitiger Verbindungen in Ihrem Plan zu bearbeiten.

1. Wenn Sie die maximale Anzahl gleichzeitiger Verbindungen in Ihrem Plan ändern möchten, klicken Sie auf das Symbol **Bearbeiten**.

1. Geben Sie in _Maximale Anzahl gleichzeitiger Verbindungen bearbeiten_ die gewünschte maximale Anzahl gleichzeitiger Verbindungen ein und klicken Sie auf **Speichern**.

Der Mindestwert für die Anzahl gleichzeitiger Anrufe, der im Self-Service-Verfahren festgelegt werden kann, ist 10, der Höchstwert 50. Wenn Sie mehr als 50 gleichzeitige Verbindungen für den Sprachagenten benötigen, lesen Sie die Informationen in [Unterstützung für Netzkonfiguration anfordern](/docs/services/voice-agent?topic=voice-agent-connect#request-setup).

## Preisinformationen für gleichzeitige Verbindungen
{: #concurrent-charge}

  * In den Plänen des Typs _Lite_ und _Standard_ sind 2 gebührenfreie gleichzeitige Verbindungen enthalten.
  * _Premium_-Pläne werden pro Instanz angepasst.
  * In einem Plan des Typs _Standard_ ist eine Mindestkapazität von 10 gleichzeitigen Verbindungen verfügbar.
  * Die Nutzung gleichzeitiger Verbindungen wird anteilmäßig pro Monat umgelegt. Wenn Sie mehr als 2 gleichzeitige Verbindungen an einem Tag nutzen, werden Gebühren auf der Basis der Tagesrate berechnet. Beispiel: Der Plan unterstützt 2 kostenfreie gleichzeitige Verbindungen und Sie legen einen Maximalwert von 12 Verbindungen fest. Wenn Sie nur 5 an einem Tag nutzen, werden Gebühren für 3 berechnet.
  * Bei der Verwendung eines _Standard_- oder _Premium_-Plans können Sie eine größere Kapazität für gleichzeitige Verbindungen kaufen.
  * Für die maximale Kapazität gleichzeitiger Verbindungen, die Sie an einem Tag nutzen, werden Gebühren auf der Basis einer Tagesrate berechnet.

Weitere Informationen zu Plänen, Raten und Features finden Sie in [Preisstrukturpläne](https://cloud.ibm.com/catalog/services/voice-agent-with-watson).
