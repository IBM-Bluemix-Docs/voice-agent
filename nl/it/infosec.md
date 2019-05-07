---

copyright:
  years: 2018
lastupdated: "2018-11-16"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Informazioni sulla sicurezza e sulla privacy dei dati
{: #infosec}

IBM si impegna a offrire ai nostri clienti e partner soluzioni innovative per la privacy, la sicurezza e la governance dei dati.
{: shortdesc}

## Gestione delle informazioni e opzioni di configurazione
{: #configure_infosec}

{{site.data.keyword.iva_short}} non archivia, raccoglie o elabora i dati ricevuti dai clienti. Invece, i dati sono instradati a servizi diversi per l'elaborazione. Durante la conversazione, gli utenti potrebbero condividere informazioni che contengono dati Protected Health Information (PHI), personally identifiable information (PII) o PCI Data Security Standard (PCI DSS). Consulta [Architettura](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window} per ulteriori informazioni sul flusso di conversazione e l'architettura di {{site.data.keyword.iva_short}}.

Considera le seguenti funzioni quando configuri la tua istanza del Voice Agent per supportare la privacy dei dati e la gestione sicura.

### Trasferimento di chiamata
{:  #calltransfer_infosec}

Quando aggiungi le funzionalità del trasferimento di chiamata al tuo Voice Agent, fornisci un numero di telefono quando configuri l'URI SIP di destinazione del trasferimento. Gli utenti non dovrebbero fornire un numero di telefono personale per questa destinazione del trasferimento.

Consulta [Configurazione del trasferimento di chiamata](/docs/services/voice-agent?topic=voice-agent-call-transfer) per ulteriori informazioni sulla configurazione dei tuoi trunk SIP e URI SIP per il trasferimento di chiamata.

### Inoltro dell'evento
{: #infosec_event_forwarding}

Puoi configurare il tuo Voice Agent per inoltrare gli eventi di segnalazione a un'istanza del database {{site.data.keyword.cloudantfull}}. Questi eventi di segnalazione possono includere dati PII, PHI e PCI DSS sui tuoi chiamanti nel formato di trascrizioni, di eventi di turno di conversazione e di eventi CDR (call detail record). I dati richiamati e gli eventi di segnalazione non vengono archiviati, elaborati o raccolti all'interno di {{site.data.keyword.iva_short}} e gli utenti dovrebbero configurare i propri servizi {{site.data.keyword.cloudant_short_notm}} esterni in modo appropriato. **Per impostazione predefinita, l'inoltro dell'evento è disattivato.**

Consulta [Abilitazione dell'inoltro dell'evento](/docs/services/voice-agent?topic=voice-agent-event_forwarding) per configurare i tuoi Voice Agent ad inoltrare gli eventi di segnalazione.

Consulta [**{{site.data.keyword.cloudant_short_notm}}: sicurezza**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window} per ulteriori informazioni sulla privacy dei dati e la sicurezza delle informazioni per {{site.data.keyword.cloudant_short_notm}}.

### Memorizzazione nella cache di Text to Speech
{: #tts_caching}

Per conversare con i clienti, {{site.data.keyword.conversationshort}} crea le risposte come del testo, che viene passato al servizio {{site.data.keyword.texttospeechshort}} e letto ad alta voce in {{site.data.keyword.iva_short}}. Le risposte create da {{site.data.keyword.conversationshort}} potrebbero contenere informazioni sensibili. Per evitare che {{site.data.keyword.iva_short}} memorizzi nella cache le risposte ricevute dal servizio {{site.data.keyword.texttospeechshort}} che contengono dati personali, puoi abilitare il comando di azione `vgwActExcludeFromTTSCache` per escludere dalla memorizzazione nella cache le espressioni che contengono alcuni tipi di informazioni. Consulta [Programmazione dei Voice Agent utilizzando l'API](/docs/services/voice-agent?topic=voice-agent-api#action-sequences).

### Connessioni sicure
{: #secure_trunking}

{{site.data.keyword.iva_short}} è basato su {{site.data.keyword.Bluemix_notm}} e integra i trunk SIP configurati dagli utenti. Poiché i trunk SIP sono esterni e collegati a {{site.data.keyword.iva_short}}, puoi abilitare le connessioni tra i tuoi trunk SIP e {{site.data.keyword.iva_short}} utilizzando SRTP (Secure Real Time Transport Protocol) e la codifica utilizzando sip sicuri (sips), che si basano su TLS (Transport Layer Security). Consulta [Protezione delle connessioni](/docs/services/voice-agent?topic=voice-agent-securing).

### Configurazione del motore di orchestrazione del servizio (SOE)
{: #SOE_config}

Puoi utilizzare un motore di orchestrazione del servizio (SOE) per elaborare le informazioni trasmesse tra {{site.data.keyword.iva_short}} e {{site.data.keyword.conversationshort}} per personalizzare la conversazione con i chiamanti. Per mantenere le connessioni sicure, assicurati di configurare il tuo SOE utilizzando un URL sicuro, `https` e l'autenticazione utente.

Consulta [Configurazione di {{site.data.keyword.conversationshort}} del tuo Voice Agent](/docs/services/voice-agent?topic=voice-agent-conversation_va#conversation_va) e [Architettura con un motore di orchestrazione del servizio](/docs/services/voice-agent?topic=voice-agent-about#arch-soe).

## Servizi correlati a {{site.data.keyword.iva_short}}
{: #related_services}

{{site.data.keyword.iva_short}} organizza diversi servizi {{site.data.keyword.Bluemix_notm}} per coordinare la comunicazione tra gli utenti e il cloud basata sui servizi cognitivi. {{site.data.keyword.iva_short}} non archivia, raccoglie o elabora i dati in un modo che viola i diritti degli utenti. Tuttavia, a seconda di come configuri i servizi correlati, questi servizi integrati potrebbero raccogliere i dati Protected Health Information (PHI), personally identifiable information (PII) o PCI Data Security Standard (PCI DSS) che gli utenti condividono durante la conversazione. Per ulteriori informazioni sul flusso di conversazione e l'architettura {{site.data.keyword.iva_short}}, consulta[Architettura](/docs/services/voice-agent?topic=voice-agent-about#architecture){: new_window}.

Vedi le seguenti risorse per trovare delle considerazioni su ogni servizio e su {{site.data.keyword.Bluemix_notm}}.

  * [**{{site.data.keyword.Bluemix_short}}: conformità di sicurezza**](/docs/overview?topic=overview-security#security)
  * [**{{site.data.keyword.conversationfull}}: sicurezza delle informazioni**](/docs/services/assistant?topic=assistant-information-security#information-security){: new_window}
  * [**{{site.data.keyword.texttospeechfull}}: sicurezza delle informazioni**](/docs/services/text-to-speech?topic=text-to-speech-information-security){: new_window}
  * [**{{site.data.keyword.speechtotextfull}}: sicurezza delle informazioni**](/docs/services/speech-to-text?topic=speech-to-text-information-security){: new_window}
  * [**{{site.data.keyword.cloudant_short_notm}}: sicurezza**](/docs/services/Cloudant/offerings?topic=cloudant-security#security){: new_window}
