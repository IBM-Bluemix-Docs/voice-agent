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

# Esercitazione introduttiva
{{site.data.keyword.iva_full}} ti aiuta ad integrare una serie di servizi Watson orchestrati con la rete telefonica utilizzando il SIP (Session Initiation Protocol). Questa esercitazione descrive come configurare un agent vocale cognitivo che chiami da qualsiasi telefono.
{: shortdesc}

Guarda una dimostrazione su come creare il tuo primo agent vocale in questa [Esercitazione {{site.data.keyword.iva_full_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/).
{: tip}

## Prima di cominciare
{: #prereqs}

Crea un nuovo account o accedi al tuo account esistente in [{{site.data.keyword.Bluemix_short}}](https://console.bluemix.net/).

## Passo 1: creazione di un'istanza del servizio {{site.data.keyword.iva_short}} in {{site.data.keyword.Bluemix_notm}}
{: #step1}

Dalla [pagina di catalogo {{site.data.keyword.iva_short}}](https://console.bluemix.net/catalog/services/voice-agent-with-watson), controlla le informazioni sul servizio e fai poi clic su **Create**.

Dopo aver creato il servizio, prendi nota dell'endpoint dell'agent vocale nel dashboard _Getting started_. Hai bisogno dell'URI SIP endpoint per configurare il tuo trunk SIP.

## Passo 2: creazione di un trunk SIP per inoltrare le chiamate a {{site.data.keyword.iva_short}} 
{: #step2}

1. Crea un trunk SIP da uno dei seguenti provider supportati. Quindi, associa un numero di telefono al tuo trunk SIP.

  * [NetFoundry](connect-SIP.html#NetFoundry-setup)
  * [Twilio](connect-SIP.html#twilio-setup)
  * [AT&T e altri provider di trunking SIP](connect-SIP.html#att-other)
  * [Peering con {{site.data.keyword.iva_short}}](connect-SIP.html#peering)

## Passo 3: creazione e collegamento del tuo agent vocale
{: #step3}

1. Passa al dashboard _Manage_ nel dashboard {{site.data.keyword.iva_short}} e fai clic su **Create a Voice Agent**.

2. Immetti le impostazioni di base del tuo agent vocale:
  * **Nome:** un nome univoco del tuo agent vocale, come `Customer Support`
  * **Numero di telefono:** il numero di telefono completo che hai associato al tuo trunk SIP, inclusi i codici area e paese. Ad esempio, per un numero 800 degli Stati Uniti, specifica il numero di telefono come 18883334444. Il numero di telefono può avere spazi e caratteri + ( ) -.
  * **Descrizione:** una descrizione facoltativa del suo utilizzo

3. Crea le istanze del servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} e {{site.data.keyword.texttospeechshort}} del tuo agent vocale. Puoi scegliere di creare un agent vocale con uno dei seguenti metodi:
  * Fai clic su **Create a voice agent** per creare tutti i servizi e un agent vocale con la configurazione predefinita in un solo passo.
  * Oppure, fai clic sui nomi del servizio per creare i servizi personalmente. Successivamente ritorna in {{site.data.keyword.iva_short}} e crea un agent vocale separatamente. 

   Se hai creato manualmente l'istanza del servizio {{site.data.keyword.conversationshort}}, aggiungi un dialogo in modo da poter verificare il tuo agent vocale.  Per un'introduzione rapida, clona la [conversazione di esempio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) da GitHub e poi [importa l'esempio](../conversation/configure-workspace.html#creating-workspaces) come uno spazio di lavoro:

   1. Nella pagina GitHub della conversazione di esempio, fai clic sul numero di riga `1` e seleziona **... > Copy line**. Incolla il testo copiato in un file e salvalo come un file JSON, ad esempio `voice-gateway-conversation-en.json`.
   2. Avvia lo strumento {{site.data.keyword.conversationshort}}. Nella pagina _Workspaces_, fai clic sull'icona ![Import workspace](../conversation/images/workspace_import.png) e importa il file JSON.

  In alternativa, puoi [creare il tuo dialogo](https://console.bluemix.net/docs/services/conversation/dialog-build.html) per simulare il tuo ambiente di produzione. Come minimo, il tuo dialogo deve contenere un nodo con la condizione `conversation_start` e un nodo con una risposta predefinita.

## Fasi successive
{: #next}

Verifica il tuo agent vocale chiamando il suo numero di telefono associato. Se senti una risposta, il tuo agent vocale è attivo!

Se non senti una risposta, puoi controllare i tuoi log di chiamata e l'utilizzo dell'agent vocale nel dashboard _Usage_. Vedi [Visualizzazione e utilizzo dei log di chiamata](logging.html).

Puoi modificare le impostazioni del tuo agent vocale, creare o rimuovere gli agent vocali e aggiungere più ubicazioni del servizio Watson dal dashboard _Manage_. Per ulteriori informazioni, vedi [Gestione degli agent vocali](managing.html).

Puoi inoltre configurare le impostazioni avanzate, come la protezione della tua connessione SIP dal tuo account Twilio. Consulta [Protezione delle connessioni](secure-trunking.html).
