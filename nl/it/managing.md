---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Gestione degli agent vocali
{: #managing}

Puoi creare, modificare, clonare, configurare e rimuovere gli agent vocali nel dashboard _Manage_. Puoi avere più agent vocali, ma ognuno di essi deve avere un numero di telefono e un nome univoci.
{: shortdesc}

<!-- Title should be task oriented and descriptive-->

## Creazione di un agent vocale
{: #config_instance}

Quando crei un agent vocale, {{site.data.keyword.iva_short}} automaticamente ricerca tutte le istanze del servizio Watson disponibili che puoi utilizzare. Se un servizio non è disponibile, puoi selezionare di crearli insieme all'agent vocale o collegarli in uno spazio dell'account {{site.data.keyword.Bluemix_short}} differente.

1. Fai clic su **Create a Voice Agent**.

1. Per **Name**, specifica un nome univoco per il tuo agent vocale. Ad esempio, `Customer Support - North America`.

1. Per **Phone number**, aggiungi il numero dal tuo trunk SIP, includendo i codice area e paese. Ad esempio, per un numero 800 degli Stati Uniti, specifica il numero di telefono come `18883334444`. Il numero di telefono può avere spazi e caratteri `+ ( ) -`.

1. Facoltativamente descrivi il tuo agent vocale.

1. Configura le connessioni alle tue istanze del servizio Watson. Puoi collegarti a più istanze del servizio Watson configurando le connessioni per **Location 1** e **Location 2**. Disporre di connessioni a più istanze del servizio consente al tuo agent vocale di passare a un'istanza del servizio alternativa se si verifica un'interruzione. Consulta [Aggiunta di più ubicazioni del servizio Watson](#add_location).

**Importante**: gli account _Trial_ e _Lite_ possono collegarsi solo all'ubicazione in cui è stata creata la tua istanza del servizio {{site.data.keyword.iva_short}}. La tua seconda ubicazione non è un secondo agent vocale. Agisce solo da backup per il ripristino di emergenza.

1. In **{{site.data.keyword.conversationshort}}**, configura la connessione alla tua istanza del servizio {{site.data.keyword.conversationshort}} facendo clic su **Enable location 1** o **Enable location 2**. Puoi utilizzare le istanze {{site.data.keyword.conversationshort}} o {{site.data.keyword.virtualagentfull}} negli account {{site.data.keyword.Bluemix_notm}} che gestisci tu o qualcun altro. Puoi anche collegare una qualsiasi di queste opzioni tramite un motore di orchestrazione del servizio.

    * Se stai creando un agent vocale nella regione Stati Uniti Sud e non hai un'istanza del servizio {{site.data.keyword.conversationshort}}, puoi crearne una nel menu **Service instance**.
    * In alternativa, puoi collegare altre risorse di un dialogo {{site.data.keyword.conversationshort}} modificando il [**Service type**](#other_service).
    * Se vuoi configurare più ubicazioni del servizio, fai clic sull'altra opzione di ubicazione e seleziona **Enable location** per configurare la connessione alla tua altra istanza {{site.data.keyword.conversationshort}}. Consulta [Aggiunta di più ubicazioni del servizio Watson](#add_location).

1. In **{{site.data.keyword.speechtotextshort}}**, controlla la configurazione predefinita della tua istanza del servizio {{site.data.keyword.speechtotextshort}} facendo clic su **Enable location 1** o **Enable location 2**. Se stai creando un agent vocale nella regione Stati Uniti Sud e non hai un'istanza del servizio {{site.data.keyword.speechtotextshort}}, puoi crearne una dal menu **Service instance**. Oppure, puoi collegare il tuo agent vocale a un'istanza {{site.data.keyword.speechtotextshort}} in uno spazio dell'account {{site.data.keyword.Bluemix_notm}} differente modificando il [**Service type**](#other_service). {{site.data.keyword.iva_short}} supporta solo i modelli a banda stretta.

    Se vuoi configurare più ubicazioni del servizio, fai clic sull'altra opzione di ubicazione e seleziona **Enable location** per configurare la connessione alla tua altra istanza {{site.data.keyword.speechtotextshort}}. Consulta [Aggiunta di più ubicazioni del servizio Watson](#add_location).

1. In **{{site.data.keyword.texttospeechshort}}**, controlla la configurazione predefinita della tua istanza del servizio {{site.data.keyword.texttospeechshort}} facendo clic su **Enable location 1** o **Enable location 2**. Se stai creando un agent vocale nella regione Stati Uniti Sud e non hai un'istanza del servizio {{site.data.keyword.texttospeechshort}}, puoi crearne una dal menu **Service instance**. Oppure, puoi collegare il tuo agent vocale a un'istanza {{site.data.keyword.texttospeechshort}} in uno spazio dell'account {{site.data.keyword.Bluemix_notm}} differente modificando il [**Service type**](#other_service).

    Se vuoi configurare più ubicazioni del servizio, fai clic sull'altra opzione di ubicazione e seleziona **Enable location** per configurare la connessione alla tua altra istanza {{site.data.keyword.texttospeechshort}}. Consulta [Aggiunta di più ubicazioni del servizio Watson](#add_location).

1. Puoi inoltre scegliere di abilitare l'inoltro dell'evento per raccogliere le informazioni sulle chiamate gestite dai tuoi agent vocali in {{site.data.keyword.cloudantfull}}. Vedi [Abilitazione dell'inoltro dell'evento per gli agent vocali](event-forwarding.html). Per ulteriori opzioni di configurazione, consulta [Configurazione di un agent vocale](#configure_va).

1. Fai clic su **Create voice agent** per creare il tuo agent vocale e tutti i nuovi servizi.

Dopo aver creato l'agent vocale, verificalo chiamandone il numero di telefono. Puoi visualizzare i dettagli sulla tua chiamata telefonica nel dashboard _Usage_.  

## Modifica del numero massimo di connessioni simultanee 
{: #edit_concurrency}

Se utilizzi il piano _Standard_, puoi modificare il numero massimo di connessioni simultanee dalle impostazioni predefinite. In tutti i piani, ricevi 2 connessioni simultanee gratuitamente. Per ulteriori informazioni, vedi i [Piani dei prezzi](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

Nel dashboard _Manage_, puoi visualizzare il numero massimo di connessioni simultanee consentite nel tuo piano elencate in **Maximum concurrent connections**. Puoi inoltre visualizzare il numero massimo di connessioni simultanee utilizzate dai tuoi agent vocali durante il mese corrente in **Maximum concurrent connections used**.

Se vuoi modificare il numero massimo di connessioni simultanee nel tuo piano, fai clic sull'icona **Edit**. Nella finestra _Edit maximum concurrent connections_, scegli il numero massimo di connessioni simultanee e fai clic su **Save**. Il numero minimo di connessioni simultanee che puoi impostare tramite la modalità self-service è 10 e il massimo è 50. Se hai bisogno di più di 50 connessioni simultanee per il tuo agent vocale, consulta [Richiesta di configurazione di rete assistita](connect-SIP.html#request-setup).

### Informazioni sul prezzo della connessione simultanea
{: #concurrent-charge}

  * I piani _Lite_, _Trial_ e _Standard_ includono 2 connessioni simultanee gratuitamente.
  * I piani _Premium_ sono personalizzati per istanza.
  * In un account _Standard_ hai una capacità minima di 10 connessioni simultanee.
  * L'utilizzo della connessione simultanea viene addebitato mensilmente. Se utilizzi più di 2 connessioni simultanee al giorno, sei addebitato con una tariffa giornaliera.
  * Se hai un piano _Standard_ o _Premium_, puoi acquistare una capacità di connessione simultanea maggiore.
  * Sei addebitato con una tariffa giornaliera per la capacità di connessione simultanea massima che utilizzi in un giorno. Ad esempio, poiché il tuo piano supporta 2 connessioni simultanee gratuite e imposti un limite massimo di 12 connessioni. Se ne utilizzi solo 5 in un giorno, vieni addebitato per 3.

Per ulteriori informazioni sui piani, le tariffe e le funzioni, consulta [Piani dei prezzi](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

## Modifica di un agent vocale
{: #edit_va}

Puoi modificare gli agent vocali esistenti modificandoli. Per modificare un agent vocale, fai clic su **Edit Agent** dall'elenco di opzioni dell'agent vocale. Modifica la configurazione e salva le modifiche.

## Clonazione di un agent vocale
{: #clone_va}

Quando cloni un agent vocale, tutte le configurazioni dei servizi Watson vengono copiate in un nuovo agent. Per clonare un agent vocale, fai clic su **Clone Agent** dall'elenco di opzioni dell'agent vocale. Fornisci al tuo agent vocale un nome e un numero di telefono univoci, modifica tutte le opzioni di configurazione come necessario e salva le modifiche.

## Eliminazione di un agent vocale
{: #delete_va}

Potresti voler eliminare un agent vocale per liberare il numero di telefono. Puoi avere solo un agent vocale per numero di telefono. Per utilizzare un numero di telefono per un agent vocale differente, devi prima eliminare ogni agent vocale che sta utilizzando il numero di telefono.

Per eliminare un agent vocale, fai clic su **Delete Agent** dall'elenco di opzioni dell'agent vocale e salva le modifiche. L'agent vocale viene rimosso dall'elenco di agent vocali.

## Configurazione di un agent vocale
{: #configure_va}

### Configurazione delle opzioni avanzate
{: #config-advanced}

Quando crei o cloni un agent vocale, puoi far clic su **Show advanced** per visualizzare le seguenti opzioni di configurazione avanzate.

* **Messaggio di risposta di errore {{site.data.keyword.conversationshort}} (facoltativo)**: il messaggio di risposta predefinito inviato al destinatario se la chiamata non può collegarsi a {{site.data.keyword.conversationshort}}.
* **Messaggio di risposta di errore di trasferimento (facoltativo)**: il messaggio di risposta predefinito trasmesso al destinatario se il trasferimento della chiamata ha esito negativo.
* **Invio della risposta sonora provvisoria da {{site.data.keyword.iva_short}}**: invia una risposta `180 ringing` mentre {{site.data.keyword.iva_short}} elabora una chiamata in entrata. Abilitato per impostazione predefinita.
* **Messa in attesa del chiamante durante il trasferimento**: mette il chiamante in attesa durante il trasferimento. Abilitato per impostazione predefinita.
* **Scollegamento della chiamata a un errore di trasferimento**: determina se scollegare o meno la chiamata se un trasferimento di chiamata ha esito negativo.  Abilitato per impostazione predefinita. Se l'impostazione è disabilitata e un trasferimento di chiamata ha esito negativo, {{site.data.keyword.iva_short}} avvia un turno di conversazione. Quindi, {{site.data.keyword.conversationshort}} può scollegare la chiamata o trasferirla a una destinazione diversa come configurato nel dialogo.
* **Invia una notifica a {{site.data.keyword.conversationshort}} per gli eventi di rete**: quando abilitato e viene rilevato un errore di rete, {{site.data.keyword.iva_short}} avvia un turno al servizio {{site.data.keyword.conversationshort}} con il testo "vgwNetworkWarningMessage". La variabile di stato `vgwNetworkWarnings` contiene un elenco di eventi di rete che si verificano durante il turno corrente. Se disabilitato, un elenco di eventi di rete che si verificano durante il turno corrente viene inviato nell'evento di turno successivo nella variabile di stato `vgwNetworkWarning`. Abilitato per impostazione predefinita.

### Aggiunta di più ubicazioni del servizio Watson
{: #add_location}

Se hai un account _Standard_ o _Premium_, puoi collegare il tuo agent vocale a più servizi Watson in ubicazioni diverse per la ridondanza del servizio. Gli account _Trial_ e _Lite_ possono collegarsi solo all'ubicazione in cui è stata creata la tua istanza del servizio {{site.data.keyword.iva_short}}. La tua seconda ubicazione non è un secondo agent vocale. Agisce solo da backup per il ripristino di emergenza.

Il tuo agent vocale utilizza le istanze del servizio Watson in ordine di distanza geografica. Ad esempio, puoi creare un agent vocale nella regione Stati Uniti Est e i tuoi servizi {{site.data.keyword.conversationshort}} in Stati Uniti Sud e Sydney, Australia. Il tuo agent vocale utilizza la regione Stati Uniti Sud {{site.data.keyword.conversationshort}} perché è geograficamente più vicina a Stati Uniti Est rispetto a Sydney. Collegando i servizi Watson in più regioni, se uno di essi è offline in un'ubicazione, il tuo agent vocale può utilizzare il servizio di ridondanza.

Puoi aggiungere un'ubicazione del servizio Watson alla tua configurazione dell'agent vocale in qualsiasi momento. Per informazioni sul collegamento a più istanze di ubicazione del servizio quando crei il tuo agent vocale, consulta [Creazione di un agent vocale](#creating).

Per aggiungere un'ubicazione del servizio Watson a un agent vocale esistente, fai clic su **Edit agent** per l'agent vocale che vuoi modificare. Scegli **Location 1** o **Location 2** per l'istanza {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} o {{site.data.keyword.speechtotextshort}} che vuoi collegare e aggiungi le tue informazioni di configurazione. Puoi utilizzare l'istanza del servizio Watson nel tuo spazio di lavoro o in altri spazi di lavoro. Consulta [Utilizzo delle istanze del servizio in altri spazi di lavoro {{site.data.keyword.Bluemix_notm}}](#other_services).

**Ricordati**: per la ridondanza del servizio, devi utilizzare le istanze del servizio Watson in regioni del servizio differenti per ubicazioni diverse.

Puoi abilitare o disabilitare un percorso utilizzando la casella **Enable location**. Per impostazione predefinita **Location 1** è abilitata e **Location 2** è disabilitata. Deve essere abilitata almeno un'ubicazione per ogni servizio Watson.

### Utilizzo delle istanze del servizio in altri spazi di lavoro {{site.data.keyword.Bluemix_notm}}
{: #other_service}

Puoi configurare il tuo agent vocale ad utilizzare le istanze del servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.speechtotextshort}} che appartengono a spazi di lavoro in altri account {{site.data.keyword.Bluemix_short}}. Per collegare il tuo agent vocale ad altre istanze del servizio, puoi utilizzare le credenziali nome utente e password o una chiave API per le tue istanze del servizio.

1. Seleziona i tuoi **Service type** e **Region**.

1. Scegli **User name and password** o **API key** e immetti le tue credenziali del servizio.
  Per trovare questi valori, passa all'istanza del servizio che vuoi configurare e seleziona **Service credentials** e **View credentials**.

  * **Nome utente e password**: nei campi **URL**, **User name** e **Password**, configura le credenziali delle tue istanze del servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.texttospeechshort}}.
  * **Chiave API**: nei campi **URL** e **API key**, configura le credenziali delle tue istanze del servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.texttospeechshort}}.

  Le credenziali non sono i tuoi nome utente e password {{site.data.keyword.Bluemix_notm}}, ma le credenziali non codificate dell'istanza del servizio specifica.
  {:tip}

1. Immetti le tue informazioni sull'istanza del servizio

  * **{{site.data.keyword.conversationshort}}:** nel campo **Workspace ID**, immetti l'ID dello spazio di lavoro che vuoi utilizzare con il tuo agent vocale. Per trovare l'ID dello spazio di lavoro, avvia lo strumento e nello spazio di lavoro che vuoi integrare, fai clic sull'icona Actions (**&vellip;**) e seleziona **View details**.

  * **{{site.data.keyword.speechtotextshort}}:** nel campo **Model**, seleziona la lingua delle funzionalità vocali e il formato del tuo servizio. {{site.data.keyword.iva_short}} supporta solo i modelli a banda stretta.

  * **{{site.data.keyword.texttospeechshort}}:** nel campo **Voice**, seleziona la lingua e la voce che il tuo servizio utilizza. Devi specificare una voce del tuo servizio.

**Ricorda:** perché il tuo agent vocale funzioni, devi configurare {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} e {{site.data.keyword.texttospeechshort}} per la stessa lingua. Vedi [Lingue supportate](about.html#supported-languages).

### Configurazione di {{site.data.keyword.conversationshort}} del tuo agent vocale
{: #conversation_va}

In alternativa alla configurazione di un'istanza del servizio {{site.data.keyword.conversationshort}}, puoi collegarti a un motore di orchestrazione del servizio (SOE) o a Watson {{site.data.keyword.virtualagentshort}}.

* **Motore di orchestrazione del servizio**: collegati a uno spazio di lavoro {{site.data.keyword.conversationshort}} o {{site.data.keyword.virtualagentshort}} tramite un [motore di orchestrazione del servizio (SOE)](about.html#arch-soe). Un SOE intercetta i messaggi in entrata e uscita dal servizio in modo che puoi modificarli utilizzando le API di terze parti.

  Nel campo **URL**, immetti l'URL completo del tuo spazio di lavoro SOE, come ad esempio `https://iva-soesample.myorg.net/SOE/myWorkspace`. Se il tuo SOE richiede l'autenticazione (consigliato), immetti il nome utente e la password nei rispettivi campi.

* **Watson {{site.data.keyword.virtualagentshort}}**: collegati a una chatbot {{site.data.keyword.virtualagentshort}} invece che a uno spazio di lavoro {{site.data.keyword.conversationshort}}. [{{site.data.keyword.virtualagentshort}}](../virtual-agent/getting-started.html#getting-started) viene creato nel servizio {{site.data.keyword.conversationshort}}, ma fornisce funzionalità pre-preparate in modo che puoi iniziare senza avere esperienza nel machine learning.

  Nel campo **URL**, immetti la credenziale URL di {{site.data.keyword.virtualagentshort}}, come ad esempio `https://api.ibm.com/virtualagent/run/api`. Per i campi **Client ID** e **Client secret**, immetti le chiavi di autenticazione, che si associano ai campi di intestazione `X-IBM-Client-Id` e `X-IBM-Client-Secret` delle chiamate API. Nel campo **Bot ID**, immetti l'ID del bot per utilizzare questo agent vocale. Per ulteriori informazioni su come trovare questi valori, vedi [Publishing the agent](../virtual-agent/publish.html) nella documentazione {{site.data.keyword.virtualagentshort}}.
