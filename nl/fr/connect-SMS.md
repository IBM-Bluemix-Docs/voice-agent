---

copyright:
  years: 2019
lastupdated: "2019-06-21"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Connexion aux fournisseurs SMS
{: #connect-sms}

Vous pouvez choisir dans la liste ci-après le fournisseur SMS que vous utilisez pour l'intégration à {{site.data.keyword.iva_full}}.
{: #shortdesc}

* [Twilio](#twilio-setup)

## Génération d'une clé d'API et définition des données d'identification
{: #sms_access}

Vous ne pouvez créer des données d'identification que pour des rôles déjà actifs dans votre compte. Pour les agents SMS Voix + SMS, vous devez avoir le rôle *Auteur* ou *Responsable*. Voir le [point 9 de Inviter des utilisateurs et leur affecter un accès initial](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. Dans le *Tableau de bord* de votre instance {{site.data.keyword.iva_short}}, cliquez sur **Nouvelles données d'identification (+)**. 
2. Dans la nouvelle boîte de dialogue qui s'affiche, entrez un **Nom** et, dans le menu déroulant **Rôle**, sélectionnez *Auteur* ou *Responsable*. 
    - **Remarque :** pour les fonctionnalités liées aux SMS, vous **_devez_** sélectionner le rôle *Auteur* ou *Responsable*. 
3. Cliquez sur **Ajouter**.
4. En regard des données d'identification que vous venez de créer, cliquez sur **Afficher les données d'identification**. Notez la valeur de `APIKEY` dans le script JSON pour une utilisation dans [Configuration de Twilio pour les SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

## Configuration de Twilio pour les SMS
{: #twilio-setup}

1. Accédez à vos numéros de téléphone Twilio en cliquant [ici](https://www.twilio.com/console/phone-numbers/) et sélectionnez celui affecté à votre agent _SMS_ ou _Voix + SMS_. 

1. Faites défiler l'écran jusqu'à la section **Messagerie**. Dans la zone _CONFIGURE WITH_, sélectionnez **Webhooks, TwiML Bins, Functions, Studio ou Proxy** dans le menu déroulant.

1. Dans la zone _A MESSAGE COMES IN_, sélectionnez **Webhook** dans le menu déroulant.

1. Dans la zone d'URL vide en regard de **Webhook**, suivez les instructions pour la région de votre agent. 

    - Si l'agent que vous avez créé se trouve dans la région de Washington, entrez `https://apikey:VOTRE_CLE_API@sms-east.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` dans cette zone.
    - Si l'agent que vous avez créé se trouve dans la région de Dallas, entrez `https://apikey:VOTRE_CLE_API@sms-south.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` dans cette zone.
    - Remplacez `VOTRE_CLE_API` de l'URL précédente par la valeur `APIKEY` issue des données d'identification précédemment créées. Voir [Génération d'une clé d'API et définition des données d'identification](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_access). 

1. Cliquez sur **Sauvegarder** 
