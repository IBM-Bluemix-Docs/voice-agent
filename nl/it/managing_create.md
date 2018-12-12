---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Creazione di un agent vocale dal dashboard _Manage_ 
{: #config_instance}

Dopo aver creato il tuo servizio {{site.data.keyword.iva_full}}, puoi creare singoli agenti vocali dal dashboard _Manage_.
{: shortdesc}


## Creazione di un agent vocale
{: #create_instance}

Quando crei un agent vocale, {{site.data.keyword.iva_short}} automaticamente ricerca tutte le istanze del servizio Watson disponibili che puoi utilizzare. Se un servizio non è disponibile, puoi selezionare di crearli insieme all'agent vocale o collegarli in uno spazio dell'account {{site.data.keyword.Bluemix_short}} differente. Puoi anche scegliere di collegare il tuo agent vocale a un'istanza del motore di orchestrazione del servizio, di Google Speech to Text o di Google Text to Speech.

1. Vai alla scheda _Voice agents_ nel dashboard _Manage_ e fai clic su **Create a Voice Agent**.

1. Per **Name**, specifica un nome univoco per il tuo agent vocale. Ad esempio, `Customer Support - North America`.

1. Per **Phone number**, aggiungi il numero dal tuo trunk SIP, includendo i codice area e paese. Ad esempio, per un numero 800 degli Stati Uniti, specifica il numero di telefono come `18883334444`. Il numero di telefono può avere spazi e caratteri `+ ( ) -`.

1. Facoltativamente descrivi il tuo agent vocale.

1. Se vuoi abilitare il trasferimento di chiamata, immetti l'URI di terminazione del **Transfer default target**. Consulta [Configurazione del trasferimento di chiamata](call-transfer.html) per informazioni su come configurare un URI di terminazione. Non utilizzare un numero di telefono personale per la tua destinazione di trasferimento.

1. Configura le connessioni alle tue istanze del servizio Watson. Puoi collegarti a più istanze del servizio Watson configurando le connessioni per **Location 1** e **Location 2**. Disporre di connessioni a più istanze del servizio consente al tuo agent vocale di passare a un'istanza del servizio alternativa se si verifica un'interruzione. Consulta [Aggiunta di più ubicazioni del servizio Watson](managing_disaster_recovery.html#add_location).

1. In **{{site.data.keyword.conversationshort}}**, configura la connessione alla tua istanza del servizio {{site.data.keyword.conversationshort}} facendo clic su **Location 1** o **Location 2** e abilitando l'ubicazione che hai selezionato. Puoi utilizzare le istanze {{site.data.keyword.conversationshort}} negli account {{site.data.keyword.Bluemix_notm}} che gestisci tu o qualcun altro. Puoi anche collegare una qualsiasi di queste opzioni tramite un motore di orchestrazione del servizio.

   * Se stai creando un agent vocale nella regione Dallas o Washington DC e non hai un'istanza del servizio {{site.data.keyword.conversationshort}}, puoi crearne una nel menu **Service instance**.
   * In alternativa, puoi eseguire la connessione ad altre origini di un dialogo {{site.data.keyword.conversationshort}} o a un SOE, modificando il [**Service type**](managing_other.html#other_service).
   * Se vuoi configurare più ubicazioni del servizio, fai clic sull'altra opzione di ubicazione e seleziona **Enable location** per configurare la connessione alla tua altra istanza {{site.data.keyword.conversationshort}}. Consulta [Aggiunta di più ubicazioni del servizio Watson](managing_disaster_recovery.html#add_location).

1. In **{{site.data.keyword.speechtotextshort}}**, controlla la configurazione predefinita della tua istanza del servizio {{site.data.keyword.speechtotextshort}} selezionando **Location 1** o **Location 2** e abilitando tale ubicazione. Puoi personalizzare la tua configurazione nel seguente modo.
   * Per collegare il tuo agent vocale a un'istanza esistente come tuo **Service type**, scegli **My speech to text instance**. Successivamente, per **Select model type**, scegli **Narrowband**, **Broadband** o **Both narrowband and broadband**, seleziona quindi il modello (**Model**) linguistico.
   * Se stai creando un agent vocale nella regione Dallas o Washington DC e non hai un'istanza del servizio {{site.data.keyword.speechtotextshort}}, puoi crearne una dal menu **Service instance**.
   * Per il tuo **Service type**, puoi scegliere [un'istanza {{site.data.keyword.speechtotextshort}} in uno spazio di lavoro {{site.data.keyword.Bluemix_notm}} differente](managing_other.html) o un [servizio speech to text di terze parti](managing_third_party.html), come Google Cloud Speech-to-Text.
   * Se vuoi configurare più ubicazioni del servizio, fai clic sull'altra opzione di ubicazione e seleziona **Enable location** per configurare la connessione alla tua altra istanza {{site.data.keyword.speechtotextshort}}. Consulta [Aggiunta di più ubicazioni del servizio Watson](managing_disaster_recovery.html).

1. In **{{site.data.keyword.texttospeechshort}}**, controlla la configurazione predefinita della tua istanza del servizio {{site.data.keyword.texttospeechshort}} facendo clic su **Location 1** o **Location 2** e abilitando tale ubicazione. Puoi personalizzare la tua configurazione nel seguente modo.
   * Se stai creando un agent vocale nella regione Dallas o Washington DC e non hai un'istanza del servizio {{site.data.keyword.texttospeechshort}}, puoi crearne una dal menu **Service instance**.
   * Per il tuo **Service type**, puoi scegliere un'[istanza {{site.data.keyword.texttospeechshort}} in uno spazio di lavoro {{site.data.keyword.Bluemix_notm}} differente](managing_other.html) o un [servizio text to speech di terze parti](managing_third_party.html), come Google Cloud Text-to-Speech.
   * Se vuoi configurare più ubicazioni del servizio, fai clic sull'altra opzione di ubicazione e seleziona **Enable location** per configurare la connessione alla tua altra istanza {{site.data.keyword.texttospeechshort}}. Consulta [Aggiunta di più ubicazioni del servizio Watson](managing_disaster_recovery.html).

1. Puoi inoltre scegliere di abilitare l'inoltro dell'evento per raccogliere le informazioni sulle chiamate gestite dai tuoi agent vocali in {{site.data.keyword.cloudantfull}}. Vedi [Abilitazione dell'inoltro dell'evento per gli agent vocali](event-forwarding.html). Per ulteriori opzioni di configurazione, consulta [Configurazione di un agent vocale](managing.html#configure_va).

1. Fai clic su **Create voice agent** per creare il tuo agent vocale e tutti i nuovi servizi.

Dopo aver creato l'agent vocale, verificalo chiamandone il numero di telefono. Puoi visualizzare i dettagli sulla tua chiamata telefonica nel dashboard _Usage_.  
