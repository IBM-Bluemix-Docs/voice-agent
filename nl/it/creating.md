---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Creazione del servizio

{: shortdesc}
Puoi creare un'istanza del servizio {{site.data.keyword.iva_full}} utilizzando il catalogo {{site.data.keyword.Bluemix_short}} o un comando {{site.data.keyword.Bluemix_notm}} `ibmcloud`.

## Creazione del servizio dal catalogo
{: #catalog_create}

1. Vai alla [Pagina del catalogo {{site.data.keyword.iva_short}}](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

   La pagina del catalogo contiene informazioni sul servizio e sui relativi piani dei prezzi. Puoi modificare il valore **Service name**.

2. Fai clic su **Create**.

## Creazione del servizio dalla riga di comando
{: #command_create}

1. [Installa la CLI {{site.data.keyword.Bluemix_notm}}](../../cli/index.html#overview).

2. Esegui il [comando `ibmcloud`](../../cli/idt/commands.html#idt-cli) che crea la tua istanza del servizio Voice Agent con il piano _di prova_:

   ```
   ibmcloud service create VoiceAgent _Trial_ "My Voice Agent Service"
   ```
   {: codeblock}

## Fasi successive
{: #next}

Crea l'agent vocale dal dashboard _Manage_. Vedi [Gestione degli agent vocali](managing.html).
