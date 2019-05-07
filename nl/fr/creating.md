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


# Création du service

Vous pouvez créer une instance de service {{site.data.keyword.iva_full}} à l'aide du catalogue {{site.data.keyword.Bluemix_short}} ou avec une commande {{site.data.keyword.Bluemix_notm}} `ibmcloud`.
{: shortdesc}


## Création du service à partir du catalogue
{: #catalog_create}

1. Accédez à la [page de catalogue de {{site.data.keyword.iva_short}}](https://cloud.ibm.com/catalog/services/voice-agent-with-watson).

   La page de catalogue contient des informations sur le service et ses plans de tarification. Vous pouvez modifier la valeur **Nom de service**.

2. Cliquez sur **Créer** pour [créer un agent vocal à partir du tableau de bord _Gestion_](/docs/services/voice-agent?topic=voice-agent-config_instance#config_instance).

## Création du service à partir de la ligne de commande
{: #command_create}

1. [Installez l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli#overview).

2. Exécutez la [commande `ibmcloud`](/docs/cli/idt?topic=cloud-cli-idt-cli#idt-cli) qui crée votre instance de service Agent vocal avec le plan _Lite_ :

   ```
   ibmcloud service create VoiceAgent _Lite_ "My Voice Agent Service"
   ```
   {: codeblock}
