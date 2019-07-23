---

copyright:
  years: 2019
lastupdated: "2019-06-17"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Foire aux questions liées à la tarification
{: #faq-pricing}

## Quel est le coût d'utilisation du service {{site.data.keyword.iva_short}} standard ?
{: #faq-pricing-zero}
{: faq}

 Pour plus d'informations, voir la [page de tarification](https://cloud.ibm.com/catalog/services/voice-agent-with-watson){: external}.

## Que signifie "tarification à la minute" ?
{: #faq-pricing-one}
{: faq}

Le prix est basé sur la quantité (nombre de minutes) d'appels envoyés au service. Le prix ne dépend pas de la durée nécessaire au service pour traiter l'appel.


## Est-ce que vous calculez à la minute près pour chaque appel de l'API ?
{: #faq-pricing-two}
{: faq}

{{site.data.keyword.IBM_notm}} ne calcule pas à la minute près la durée de l'appel pour chaque appel d'API que reçoit le service. {{site.data.keyword.IBM_notm}} cumule la durée d'utilisation sur le mois, puis calcule à la minute près en fin de chaque mois. La durée de chaque appel est arrondie à la minute supérieure. Par exemple, si vous effectuez un premier appel de 3,1 secondes et un second de 25,9 secondes, {{site.data.keyword.IBM_notm}} comptabilise 4 secondes pour le premier appel et 26 secondes pour le deuxième appel. Puis la durée d'appel totale est comptée pour une minute.


## Comment est calculée une connexion simultanée et où est-ce appliqué ?
{: #faq-pricing-three}
{: faq}

La connexion simultanée est applicable uniquement aux appels vocaux (pas aux SMS). Une connexion simultanée est calculée d'après le nombre de connexions vers tous les numéros de téléphone définis simultanément dans l'instance de service. Le nombre maximum effectif quotidien de connexions simultanées utilisées est facturé, au prorata des frais mensuels.

## Quelle est la définition du nombre maximum de connexions simultanées et comment la modifier ?

{: #faq-pricing-four}
{: faq}

Le nombre maximum de connexions simultanées correspond au nombre maximum de connexions autorisées à tout moment et il s'agit du nombre maximum de connexions facturées. Le nombre maximum de connexions simultanées peut être défini et modifié dans le [tableau de bord](https://cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-edit_concurrency). La capacité simultanée maximale sur un plan standard est de 50 connexions et vous pouvez ouvrir un ticket de demande de service s'il vous en faut plus.

## Comment sont facturés les messages SMS/MMS entrants et sortants ?

{: #faq-pricing-five}
{: faq}

Les messages entrants ne sont pas facturés tant qu'une réponse n'a pas été envoyée à l'utilisateur. Une session est créée lorsqu'un message sortant est envoyé à l'utilisateur via Voice Gateway (passerelle vocale) ou comme réponse à un message entrant. Les messages entrants et sortants qui ont reçu une réponse sont tous deux facturés, le cas échéant.
Les messages entrants comme sortants sont facturés jusqu'à expiration de la session. Une fois la session expirée, le contexte de la conversation est supprimé. Le délai d'expiration de session, qui est de 3600 secondes par défaut, peut être défini dans le tableau de bord.
