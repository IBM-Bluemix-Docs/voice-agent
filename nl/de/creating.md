---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Service erstellen

{: shortdesc}
Sie können mithilfe des {{site.data.keyword.Bluemix_short}}-Katalogs oder eines {{site.data.keyword.Bluemix_notm}} `ibmcloud`-Befehls eine {{site.data.keyword.iva_full}}-Serviceinstanz erstellen.

## Service über den Katalog erstellen
{: #catalog_create}

1. Wechseln Sie zur [{{site.data.keyword.iva_short}}-Katalogseite](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

   Die Katalogseite enthält Informationen über den Service und die zugehörigen Preistarife. Sie können den Wert für **Servicename** ändern.

2. Klicken Sie auf **Erstellen**.

## Service über die Befehlszeile erstellen
{: #command_create}

1. [Installieren Sie die {{site.data.keyword.Bluemix_notm}}-CLI](../../cli/reference/bluemix_cli/get_started.html).

2. Führen Sie den [`ibmcloud`-Befehl](../../cli/reference/bluemix_cli/bx_cli.html#bluemix_cli) aus, mit dem Ihre VoiceAgent-Serviceinstanz im Rahmen des Testplans (_Trial_) erstellt wird:

   ```
   ibmcloud service create VoiceAgent _Trial_ "My Voice Agent Service"
   ```
   {: codeblock}

## Nächste Schritte
{: #next}

Erstellen Sie den Sprachagenten über das Dashboard _Verwalten_. Siehe hierzu den Abschnitt [Sprachagenten verwalten](managing.html).
