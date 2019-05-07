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

# Edition du nombre maximal de connexions simultanées
{: #edit_concurrency}

Si vous utilisez les plans _Standard_ ou _Premium_, vous pouvez changer le nombre maximal de connexions simultanées défini dans les paramètres par défaut.
{: shortdesc}

Dans tous les plans, vous recevez gratuitement 2 connexions simultanées. Pour plus d'informations, voir [Plans de tarification](https://cloud.ibm.com/catalog/services/voice-agent-with-watson). Sur le tableau de bord _Gestion_, le nombre maximal de connexions simultanées autorisées dans votre plan figure dans la zone **Nombre maximal de connexions simultanées**. En outre, le nombre maximal de connexions simultanées qui sont utilisées par vos agents vocaux durant le mois en cours figure dans la zone **Nombre maximal de connexions simultanées utilisées**.

1. Pour modifier le nombre maximal de connexions simultanées de votre plan, accédez à l'onglet _Instances_ sur votre tableau de bord _Gestion_.

1. Si vous souhaitez modifier le nombre maximal de connexions simultanées de votre plan, cliquez sur l'icône **Editer**.

1. Dans _Editer le nombre maximal de connexions simultanées_, entrez le nombre maximal de connexions simultanées, puis cliquez sur **Sauvegarder**.

Vous pouvez définir entre 10 et 50 connexions simultanées en libre-service. Si vous avez besoin de plus de 50 connexions simultanées pour votre agent vocal, voir [Demande de configuration réseau assistée](/docs/services/voice-agent?topic=voice-agent-connect#request-setup).

## Informations de tarification relatives aux connexions simultanées
{: #concurrent-charge}

  * Les plans _Lite_ et _Standard_ incluent 2 connexions simultanées gratuites.
  * Les plans _Premium_ sont personnalisés par instance.
  * Dans un plan _Standard_, vous disposez d'une capacité minimale de 10 connexions simultanées.
  * L'utilisation des connexions simultanées est répartie au prorata mois par mois. Si vous utilisez plus de 2 connexions simultanées dans une même journée, le tarif quotidien vous est facturé. Par exemple, votre plan prend en charge 2 connexions simultanées gratuites et vous définissez une limite maximale de 12 connexions. Si vous utilisez uniquement 5 connexions simultanées dans une journée, 3 connexions simultanées vous sont facturées.
  * Si vous disposez d'un plan _Standard_ ou _Premium_, vous pouvez acheter une capacité de connexions simultanées supérieure.
  * Un tarif quotidien vous est facturé pour la capacité maximale de connexions simultanées que vous utilisez dans une journée.

Pour plus d'informations sur les plans, les tarifs et les fonctions, voir [Plans de tarification](https://cloud.ibm.com/catalog/services/voice-agent-with-watson).
