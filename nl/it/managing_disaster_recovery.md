---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configurazione di più ubicazioni del servizio
{: #disaster-recovery}

Puoi collegare il tuo Voice Agent a più servizi in ubicazioni diverse per la ridondanza del servizio. La tua seconda ubicazione non è un secondo Voice Agent, serve solo da backup.
{: shortdesc}

Se utilizzi un piano _Lite_ per la tua istanza del Voice Agent, puoi collegare il tuo trunk SIP a solo un endpoint, in cui viene creata la tua istanza del Voice Agent. Poiché il piano _Lite_ fornisce le connessioni a una sola ubicazione, puoi fornire le ridondanze ai tuoi servizi collegati, ma non al tuo Voice Agent. Se si verifica un'interruzione del servizio nella tua ubicazione del Voice Agent, le chiamate non possono essere indirizzate a un'ubicazione secondaria.
{: tip}

## Aggiunta dei servizi ridondanti
{: #add_redundant}

Puoi aggiungere un'ubicazione del servizio Watson o di terze parti alla tua configurazione del Voice Agent in qualsiasi momento modificando il tuo Voice Agent.

1. Per aggiungere un servizio ridondante a un Voice Agent esistente, passa alla scheda _Voice agents_ nel tuo dashboard _Manage_. Fai clic su **Edit agent** per il Voice Agent che vuoi modificare.

1. Scegli **Location 1** o **Location 2** per il servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} o {{site.data.keyword.speechtotextshort}} che vuoi collegare e aggiungi le tue informazioni di configurazione. Puoi utilizzare le istanze del servizio Watson o dei servizi di terze parti nel tuo spazio di lavoro o in altri spazi di lavoro. Consulta [Utilizzo delle istanze del servizio in altri spazi di lavoro {{site.data.keyword.Bluemix_notm}}](/docs/services/voice-agent?topic=voice-agent-other_service).

**Ricorda**: per la ridondanza del servizio, devi utilizzare le istanze del servizio Watson in regioni del servizio differenti per ubicazioni diverse.

Puoi abilitare o disabilitare un percorso utilizzando la casella **Enable location**. Per impostazione predefinita **Location 1** è abilitata e **Location 2** è disabilitata. Deve essere abilitata almeno un'ubicazione per ogni servizio Watson.

## Aggiunta di più ubicazioni del servizio Watson
{: #add_location}

Il tuo Voice Agent utilizza le istanze del servizio Watson in ordine di distanza geografica. Ad esempio, puoi creare un Voice Agent nella regione Washington DC e i tuoi servizi {{site.data.keyword.conversationshort}} in Dallas e Sydney, Australia. Il tuo Voice Agent utilizza la regione Dallas {{site.data.keyword.conversationshort}} perché è geograficamente più vicina a Washington DC rispetto a Sydney. Collegando i servizi Watson in più regioni, se uno di essi è offline in un'ubicazione, il tuo Voice Agent può utilizzare il servizio di ridondanza.
