---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Utilizzo delle istanze del servizio in altri spazi di lavoro {{site.data.keyword.Bluemix_notm}}
{: #other_service}

Puoi configurare il tuo agent vocale ad utilizzare le istanze del servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.speechtotextshort}} che appartengono a spazi di lavoro in altri account {{site.data.keyword.Bluemix_short}}.
{: shortdesc}

Per collegare il tuo agent vocale ad altre istanze del servizio, puoi utilizzare le credenziali nome utente e password o una chiave API per le tue istanze del servizio.

1. Nella scheda _Voice agents_ nel dashboard _Manage_, seleziona **Create a new voice agent** o un agent vocale che vuoi modificare.

1. In {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.speechtotextshort}}, seleziona **Other service instance** per il tuo **Service type** e quindi seleziona **Region**.

1. Scegli **User name and password** o **API key** e immetti le tue credenziali del servizio.
  Per trovare questi valori, passa all'istanza del servizio che vuoi configurare e seleziona **Service credentials** e **View credentials**.

  * **Nome utente e password**: nei campi **URL**, **User name** e **Password**, configura le credenziali delle tue istanze del servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.texttospeechshort}}.
  * **Chiave API**: nei campi **URL** e **API key**, configura le credenziali delle tue istanze del servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.texttospeechshort}}.

  Le credenziali non sono i tuoi nome utente e password {{site.data.keyword.Bluemix_notm}}, ma le credenziali non codificate dell'istanza del servizio specifica.
  {:tip}

1. Immetti le tue informazioni sull'istanza del servizio

  * **{{site.data.keyword.conversationshort}}:** nel campo **Workspace ID**, immetti l'ID dello spazio di lavoro che vuoi utilizzare con il tuo agent vocale. Per trovare l'ID dello spazio di lavoro, avvia lo strumento e nello spazio di lavoro che vuoi integrare, fai clic sull'icona Actions (**&vellip;**) e seleziona **View details**.
  * **{{site.data.keyword.speechtotextshort}}:** per **Select model type**, scegli **Narrowband**, **Broadband** o **Both narrowband and broadband**, seleziona quindi il modello (**Model**) linguistico.
  * **{{site.data.keyword.texttospeechshort}}:** nel campo **Voice**, seleziona la lingua e la voce che il tuo servizio utilizza. Devi specificare una voce del tuo servizio.

**Ricorda:** perché il tuo agent vocale funzioni, devi configurare {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} e {{site.data.keyword.texttospeechshort}} per la stessa lingua. Vedi [Lingue supportate](about.html#supported-languages).
