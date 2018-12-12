---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configurazione di più ubicazioni del servizio 
{: #disaster-recovery}

Puoi collegare il tuo agent vocale a più servizi in ubicazioni diverse per la ridondanza del servizio. La tua seconda ubicazione non è un secondo agent vocale, serve solo da backup.
{: shortdesc}

Se utilizzi un piano _Lite_ per la tua istanza dell'agent vocale, puoi collegare il tuo trunk SIP a solo un endpoint, in cui viene creata la tua istanza dell'agent vocale. Poiché il piano _Lite_ fornisce le connessioni a una sola ubicazione, puoi fornire le ridondanze ai tuoi servizi collegati, ma non al tuo agent vocale. Se si verifica un'interruzione del servizio nella tua ubicazione dell'agent vocale, le chiamate non possono essere indirizzate a un'ubicazione secondaria.
{: tip}

## Aggiunta dei servizi ridondanti 
{: #add_redundant}

Puoi aggiungere un'ubicazione del servizio Watson o di terze parti alla tua configurazione dell'agent vocale in qualsiasi momento modificando il tuo agent vocale.

1. Per aggiungere un servizio ridondante a un agent vocale esistente, passa alla scheda _Voice agents_ nel tuo dashboard _Manage_. Fai clic su **Edit agent** per l'agent vocale che vuoi modificare.

1. Scegli **Location 1** o **Location 2** per il servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} o {{site.data.keyword.speechtotextshort}} che vuoi collegare e aggiungi le tue informazioni di configurazione. Puoi utilizzare le istanze del servizio Watson o dei servizi di terze parti nel tuo spazio di lavoro o in altri spazi di lavoro. Consulta [Utilizzo delle istanze del servizio in altri spazi di lavoro {{site.data.keyword.Bluemix_notm}}](managing_other.html).

**Ricorda**: per la ridondanza del servizio, devi utilizzare le istanze del servizio Watson in regioni del servizio differenti per ubicazioni diverse.

Puoi abilitare o disabilitare un percorso utilizzando la casella **Enable location**. Per impostazione predefinita **Location 1** è abilitata e **Location 2** è disabilitata. Deve essere abilitata almeno un'ubicazione per ogni servizio Watson.

## Aggiunta di più ubicazioni del servizio Watson
{: #add_location}

Il tuo agent vocale utilizza le istanze del servizio Watson in ordine di distanza geografica. Ad esempio, puoi creare un agent vocale nella regione Washington DC e i tuoi servizi {{site.data.keyword.conversationshort}} in Dallas e Sydney, Australia. Il tuo agent vocale utilizza la regione Dallas {{site.data.keyword.conversationshort}} perché è geograficamente più vicina a Washington DC rispetto a Sydney. Collegando i servizi Watson in più regioni, se uno di essi è offline in un'ubicazione, il tuo agent vocale può utilizzare il servizio di ridondanza.
