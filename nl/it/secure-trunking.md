---

copyright:
  years: 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Protezione delle connessioni
{: #securing}

Puoi abilitare SRTP (Secure Real Time Transport Protocol) e la codifica utilizzando TLS (Transport Layer Security) per i tuoi trunk SIP per proteggere le connessioni effettuate con {{site.data.keyword.iva_full}}.

## Configurazione di SRTP in Twilio
{: #SRTP}

**Nota:** se abiliti SRTP, vengono codificati anche i messaggi SIP. Non devi abilitare la codifica SRTP e dei messaggi SIP separatamente.

1. Nel tuo account Twilio, passa al dashboard _Elastic SIP Trunking_ e seleziona **Trunks**.

1. Scegli il trunk che vuoi proteggere con SRTP selezionando un trunk esistente oppure creandone uno nuovo facendo clic sull'icona **+**.

  * Se crei un nuovo trunk, devi configurare il _SIP Trunk URI_ nel dashboard **Origination**.  Per ulteriori informazioni, vedi [Connessione a un trunk SIP](connect-SIP.html).

1. Nel dashboard _General_, trova la sezione _Secure Trunking_. Fai clic su **Disabled** per modificare l'impostazione di trunking protetto con **Enabled** e salva le tue modifiche.

## Abilitazione della codifica solo per i messaggi SIP utilizzando TLS in Twilio
{: #TLS}

Se vuoi codificare soltanto i messaggi SIP in {{site.data.keyword.iva_short}} senza SRTP, puoi selezionare un endpoint URI che utilizza TLS (Transport Layer Security) in Twilio.

1. Nel tuo account Twilio, passa al dashboard _Elastic SIP Trunking_ e seleziona **Trunks**.

1. Scegli il trunk a cui desideri aggiungere il trasferimento di chiamata selezionando un trunk esistente oppure creandone uno nuovo facendo clic sull'icona **+**.

1. Seleziona **Origination** dal menu e immetti i seguenti URI di origine protetti, uno alla volta. Includendo più nomi host o indirizzi IP, se il primo endpoint host presenta un errore o è fuori servizio, il tuo provider del trunk SIP indirizza le chiamate al nome host successivo elencato.

```
sip:us-south.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}

O

```
sip:us-east.voiceagent.cloud.ibm.com;transport=tls
```
{:codeblock}
