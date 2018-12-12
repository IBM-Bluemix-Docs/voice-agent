---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-08"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Tag di azione e variabili di stato nell'API
{: #api}

Utilizza il materiale di riferimento per trovare le tag di azione che avviano le azioni eseguite dal tuo agent vocale durante una sessione di conversazione o le variabili di stato, che definiscono le caratteristiche dell'agent vocale che perdurano durante la conversazione a meno che modificato diversamente.
{: shortdesc}

Consulta [Programmazione degli agent vocali utilizzando l'API](api.html) per esempi ed esempi di codice su come configurare e avviare le sequenze di azioni.

Poiché {{site.data.keyword.iva_full}} si basa su IBM Voice Gateway, l'API funziona nello stesso modo. Se hai familiarità con Voice Gateway, puoi utilizzare le stesse azioni e variabili di stato nei tuoi dialoghi {{site.data.keyword.conversationshort}} con {{site.data.keyword.iva_short}}. Consulta [Action tags and state variables in the Voice Gateway API](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html).
{: tip}

## Attributi e comandi di azione
{: #actions-and-attributes}

La seguente tabella elenca le azioni che puoi specificare nel dialogo {{site.data.keyword.conversationshort}} e tutti gli attributi che puoi definire per ogni azione.

| Comando azione | Descrizione | Attributi |
| ----- | ----- | ----- |
| `vgwActPlayText`| Riproduce un'espressione convertita in voce dal servizio {{site.data.keyword.texttospeechshort}}. | <ul><li>`text`: un elenco di espressioni da riprodurre. Facoltativo. <p>Ad esempio:<br/><code>"text": [<br/>&nbsp;&nbsp;&nbsp;"Hello. How can I help you today?"<br/>&nbsp;&nbsp;&nbsp;]</code><p> Per impostazione predefinita, l'azione riproduce un elenco di espressioni configurate nel campo `output.text`. </li><li>`errAudioURL`: un URL a un file audio riprodotto se l'agent vocale non può contattare il servizio {{site.data.keyword.texttospeechshort}} per completare l'azione. Il file audio deve essere nel formato WAV.</li></ul>|
| `vgwActPlayUrl` | Riproduce un file audio non appena il testo incluso viene riprodotto, come per la riproduzione di MOH (music on hold) o delle espressioni monouso comuni. Se non viene incluso del testo, l'audio viene riprodotto immediatamente. Il file deve essere di un solo canale (mono), codificato PCM e avere una frequenza di trasmissione di 8.000 Hz con 16 bit per campionamento. | <ul><li>`url`: l'URL da riprodurre. Obbligatorio.</li><li> `playURLInLoop`: impostato facoltativamente su `Yes` r `No` per indicare se riprodurre l'URL in un loop. Il valore predefinito è `No`.</li></ul> |
| `vgwActHangup` | Riaggancia la chiamata. | Nessun attributo. |
| `vgwActSetSTTConfig` | Applica una serie di parametri dell'agent vocale da passare al servizio Watson {{site.data.keyword.speechtotextshort}}. Il servizio {{site.data.keyword.conversationshort}} definisce in modo dinamico i parametri in base alla chiamata. | Gli attributi vengono trasmessi in modo trasparente come proprietà JSON al servizio {{site.data.keyword.speechtotextshort}}. |
| `vgwActSetTTSConfig` | Applica una serie di parametri dell'agent vocale da passare al servizio Watson {{site.data.keyword.texttospeechshort}}. Il servizio {{site.data.keyword.conversationshort}} definisce in modo dinamico i parametri in base alla chiamata. |  Gli attributi vengono trasmessi in modo trasparente come proprietà JSON al servizio {{site.data.keyword.texttospeechshort}}.  |
| `vgwActSetConversationConfig` | Applica una serie di parametri dell'agent vocale per definire uno spazio di lavoro {{site.data.keyword.conversationshort}}. Il servizio {{site.data.keyword.conversationshort}} definisce in modo dinamico i parametri in base alla chiamata. | <ul><li>`url`: le credenziali `url` dell'API del servizio {{site.data.keyword.conversationshort}}.</li><li>`workspaceID`: l'ID dello spazio di lavoro {{site.data.keyword.conversationshort}}</li><li>`username`: le credenziali `username` del servizio {{site.data.keyword.conversationshort}}.</li><li>`password`: le credenziali `password` del servizio {{site.data.keyword.conversationshort}}.</li></ul> |
| `vgwActCollectDtmf` | Indica all'agent vocale di raccogliere l'input della trasmissione dual-tone multi-frequency (DTMF). | Deve essere definito uno dei seguenti attributi. <ul><li> `dtmfTermKey`: la chiave di terminazione DTMF, che segnala la fine dell'input DTMF. Ad esempio, "`#`". </li><li> `dtmfCount`:il numero di cifre DTMF da raccogliere.</li></ul> Quando viene soddisfatta una di queste condizioni, l'agent vocale interrompe la raccolta dell'input DTMF. |
| `vgwActPauseDTMF` | Disabilita l'input DTMF. Tutto l'input DTMF viene ignorato finché non viene riabilitato dall'azione `vgwActUnPauseDTMF`. | Nessun attributo. |
| `vgwActUnPauseDTMF` | Abilita l'input DTMF che era stato disabilitato dall'azione `vgwActPauseDTMF`. | Nessun attributo. |
| `vgwActExcludeFromTTSCache` | Indica all'agent vocale di non memorizzare nella cache la risposta dal servizio {{site.data.keyword.texttospeechshort}}. Ad esempio, le risposte che contengono dati PHI, PII e PCI DSS sensibili o informazioni dinamiche come i nomi o le date di nascita dei clienti, dovrebbero essere escluse. <br/>Questa tag di azione deve essere impostata sul nodo di dialogo {{site.data.keyword.conversationshort}} di ogni espressione che non vuoi memorizzare nella cache. | Nessun attributo. |
| `vgwActPauseSTT` | Mette in pausa l'elaborazione da voce a testo finché non viene riabilitata dall'azione `vgwActUnPauseSTT`. Se la registrazione è abilitata e l'elaborazione da voce a testo è in pausa, l'audio dal chiamante non viene acquisito. | Nessun attributo. |
| `vgwActUnPauseSTT` | Riprende l'elaborazione da voce a testo che era stata precedentemente messa in pausa dall'azione `vgwActPauseSTT`. | Nessun attributo. |
| `vgwActEnableSpeechBargeIn` | Abilita l'interruzione del discorso in modo che i chiamanti possano interrompere la riproduzione dall'agent vocale parlando. | Nessun attributo. |
| `vgwActDisableSpeechBargeIn` | Disabilita l'interruzione del discorso in modo che la riproduzione dall'agent vocale non venga interrotta quando i chiamanti parlano. | Nessun attributo. |
| `vgwActEnableDTMFBargeIn`| Abilita l'interruzione DTMF in modo che i chiamanti possano interrompere la riproduzione dall'agent vocale premendo un tasto. | Nessun attributo. |
| `vgwActDisableDTMFBargeIn` | Disabilita l'interruzione DTMF in modo che la riproduzione dall'agent vocale non venga interrotta quando i chiamanti premono i tasti. | Nessun attributo. |
| `vgwActForceNoInputTurn` | Forza un nuovo turno nella conversazione senza attendere l'input dal chiamante. | Nessun attributo. |
{: caption="Tabella 1. Azioni che puoi avviare dal servizio {{site.data.keyword.conversationshort}}" caption-side="top"}

## Le variabili di stato impostate nel dialogo {{site.data.keyword.conversationshort}}
{: #state-variables-conv}

Puoi impostare le seguenti variabili di stato all'interno del dialogo {{site.data.keyword.conversationshort}} per modificare il comportamento del tuo agent vocale.

| Nome variabile stato | Valore previsto | Descrizione |
| -------------- | ------ | ----------- |
| `vgwByeCustomHeader` | Definito dall'utente | Definisce un'intestazione personalizzata in un messaggio SIP BYE in uscita. Il valore dell'intestazione personalizzata viene definito dalle variabili di stato `vgwByeCustomHeaderVal`.  |
| `vgwByeCustomHeaderVal` | Definito dall'utente | Definisce il valore di un'intestazione personalizzata in un messaggio SIP BYE in uscita. L'intestazione personalizzata viene definita dalle variabili di stato `vgwByeCustomHeader`. |
| `vgwPostResponseTimeoutCount` | Tempo in millisecondi | La quantità di tempo che deve attendere una nuova espressione dopo che la risposta viene riprodotta al chiamante. Se il valore viene superato, {{site.data.keyword.conversationshort}} riceve un aggiornamento di testo con la parola "vgwPostResponseTimeout" per indicare che si è verificato un timeout.|
| `vgwConversationFailedMessage` | Stringa di testo | Il messaggio trasmesso al chiamante se il servizio {{site.data.keyword.conversationshort}} riscontra un errore. Configura il tuo dialogo {{site.data.keyword.conversationshort}} per impostare questa variabile nel primo turno. |
| `vgwSessionInactivityTimeout` | Tempo in minuti <br/><br/>Valore predefinito: `2` | L'intervallo di timeout di inattività. Il valore dell'intervallo di timeout specifica in minuti per quanto tempo l'agent vocale consente ad una sessione di essere inattiva. Quando il timeout scade, l'agent vocale termina la sessione. |
| `vgwErrAudioURL` | Definito dall'utente | Un URL a un file audio riprodotto se il servizio {{site.data.keyword.texttospeechshort}} non può essere contattato quando l'agent vocale tenta di riprodurre una risposta. Il file audio deve essere nel formato WAV. |
{: caption="Tabella 2. Le variabili impostate dal servizio {{site.data.keyword.conversationshort}}" caption-side="top"}

## Le variabili di stato impostate dall'agent vocale
{: #state-variables-iva}

| Nome variabile stato | Valore previsto | Descrizione |
| -------------- | ----- | ----------- |
| `vgwSessionID`   | Definito dall'utente <br/><br/> Valore predefinito: `Call-ID` | Un'intestazione dell'ID della sessione personalizzata estratta dalla richiesta SIP INVITE. Il valore rappresenta l'ID di sessione globale utilizzato in tutti i log di controllo dell'agent vocale correlati alla sessione. |
| `vgwSIPCallID` | SIP `Call-ID` | L'ID della chiamata SIP associato alla chiamata. |
| `vgwSIPRequestURI` | SIP `Request-URI` | L'URI della richiesta SIP che ha avviato la chiamata. |
| `vgwSIPToURI` | SIP `To` URI | Il SIP `To` URI associato alla chiamata. |
| `vgwSIPFromURI` | SIP `From` URI | Il SIP `From` URI associato alla chiamata. |
| `vgwBargeInOccurred` | `Sì` / `No` | Indica se si è verificata o meno un'interruzione. |
| `vgwHangUp` | `Sì` / `No` | Indica se la conversazione è stata terminata. |
| `vgwHangupReason` | Stringa | Quando viene eseguito un riaggancio dal chiamante o a causa di un errore, questa variabile viene inviata al servizio {{site.data.keyword.conversationshort}} per indicare il motivo della disconnessione della chiamata. Il testo nella richiesta di messaggio che viene inviato al servizio {{site.data.keyword.conversationshort}} include inoltre "vgwHangUp". |
| `vgwConversationResponseTimeout` | Tempo in secondi<br/><br/>Valore predefinito: `5`  | Il tempo in secondi in cui l'agent vocale attende una risposta dal servizio {{site.data.keyword.conversationshort}}. Se il tempo viene superato, l'agent vocale ritenta di contattare il servizio {{site.data.keyword.conversationshort}}. Se il servizio non può ancora essere raggiunto, la chiamata non riesce. |
| `vgwSTTResponse` | Oggetto JSON | La risposta finale dal servizio {{site.data.keyword.speechtotextshort}} nel formato JSON, che include la trascrizione e il punteggio di affidabilità per le ipotesi preferite e tutte le alternative. <p>Ad esempio, il seguente formato corrisponde esattamente al formato ricevuto dal servizio {{site.data.keyword.speechtotextshort}}.</p><p><code>{<br/>&nbsp;&nbsp;"result_index": 0,<br/>&nbsp;&nbsp;"warnings": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;"Unknown arguments: continuous."<br/>&nbsp;&nbsp;],<br/>&nbsp;&nbsp;"results": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"final": true,<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"alternatives": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello world",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.758<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"transcript": "Hello wooled",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"confidence": 0.358<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;]<br/>&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}.</code></p> |
| `vgwIsDTMF` | `Sì` / `No` | Indica se l'input al servizio {{site.data.keyword.conversationshort}} è una trasmissione dual-tone multi-frequency (DTMF). |
{: caption="Tabella 3. Le variabili impostate dall'agent vocale" caption-side="top"}
