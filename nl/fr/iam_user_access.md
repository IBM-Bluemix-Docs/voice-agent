---

copyright:

  years: 2019

lastupdated: "2019-06-06"
subcollection: "voice-agent"

keywords: Voice Agent IAM, Voice Agent user access, get started with IAM, IAM tutorial, IAM quick start, user access, SMS IAM, SMS user access

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}

# Configuration d'IAM et de l'accès utilisateur
{: #iam}

Ce tutoriel est conçu pour vous aider à maîtriser rapidement IBM Cloud Identity and Access Management (IAM) en invitant des utilisateurs dans votre compte et en affectant des droits d'accès Cloud IAM à ces utilisateurs pour une instance {{site.data.keyword.iva_short}}.
{:shortdesc}

## Avant de commencer
{: #iam-before-you-begin}

Si vous débutez avec IAM, consultez la documentation suivante pour en savoir plus sur les fonctionnalités, concepts et composants du système de gestion des accès.

* [IBM Cloud Identity and Access Management](/docs/iam?topic=iam-iamoverview) qui présente rapidement la fonction d'IAM dans IBM, la disponibilité des fonctions et les liens vers les documentations disponibles concernant l'interface de ligne de commande et les API.
* [Concepts IAM](/docs/iam?topic=iam-iamconcepts) qui présente les concepts de haut niveau d'IAM qui vous aideront à mieux appréhender les différents composants lorsque vous démarrez.
* [Accès IAM](/docs/iam?topic=iam-userroles) qui examine plus en profondeur le fonctionnement de la gestion des accès par le biais de règles d'accès.

Ce guide couvre les scénarios les plus courants d'ajout et d'affectation de droits d'accès à des utilisateurs. Il existe de nombreuses autres options et configurations pour les rôles et les droits d'accès des utilisateurs. Les liens précédents fournissent plus de détails. 

## Etape 1. Inviter des utilisateurs et leur affecter un accès initial
{: #step1}

Vous pouvez inviter un ou plusieurs utilisateurs et définir une règle d'accès initiale pour les utilisateurs sur l'invitation. Si vous invitez plusieurs utilisateurs avec une seule invitation, le même accès est accordé à chacun de ces utilisateurs. Dans la section **accès** de la page **Inviter des utilisateurs**, seuls les rôles de l'utilisateur que vous êtes autorisé à affecter s'affichent.

Le propriétaire du compte peut affecter des rôles Cloud IAM aux utilisateurs invités dans la section **Services**. En tant que propriétaire de compte, vous pouvez accorder des droits d'accès à :
* toutes les ressources d'un groupe de ressources ;
* toutes les ressources d'un service spécifique d'un groupe de ressources ; 
* tous les services avec l'offre Identity and Access du compte ;
* une seule ressource du compte ;
* aux services de gestion des comptes.

Pour affecter des rôles Cloud IAM à des utilisateurs dans votre nuage, procédez comme suit.

1. Accédez à **Gérer** &gt; **Accès (IAM)**, puis sélectionnez **Utilisateurs**.
2. Cliquez sur **Inviter des utilisateurs**.
3. Indiquez l'adresse électronique de l'utilisateur que vous voulez inviter.
4. Dans la section **Accès**, développez l'option **Services**.
5. Sélectionnez d'accorder l'accès à une **Ressource**, à des ressources dans un **Groupe de ressources** ou aux **Services de gestion des comptes**.
6. Selon votre sélection, suivez les invites pour indiquer l'accès souhaité. Si vous avez sélectionné l'option _Groupe de ressources_, vous pouvez également la fournir à l'utilisateur un accès pour affichage, édition ou gestion au groupe de ressources en sélectionnant un rôle pour l'accès au groupe de ressources.
7. Dans la zone d'entrée **Services**, sélectionnez *{{site.data.keyword.iva_short}}* dans le menu déroulant ou saisissez cet intitulé dans la zone et appuyez sur Entrée. 
8. Sélectionnez la **Région** et l'**Instance de service** appropriées.
9. Sous la section **Sélectionner des rôles**, choisissez entre *Responsable*, *Auteur* et *Lecteur*. Si votre *Instance de service* {{site.data.keyword.iva_short}} utilise des SMS, vous **devez** sélectionner le rôle *Auteur* ou *Responsable* en plus de tout autre rôle que vous voulez accorder.
    - Pour plus d'informations sur les **Rôles**, voir [Rôles Accès au service](/docs/iam?topic=iam-userroles#service_access_roles).
10. Si vous détenez le droit approprié, vous pouvez également affecter un accès à Cloud Foundry ou à l'infrastructure lors de l'invitation.
11. Cliquez sur **Inviter des utilisateurs**.

Pour plus d'informations, voir [Invitation d'utilisateurs et affectation d'accès](/docs/iam?topic=iam-iamuserinv#iamuserinv).

## Etape 2. Créer des groupes d'accès
{: #step2}

Pour rationaliser le processus d'affectation d'accès à des utilisateurs de votre compte, vous pouvez créer des groupes d'accès. Ces derniers permettent d'organiser des utilisateurs et des ID de service auxquels vous pouvez facilement affecter l'accès en définissant une règle unique pour l'ensemble du groupe.

### Configuration de vos groupes
{: #group_setup}

Pour créer un groupe d'accès, procédez comme suit.

1. Dans la barre de menus, cliquez sur **Gérer** &gt; **Accès (IAM)** puis sélectionnez **Groupes d'accès**.
2. Cliquez sur **Créer**.
3. Entrez un nom pour votre groupe. L'ajout d'une description est facultatif.
4. Cliquez sur **Créer**.

Ensuite, poursuivez la configuration de votre groupe en ajoutant des utilisateurs ou des ID de service.

1. Vous serez dirigé vers la page groupe d'accès nouvellement créé. Ce groupe figure également dans la liste _Groupe_ de la page **Groupes d'accès** sur la barre de menus.
2. Cliquez sur **Ajouter des utilisateurs**.
3. Sélectionnez dans la liste les utilisateurs que vous voulez ajouter, puis cliquez sur **Ajouter au groupe**.
4. Pour ajouter des ID de service au groupe, cliquez sur **ID de service**.
5. Sélectionnez dans la liste les ID que vous voulez ajouter, puis cliquez sur **Ajouter au groupe**.

### Affectation d'accès à vos groupes
{: #group_access}

Une fois votre groupe créé, vous pouvez affecter des accès à toutes les entités du groupe en utilisant une seule règle ou plusieurs règles.

1. Dans la barre de menus, cliquez sur **Gérer** &gt; **Accès (IAM)** puis sélectionnez **Groupes d'accès**.
2. Sélectionnez le groupe auquel vous voulez affecter un accès.
3. Dans l'onglet **Règles d'accès**, cliquez sur **Affecter un accès** pour définir une règle d'accès. Répétez cette action autant de fois que nécessaire pour affecter des accès supplémentaires.

En organisant les utilisateurs en groupes d'accès, vous pouvez affecter à un groupe d'utilisateurs un accès à une seule règle, ce qui réduit le nombre total de règles à gérer.
{: tip}


## Etape 3. Gérer l'accès d'utilisateurs existants
{: #user_access_manage}

La section suivante décrit comment gérer et éditer l'accès pour les utilisateurs et les groupes que vous avez déjà configurés dans votre compte.

### Affectation d'un nouvel accès
{: #new_access}

Pour affecter une nouvelle règle d'accès, procédez comme suit :

1. Dans la barre de menus, cliquez sur **Gérer** &gt; **Accès (IAM)** puis sélectionnez **Utilisateurs**.
2. Sélectionnez le nom de l'utilisateur auquel vous voulez affecter un accès.
3. Cliquez sur **Règles d'accès**.
4. Cliquez sur **Affecter un accès**.
5. Choisissez comment vous voulez affecter l'accès :
    * Sélectionnez **Affecter l'accès au sein d'un groupe de ressources** pour affecter l'accès à toutes les ressource d'un groupe ou aux ressources désignées d'un service spécifique au sein d'un groupe. Vous pouvez également accorder à des utilisateur un droit d'affichage, d'édition ou de gestion des accès au groupe de ressources en leur attribuant un rôle de l'utilisateur pour le groupe de ressources. Sélectionnez **Aucun accès** si vous voulez n'accorder à un utilisateur que l'accès à une ressource spécifique et non à l'intégralité du groupe de ressources.
    * Sélectionnez **Affecter l'accès aux ressources** pour affecter l'accès à toutes les ressources du compte pour lesquelles l'offre Identity and Access est activée, à toutes les ressources d'un service spécifique du compte, à une seule instance ou à une seule ressource d'une instance de service spécifique.
    * Sélectionnez **Affecter l'accès aux services de gestion des comptes** pour accorder l'accès à tous les services de gestion de compte ou bien à un seul.
5. Sélectionnez toute combinaison de rôles afin de définir la portée de l'accès. Pour plus d'informations, voir [Rôles Cloud IAM](/docs/iam?topic=iam-userroles#iamusermanrol).
6. Cliquez sur **Affecter**.


### Edition d'un accès existant
{: #editing_access}

Vous pouvez mettre à jour un accès existant en éditant les rôles affectés à un utilisateur.

1. Dans la barre de menus, cliquez sur **Gérer** &gt; **Accès (IAM)** puis sélectionnez **Utilisateurs**.
2. Sélectionnez le nom de l'utilisateur dont vous voulez éditer l'accès.
3. Cliquez sur **Règles d'accès**.
4. Cliquez sur **Editer** dans le menu **Actions** ![Icône Liste des actions](../icons/action-menu-icon.svg) sur la ligne correspondant à la règle à éditer.
4. Editez la règle en mettant à jour les rôles affectés.
5. Cliquez sur **Sauvegarder**

Vous pouvez supprimer l'accès d'un utilisateur en cliquant sur l'option **Retirer** du menu **Actions** ![Icône Liste des actions](../icons/action-menu-icon.svg) pour la règle à retirer.

## Etape 4. Affectation d'un accès à des agents SMS ou Voix + SMS (facultatif)
{: #sms_access}

Si l'agent auquel vous affectez un accès est un agent **SMS** ou **Voix + SMS**, créez de *Nouvelles données d'identification*.

### Création de nouvelles données d'identification
{: #new_cred}

Vous ne pouvez créer des données d'identification que pour des rôles déjà actifs dans votre compte. Pour les agents SMS et Voix + SMS, vous devez avoir le rôle *Auteur* ou *Responsable*. Voir le [point 9 de Inviter des utilisateurs et leur affecter un accès initial](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. Dans le *Tableau de bord* de votre instance {{site.data.keyword.iva_short}}, cliquez sur **Nouvelles données d'identification (+)**. 
2. Dans la nouvelle boîte de dialogue qui s'affiche, entrez un **Nom** et, dans le menu déroulant **Rôle**, sélectionnez *Auteur* ou *Responsable*. 
    - **Remarque :** pour les fonctionnalités liées aux SMS, vous **_devez_** sélectionner le rôle *Auteur* ou *Responsable*. 
3. Cliquez sur le bouton **Ajouter**. 

## Traitement des incidents
{: #troubleshoot}

Lorsque vous essayez de créer de *Nouvelles données d'identification*, si un message d'erreur tel que le suivant s'affiche sur la page **Données d'identification pour le service** :
> You do not have the required permission to assign role ‘Writer’. Contact the account owner to update your access.

suivez alors les instructions pour vous affecter un accès *Auteur* ou *Responsable*, accès **requis** pour les fonctions liées aux SMS. Voir le [point 9 de Affectation d'un accès](/docs/services/voice-agent?topic=voice-agent-iam#step1) et poursuivez avec [Création de nouvelles données d'identification](/docs/services/voice-agent?topic=voice-agent-iam#new_cred).

## Etapes suivantes
{: #next}

Pour en savoir plus sur ce que Cloud IAM peut faire, voir la liste des [fonctions Cloud IAM](/docs/iam?topic=iam-iamoverview#features).
