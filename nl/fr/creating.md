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


# Création du service

{: shortdesc}
Vous pouvez créer une instance de service {{site.data.keyword.iva_full}} en utilisant le catalogue {{site.data.keyword.Bluemix_short}} ou une commande {{site.data.keyword.Bluemix_notm}} `ibmcloud`.

## Création du service à partir du catalogue
{: #catalog_create}

1. Accédez à la [page de catalogue {{site.data.keyword.iva_short}}](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

   La page de catalogue contient des informations sur le service et ses plans de tarification. Vous pouvez modifier la valeur **Nom de service**.

2. Cliquez sur **Créer**.

## Création du service à partir de la ligne de commande
{: #command_create}

1. [Installez l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}](../../cli/reference/bluemix_cli/get_started.html).

2. Exécutez la commande [`ibmcloud` ](../../cli/reference/bluemix_cli/bx_cli.html#bluemix_cli) qui permet de créer votre instance de service Voice Agent avec le plan _Trial_ :

   ```
   ibmcloud service create VoiceAgent _Trial_ "My Voice Agent Service"
   ```
   {: codeblock}

## Etapes suivantes
{: #next}

Créez l'agent vocal à partir du tableau de bord _Gestion_. Voir [Gestion des agents vocaux](managing.html).
