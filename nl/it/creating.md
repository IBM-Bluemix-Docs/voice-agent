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


# Creazione del servizio

Puoi creare un'istanza del servizio {{site.data.keyword.iva_full}} utilizzando il catalogo {{site.data.keyword.Bluemix_short}} o con un comando {{site.data.keyword.Bluemix_notm}} `ibmcloud`.
{: shortdesc}


## Creazione del servizio dal catalogo
{: #catalog_create}

1. Vai alla [pagina del catalogo {{site.data.keyword.iva_short}}](https://cloud.ibm.com/catalog/services/voice-agent-with-watson).

   La pagina del catalogo contiene informazioni sul servizio e sui relativi piani dei prezzi. Puoi modificare il valore **Service name**.

2. Fai clic su **Create** per [creare un Voice Agent dal dashboard _Manage_](/docs/services/voice-agent?topic=voice-agent-config_instance#config_instance).

## Creazione del servizio dalla riga di comando
{: #command_create}

1. [Installa la CLI {{site.data.keyword.Bluemix_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli#overview).

2. Esegui il [comando `ibmcloud`](/docs/cli/idt?topic=cloud-cli-idt-cli#idt-cli) che crea la tua istanza del servizio Voice Agent con il piano _Lite_:

   ```
   ibmcloud service create VoiceAgent _Lite_ "My Voice Agent Service"
   ```
   {: codeblock}
