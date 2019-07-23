---

copyright:
  years: 2019
lastupdated: "2019-06-21"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Connessione ai provider SMS
{: #connect-sms}

Puoi scegliere il provider SMS che utilizzi per l'integrazione con {{site.data.keyword.iva_full}} dal seguente elenco.
{: #shortdesc}

* [Twilio](#twilio-setup)

## Generazione di una chiave API e configurazione delle credenziali
{: #sms_access}

Puoi creare le credenziali solo per i ruoli già attivi nel tuo account. Per gli agent SMS e Voice + SMS, ti deve essere stato assegnato il ruolo *Writer* o *Manager*. Vedi il [passo 9 di Invita gli utenti e assegna l'accesso iniziale](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. Sul *Dashboard* della tua istanza {{site.data.keyword.iva_short}}, fai clic su **New Credential (+)**. 
2. Nella nuova casella di dialogo che viene visualizzata, immetti un nome (**Name**) e nel menu a discesa **Role**, seleziona *Writer* o *Manager*. 
    - **NOTA:** per tutte le funzionalità correlate SMS, **_devi_** selezionare il ruolo *Writer* o *Manager*. 
3. Fai clic su **Add**.
4. Accanto alle tue credenziali appena create, fai clic su **View credentials**. Prendi nota del valore per `APIKEY` nello script JSON da utilizzare in [Configurazione di Twilio per SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

## Configurazione di Twilio per SMS
{: #twilio-setup}

1. Accedi ai tuoi numeri di telefono Twilio, che trovi [qui](https://www.twilio.com/console/phone-numbers/) e seleziona il numero di telefono assegnato al tuo agent _SMS_ o _Voice + SMS_. 

1. Scorri verso il basso fino alla sezione **Messaging**. Nel campo _CONFIGURE WITH_, seleziona **Webhooks, TwiML Bins, Functions, Studio, or Proxy** dal menu a discesa.

1. Nel campo _A MESSAGE COMES IN_, seleziona **Webhook** dal menu a discesa.

1. Nel campo URL vuoto accanto a **Webhook**, segui le istruzioni in base alla regione del tuo agent. 

    - Se l'agent che hai creato si basa sulla regione di Washington, scrivi `https://apikey:YOUR_API_KEY@sms-east.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` nel campo.
    - Se l'agent che hai creato si basa sulla regione di Dallas, scrivi `https://apikey:YOUR_API_KEY@sms-south.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` nel campo.
    - Sostituisci `YOUR_API_KEY` nel precedente URL con l'`APIKEY` dalle credenziali che hai creato precedentemente. Vedi [Generazione di una chiave API e configurazione delle credenziali](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_access). 

1. Fai clic su **Save**. 
