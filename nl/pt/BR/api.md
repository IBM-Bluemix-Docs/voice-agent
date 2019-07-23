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

# Programando agentes de voz usando a API
{: #api}

É possível controlar o comportamento do seu agente de voz definindo tags de ação e variáveis de estado de dentro do serviço {{site.data.keyword.conversationfull}}. As tags de ação iniciam as ações realizadas pelo agente de voz durante uma sessão de conversa e as variáveis de estado definem as características do agente de voz que persistem durante toda a conversa, a menos que sofram mudanças.
{: shortdesc}

Como o {{site.data.keyword.iva_full}} é baseado no IBM Voice Gateway, a API funciona da mesma maneira. Se você estiver familiarizado com o Voice Gateway e o SMS Gateway, será possível usar as mesmas ações e variáveis de estado em seus diálogos do {{site.data.keyword.conversationshort}} com o {{site.data.keyword.iva_short}}. Consulte [Tags de ação e variáveis de estado na API do Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html) e na [API para o SMS Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/sms_api.html), respectivamente.
{: tip}

## Editando JSON na resposta do diálogo
{: #json-editor}

As ações e os estados são definidos em uma resposta do nó de diálogo no formato JSON. Para editar o código JSON, abra o editor JSON.

1. No painel {{site.data.keyword.Bluemix_short}}, selecione sua instância de serviço {{site.data.keyword.conversationshort}}.
1. Ative a ferramenta {{site.data.keyword.conversationshort}}.
1. Clique na qualificação que contém o diálogo que você deseja editar.
1. Acesse a guia **Dialog** e selecione o nó no qual deseja configurar uma ação ou estado.
1. Na resposta, clique no ícone ![Resposta avançada](../conversation/images/kabob.png) e selecione **Abrir editor JSON**.

Dentro do editor JSON, é possível definir ações na propriedade `output` e estados na propriedade `context` conforme descrito nas seções a seguir.

## Iniciando ações
{: #defining-actions}

Para iniciar ações no agente de voz durante uma chamada, é possível definir tags de ação em um nó de diálogo {{site.data.keyword.conversationshort}} no formato JSON na propriedade `output`. É possível definir uma única ação na tag `vgwAction` ou uma sequência de ações na tag `vgwActionSequence`. Cada ação consiste em uma propriedade `command`, seguida por uma propriedade `parameter` opcional para definir atributos para comandos que os requerem.

### Ações Simples
{: #single-actions}

Para executar uma única ação, defina a ação na tag `vgwAction` com todos os atributos de parâmetro necessários. No bloco `text` na propriedade `output`, é possível, opcionalmente, incluir uma elocução que o agente de voz reproduz após a ação ser executada.

A ação única a seguir na tag `vgwAction` diz ao agente de voz para desligar a chamada quando a resposta do nó for acionada. Como o comando `vgwActHangup` não tem parâmetros, nenhum é definido.
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

A ação a seguir diz para o agente de voz coletar entrada de dual-tone multi-frequency signaling (DTMF) e
reproduzir o texto definido para o responsável pela chamada.

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

### Sequências de Ação
{: #action-sequences}

Para executar uma ou mais ações em um único turno de conversa, é possível definir uma sequência de ações dentro da tag `vgwActionSequence` como uma lista JSON. As ações são executadas na ordem definida.

Diferentemente de ações únicas, para que o agente de voz reproduza uma elocução ao usar a tag `vgwActionSequence`, a lista de ações deve conter a ação `vgwActPlayText`. Em contraste com a tag `vgwAction`, uma elocução no campo `output.text` não é reproduzida automaticamente.
{: tip}

No exemplo mais complexo a seguir, as ações definidas na tag `vgwActionSequence` informam ao agente de voz
que desativem o processamento de fala para texto e coletem entrada DTMF enquanto reproduzem uma elocução.

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

## Configurando estados
{: #setting-states}

Para indicar uma mudança de estado que permanece entre turnos de conversas, o agente de voz troca variáveis de estado com o serviço {{site.data.keyword.conversationfull}} configurado. Essas variáveis de estado são definidas em um nó de diálogo de {{site.data.keyword.conversationshort}} como [variáveis de contexto](/docs/services/assistant?topic=assistant-dialog-build#dialog-build) no formato JSON.

Por exemplo, é possível definir a seguinte variável de estado para configurar a mensagem que será transmitida ao responsável pela chamada se a conexão com o serviço {{site.data.keyword.conversationshort}} falhar.

```json
{
  "context": {
    "vgwConversationFailedMessage": "Sorry, we're unable to connect you to our help line. Please try again later."
  }
}
```
{: codeblock}

O agente de voz assume que o serviço {{site.data.keyword.conversationshort}} é stateless e que todo o estado é mantido no agente de voz entre trocas com o serviço {{site.data.keyword.conversationshort}}. Para cada turno de conversa dentro de uma chamada, o estado é transmitido para o serviço {{site.data.keyword.conversationshort}}
e recebido de volta do serviço na seção `context` das mensagens REST.
