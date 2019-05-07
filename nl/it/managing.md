---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Gestione delle istanze del servizio e dei Voice Agent
{: #managing}

Puoi utilizzare il dashboard _Manage_ per modificare le configurazioni delle tue istanze del servizio e creare, modificare, clonare, configurare o rimuovere singoli Voice Agent. Puoi avere più Voice Agent nella tua istanza del servizio e ogni Voice Agent può avere fino a 1000 numeri univoci e descrizioni. Tuttavia, ogni Voice Agent deve avere un nome univoco e almeno un numero di telefono.

* **NOTA**: una singola istanza del servizio {{site.data.keyword.iva_full}} può avere fino a 150 Voice Agent.
{: shortdesc}

## Passa al tuo dashboard del servizio Voice Agent
{: #navigate_manage}

Puoi trovare il dashboard _Manage_ dal tuo dashboard del servizio {{site.data.keyword.iva_short}}.

1. Vai al tuo [elenco risorse dell'account {{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/resources).

1. Dall'elenco **Services**, seleziona la tua istanza del servizio **Voice Agent** per aprire il dashboard del servizio nella scheda _Manage_.

## Riepilogo del Voice Agent
{: #agent_summary}

Se già hai un Voice Agent esistente, puoi visualizzare un riepilogo di tutti i numeri, di tutte le descrizioni e di tutte le impostazioni di configurazione per l'agent. Per visualizzare il riepilogo, fai clic sul pulsante freccia a discesa a sinistra del nome (**Name**) del Voice Agent. Il riepilogo verrà quindi espanso.

Mentre il Voice Agent può contenere più numeri, nel riepilogo dell'agent solo il numero primario (**Primary Number**) è selezionato per essere visualizzato. Per impostazione predefinita, è il primo numero aggiunto al Voice Agent ed è solo per la visualizzazione, non ha alcuno scopo funzionale. Se desideri visualizzare un numero diverso dal Voice Agent, vedi la sezione relativa alla [gestione di più numeri](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

Puoi visualizzare tutti i numeri nel Voice Agent dal riepilogo dell'agent. Dopo che il riepilogo della configurazione è stato espanso, fai clic sul pulsante **View Numbers**; verrà visualizzato un elenco di tutti i numeri in una nuova finestra di dialogo **Manage**. Vedi la pagina relativa alla [gestione di più numeri](/docs/services/voice-agent?topic=voice-agent-multi_num) per ulteriori informazioni sulla gestione della finestra di dialogo **Manage**.

## Modifica del numero massimo di connessioni simultanee per la tua istanza del servizio
{: #edit_service}

In tutti i piani, ricevi 2 connessioni simultanee gratuitamente. Se utilizzi i piani _Standard_ o _Premium_, puoi [modificare il numero massimo di connessioni simultanee](/docs/services/voice-agent?topic=voice-agent-edit_concurrency) dalle impostazioni predefinite dalla scheda _Instances_.

## Creazione di un Voice Agent
{: #create_va}

[Crea un nuovo Voice Agent](/docs/services/voice-agent?topic=voice-agent-config_instance) dalla scheda _Voice agents_ nel dashboard _Manage_.

## Modifica di un Voice Agent
{: #edit_va}

Puoi modificare i Voice Agent esistenti modificandoli nella scheda _Voice agents_ nel dashboard _Manage_. Per modificare un Voice Agent, fai clic su **Edit Agent** dall'elenco di opzioni del Voice Agent. Modifica la configurazione e salva le modifiche.

## Clonazione di un Voice Agent
{: #clone_va}

Quando cloni un Voice Agent, tutte le configurazioni dei servizi Watson vengono copiate in un nuovo agent. Per clonare un Voice Agent, fai clic su **Clone Agent** dall'elenco di opzioni del Voice Agent. Fornisci al tuo Voice Agent un nome e un numero di telefono univoci, modifica tutte le opzioni di configurazione come necessario e salva le modifiche.

## Eliminazione di un Voice Agent
{: #delete_va}

Potresti voler eliminare un Voice Agent per liberare il numero di telefono. Puoi avere solo un Voice Agent per ogni numero di telefono. Per utilizzare un numero di telefono per un Voice Agent differente, devi prima eliminare ogni Voice Agent che sta utilizzando il numero di telefono.

Per eliminare un Voice Agent, vai alla scheda _Voice agents_, fai clic su **Delete Agent** dall'elenco di opzioni del Voice Agent e salva le modifiche. Il Voice Agent viene rimosso dall'elenco di Voice Agent.

## Ricerca di un Voice Agent in base al numero o alla descrizione
{: #search}

Puoi cercare i Voice Agent in base ai numeri o alle descrizioni salvati nell'agent.

Nella barra _Search_, puoi immettere un numero o una descrizione. Man mano che digiti, i risultati della ricerca vengono aggiornati automaticamente.  

## Configurazione di un Voice Agent
{: #configure_va}

Quando crei, cloni o modifichi un Voice Agent, puoi apportare modifiche alle impostazioni di configurazione delle connessioni e del Voice Agent correlati ai servizi.

* **[Configurazione di più numeri di telefono](/docs/services/voice-agent?topic=voice-agent-multi_num):** puoi configurare il tuo Voice Agent per includere più numeri di telefono.
* **[Configurazione di più ubicazioni del servizio](/docs/services/voice-agent?topic=voice-agent-disaster-recovery):** includi più ubicazioni del servizio per i tuoi servizi collegati per supportare la ridondanza del servizio.
* **[Connessione ai servizi di discorso e testo di terze parti](/docs/services/voice-agent?topic=voice-agent-third-party):** invece di utilizzare {{site.data.keyword.texttospeechshort}} o {{site.data.keyword.speechtotextshort}}, puoi collegare il tuo Voice Agent a API di terze parti, come Google Cloud Speech-to-Text.
* **[Utilizzo dei servizi in altri spazi di lavoro {{site.data.keyword.Bluemix_notm}}](/docs/services/voice-agent?topic=voice-agent-other_service):** puoi configurare il tuo Voice Agent in modo da utilizzare le istanze del servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.speechtotextshort}} che appartengono a spazi di lavoro in altri account {{site.data.keyword.Bluemix_short}}.
* **[Configurazione di Watson Assistant con un motore di orchestrazione del servizio](/docs/services/voice-agent?topic=voice-agent-conversation_va):** puoi connetterti a una competenza {{site.data.keyword.conversationshort}} tramite un motore di orchestrazione del servizio (SOE). Un SOE intercetta i messaggi in entrata e uscita dal servizio in modo che puoi modificarli utilizzando le API di terze parti.
* **[Abilitazione dell'inoltro dell'evento per i Voice Agent](/docs/services/voice-agent?topic=voice-agent-event_forwarding):** potresti voler raccogliere ed analizzare i dati della chiamata da {{site.data.keyword.iva_short}} per migliorare quanto naturale la conversazione sembri al chiamante. Ogni Voice Agent che crei può inoltrare i report dell'evento a un {{site.data.keyword.cloudant_short_notm}} specificato che gestisci.

## Configurazione delle opzioni del Voice Agent avanzate
{: #config-advanced}

Quando crei o cloni un Voice Agent, puoi far clic su **Show advanced** per visualizzare le seguenti opzioni di configurazione avanzate.

* **Conversation read timeout (optional)**: questa opzione imposta il tempo, in secondi, per cui il Voice Agent attende una risposta da Watson Assistant. Se il tempo viene superato, il Voice Agent riprova a contattare Watson Assistant. Se il servizio non può ancora essere raggiunto, la chiamata non riesce. L'impostazione predefinita è 5 secondi.
* **Messaggio di risposta di errore {{site.data.keyword.conversationshort}} (facoltativo)**: il messaggio di risposta predefinito inviato al destinatario se la chiamata non può collegarsi a {{site.data.keyword.conversationshort}}. Puoi immettere fino a 1024 caratteri.
* **Messaggio di risposta di errore di trasferimento (facoltativo)**: il messaggio di risposta predefinito trasmesso al destinatario se il trasferimento della chiamata ha esito negativo. Puoi immettere fino a 1024 caratteri.
* **Custom SIP INVITE Header (optional)**: specifica l'intestazione SIP personalizza da estrarre dalle richieste SIP INVITE in entrata. Puoi immettere fino a 1024 caratteri.
* **Invio della risposta sonora provvisoria da {{site.data.keyword.iva_short}}**: invia una risposta `180 ringing` mentre {{site.data.keyword.iva_short}} elabora una chiamata in entrata. Abilitato per impostazione predefinita.
* **Messa in attesa del chiamante durante il trasferimento**: mette il chiamante in attesa durante il trasferimento. Abilitato per impostazione predefinita.
* **Scollegamento della chiamata a un errore di trasferimento**: determina se scollegare o meno la chiamata se un trasferimento di chiamata ha esito negativo.  Abilitato per impostazione predefinita. Se l'impostazione è disabilitata e un trasferimento di chiamata ha esito negativo, {{site.data.keyword.iva_short}} avvia un turno di conversazione. Quindi, {{site.data.keyword.conversationshort}} può scollegare la chiamata o trasferirla a una destinazione diversa come configurato nel dialogo.
* **Invia una notifica a {{site.data.keyword.conversationshort}} per gli eventi di rete**: quando abilitato e viene rilevato un errore di rete, {{site.data.keyword.iva_short}} avvia un turno al servizio {{site.data.keyword.conversationshort}} con il testo "vgwNetworkWarningMessage". La variabile di stato `vgwNetworkWarnings` contiene un elenco di eventi di rete che si verificano durante il turno corrente. Se disabilitato, un elenco di eventi di rete che si verificano durante il turno corrente viene inviato nell'evento di turno successivo nella variabile di stato `vgwNetworkWarning`. Abilitato per impostazione predefinita.
