---

copyright:
  years: 2018
lastupdated: "2018-10-30"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Evénements Activity Tracker
{: #activity-tracker}

Utilisez le service {{site.data.keyword.cloudaccesstrailfull}} pour savoir comment les utilisateurs et les applications interagissent avec le service {{site.data.keyword.iva_full}} dans {{site.data.keyword.Bluemix}}. {: shortdesc}

Le service {{site.data.keyword.cloudaccesstrailfull_notm}} enregistre les activités initiées par l'utilisateur qui changent l'état d'un service dans {{site.data.keyword.Bluemix_notm}}. Pour plus d'informations, voir [{{site.data.keyword.cloudaccesstrailshort}}](../cloud-activity-tracker/index.html#getting-started-with-cla).

## Liste des événements
{: #event-List}

Le tableau suivant répertorie les actions qui génèrent un événement.

|Action| Description |
| --- | ---- |
| `create agent: POST /config/submitconfig` | Création d'un nouvel agent vocal |
| `update agent: POST /config/submitconfig` | Mise à jour d'un agent vocal |
| `Update concurrency: POST /config/updatemax` | Mise à jour du nombre maximal d'accès concurrents pour les appels |
| `delete agent: POST /config/submitconfig` | Suppression d'un agent vocal |
{: caption="Tableau 1. Actions qui génèrent des événements" caption-side="top"}

## Où consulter les événements d'activité
{: #view-event}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le domaine de compte {{site.data.keyword.cloudaccesstrailshort}} qui se trouve dans la région {{site.data.keyword.Bluemix_notm}} où les événements sont générés.

## Filtrage des événements
{: #filter_events}

### Filtrage par ID d'agent vocal
{: #filter_id}

Vous pouvez filtrer la liste des événements d'activité d'un agent vocal donné en fonction de son ID d'instance.

1. Accédez à la page de gestion d'{{site.data.keyword.cloudaccesstrailshort}}.
2. Entrez `target.name_str` dans la **zone de recherche** et votre ID d'instance d'agent vocal dans la zone **Rechercher**, sous la forme d'une chaîne. Vérifiez que votre ID d'instance d'agent vocal est codé avec des caractères % et que vous utilisez un caractère générique de recherche (_*_).

Par exemple, pour rechercher votre ID D'instance d'agent vocal `serviceInstanceId=crn%3A...` :

  * **Zone de recherche** : `target.name_str`
  * **Rechercher** : `"*crn%3A...*"`

### Filtrage par événement d'action
{: #filter_action}

Vous pouvez également filtrer la liste des événements d'activité pour des événements d'action spécifiques.

1. Accédez à la page de gestion d'{{site.data.keyword.cloudaccesstrailshort}} et entrez les valeurs de configuration suivantes pour chacune des zones.

  * **Afficher les journaux** : `Journaux d'espace`
  * **Zone de recherche** : `action_str`
  * **Rechercher** : `"chaîne action"`

## Création de filtres avancés
{: #advanced_filters}

Vous pouvez aussi créer des filtres avancés en utilisant les opérateurs `AND` ou `OR` pour combiner des termes de recherche dans la zone **Rechercher**.

Par exemple, pour filtrer en fonction d'un ID d'instance d'agent vocal donné et d'une action spécifique :

* **Afficher les journaux** : `Journaux d'espace`
* **Zone de recherche** : `target.name_str`
* **Rechercher** : `"*crn%3A...*" AND action_str:"chaîne action"`

**N'oubliez pas !** Vérifiez que votre id d'instance d'agent vocal est codé avec des caractères % et que vous utilisez un caractère générique de recherche (_*_).
