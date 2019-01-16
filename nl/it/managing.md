---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Gestione delle istanze del servizio e degli agent vocali
{: #managing}

Puoi utilizzare il dashboard _Manage_ per modificare le configurazioni delle tue istanze del servizio e creare, modificare, clonare, configurare o rimuovere singoli agent vocali. Puoi avere più agent vocali nella tua istanza del servizio, ma ognuno di essi deve avere un numero di telefono e un nome univoci.
{: shortdesc}

## Passa al tuo dashboard del servizio Voice Agent
{: #navigate_manage}

Puoi trovare il dashboard _Manage_ dal tuo dashboard del servizio {{site.data.keyword.iva_short}}.

1. Vai al tuo [elenco risorse dell'account {{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/resources).

1. Dall'elenco **Services**, seleziona la tua istanza del servizio **Voice Agent** per aprire il dashboard del servizio nella scheda _Manage_.

## Modifica del numero massimo di connessioni simultanee per la tua istanza del servizio
{: #edit_service}

In tutti i piani, ricevi 2 connessioni simultanee gratuitamente. Se utilizzi i piani _Standard_ o _Premium_, puoi [modificare il numero massimo di connessioni simultanee](managing_concurrency.html) dalle impostazioni predefinite dalla scheda _Instances_.

## Creazione di un agent vocale
{: #create_va}

[Crea un nuovo agent vocale](managing_create.html) dalla scheda _Voice agents_ nel dashboard _Manage_.

## Modifica di un agent vocale
{: #edit_va}

Puoi modificare gli agent vocali esistenti modificandoli nella scheda _Voice agents_ nel dashboard _Manage_. Per modificare un agent vocale, fai clic su **Edit Agent** dall'elenco di opzioni dell'agent vocale. Modifica la configurazione e salva le modifiche.

## Clonazione di un agent vocale
{: #clone_va}

Quando cloni un agent vocale, tutte le configurazioni dei servizi Watson vengono copiate in un nuovo agent. Per clonare un agent vocale, fai clic su **Clone Agent** dall'elenco di opzioni dell'agent vocale. Fornisci al tuo agent vocale un nome e un numero di telefono univoci, modifica tutte le opzioni di configurazione come necessario e salva le modifiche.

## Eliminazione di un agent vocale
{: #delete_va}

Potresti voler eliminare un agent vocale per liberare il numero di telefono. Puoi avere solo un agent vocale per numero di telefono. Per utilizzare un numero di telefono per un agent vocale differente, devi prima eliminare ogni agent vocale che sta utilizzando il numero di telefono.

Per eliminare un agent vocale, vai alla scheda _Voice agents_, fai clic su **Delete Agent** dall'elenco di opzioni dell'agent vocale e salva le modifiche. L'agent vocale viene rimosso dall'elenco di agent vocali.

## Configurazione di un agent vocale
{: #configure_va}

Quando crei, cloni o modifichi un agent vocale, puoi apportare modifiche alle impostazioni di configurazione delle connessioni e dell'agent vocale correlati ai servizi.

* **[Configurazione di più ubicazioni del servizio](managing_disaster_recovery.html):** includi più ubicazioni del servizio per i tuoi servizi collegati per supportare la ridondanza del servizio.
* **[Connessione ai servizi di discorso e testo di terze parti](managing_third_party.html):** invece di utilizzare {{site.data.keyword.texttospeechshort}} o {{site.data.keyword.speechtotextshort}}, puoi collegare il tuo agent vocale a API di terze parti, come Google Cloud Speech-to-Text.
* **[Utilizzo dei servizi in altri spazi di lavoro {{site.data.keyword.Bluemix_notm}}](managing_other.html):** puoi configurare il tuo agent vocale in modo da utilizzare le istanze del servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} o {{site.data.keyword.speechtotextshort}} che appartengono a spazi di lavoro in altri account {{site.data.keyword.Bluemix_short}}.
* **[Configurazione di Watson Assistant con un motore di orchestrazione del servizio](managing_SOE.html):** puoi collegare uno spazio di lavoro {{site.data.keyword.conversationshort}} tramite un motore di orchestrazione del servizio (SOE). Un SOE intercetta i messaggi in entrata e uscita dal servizio in modo che puoi modificarli utilizzando le API di terze parti.
* **[Abilitazione dell'inoltro dell'evento per gli agent vocali](event-forwarding.html):** potresti voler raccogliere ed analizzare i dati della chiamata da {{site.data.keyword.iva_short}} per migliorare quanto naturale la conversazione sembri al chiamante. Ogni agent vocale che crei può inoltrare i report dell'evento a un {{site.data.keyword.cloudant_short_notm}} specificato che gestisci.

## Configurazione delle opzioni dell'agent vocale avanzate
{: #config-advanced}

Quando crei o cloni un agent vocale, puoi far clic su **Show advanced** per visualizzare le seguenti opzioni di configurazione avanzate.

* **Messaggio di risposta di errore {{site.data.keyword.conversationshort}} (facoltativo)**: il messaggio di risposta predefinito inviato al destinatario se la chiamata non può collegarsi a {{site.data.keyword.conversationshort}}.
* **Messaggio di risposta di errore di trasferimento (facoltativo)**: il messaggio di risposta predefinito trasmesso al destinatario se il trasferimento della chiamata ha esito negativo.
* **Intestazione SIP INVITE personalizzata (facoltativo)**: specifica l'intestazione SIP personalizzata da estrarre dalle richieste SIP INVITE in entrata
* **Invio della risposta sonora provvisoria da {{site.data.keyword.iva_short}}**: invia una risposta `180 ringing` mentre {{site.data.keyword.iva_short}} elabora una chiamata in entrata. Abilitato per impostazione predefinita.
* **Messa in attesa del chiamante durante il trasferimento**: mette il chiamante in attesa durante il trasferimento. Abilitato per impostazione predefinita.
* **Scollegamento della chiamata a un errore di trasferimento**: determina se scollegare o meno la chiamata se un trasferimento di chiamata ha esito negativo.  Abilitato per impostazione predefinita. Se l'impostazione è disabilitata e un trasferimento di chiamata ha esito negativo, {{site.data.keyword.iva_short}} avvia un turno di conversazione. Quindi, {{site.data.keyword.conversationshort}} può scollegare la chiamata o trasferirla a una destinazione diversa come configurato nel dialogo.
* **Invia una notifica a {{site.data.keyword.conversationshort}} per gli eventi di rete**: quando abilitato e viene rilevato un errore di rete, {{site.data.keyword.iva_short}} avvia un turno al servizio {{site.data.keyword.conversationshort}} con il testo "vgwNetworkWarningMessage". La variabile di stato `vgwNetworkWarnings` contiene un elenco di eventi di rete che si verificano durante il turno corrente. Se disabilitato, un elenco di eventi di rete che si verificano durante il turno corrente viene inviato nell'evento di turno successivo nella variabile di stato `vgwNetworkWarning`. Abilitato per impostazione predefinita.
