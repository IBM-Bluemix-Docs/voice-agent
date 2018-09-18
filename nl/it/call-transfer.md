---

copyright:
  years: 2018
lastupdated: "2018-06-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configurazione del trasferimento di chiamata
{: #call-transfer}

Puoi configurare un trasferimento di chiamata in modo che se un chiamante richiede di parlare a un agent dal vivo durante una conversazione, l'agent vocale automaticamente trasferisce la chiamata.
{: shortdesc}

## Informazioni sul trasferimento di chiamata
{: #about-ct}

Abilitando il trasferimento di chiamata, se un chiamante richiede di parlare con un agent dal vivo durante la conversazione, l'agent vocale reindirizzerà la chiamata. Puoi abilitare il trasferimento di chiamata configurando un URI di terminazione nella configurazione del provider SIP. Successivamente definisci la destinazione del trasferimento in un'azione API in un nodo di dialogo della tua istanza {{site.data.keyword.conversationshort}}. La tua destinazione del trasferimento è un URI SIP che contiene l'URI di terminazione e il numero di telefono.

Per ulteriori informazioni dettagliate sulle azioni supportate e sulla personalizzazione dei tuoi agent vocali, consulta [Programmazione degli agent vocali utilizzando l'API](api.html).

## Passo 1: configurazione dell'URI di terminazione
{: #termination-setup}

### Configurazione di un URI di terminazione in NetFoundry
{: #termination-netfoundry}

Prendi nota del numero di telefono nel tuo [account NetFoundry ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson.netfoundry.io/watson-login){: new_window} che desideri trasferire. In seguito, puoi specificare questo numero di telefono e l'URI di terminazione come destinazione del trasferimento nel tuo dialogo {{site.data.keyword.conversationshort}}. Non utilizzare un numero di telefono personale.

Puoi copiare il seguente URI di terminazione NetFoundry da utilizzare nella destinazione del trasferimento.

```
dal.watson-va.netfoundry.net
```
{: codeblock}

Non hai bisogno di configurare manualmente l'URI di terminazione nel tuo account NetFoundry quando [Configuri {{site.data.keyword.conversationshort}} per il trasferimento di chiamata](#conversation-setup).

### Configurazione di un URI di terminazione in Twilio
{: #termination-Twilio}

1. Nel tuo account Twilio, passa al dashboard _Elastic SIP Trunking_ e seleziona **Trunks**.

1. Scegli il trunk a cui desideri aggiungere il trasferimento di chiamata selezionando un trunk esistente oppure creandone uno nuovo facendo clic sull'icona **+**.

  * Se crei un nuovo trunk, devi configurare il _SIP Trunk URI_ nel dashboard **Origination**.  Per ulteriori informazioni, vedi [Connessione a un trunk SIP](connect-SIP.html).

1. Seleziona **Termination** nella tua barra di navigazione e immetti un nome per il tuo URI di terminazione.

  * I nomi dell'URI di terminazione devono essere univoci. Twilio automaticamente controlla se è disponibile il nome che hai scelto. Consulta [SIP Trunk termination settings ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window} per ulteriori dettagli sui servizi Twilio.

1. Nella sezione _Authentication_, fai clic sull'icona **+** per aggiungere un indirizzo IP dell'agent vocale nell'elenco Access Control IP.

  Aggiungi entrambi i seguenti indirizzi IP:
   * 169.60.154.134 (regione servizio Stati Uniti Sud)
   * 169.61.86.179 (regione servizio Stati Uniti Est)

1. Fai clic su **Save** per finire la configurazione del tuo URI di terminazione.

Prendi nota del numero di telefono e dell'URI di terminazione che desideri trasferire. Assicurati che il numero di telefono non sia personale.

Puoi utilizzare il numero di telefono e la terminazione URI per specificare la destinazione del trasferimento nel tuo dialogo {{site.data.keyword.conversationshort}}.


## Passo 2: Configurazione di {{site.data.keyword.conversationshort}} per il trasferimento di chiamata
{: #conversation-setup}

Per ulteriori informazioni sull'utilizzo del servizio {{site.data.keyword.conversationshort}}, vedi [Informazioni su {{site.data.keyword.conversationshort}}](../conversation/index.html#about).

1. Nel tuo dashboard {{site.data.keyword.Bluemix_notm}}, seleziona l'istanza {{site.data.keyword.conversationshort}} che il tuo agent vocale utilizza.

1. Dal dashboard _Getting started_, fai clic sul pulsante **Launch tool**.

1. Fai clic su **Getting Started** nello spazio di lavoro che vuoi modificare.

1. Fai clic su **Add intent** e immetti un nome per l'intento, come ad esempio _Transfer_.

  Puoi immettere ulteriori informazioni dettagliate oppure ritornare in un secondo momento per modificare e rifinire l'intento.

1. Dopo aver creato il tuo intento di trasferimento di chiamata, seleziona la scheda _Dialog_.

1. Fai clic su **Add node** e immetti un nome per il nodo, come ad esempio _Call Transfer_.

1. Nella sezione _If the bot recognizes:_, immetti **Call transfer intent** per trovare l'intento creato.

1. Per la sezione _Then respond with:_, fai clic sull'icona **&vellip;** e seleziona **Open JSON editor**. Copia e incolla il seguente frammento di codice per sostituire il codice nel campo.

```json
{
    "output": {
        "text": {
            "values": [ "Please hold on while I connect you with a live agent." ],
     "selection_policy": "sequential"
        },
   "vgwAction": {
            "command": "vgwActTransfer",
     "parameters": {
                "transferTarget": "sip:18889990000\\@dal.watson-va.netfoundry.net"
            }
        }
    }
}
```
{: codeblock}

**Ricorda**: l'URI SIP della destinazione del trasferimento include un numero di telefono e l'URI di terminazione che hai creato. Non utilizzare un numero di telefono personale nella tua destinazione di trasferimento. Ad esempio, se il numero di telefono è `18889990000` e il tuo URI di terminazione è `mysiptrunk.pstn.twilio.com`, l'URI SIP completo è `sip:18889990000\\@mysiptrunk.pstn.twilio.com`. Se utilizzi Netfoundry e hai un numero di telefono `18889990000`, l'URI SIP completo è `sip:18889990000\\@dal.watson-va.netfoundry.net`.

Per proteggere i PII (Personally Identifiable Information), non utilizzare un numero di telefono personale quando configuri il tuo URI SIP di destinazione di trasferimento. Consulta [{{site.data.keyword.iva_short}} e gestione delle informazioni](infosec.html#configure_infosec){:new_window} per ulteriori informazioni sulle configurazioni e i PII.
{: tip}

## Fasi successive
{: #Next}

Verifica il tuo agent vocale chiamando il suo numero di telefono associato e utilizza i termini chiave che hai identificato nel tuo intento. Se il tuo agent vocale ti reindirizza, allora ha funzionato!

Ora puoi rifinire e configurare il dialogo e l'intento **Transfer** per rispondere alle frasi e ai termini chiave di tua scelta.
