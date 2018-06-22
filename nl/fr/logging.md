---

copyright:
  years: 2018
lastupdated: "2018-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Affichage des informations d'utilisation et des journaux d'appels
{: #logging}

Vous pouvez afficher l'historique d'utilisation et les journaux d'appels relatifs à vos agents locaux à partir du tableau de bord {{site.data.keyword.Bluemix_notm}}.
{: shortdesc}

## A propos de la journalisation

La journalisation est automatiquement activée pour {{site.data.keyword.iva_full}}. Vous pouvez afficher les journaux d'appels de votre agent vocal dans le tableau de bord _Utilisation_.

Le tableau de bord _Utilisation_ présente des statistiques rapides relatives à l'utilisation de votre service pour le mois en cours et les autres ressources disponibles dans votre plan. Ces informations incluent notamment le nombre maximal de connexions simultanées qui sont détectées pour le mois en cours et le nombre maximal de connexions simultanées disponibles dans votre plan. Vous pouvez également visualiser le nombre de minutes gratuites incluses dans le plan et le nombre de minutes utilisées. La section _Journaux d'appels_ suit votre section _Statistiques rapides_.

Dans la section _Journaux d'appels_, vous pouvez filtrer les journaux d'appels par date et par nom d'agent vocal afin de réduire le nombre d'appels affichés et d'isoler des journaux d'appels spécifiques.

Pour en savoir plus sur la création et l'édition d'agents vocaux, voir [Gestion des agents vocaux](managing.html).

##  Affichage des journaux d'appels

1. Depuis votre tableau de bord {{site.data.keyword.iva_short}}, accédez au tableau de bord _Utilisation_ pour afficher les tableaux _Statistiques rapides_ et _Journaux d'appels_. Chaque ligne du tableau _Journaux d'appels_ correspond à un appel.

      Pour chaque appel, vous pouvez visualiser le nom et le numéro de téléphone de votre agent local, l'heure de début et l'heure de fin, ainsi que la durée de l'appel. Il se peut également qu'un symbole d'avertissement figure en regard du nom de l'agent vocal, ce qui indique que l'appel a échoué.

1.  Vous pouvez filtrer la liste des appels en affichant les appels passés à une date spécifique ou en filtrant les appels par nom d'agent vocal.

1. Afin d'accéder aux journaux des échecs d'appel pour un appel individuel, cliquez sur l'icône **Journaux** dans la colonne **Journaux des échecs** pour cet appel.

1. Vous pouvez examiner la liste détaillée des journaux de messages dans la nouvelle vue à l'aide des méthodes suivantes :
  * Recherche dans les journaux des échecs
  * Filtrage des messages en fonction du type de journal, **Erreur** ou **Avertissement**
  * Téléchargement de votre jeu de données
  * Tri des journaux des échecs par horodatage croissant ou décroissant

1. Pour afficher les détails d'un message de journal des échecs, cliquez sur la flèche située au début de la ligne qui vous intéresse pour développer la vue. Vous pouvez consulter des informations plus détaillées dans [Messages système de Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/messages.html){:new_window}.

1. Cliquez sur la flèche de retour située en haut de la page pour revenir au tableau de bord _Utilisation_.

## Liens connexes
Vous trouverez des informations plus détaillées au sujet de la journalisation dans la rubrique [Traitement des incidents et support dans Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/troubleshooting.html){:new_window} de la documentation IBM Voice Gateway.
