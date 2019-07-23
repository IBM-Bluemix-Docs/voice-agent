---

copyright:
  years: 2019
lastupdated: "2019-06-17"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Häufig gestellte Fragen zur Preisstruktur
{: #faq-pricing}

## Was kostet die Nutzung des {{site.data.keyword.iva_short}}-Standardservice?
{: #faq-pricing-zero}
{: faq}

 Weitere Informationen finden Sie auf der [Seite für die Preisstruktur](https://cloud.ibm.com/catalog/services/voice-agent-with-watson){: external}.

## Was bedeutet 'Preis pro Minute'?
{: #faq-pricing-one}
{: faq}

Der Preis basiert auf dem Umfang der Audiodaten (Anzahl der Minuten), die Sie an den Service senden. Er ist nicht davon abhängig, wie lange der Service für die Verarbeitung der Audiodaten benötigt.


## Wird bei jedem Aufruf der API zur Berechnung auf die nächste Minute aufgerundet?
{: #faq-pricing-two}
{: faq}

{{site.data.keyword.IBM_notm}} rundet die Länge der Audiodaten für jeden API-Aufruf, den der Service empfängt, nicht auf die nächste Minute auf. Die Nutzung wird von {{site.data.keyword.IBM_notm}} stattdessen für den Monat zusammengefasst; bei der Berechnung wird am Ende des Monats auf die nächste Minute aufgerundet. Die Dauer jedes Aufrufs wird auf die nächste Minute gerundet. Beispiel: Falls Ihr erster Aufruf 3,1 Sekunden und der zweite Aufruf 25,9 Sekunden dauert, berechnet {{site.data.keyword.IBM_notm}} für den ersten Aufruf 4 Sekunden und für den zweite Aufruf 26 Sekunden. Die Dauer der gesamten Audiodaten wird anschließend auf eine Minute gerundet.


## Wie werden gleichzeitige Verbindungen berechnet und wo werden sie angewendet?
{: #faq-pricing-three}
{: faq}

Gleichzeitige Verbindungen sind nur auf Sprachanrufe (nicht auf SMS) anwendbar. Die gleichzeitigen Verbindungen werden als die Anzahl von Verbindungen zu beliebigen Telefonnumern berechnet, die gleichzeitig in der Serviceinstanz definiert sind. In Rechnung gestellt wird anteilmäßig an der monatlichen Gebühr die tatsächliche höchste Anzahl von gleichzeitigen Verbindungen an einem Tag.

## Wie ist der Maximalwert für gleichzeitige Verbindungen definiert und wie kann er geändert werden?

{: #faq-pricing-four}
{: faq}

Der Maximalwert für gleichzeitige Verbindungen ist die zu jedem Zeitpunkt höchstens zulässige Anzahl von Verbindungen und die höchste Anzahl der in Rechnung gestellten Verbindungen. Der Maximalwert für gleichzeitige Verbindungen kann im [Dashboard](https://cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-edit_concurrency) definiert und geändert werden. Bei einem Standard-Plan liegt die maximale Kapazität für gleichzeitige Verbindungen bei 50 Verbindungen; falls Sie mehr Verbindungen benötigen, können Sie ein Support-Ticket öffnen.

## Wie werden eingehende und ausgehende SMS/MMS-Nachrichten in Rechnung gestellt?

{: #faq-pricing-five}
{: faq}

Eingehende Nachrichten werden erst dann in Rechnung gestellt, wenn eine Antwort an den Benutzer gesendet wird. Wenn eine ausgehende Nachricht über Voice Gateway an den Benutzer oder als Antwort auf eine eingehende Nachricht gesendet wird, wird eine Sitzung erstellt. Sowohl die ausgehende als auch die eingehende Nachricht, auf die geantwortet wird, werden gegebenenfalls in Rechnung gestellt. Alle ausgehenden und eingehenden Rechnungen werden in Rechnung gestellt, bis das Sitzungszeitlimit überschritten wird. Nach der Sitzungszeitlimitüberschreitung wird der Dialogkontext gelöscht. Das Standardsitzungszeitlimit beträgt 3600 Sekunden; Benutzer können die Dauer des Sitzungszeitlimits im Dashboard konfigurieren.
