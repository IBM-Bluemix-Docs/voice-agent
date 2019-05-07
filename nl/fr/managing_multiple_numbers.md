---

copyright:
  years: 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configuration de plusieurs numéros de téléphone pour un _agent unique_
{: #multi_num}

[comment]: # (Après avoir créé votre instance de service {{site.data.keyword.iva_full}}, )

Vous pouvez ajouter plusieurs numéros de téléphone à un même agent, de sorte que la configuration de l'agent s'applique à tous les numéros qui lui sont associés. La page du tableau de bord de _gestion des instances de service_ affichera le **Numéro principal** associé à l'agent. Voir [Définition d'un numéro principal](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

Vous pouvez accéder à la boîte de dialogue **Gestion** en cliquant sur **Gérer** en regard de l'option **Numéro de téléphone** depuis la page _Créer un agent vocal_ ou _Editer un agent vocal_.

  * _**Remarque :**_ Il existe une limite de 1 000 membres uniques par configuration d'agent.
{: shortdesc}


## Ajout d'un nouveau numéro
{: #add_num}

1. Cliquez sur **Gérer** en regard de **Numéro de téléphone** depuis la page _Créer un agent vocal_ ou _Editer un agent vocal_ pour ouvrir la boîte de dialogue **Gestion**.

1. Cliquez sur l'icône "Ajouter un numéro" en haut à droite de la boîte de dialogue **Gestion**. Une nouvelle entrée vide est créée dans la liste.

1. {: #format_num} Dans la zone **Numéro de téléphone**, ajoutez le numéro depuis votre liaison SIP, en incluant le code pays et l'indicatif régional. Par exemple, pour un numéro 800 aux Etats-Unis, spécifiez le numéro de téléphone sous la forme suivante : 18883334444. Le numéro de téléphone peut comporter des espaces, ainsi que les caractères + ( ) -, sans dépasser 30 caractères.  

  * _**Remarque :**_ Il existe une limite de 1 000 membres uniques par configuration d'agent.

1. Vous pouvez éventuellement fournir une description de votre numéro de téléphone dans la zone **Description**, dans la limite de 64 caractères.

1. Cliquez sur l'icône "Coche" pour sauvegarder le numéro dans la liste, ou cliquez sur l'icône "X" pour ignorer l'ajout.

1. Un message "Opération réussie !" s'affiche en haut de l'écran, ainsi qu'une nouvelle entrée de liste comportant le numéro de téléphone. Dans le cas contraire, un message d'erreur s'affiche avec la description du problème.

1. Le numéro s'affiche avec une coche **verte** dans la colonne Statut de la liste, ce qui indique que le numéro est valide.

1. Cliquez sur **Terminé** pour enregistrer et confirmer le numéro dans l'agent.

## Edition d'un numéro et/ou d'une description
{: #edit_num}

1. Cliquez sur **Gérer** en regard de **Numéro de téléphone** dans la page _Créer un agent vocal_ ou _Editer un agent vocal_. Si vous avez plusieurs numéros dans l'agent vocal, vous pouvez simplement cliquer sur la zone grisée **Numéro de téléphone** pour ouvrir la boîte de dialogue **Gestion**.

1. Mettez en évidence l'entrée du numéro que vous voulez éditer et cliquez sur la liste d'options, représentée par l'icône **trois points**, qui apparaît sur le côté droit de la liste.

1. Dans le menu déroulant qui s'ouvre, sélectionnez **Editer**.

1. Vous pouvez modifier le **Numéro de téléphone** et/ou la **Description**.

1. Cliquez sur l'icône "Coche" pour accepter la mise à jour, ou cliquez sur l'icône "X" pour ignorer les changements.

1. Un message "Opération réussie !" s'affiche en haut de l'écran, ainsi que la liste des entrées mise à jour. Dans le cas contraire, un message d'erreur s'affiche avec la description du problème.

1. Cliquez sur **Terminé** pour enregistrer les modifications apportées à l'agent.

## Suppression de numéros
{: #delete_num}

1. Cliquez sur **Gérer** en regard de **Numéro de téléphone** dans la page _Créer un agent vocal_ ou _Editer un agent vocal_. 

1. Cochez la case en regard de chaque numéro à supprimer. Si vous voulez _tous_ les supprimer, cochez la case en regard de l'en-tête **Numéro de téléphone**.

1. Cliquez sur l'icône "Supprimer l'élément" en haut à droite de la boîte de dialogue **Gestion**.

1. Un message "Opération réussie !" s'affiche en haut de l'écran, et les entrées sélectionnées sont retirées de la liste. Dans le cas contraire, un message d'erreur s'affiche avec la description du problème.

1. Pour supprimer un seul numéro de téléphone, vous pouvez également mettre en évidence l'entrée du numéro à supprimer et cliquer sur la liste d'options, représentée par **trois points**, sur le côté droit de la liste.

1. Dans le menu déroulant qui s'affiche, sélectionnez **Supprimer**.

1. Un message "Opération réussie !" s'affiche en haut de l'écran, et l'entrée mise en évidence est retirée de la liste. Dans le cas contraire, un message d'erreur s'affiche avec la description du problème.

1. Cliquez sur **Terminé** pour enregistrer et confirmer la suppression du ou des numéros de l'agent.

## Importation de numéros
{: #import_num}

Vous pouvez télécharger une liste de numéros dans l'agent, en une seule fois. Cette liste _doit_ être un fichier de type **.csv**. Le fichier peut comporter jusqu'à 1 000 **numéros de téléphone** uniques, avec un numéro par ligne, ainsi qu'une **Description** facultative pour chaque numéro.

  * _**Remarque :**_ Le téléchargement de numéros à partir d'un fichier .CSV remplace _TOUS_ les numéros actuels de l'agent. La liste de numéros ne sera _pas_ ajoutée aux numéros du fichier .CSV.

  * Les numéros du fichier .CSV _doivent_ utiliser le même format que celui utilisé lors de l'ajout d'un numéro via le tableau de bord, et doit être unique. Voir [Number Format](/docs/services/voice-agent?topic=voice-agent-multi_num#format_num).

1. Cliquez sur **Gérer** en regard de **Numéro de téléphone** dans la page _Créer un agent vocal_ ou _Editer un agent vocal_. 

1. Cliquez sur l'icône "Transférer un fichier CSV" en haut à droite de la boîte de dialogue **Gestion**. 

1. Une fenêtre s'affiche vous demandant de confirmer le remplacement de tous les numéros de la liste par les numéros du fichier .CSV. Cliquez sur **OK** pour confirmer et poursuivre.

1. Dans la nouvelle fenêtre, recherchez le fichier .CSV, sélectionnez-le et cliquez sur **Ouvrir**.

1. Un message "Opération réussie !" s'affiche en haut de l'écran, et tous les nouveaux numéros sont ajoutés à la liste. Dans le cas contraire, un message d'erreur s'affiche avec la description du problème, ainsi qu'un message d'erreur en regard de chaque numéro non valide.

1. Les numéros individuels importés s'affichent avec une coche **verte** dans la colonne _Statut_ de la liste, ce qui signifie que les numéros ne comportent pas d'erreurs. Dans le cas contraire, une erreur spécifique s'affiche dans la colonne _Statut_.

1. Cliquez sur **Terminé** pour enregistrer et confirmer l'ajout du ou des numéros de l'agent.

## Exportation de numéros
{: #export_num}

Vous pouvez exporter une liste de numéros et leurs descriptions à partir de l'agent vers un fichier **.CSV** et télécharger ce dernier vers votre ordinateur. Vous pourrez ainsi modifier les numéros et/ou les descriptions comme vous le souhaitez, puis télécharger de nouveau le fichier dans l'agent. Voir [Importation de numéros](/docs/services/voice-agent?topic=voice-agent-multi_num#import_num).

1. Cliquez sur **Gérer** en regard de **Numéro de téléphone** dans la page _Créer un agent vocal_ ou _Editer un agent vocal_. 

1. Cliquez sur l'icône "Télécharger un fichier CSV" en haut à droite de la boîte de dialogue **Gestion**.

1. Un fichier .CSV comportant tous les numéros sauvegardés dans l'agent est téléchargé sur votre ordinateur.

1. Cliquez sur **Terminé** pour quitter la boîte de dialogue **Gestion**.

## Définition d'un numéro principal
{: #primary_num}

Le _Numéro principal_ est utilisé uniquement à des fins d'affichage et n'a aucun but fonctionnel. Par défaut, le premier numéro ajouté à l'agent sera libellé en tant que **Numéro principal**, qui désigne le numéro affiché sur la page de tableau de bord de _gestion d'une instance de service_. Au moins un **Numéro principal** doit exister dans un agent vocal.

Vous pouvez remplacer le libellé **Numéro principal** par n'importe quel numéro de votre choix dans l'agent vocal.

1. Cliquez sur **Gérer** en regard de **Numéro de téléphone** dans la page _Créer un agent vocal_ ou _Editer un agent vocal_. 

1. Mettez en évidence l'entrée du numéro que vous voulez éditer et cliquez sur la liste d'options, représentée par l'icône **trois points**, qui apparaît sur le côté droit de la liste.

1. Dans le menu déroulant qui s'affiche, sélectionnez **Définir comme principal**.

1. Un message "Opération réussie !" s'affiche en haut de l'écran. L'entrée que vous avez choisie est associée au libellé **Principal** dans la colonne _Statut_. Dans le cas contraire, un message d'erreur s'affiche avec la description du problème.

1. Cliquez sur **Terminé** pour enregistrer les modifications apportées à l'agent.

## Tri et navigation des numéros de téléphone
{: #sort_num}

Vous pouvez trier la liste par _Numéro de téléphone_ ou _Description_, dans l'ordre croissant ou décroissant. Par défaut, la liste des numéros de téléphone est triée dans l'ordre croissant par **Numéro de téléphone**.

1. Cliquez sur l'en-tête **Numéro de téléphone** pour effectuer un tri numérique sur les numéros de la liste.

1. Cliquez sur l'en-tête **Description** pour effectuer un tri alphabétique sur les _descriptions_ de la liste.  

Vous pouvez également choisir un nombre différent de numéros à afficher par page dans la liste. Vous pouvez choisir d'afficher 5, 10 ou 30 numéros par page. Vous pouvez également accéder à différentes pages de numéros.

1. Cliquez sur le numéro en regard de l'option **Eléments par page** pour choisir le nombre d'entrées à afficher dans la liste. Par défaut, 5 entrées par page sont affichées.

1. Cliquez sur la flèche _Droite_ ou _Gauche_ au-dessus de l'en-tête **Statut** pour passer d'une page à l'autre.

1. Vous pouvez également cliquer directement sur le nombre entre les flèches pour choisir la page à afficher.

1. Cliquez sur **Terminé** pour enregistrer les modifications apportées à l'agent.

## Enregistrement de modifications
{: #save_changes}

Si vous souhaitez apporter des modifications à la liste de numéros dans l'agent vocal, vous _devez_ sauvegarder les modifications dans la page **Gestion**, ainsi que celles apportées dans la page _Editer un agent vocal_.

1. Cliquez sur **Gérer** en regard de **Numéro de téléphone** dans la page _Créer un agent vocal_ ou _Editer un agent vocal_. 

1. Apportez les modifications aux numéros de la liste selon vos besoins.

1. Cliquez sur **Terminé** pour enregistrer les modifications dans l'agent.

1. Vous serez redirigé vers la page _Editer un agent vocal_. Cliquez sur **Sauvegarder les modifications** en haut à droite pour appliquer l'ensemble de vos modifications.

* _**Remarque :**_ Vous _devez_ cliquer sur **Terminé** dans la boîte de dialogue **Gestion** _et_ sur **Sauvegarder les modifications** sur la page _Editer un agent vocal_ pour enregistrer vos modifications, faute de quoi elles seront ignorées.

## Recherche de numéros ou de descriptions
{: #search_num}

Vous pouvez retrouver un numéro à l'aide d'une recherche sur un numéro ou une description.

1. Cliquez sur **Gérer** en regard de **Numéro de téléphone** dans la page _Créer un agent vocal_ ou _Editer un agent vocal_. 

1. Dans la barre de _recherche_, entrez un numéro ou une description à rechercher dans la liste. Lorsque vous tapez, les résultats de la recherche sont mis à jour automatiquement.

1. Cliquez sur **Terminé** pour enregistrer les modifications dans l'agent.
