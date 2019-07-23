---

copyright:
  years: 2019
lastupdated: "2019-06-24"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Creazione di un Voice Agent
{: #config_instance}

Dopo aver creato il tuo servizio {{site.data.keyword.iva_full}}, puoi creare singoli Voice Agent dal dashboard _Manage_.
{: shortdesc}

Quando crei un Voice Agent, {{site.data.keyword.iva_short}} automaticamente ricerca tutte le istanze del servizio Watson disponibili che puoi utilizzare. Se non è disponibile alcuna istanza del servizio, puoi crearne una insieme al Voice Agent o eseguire la connessione ai servizi da un account {{site.data.keyword.Bluemix_short}} diverso. Puoi anche scegliere di collegare il tuo Voice Agent a un'istanza del motore di orchestrazione del servizio, di Google Speech to Text o di Google Text to Speech.

1. Vai alla scheda _Voice agents_ nel dashboard _Manage_ e fai clic su **Create a Voice Agent**.

1. Per **Agent Type**, seleziona _Voice_.

1. Per **Name**, specifica un nome univoco per il tuo Voice Agent. Ad esempio, `Customer Support - North America`. Il nome può includere fino a 64 caratteri.

1. Per **Phone number**, aggiungi il numero dal tuo trunk SIP, inclusi il prefisso internazionale e quello nazionale. Ad esempio, per un numero 800 degli Stati Uniti, specifica il numero di telefono come `18883334444`. Il numero di telefono può avere un massimo di 30 caratteri, inclusi spazi e caratteri + ( ) -.

1. Per impostazione predefinita, questo numero di telefono verrà impostato come **Primary Number** per il servizio; si tratta semplicemente del primo numero che ti viene presentato quando hai un elenco di numeri ed è solo per scopi di visualizzazione. Per modificare il tuo numero primario, vedi [Impostazione del numero primario](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

1. Facoltativamente, utilizza fino a 256 caratteri per descrivere il tuo Voice Agent.

1. Puoi aggiungere più numeri di telefono a un singolo Voice Agent facendo clic su **Manage** accanto a **Phone Number**. Vedi la sezione relativa alla [configurazione di più numeri di telefono in un'istanza Voice Agent](/docs/services/voice-agent?topic=voice-agent-multi_num) per informazioni su come configurare e associare più numeri. Puoi anche modificare i numeri e aggiungere descrizioni per i singoli numeri dalla finestra di dialogo **Manage**.
    
1. In alternativa, per modificare i numeri, fai clic sul campo **Phone Number** in grigio oppure su **Manage**. Per ulteriori informazioni, vedi [Modifica di un numero di telefono e/o di una descrizione per più numeri](/docs/services/voice-agent?topic=voice-agent-multi_num#edit_num).
    
1. Per abilitare il trasferimento di chiamata, immetti l'URI di terminazione per la tua destinazione di trasferimento predefinita (**Default transfer target**). Consulta [Configurazione del trasferimento di chiamata](/docs/services/voice-agent?topic=voice-agent-call-transfer) per informazioni su come configurare un URI di terminazione. Non utilizzare un numero di telefono personale per la tua destinazione di trasferimento. L'URI di terminazione della destinazione di trasferimento predefinita (**Default transfer target**) può includere fino a 256 caratteri.
    
1. Configura le connessioni alle tue istanze del servizio Watson. Puoi collegarti a più istanze del servizio Watson configurando le connessioni per **Location 1** e **Location 2**. Disporre di connessioni a più istanze del servizio consente al tuo Voice Agent di passare a un'istanza del servizio alternativa se si verifica un'interruzione. Consulta [Aggiunta di più ubicazioni del servizio Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).
    
1. In **Conversation**, configura la connessione alla tua istanza del servizio {{site.data.keyword.conversationshort}} facendo clic su **Location 1** o **Location 2** e abilitando l'ubicazione che hai selezionato. Puoi utilizzare le istanze del servizio {{site.data.keyword.conversationshort}} negli account {{site.data.keyword.Bluemix_notm}} che gestisci tu o qualcun altro. Puoi anche collegare una qualsiasi di queste opzioni tramite un motore di orchestrazione del servizio.
    
   * Se stai creando un Voice Agent nella regione Dallas o Washington DC e non hai un'istanza del servizio {{site.data.keyword.conversationshort}}, puoi crearne una nel menu **Service instance**.
   * In alternativa, puoi eseguire la connessione ad altre origini di un dialogo {{site.data.keyword.conversationshort}} o a un SOE, modificando il [**Service type**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service).
   * Se vuoi configurare più ubicazioni del servizio, fai clic sull'opzione **other location** e seleziona **Enable location** per configurare la connessione alla tua altra istanza {{site.data.keyword.conversationshort}}. Per ulteriori informazioni, vedi [Aggiunta di più ubicazioni del servizio Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).
    
1. In **{{site.data.keyword.speechtotextshort}}**, controlla la configurazione predefinita della tua istanza del servizio {{site.data.keyword.speechtotextshort}} selezionando **Location 1** o **Location 2** e abilitando tale ubicazione. Puoi personalizzare la tua configurazione nel seguente modo.
   * Per collegare il tuo Voice Agent a un'istanza esistente come tuo **Service type**, scegli **My speech to text instance**. Successivamente, per **Select model type**, scegli **Narrowband**, **Broadband** o **Both narrowband and broadband**, seleziona quindi il modello (**Model**) linguistico.
   * Se stai creando un Voice Agent nella regione Dallas o Washington DC e non hai un'istanza del servizio {{site.data.keyword.speechtotextshort}}, puoi crearne una dal menu **Service instance**.
   * Per il tuo **Service type**, puoi scegliere [un'istanza {{site.data.keyword.speechtotextshort}} in uno spazio di lavoro {{site.data.keyword.Bluemix_notm}} differente](/docs/services/voice-agent?topic=voice-agent-other_service) o un [servizio speech to text di terze parti](/docs/services/voice-agent?topic=voice-agent-third-party#third-party), come Google Cloud Speech-to-Text.
   * Se vuoi configurare più ubicazioni del servizio, fai clic sull'altra opzione di ubicazione e seleziona **Enable location** per configurare la connessione alla tua altra istanza {{site.data.keyword.speechtotextshort}}. Per ulteriori informazioni, vedi [Aggiunta di più ubicazioni del servizio Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery).
    
1. In **{{site.data.keyword.texttospeechshort}}**, controlla la configurazione predefinita della tua istanza del servizio {{site.data.keyword.texttospeechshort}} facendo clic su **Location 1** o **Location 2** e abilitando tale ubicazione. Puoi personalizzare la tua configurazione nel seguente modo.
   * Se stai creando un Voice Agent nella regione Dallas o Washington DC e non hai un'istanza del servizio {{site.data.keyword.texttospeechshort}}, puoi crearne una dal menu **Service instance**.
   * Per il tuo **Service type**, puoi scegliere un'[istanza {{site.data.keyword.texttospeechshort}} in uno spazio di lavoro {{site.data.keyword.Bluemix_notm}} differente](/docs/services/voice-agent?topic=voice-agent-other_service) o un [servizio text to speech di terze parti](/docs/services/voice-agent?topic=voice-agent-third-party), come Google Cloud Text-to-Speech.
   * Se vuoi configurare più ubicazioni del servizio, fai clic sull'altra opzione di ubicazione e seleziona **Enable location** per configurare la connessione alla tua altra istanza {{site.data.keyword.texttospeechshort}}. Consulta [Aggiunta di più ubicazioni del servizio Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery).
      
1. Puoi inoltre scegliere di abilitare l'inoltro dell'evento per raccogliere le informazioni sulle chiamate gestite dai tuoi Voice Agent in {{site.data.keyword.cloudantfull}}. Vedi [Abilitazione dell'inoltro dell'evento per i Voice Agent](/docs/services/voice-agent?topic=voice-agent-event_forwarding). Per ulteriori opzioni di configurazione, consulta [Configurazione di un Voice Agent](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1. Fai clic su **Create voice agent** per creare il tuo Voice Agent e tutti i nuovi servizi.

Dopo aver creato il Voice Agent, verificalo chiamandone il numero di telefono. Puoi visualizzare i dettagli sulla tua interazione nel dashboard _Usage_. Per ulteriori informazioni, vedi [Visualizzazione dei log e utilizzo](/docs/services/voice-agent?topic=voice-agent-logging).   
