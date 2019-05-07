---

copyright:
  years: 2018
lastupdated: "2018-06-14"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Sécurisation des connexions
{: #securing}

Vous pouvez activer le protocole SRTP (Secure Real Time Transport Protocol) et le chiffrement à l'aide de TLS (Transport Layer Security) pour vos liaisons SIP afin de sécuriser les connexions qui sont établies avec {{site.data.keyword.iva_full}}.

## Configuration de SRTP dans Twilio
{: #SRTP}

**Remarque :** si vous activez SRTP, les messages SIP sont également chiffrés. Vous n'avez pas besoin d'activer SRTP et le chiffrement de message SIP séparément.

1. Dans votre compte Twilio, accédez au tableau de bord _Elastic SIP Trunking_ et sélectionnez **Trunks**.

1. Choisissez la liaison que vous souhaitez sécuriser avec SRTP en sélectionnant une liaison existante ou en créant une nouvelle liaison en cliquant sur l'icône **+**.

  * Si vous créez une nouvelle liaison, vous devez configurer l'_URI de liaison SIP_ dans le tableau de bord **Origination**.  Pour plus d'informations, voir [Connexion d'une liaison SIP](/docs/services/voice-agent?topic=voice-agent-connect).

1. Sur le tableau de bord _General_, recherchez la section _Secure Trunking_. Cliquez sur **Disabled** pour affecter la valeur **Enabled** au paramètre de commutation automatique de canaux sécurisé, puis sauvegardez vos modifications.

## Activation du chiffrement uniquement pour les messages SIP à l'aide de TLS dans Twilio
{: #TLS}

Si vous souhaitez chiffrer uniquement des messages SIP dans {{site.data.keyword.iva_short}} sans SRTP, vous pouvez sélectionner un noeud final d'URI qui utilise TLS (Transport Layer Security) dans Twilio.

1. Dans votre compte Twilio, accédez au tableau de bord _Elastic SIP Trunking_ et sélectionnez **Trunks**.

1. Choisissez la liaison à laquelle vous souhaitez ajouter le transfert d'appel en sélectionnant une liaison existante ou en créant une nouvelle liaison en cliquant sur l'icône **+**.

1. Sélectionnez **Origination** dans le menu et entrez un par un les URI d'origine sécurisé suivants. Grâce à l'ajout de plusieurs noms d'hôte ou adresses IP, si le premier noeud final d'hôte échoue ou est hors service, votre fournisseur de liaison SIP dirige les appels vers le nom d'hôte suivant dans la liste.

```
sip:us-south.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}

Ou

```
sip:us-east.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}
