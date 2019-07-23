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


# Creazione di un agent SMS
{: #sms_config_instance}

Dopo aver creato il tuo servizio {{site.data.keyword.iva_full}}, puoi creare singoli agent SMS dal dashboard _Manage_.
{: shortdesc}

1. Vai alla scheda _Voice agents_ nel dashboard _Manage_ e fai clic su **Create a Voice Agent**.

1. Per **Agent Type**, seleziona _SMS_.

1. Per **Name**, specifica un nome univoco per il tuo Voice Agent. Ad esempio, `Customer Support - North America`. Il nome può includere fino a 64 caratteri.

1. Per Phone number, aggiungi il numero dal tuo trunk SIP, inclusi il prefisso internazionale e quello nazionale. Ad esempio, per un numero 800 degli Stati Uniti, specifica il numero di telefono come 18883334444. Il numero di telefono può avere un massimo di 30 caratteri, inclusi spazi e caratteri + ( ) -. SMS supporta solo un numero per utente.

1. In **SMS Provider**, immetti il nome utente, la password e l'URL API del tuo provider SMS. Ad esempio, se utilizzi _Twilio_, il nome utente è il tuo **Account SID**, la password è il tuo **Auth Token** e il tuo provider SMS è `https://api.twilio.com`

1. In **Conversation**, configura la connessione alla tua istanza del servizio {{site.data.keyword.conversationshort}}. Puoi utilizzare le istanze del servizio {{site.data.keyword.conversationshort}} negli account {{site.data.keyword.Bluemix_notm}} che gestisci tu o qualcun altro. Puoi anche collegare una qualsiasi di queste opzioni tramite un motore di orchestrazione del servizio (SOE).

   * Se stai creando un agent SMS nella regione Dallas o Washington DC e non hai un'istanza del servizio {{site.data.keyword.conversationshort}}, puoi crearne una nel menu **Service instance**.
   * In alternativa, puoi eseguire la connessione ad altre origini di un dialogo {{site.data.keyword.conversationshort}} o a un SOE, modificando il [**Service type**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service).
   * Se vuoi configurare più ubicazioni del servizio, fai clic sull'altra opzione di ubicazione e seleziona **Enable location** per configurare la connessione alla tua altra istanza {{site.data.keyword.conversationshort}}. Per ulteriori informazioni, vedi [Aggiunta di più ubicazioni del servizio Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).

1. Seleziona la casella **Initiate conversation from inbound messages** per consentire agli utenti di avviare una sessione SMS con il tuo agent SMS.

1. Seleziona la casella **Notify on session timeout** in modo che il tuo agent SMS invii un messaggio SMS all'utente, avvertendolo che l'agent non ha ricevuto una risposta da un po' di tempo ed andrà in timeout. 

    - Vedi [Opzioni avanzate](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) per ulteriori informazioni sulle **Opzioni avanzate** disponibili per il tuo agent SMS, ad esempio un periodo di tempo personalizzato per il timeout della sessione.
    - Seleziona la casella solo se vuoi ricevere una notifica quando una sessione va in timeout.

1. Puoi inoltre scegliere di abilitare l'inoltro dell'evento per raccogliere le informazioni sulle chiamate gestite dai tuoi Voice Agent in {{site.data.keyword.cloudantfull}}. Per ulteriori informazioni, vedi [Abilitazione dell'inoltro dell'evento per i Voice Agent](/docs/services/voice-agent?topic=voice-agent-event_forwarding). Per ulteriori opzioni di configurazione, consulta [Configurazione di un Voice Agent](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1.  Fai clic su **Create voice agent** per creare il tuo agent SMS e tutti i nuovi servizi.

1. Segui [le istruzioni](/docs/services/voice-agent?topic=voice-agent-connect-sms) per la connessione a un provider SMS.

Dopo aver creato l'agent SMS, verificalo chiamandone il numero di telefono. Puoi visualizzare i dettagli sulla tua interazione nel dashboard _Usage_. Vedi [Visualizzazione dei log e utilizzo](/docs/services/voice-agent?topic=voice-agent-logging).

Per abilitare la messaggistica SMS tra i clienti e un Voice Agent durante una chiamata vocale, il numero SMS deve corrispondere al numero vocale.
{: tip}

Prima di creare un agent SMS o aggiungere la funzionalità SMS al tuo Voice Agent, **devi** aver configurato le credenziali appropriate e generato una chiave API per programmare il tuo numero SMS. Per ulteriori informazioni, vedi [Generazione della chiave API e configurazione delle credenziali](/docs/services/voice-agent?topic=voice-agent-connect-sms#sms_access).

**Devi** anche configurare il tuo trunk SIP per la funzionalità SMS. Vedi le istruzioni del tuo provider, ad esempio, Twilio. Se non hai un numero di telefono Twilio, vedi [Creazione di un trunk SIP Twilio](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup).

Una volta che disponi di un numero Twilio, dovrai configurarlo per la funzionalità SMS. Per ulteriori informazioni, vedi [Configurazione di Twilio per SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

Se hai problemi durante la creazione delle credenziali, contatta il tuo amministratore dell'istanza del servizio per farti concedere l'accesso da *Manager* o *Writer*.
{: tip}

## Opzioni avanzate per gli agent SMS
{: #sms_advanced}

Fai clic su **Show Advanced** dopo il campo **Phone Number**.

1. Imposta un valore **Conversation read timeout** facoltativo. Questo è il tempo in secondi in cui l'SMS Gateway attende una risposta da Watson Assistant. Se il tempo viene superato, l'SMS Gateway riprova a contattare Watson Assistant. Se il servizio non può ancora essere raggiunto, il messaggio SMS/MMS ha esito negativo. L'impostazione predefinita è 30 secondi.

1. Imposta un valore facoltativo per **Session Timeout**. Questo è il tempo in secondi dopo il quale scade la sessione se l'SMS Gateway non riceve una risposta dall'utente.

1. Imposta un **Conversation failure reply message**. Questo è il messaggio di risposta predefinito che viene inviato se Watson Assistant non può essere raggiunto. Per impostazione predefinita, è impostato su `We're sorry, but we can't respond to your message.`.

### Configurazione dell'agent SMS per terminare la sessione.
{: #sms_terminate}

L'agent SMS {{site.data.keyword.iva_full}} termina una sessione in base al valore di timeout della sessione, il quale è configurabile e, per impostazione predefinita, è impostato su 30 secondi. 

Puoi anche aggiungere un nodo al tuo servizio {{site.data.keyword.conversationshort}} per rispondere a un comando di termine della sessione dall'utente. 

1. Nel tuo dashboard {{site.data.keyword.Bluemix_notm}}, seleziona l'istanza {{site.data.keyword.conversationshort}} che il tuo Voice Agent utilizza.

1. Crea un **Terminate SMS intent** dal dashboard. In alternativa, puoi modificare un intento esistente che già utilizzi per il Voice Agent, ad esempio _End the call_.

1. Aggiungi un **Terminate SMS node** dal dashboard.

1. Nella sezione _If assistant recognizes:_, aggiungi l'attributo **Terminate SMS intent** che hai precedentemente creato.

1. Aggiungi la risposta al nodo. Copia e incolla il seguente frammento di codice per sostituire il codice nel campo.

    ```json
        {
            "output": {
                 "text": {
                    "values": [
                        "Thank you for using the service. Goodbye!"
                    ],
                    "selection_policy”: “sequential"
                },
                "smsAction": {
                    "command": "terminateSession"
                }
            }
        }
    ```
    {: codeblock}

Dopo aver creato il Voice Agent, verificalo chiamandone o inserendone il numero di telefono in base al suo tipo. Puoi visualizzare i dettagli sulla tua interazione nel dashboard _Usage_. Vedi [Visualizzazione dei log e utilizzo](/docs/services/voice-agent?topic=voice-agent-logging).
