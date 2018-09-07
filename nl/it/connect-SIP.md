---

copyright:
  years: 2018
lastupdated: "2018-08-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Connessione a un trunk SIP
{: #connect}

Puoi scegliere il provider del trunk SIP che utilizzi per l'integrazione con {{site.data.keyword.iva_full}} dal seguente elenco.
{: #shortdesc}

* [NetFoundry](#NetFoundry-setup)
* [Twilio](#twilio-setup)
* [AT&T e altri provider](#att-other)
* [Peering con {{site.data.keyword.iva_short}}](#peering)
* [Richiesta di configurazione assistita](#request-setup)

## Creazione di un numero di telefono e di un trunk SIP NetFoundry
{: #NetFoundry-setup}

**Nota:** la creazione di un account richiede una carta di credito, che viene addebitata periodicamente in base al tuo utilizzo. Se già hai un account NetFoundry, puoi utilizzarlo.

1. Crea un account nel sito web [NetFoundry![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson.netfoundry.io/watson-login){: new_window}.

1. Vai alla pagina principale _Watson account_.

1. Seleziona una regione da cui vuoi il numero.

  **Nota:** controlla il sito web Netfoundry per le regioni disponibili. Nuove regioni vengono aggiunte di continuo.

1. Fai clic su **Purchase** e segui le istruzioni sullo schermo per completare l'acquisto.

1. Una volta che il pagamento è stato elaborato correttamente, il tuo numero di telefono trunk SIP viene visualizzato nel tuo account.

Hai bisogno di questo numero di telefono per configurare il tuo agent vocale e il trasferimento di chiamata, inclusi i codici area e paese. Consulta [Creazione e collegamento del tuo agent vocale](getting-started.html#step3).


## Creazione di un trunk SIP Twilio
{: #twilio-setup}

**Nota:** la creazione di un [account Twilio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.twilio.com/try-twilio){: new_window} richiede una carta di credito, che viene addebitata periodicamente in base al tuo utilizzo del trunk SIP che configuri. Se già hai un account Twilio, puoi utilizzarlo.

  1. Crea un account Twilio nel [sito web Twilio  ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.twilio.com/try-twilio){: new_window}.

  1. Crea un trunk SIP con il tuo account Twilio.

  1. Dal sito web Twilio, passa al dashboard Elastic SIP Trunking.

  1. Seleziona **Trunks** dalla barra di navigazione e crea un trunk SIP. Se già hai un trunk SIP, fai clic sull'icona **+**. Nella finestra di dialogo risultante, immetti un nome per il tuo trunk SIP e fai clic su **Create**.

  1. Dalla pagina Elastic SIP Trunks, seleziona il tuo trunk SIP.

  1. Seleziona **Origination** dalla barra di navigazione del tuo trunk SIP e configura l'URI SIP di origine. Puoi includere più nomi host per evitare errori con il servizio selezionando l'icona **+**.

  L'indirizzo IP o il nome host è il valore che hai annotato nel dashboard _Getting Started_ della tua istanza del servizio {{site.data.keyword.iva_short}}. Quando configuri l'URI di origine, deve essere nel formato URI SIP, come ad esempio `sip:us-south.voiceagent.cloud.ibm.com/`. Includendo più nomi host o indirizzi IP, se il primo endpoint host presenta un errore o è fuori servizio, il tuo provider del trunk SIP indirizza le chiamate al nome host successivo elencato.

  1. Seleziona **Numbers** dalla barra di navigazione del tuo trunk SIP. Poi, crea un numero di telefono e assegnalo al tuo trunk SIP.

  Nella pagina Numbers, fai clic su **Buy a Number** o, se hai già un numero, sull'icona **+**. Viene visualizzato un pannello in cui puoi fornire un nuovo numero di telefono nella tua regione. Assegna il numero al trunk SIP che hai creato ritornando al trunk SIP e facendo clic sull'icona Number.

  Hai bisogno di questo numero di telefono per configurare il tuo agent vocale, inclusi i codici area e paese. Consulta [Creazione e collegamento del tuo agent vocale](getting-started.html#step3).


## Connessione con AT&T e altri provider
{: #att-other}

{{site.data.keyword.iva_short}} supporta le connessioni con AT&T&reg; e altri provider di trunking SIP. Tuttavia, queste connessioni non sono configurate in modalità self-service e richiedono ulteriore assistenza. Consulta [Richiesta di configurazione assistita](#request-setup).

## Peering con {{site.data.keyword.iva_short}}
{: #peering}

{{site.data.keyword.iva_short}} supporta le connessioni peer, come un tunnel IPSec. Tuttavia, queste connessioni non sono configurate in modalità self-service e richiedono ulteriore assistenza. Consulta [Richiesta di configurazione assistita](#request-setup).

## Richiesta di configurazione assistita
{: #request-setup}

Puoi richiedere la configurazione di rete assistita per collegarti con AT&T o altri provider di trunking SIP, eseguire il peer con {{site.data.keyword.iva_short}} o per richiedere più di 50 connessioni simultanee utilizzando il seguente processo.

1. Apri un nuovo [ticket di supporto {{site.data.keyword.Bluemix_notm}} ](https://console.bluemix.net/unifiedsupport/tickets/add)

1. Seleziona **Technical** per **Ticket Type**.

1. Scegli **Cloud Foundry** per **Select a resource context**.

1. Per **Technical area of support**, scegli **Application Services**.

1. Scegli **Region**, **Organization** e **Space** per la tua istanza {{site.data.keyword.iva_short}}.

1. Seleziona la tua istanza del servizio {{site.data.keyword.iva_short}} per **Associated resource**.

1. Scegli **Severity 4 - Minimal Impact** per **Severity**

1. Per **Subject**, immetti `{{site.data.keyword.iva_short}} assisted network setup`.

1. Nella sezione **Brief description**, descrivi come intendi collegarti al tuo servizio {{site.data.keyword.iva_short}} o di richiedere più di 50 connessioni simultanee per il tuo agent vocale. La connessione peer è disponibile per gli utenti con i piani _Standard_ o _Premium_. Se cambi la tua istanza da un piano _Standard_ o _Premium_ a un piano _Lite_ o se elimini la tua propria istanza, la connessione peer viene disabilitata.

  Puoi collegarti utilizzando un provider di trunking SIP o una connessione peer, come un tunnel IPSec. Nel tuo ticket, puoi allegare un diagramma di rete che descrive la tua topologia di rete in un formato immagine o PDF. Puoi anche allegare dei libri bianchi che descrivono nel dettaglio le funzionalità del servizio che desideri.

  In **Brief description** immetti le seguenti informazioni:
  * Nome azienda
  * ID account {{site.data.keyword.Bluemix_notm}}
  * URL dashboard del servizio {{site.data.keyword.iva_short}}
  * Casi di utilizzo
  * Diagramma di rete con indirizzo IP o informazioni sul provider di trunk SIP
