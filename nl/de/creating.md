---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Service erstellen

Sie können mithilfe des {{site.data.keyword.Bluemix_short}}-Katalogs oder eines {{site.data.keyword.Bluemix_notm}}-Befehls vom Typ `ibmcloud` eine {{site.data.keyword.iva_full}}-Serviceinstanz erstellen.
{: shortdesc}


## Service über den Katalog erstellen
{: #catalog_create}

1. Wechseln Sie zur [{{site.data.keyword.iva_short}}-Katalogseite](https://cloud.ibm.com/catalog/services/voice-agent-with-watson).

   Die Katalogseite enthält Informationen über den Service und die zugehörigen Preistarife. Sie können den Wert für **Servicename** ändern.

2. Klicken Sie auf **Erstellen**, um [einen Sprachagenten über das Dashboard _Verwalten_ zu erstellen](managing_create.html#config_instance).

## Service über die Befehlszeile erstellen
{: #command_create}

1. [Installieren Sie die {{site.data.keyword.Bluemix_notm}}-CLI](../cli/index.html#overview).

2. Führen Sie den [Befehl `ibmcloud`](../cli/idt/commands.html#idt-cli) aus, mit dem Ihre Voice Agent-Serviceinstanz im Rahmen des _Lite_-Plans erstellt wird:

   ```
   ibmcloud service create VoiceAgent _Lite_ "My Voice Agent Service"
   ```
   {: codeblock}
