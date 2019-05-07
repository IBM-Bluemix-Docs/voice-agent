---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

keywords: voice agent, creating a SIP trunk, creating and connecting your voice agent,

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Esercitazione introduttiva
{: #getting-started}
{{site.data.keyword.iva_full}} ti aiuta ad integrare una serie di servizi Watson orchestrati con la rete telefonica utilizzando il SIP (Session Initiation Protocol). Questa esercitazione descrive come configurare un Voice Agent cognitivo che chiami da qualsiasi telefono.
{: shortdesc}

Guarda una dimostrazione su come creare il tuo primo Voice Agent in questa [Esercitazione {{site.data.keyword.iva_full_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/).
{: tip}

Se hai bisogno di assistenza, ci trovi su Slack nel team [IBM Cloud Technology ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) nel canale `#ibmvoicegateway`
{: tip}

## Prima di cominciare
{: #prereqs}

Crea un nuovo account o accedi al tuo account esistente in [{{site.data.keyword.Bluemix_short}}](https://cloud.ibm.com/).

## Passo 1: creazione di un'istanza del servizio {{site.data.keyword.iva_short}} in {{site.data.keyword.Bluemix_notm}}
{: #step1}

Dalla pagina di catalogo [{{site.data.keyword.iva_short}} ](https://cloud.ibm.com/catalog/services/voice-agent-with-watson), controlla le informazioni sul servizio e fai poi clic su **Crea**.

Dopo aver creato il servizio, prendi nota dell'endpoint del Voice Agent nel dashboard _Getting started_. Hai bisogno dell'URI SIP endpoint per configurare il tuo trunk SIP.

## Passo 2: creazione di un trunk SIP per inoltrare le chiamate a {{site.data.keyword.iva_short}}
{: #step2}

1. Crea un trunk SIP da uno dei seguenti provider supportati. Quindi, associa un numero di telefono al tuo trunk SIP.

  * [NetFoundry](/docs/services/voice-agent?topic=voice-agent-connect#NetFoundry-setup)
  * [Twilio](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup)
  * [AT&T e altri provider di trunking SIP](/docs/services/voice-agent?topic=voice-agent-connect#att-other)
  * [Peering con {{site.data.keyword.iva_short}}](/docs/services/voice-agent?topic=voice-agent-connect#peering)

## Passo 3: creazione e collegamento del tuo Voice Agent
{: #step3}

1. Passa al dashboard _Manage_ nel dashboard {{site.data.keyword.iva_short}} e fai clic su **Create a Voice Agent**.

2. Immetti le impostazioni di base del tuo Voice Agent:
  * **Name:** un nome univoco del tuo Voice Agent, come `Customer Support`
  * **Phone number:** il numero di telefono completo che hai associato al tuo trunk SIP, inclusi il prefisso internazionale e quello nazionale. Ad esempio, per un numero 800 degli Stati Uniti, specifica il numero di telefono come 18883334444. Il numero di telefono può avere spazi e caratteri + ( ) -.
  * **Description:** una descrizione facoltativa del suo utilizzo
  * **Default transfer target:** un URI di terminazione facoltativo a cui possono essere trasferite le chiamate.

3. Crea le istanze del servizio {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} e {{site.data.keyword.texttospeechshort}} del tuo Voice Agent. Puoi scegliere di creare un Voice Agent con uno dei seguenti metodi:
  * Fai clic su **Create a voice agent** per creare tutti i servizi e un Voice Agent con la configurazione predefinita in un solo passo.
  * Oppure, fai clic sui nomi del servizio per creare i servizi personalmente. Successivamente ritorna in {{site.data.keyword.iva_short}} e crea un Voice Agent separatamente.

   Se hai creato manualmente l'istanza del servizio {{site.data.keyword.conversationshort}}, aggiungi un dialogo in modo da poter verificare il tuo Voice Agent.  Per iniziare rapidamente, clona la [conversazione di esempio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) da GitHub e quindi [importa l'esempio ](/docs/conversation?topic=services/conversation-configuring-a-watson-assistant-workspace#creating-workspaces) come competenza:

   1. Nella pagina GitHub della conversazione di esempio, fai clic sul numero di riga `1` e seleziona **... > Copy line**. Incolla il testo copiato in un file e salvalo come un file JSON, ad esempio `voice-gateway-conversation-en.json`.
   2. Avvia lo strumento {{site.data.keyword.conversationshort}}. Nella pagina _Skills_, fai clic sull'icona ![Import workspace](../conversation/images/workspace_import.png) e importa il file JSON.

  In alternativa, puoi [creare il tuo dialogo](/docs/services/assistant?topic=assistant-getting-started#getting-started-build-dialog) per simulare il tuo ambiente di produzione. Come minimo, il tuo dialogo deve contenere un nodo con la condizione `conversation_start` e un nodo con una risposta predefinita.


## Passi successivi
{: #next-steps}

Verifica il tuo Voice Agent chiamando il suo numero di telefono associato. Se senti una risposta, il tuo Voice Agent è attivo!

Se non senti una risposta, puoi controllare i tuoi log di chiamata e l'utilizzo del Voice Agent nel dashboard _Usage_. Vedi [Visualizzazione dei log di chiamata e utilizzo](/docs/services/voice-agent?topic=voice-agent-logging).

Puoi modificare le impostazioni del tuo Voice Agent, creare o rimuovere i Voice Agent e aggiungere più ubicazioni del servizio Watson dal dashboard _Manage_. Per ulteriori informazioni, vedi [Gestione dei Voice Agent](/docs/services/voice-agent?topic=voice-agent-managing).

Puoi inoltre configurare le impostazioni avanzate, come la protezione della tua connessione SIP dal tuo account Twilio. Consulta [Protezione delle connessioni](/docs/services/voice-agent?topic=voice-agent-securing).
