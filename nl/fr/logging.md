---

copyright:
  years: 2018
lastupdated: "2018-11-12"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Affichage de l'utilisation et des journaux d'appels et de SMS
{: #logging}

Vous pouvez afficher l'historique d'utilisation et les journaux d'appels et de SMS de vos agents vocaux à partir du tableau de bord {{site.data.keyword.Bluemix_notm}}.
{: shortdesc}

## A propos de la journalisation

La journalisation est automatiquement activée pour {{site.data.keyword.iva_full}}. Vous pouvez afficher les journaux d'appels de votre agent vocal dans le tableau de bord _Utilisation_.

Le tableau de bord _Utilisation_ présente des statistiques rapides relatives à l'utilisation de votre service et les autres ressources disponibles dans votre plan. Ces informations incluent notamment le nombre maximal de connexions simultanées qui sont détectées pour le mois en cours et le nombre maximal de connexions simultanées disponibles dans votre plan. Dans la zone _Minutes d'appels_, vous pouvez voir le nombre de minutes gratuites incluses dans le plan et le nombre de minutes utilisées. La section _Journaux d'appels_ suit votre section _Statistiques rapides_. La section _Journaux SMS_ affiche des statistiques similaires d'utilisation des SMS sur vos agents. 

Vous pouvez filtrer les _journaux d'appels_ et les _minutes d'appels_ par date et par noms ou numéros d'agent afin de réduire le nombre d'appels affichés et d'isoler des journaux d'appels spécifiques. Vous pouvez filtrer les _journaux SMS_ par date et par noms ou numéros d'agent. En outre, vous pouvez filtrer les _journaux d'appels_ pour afficher uniquement les appels ayant échoué.

Pour en savoir plus sur la création et l'édition d'agents vocaux, voir [Gestion des agents vocaux](/docs/services/voice-agent?topic=voice-agent-managing).

##  Affichage des journaux d'appels

1. Depuis votre tableau de bord {{site.data.keyword.iva_short}}, accédez au tableau de bord _Utilisation_ pour afficher les tableaux _Statistiques rapides_ et *Journaux d'appels*. Chaque ligne du tableau _Journaux d'appels_ correspond à un appel.

      Pour chaque appel, vous pouvez visualiser le nom et le numéro de téléphone de votre agent local, l'heure de début et l'heure de fin, ainsi que la durée de l'appel. Il se peut également qu'un symbole d'avertissement figure en regard du nom de l'agent vocal, ce qui indique que l'appel a échoué.

1.  Vous pouvez filtrer la liste des appels en affichant les appels passés à une date spécifique et en filtrant les appels par nom ou numéro d'agent vocal. Vous pouvez également choisir de n'afficher que les appels ayant échoué.

1. Afin d'accéder aux journaux des échecs d'appel pour un appel individuel, cliquez sur les points dans la colonne **Actions** de cet appel pour développer le menu. Choisissez ensuite **Journaux des échecs**. Cette option apparaît uniquement pour les appels ayant échoué.

1. Vous pouvez examiner la liste détaillée des journaux de messages dans la nouvelle vue à l'aide des méthodes suivantes :
  * Recherche dans les journaux des échecs
  * Filtrage des messages en fonction du type de journal, **Erreur** ou **Avertissement**
  * Téléchargement de votre jeu de données
  * Tri des journaux des échecs par horodatage croissant ou décroissant

1. Pour afficher les détails d'un message de journal des échecs, cliquez sur la flèche située au début de la ligne qui vous intéresse pour développer la vue. Vous pouvez consulter des informations plus détaillées dans [Messages système de Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/messages.html){:new_window}.

1. Cliquez sur la flèche de retour située en haut de la page pour revenir au tableau de bord _Utilisation_.

##  Affichage des journaux SMS

1. Depuis votre tableau de bord {{site.data.keyword.iva_short}}, accédez au tableau de bord _Utilisation_ pour afficher la section _Statistiques rapides_, puis cliquez sur *Journaux SMS*. Chaque ligne du tableau _Journaux SMS_ correspond à un agent et un numéro.

      Pour un agent, vous pouvez afficher le numéro de téléphone de votre agent vocal ainsi que les messages entrants, les messages sortants et les messages facturables. Il se peut également qu'un symbole d'avertissement figure en regard du nom de l'agent vocal, ce qui indique que les messages SMS ont échoué.

      - Les **messages entrants** sont des messages envoyés par l'utilisateur à l'agent ; ils ne sont facturés que si l'agent envoie une réponse à l'utilisateur. 

      - Les **messages sortants** sont les messages envoyés de l'agent à l'utilisateur. Ces messages sont envoyés en réponse à un message entrant ou lorsque Voice Gateway envoie un message à l'utilisateur sans nécessiter d'autre message entrant. 

      - Les **messages facturables** sont tous les messages entrants et sortants auxquels l'agent a répondu.

1.  Vous pouvez filtrer la liste des agents en affichant les messages d'une date spécifique et en filtrant les messages par nom ou numéro d'agent vocal. 

1. Pour accéder aux journaux SMS d'un agent individuel :

  - Dans la colonne **Actions** de l'appel concerné, cliquez sur les points pour développer le menu.
  
  - Cliquez sur **Journaux SMS**.

1. Cliquez sur la flèche de retour située en haut de la page pour revenir au tableau de bord _Utilisation_.

## Liens connexes
Vous trouverez des informations plus détaillées au sujet de la journalisation dans la rubrique [Traitement des incidents et support dans Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/troubleshooting.html){:new_window} de la documentation IBM Voice Gateway.
