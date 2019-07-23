---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-01"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Programmazione dei Voice Agent utilizzando l'API
{: #api}

Puoi controllare il comportamento del tuo Voice Agent definendo le tag di azione e le variabili di stato dall'interno del servizio {{site.data.keyword.conversationfull}}. Le tag di azione avviano le azioni eseguite dal tuo Voice Agent durante una sessione di conversazione e le variabili di stato definiscono le caratteristiche del Voice Agent che perdurano durante la conversazione a meno che modificato diversamente.
{: shortdesc}

Poiché {{site.data.keyword.iva_full}} si basa su IBM Voice Gateway, l'API funziona nello stesso modo. Se hai familiarità con Voice Gateway e SMS Gateway, puoi utilizzare le stesse azioni e variabili di stato nei tuoi dialoghi {{site.data.keyword.conversationshort}} con {{site.data.keyword.iva_short}}. Vedi rispettivamente [Action tags and state variables in the Voice Gateway API](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html) e [API for SMS Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/sms_api.html).
{: tip}

## Modifica del JSON nella risposta del dialogo
{: #json-editor}

Sia le azioni che gli stati vengono definiti in una risposta del nodo di dialogo nel formato JSON. Per modificare il codice JSON, apri l'editor JSON.

1. Dal dashboard {{site.data.keyword.Bluemix_short}}, seleziona la tua istanza del servizio {{site.data.keyword.conversationshort}}.
1. Avvia lo strumento {{site.data.keyword.conversationshort}}.
1. Fai clic sulla competenza che contiene il dialogo che vuoi modificare.
1. Vai alla scheda **Dialog** e seleziona il nodo dove vuoi impostare un'azione o uno stato.
1. Nella risposta, fai clic sull'icona ![Advanced response](../conversation/images/kabob.png) e seleziona **Open JSON editor**.

All'interno dell'editor JSON, puoi definire le azioni nella proprietà `output` e gli stati nella proprietà `context` come descritto nelle seguenti sezioni.

## Inizializzazione delle azioni
{: #defining-actions}

Per inizializzare le azioni nel Voice Agent durante una chiamata, puoi definire le tag di azioni nel nodo di dialogo {{site.data.keyword.conversationshort}} nel formato JSON nella proprietà `output`. Puoi definire una sola azione nella tag `vgwAction` o una sequenza di azioni nella tag `vgwActionSequence`. Ogni azione è formata da una proprietà `command`, seguita da una proprietà `parameter` facoltativa per definire gli attributi dei comandi che le richiede.

### Azioni singole
{: #single-actions}

Per eseguire una sola azione, definiscila nella tag `vgwAction` con tutti gli attributi del parametro necessari. Nel blocco `text` nella proprietà `output`, puoi facoltativamente includere un'espressione che il Voice Agent riproduce dopo che viene eseguita l'azione.

La seguente azione singola nella tag `vgwAction` dice al Voice Agent di riagganciare la chiamata quando viene attivata la risposta del nodo. Poiché il comando `vgwActHangup` non ha parametri, non vengono definiti.
```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActHangup"
    }
  }
}
```
{: codeblock}

La seguente azione dice al Voice Agent di raccogliere l'input della trasmissione dual-tone multi-frequency (DTMF) e riproduce il testo definito al chiamante.

```json
{
  "output": {
    "vgwAction": {
      "command": "vgwActCollectDtmf",
      "parameters": {
        "dtmfTermKey": "#"
      }
    },
    "text": {
      "values": [
        "Enter your phone number."
      ]
    }
  }
}
```
{: codeblock}

### Sequenze di azioni
{: #action-sequences}

Per eseguire una o più azioni in un solo turno di conversazione, puoi definire una sequenza di azioni all'interno della tag `vgwActionSequence` come un elenco JSON. Le azioni vengono eseguite nell'ordine in cui le definisci.

Diversamente dalle azioni singole, perché un Voice Agent riproduca un'espressione quando utilizzi la tag `vgwActionSequence`, l'elenco delle azioni deve contenere l'azione `vgwActPlayText`. A differenza della tag `vgwAction`, un'espressione nel campo `output.text` non viene automaticamente riprodotta.
{: tip}

Nel seguente esempio più complesso, le azioni definite nella tag `vgwActionSequence` dicono al Voice Agent di disabilitare l'elaborazione da voce a testo e raccogliere l'input DTMF quando riproduce un'espressione.

```json
{
  "output": {
    "vgwActionSequence": [
      {
        "command": "vgwActPauseSTT"
      },
      {
        "command": "vgwActCollectDtmf",
        "parameters": {
          "dtmfTermKey": "#"
        }
      },
      {
        "command": "vgwActPlayText",
        "parameters": {
          "text": [
            "Enter your social security number."
          ]
        }
      }
    ]
  }
}

```
{: codeblock}

## Impostazione degli stati
{: #setting-states}

Per indicare una modifica di stato che rimane tra i turni di conversazione, il Voice Agent scambia le variabili di stato con il servizio {{site.data.keyword.conversationfull}} configurato. Queste variabili di stato sono definite in un nodo di dialogo {{site.data.keyword.conversationshort}} come [variabili di contesto](/docs/services/assistant?topic=assistant-dialog-build#dialog-build) nel formato JSON.

Ad esempio, puoi definire la seguente variabile di stato per impostare il messaggio che viene trasmesso al chiamante se la connessione al servizio {{site.data.keyword.conversationshort}} non riesce.

```json
{
  "context": {
    "vgwConversationFailedMessage": "Sorry, we're unable to connect you to our help line. Please try again later."
  }
}
```
{: codeblock}

Il Voice Agent presume che il servizio {{site.data.keyword.conversationshort}} è senza stato e che tutti gli stati vengono conservati dal Voice Agent tra gli scambi con il servizio {{site.data.keyword.conversationshort}}. Per ogni turno di conversazione in una chiamata, lo stato viene trasmesso al servizio {{site.data.keyword.conversationshort}} e restituito dal servizio nella sezione `context` dei messaggi REST.
