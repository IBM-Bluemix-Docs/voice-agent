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

# Creazione di un Voice Agent abilitato SMS
{: #sms_voice_config_instance}

Dopo aver creato il tuo servizio {{site.data.keyword.iva_full}}, puoi creare singoli Voice Agent con la funzione SMS o Voice Agent con solo le funzionalità SMS, dal dashboard _Manage_. Puoi configurare il tuo {{site.data.keyword.iva_full}} per ricevere le chiamate vocali in entrata e rispondere con messaggi in uscita SMS, a seconda del comando vocale ricevuto dall'utente. Per la configurazione, aggiungi un nodo e un intento al tuo servizio {{site.data.keyword.conversationshort}}.
{: shortdesc}


1. Vai alla scheda _Voice agents_ nel dashboard _Manage_ e fai clic su **Create a Voice Agent**.

1. Per **Agent Type**, seleziona _Voice + SMS_.

1. Segui le istruzioni in [Creazione di un Voice Agent](/docs/services/voice-agent?topic=voice-agent-config_instance).

1. Seleziona la casella **Initiate conversation from inbound messages** per consentire agli utenti di avviare una sessione SMS con il tuo agent SMS.

1. Seleziona **Notify on session timeout** in modo che il tuo agent SMS invii un messaggio SMS all'utente, avvertendolo che l'agent non ha ricevuto una risposta da un po' di tempo ed andrà in timeout. 

   - Vedi [Opzioni avanzate](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) per ulteriori informazioni sulle **Opzioni avanzate** disponibili per il tuo agent SMS, ad esempio un periodo di tempo personalizzato per il timeout della sessione.

1. Segui le istruzioni in [Creazione di un Voice Agent](/docs/services/voice-agent?topic=voice-agent-sms_config_instance) per creare un agent SMS.

1. _**NOTA:**_ perché un agent abbia sia l'integrazione vocale che SMS, ad esempio per ricevere un input vocale e restituire un messaggio in uscita SMS per una risposta, **devi** utilizzare uno dei tuoi numeri **vocali** per l'agent **SMS**.

### Configurazione di Watson Assistant per l'integrazione vocale e SMS
{: #sms_outbound}

1. Nel tuo dashboard {{site.data.keyword.Bluemix_notm}}, seleziona l'istanza {{site.data.keyword.conversationshort}} che il tuo Voice Agent utilizza.

1. Crea un **outbound SMS intent** dal dashboard.

1. Aggiungi un **outbound SMS node** dal dashboard.

1. Nella sezione _If assistant recognizes:_, seleziona l'attributo **outbound SMS intent** che hai precedentemente creato.

1. Aggiungi la risposta al nodo. Copia e incolla il seguente frammento di codice per sostituire il codice nel campo.

    ```json
        {
            "output": {
                "text": {
                "values": [
                    "Okay. I will send you a text message now."
                ],
     "selection_policy": "sequential"
                },
                "vgwActionSequence": [
                {
                    "command": "vgwActSendSMS",
                    "parameters": {
                    "message": "This is a test message from Watson Assistant"
                    }
                },
                {
                    "command": "vgwActPlayText"
                }
                ]
            }
        }
    ```
    {: codeblock}


1. Chiama il tuo agent e attiva il nodo per ricevere un messaggio di testo sul telefono da cui stai chiamando. 

Per ulteriori informazioni sull'utilizzo del servizio {{site.data.keyword.conversationshort}}, vedi [Informazioni su {{site.data.keyword.conversationshort}}](/docs/services/assistant?topic=assistant-index#indext).
