---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Configurazione di {{site.data.keyword.conversationshort}} con un motore di orchestrazione del servizio
{: #conversation_va}

Come alternativa alla configurazione di un'istanza del servizio {{site.data.keyword.conversationshort}}, puoi eseguire il collegamento a un motore di orchestrazione del servizio (SOE).
{: shortdesc}

Puoi eseguire il collegamento a uno spazio di lavoro {{site.data.keyword.conversationshort}} tramite un [motore di orchestrazione del servizio (SOE)](about.html#arch-soe). Un SOE intercetta i messaggi in entrata e uscita dal servizio in modo che puoi modificarli utilizzando le API di terze parti.

## Configurazione di una connessione a un SOE
{: #how-to}

1. Nella scheda _Voice agent_ nella pagina _Manage_ del tuo agent vocale, passa alla sezione di configurazione di {{site.data.keyword.conversationshort}}.

1. Scegli **Service orchestration engine** come tuo **Service type**.

1. Seleziona la regione (**Region**) del tuo **Service type**.

1. Nel campo **URL**, immetti l'URL completo del tuo spazio di lavoro SOE, come ad esempio `https://iva-soesample.myorg.net/SOE/myWorkspace`.

  **Importante**: per la sicurezza dei dati, assicurati di utilizzare un URL sicuro per il tuo spazio di lavoro SOE, utilizzando `https:` invece di `http:` e richiedi l'autenticazione. Consulta [Informazioni sulla sicurezza e sulla privacy dei dati](infosec.html) per ulteriori informazioni sulle considerazioni sulla sicurezza.

1. **Facoltativo** se il tuo SOE richiede l'autenticazione (consigliato), immetti il nome utente e la password nei rispettivi campi.
