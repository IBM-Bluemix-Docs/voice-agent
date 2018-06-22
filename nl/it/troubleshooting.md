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

# Risoluzione dei problemi e supporto
{: #troubleshooting}

Hai problemi con {{site.data.keyword.iva_full}}? Controlla i suggerimenti sulla risoluzione dei problemi per i problemi comuni e contatta la community per qualsiasi domanda.
{: shortdesc}

## Come risolvere i problemi di {{site.data.keyword.iva_short}}
{: #how-to}

Per risolvere i problemi con i tuoi agent vocali, puoi utilizzare la registrazione, l'utilizzo e l'inoltro dell'evento per trovare i record di errori e malfunzionamenti. Questi record possono aiutarti a diagnosticare e risolvere i problemi con i tuoi agent vocali. Se stai avendo dei problemi con {{site.data.keyword.iva_short}}, prova la seguente procedura.

1. Quando una chiamata ha esito negativo, il turno {{site.data.keyword.conversationshort}} finale potrebbe spiegare l'errore.

1. I log di utilizzo ti mostrano tutti gli errori che potrebbero essersi verificati durante una chiamata particolare. Vedi [Visualizzazione e utilizzo dei log di chiamata](logging.html).

1. Controlla i tuoi log del provider del servizio per la segnalazione degli errori. Ad esempio, Twilio fornisce i log per ogni trunk SIP che ospita.

1. [Abilitando l'inoltro dell'evento per gli agent vocali](event-forwarding.html), puoi configurare il tuo agent vocale per inoltrare i CDR (Call Detail Record) a un database Cloudant e determinare il motivo di un malfunzionamento di una chiamata. Altri eventi, come gli eventi di turno {{site.data.keyword.conversationshort}} possono fornire dettagli su ogni turno di conversazione all'interno di una chiamata.

**Importante:** gli eventi CDR, trascrizione e turno includono informazioni dai tuoi utenti che potrebbero potenzialmente contenere dati Protected Health Information (PHI), personally identifiable information (PII) o PCI Data Security Standard (PCI DSS). Per evitare l'esposizione di informazioni personali, devi assicurarti che la tua istanza {{site.data.keyword.cloudant_short_notm}} protegga in modo appropriato le informazioni confidenziali che i tuoi utenti condividono durante la conversazione.


## Come ottenere supporto
{: #help}

Se necessiti aiuto, unisciti alla nostra community di sviluppatori inserendo le tue domande o i tuoi commenti in una qualsiasi delle seguenti posizioni, che sono tutte monitorate in modo attivo. 

* Pubblica in [dwAnswers forum ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/topics/voice-agent/) con la tag `voice-agent`
* Pubblica in [StackOverflow ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://stackoverflow.com/questions/tagged/voice-agent){: new_window} con la tag `voice-agent`
* Contattaci in Slack nel team [IBM Cloud Technology ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) nel canale `#ibmvoicegateway`

**Ricorda**: prima di pubblicare un log o un record delle chiamate, rimuovi tutte le informazioni personali che i tuoi utenti o chiamanti potrebbero condividere durante la conversazione.

## Suggerimenti sulla risoluzione dei problemi
{: #troubleshooting-tips}

### Perché non ricevo una risposta al telefono quando chiamo il mio agent vocale?

La tua chiamata probabilmente non è stata collegata ai servizi. Questo problema si verifica quando l'istanza del servizio {{site.data.keyword.iva_short}} non è configurata correttamente. Controlla le seguenti impostazioni dell'agent vocale:

* Verifica che il numero di telefono nel dashboard _Manage_ dell'agent vocale sia lo stesso dal tuo provider di trunking SIP, come NetFoundry o Twilio.

   **Nota:** includi il codice area e paese quando specifichi il numero di telefono nel dashboard _Manage_ dell'agent vocale. Ad esempio, `18884253968`.

* Verifica che le credenziali del servizio Watson, gli URL e l'ID dello spazio di lavoro {{site.data.keyword.conversationshort}} siano tutti validi.
* Verifica che il dialogo nel tuo spazio di lavoro {{site.data.keyword.conversationshort}} sia stato creato correttamente.
  * Puoi importare la [conversazione di esempio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) da GitHub per uno spazio di lavoro pre-creato. Consulta il [Passo 3 nell'*Esercitazione introduttiva*](getting-started.html#step3) per i dettagli su come salvare la conversazione di esempio come un file JSON e poi importare il file come uno spazio di lavoro nello strumento {{site.data.keyword.conversationshort}}.
  * Se hai creato il tuo dialogo {{site.data.keyword.conversationshort}}, verifica che contenga un nodo con la condizione `conversation_start` e un nodo con una risposta predefinita. Per istruzioni dettagliate, vedi [Creazione di un dialogo](../conversation/dialog-build.html) nella documentazione {{site.data.keyword.conversationshort}}.
* Vedi se la tua chiamata telefonica è elencata nel dashboard _Usage_ dell'agent vocale. Se vedi un elemento per la tua chiamata telefonica, il tuo agent vocale è collegato al servizio Watson.

### Perché non posso specificare un numero di telefono quando creo un agent vocale?

Controlla se il numero telefonico che hai specificato viene utilizzato da un agent vocale esistente. Puoi avere solo un agent vocale per numero di telefono. Puoi fornire un altro numero telefonico dal tuo provider di trunking SIP e utilizzarlo per creare un altro agent vocale. Oppure [elimina l'agent vocale esistente nel dashboard _Manage_](managing.html#delete_va) per liberare il numero telefonico e poi crea un nuovo agent vocale.

### Perché le mie chiamate hanno spesso esito negativo?

Gli agent vocali possono avere problemi quando le chiamate hanno esito negativo perché un motore di orchestrazione del servizio (SOE) avvia una lunga transazione e non risponde al tuo agent vocale in modo tempestivo. Se una transazione supera il timeout {{site.data.keyword.conversationshort}} predefinito, la chiamata ha esito negativo. Per evitare errori di chiamata, SOE può modificare il timeout {{site.data.keyword.conversationshort}} predefinito utilizzando la variabile di stato `vgwConversationResponseTimeout`. Consulta [Variables set in the {{site.data.keyword.conversationshort}} dialog](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html#variables-conv).
