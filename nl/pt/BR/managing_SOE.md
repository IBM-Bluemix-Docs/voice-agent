---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Configurando o {{site.data.keyword.conversationshort}} com um mecanismo de orquestração de serviço
{: #conversation_va}

Como uma alternativa à configuração de uma instância de serviço do {{site.data.keyword.conversationshort}}, é possível se conectar a um mecanismo de orquestração de serviço (SOE).
{: shortdesc}

É possível se conectar a uma área de trabalho do {{site.data.keyword.conversationshort}} por meio de um [ mecanismo de orquestração de serviço (SOE) ](/docs/services/voice-agent?topic=voice-agent-about#arch-soe). Um SOE intercepta mensagens para e do serviço para que seja possível modificá-las usando APIs de terceiros.

## Configurando uma conexão com um SOE
{: #how-to-SEO}

1. Na guia _Agente de voz_ na página _Gerenciar_ para o agente de voz, navegue para a seção de configuração do {{site.data.keyword.conversationshort}}.

1. Escolha **Mecanismo de orquestração de serviço** como o **Tipo de serviço**.

1. Selecione a **Região** para o **Tipo de serviço**.

1. No campo **URL**, insira a URL completa para sua área de trabalho SOE, por exemplo `https://iva-soesample.myorg.net/SOE/myWorkspace`. Até 256 caracteres podem ser inseridos
para a URL.

  **Importante**: para segurança de dados, assegure-se de usar uma URL segura para sua área de trabalho SOE usando `https:` em vez de `http:` e de requerer autenticação. Consulte [Segurança de informações e privacidade de dados](/docs/services/voice-agent?topic=voice-agent-infosec) para saber mais sobre considerações de segurança.

1. **Opcional** se seu SOE requerer autenticação (recomendado), insira o
nome do usuário e a senha nos campos respectivos, até 64 e 256 caracteres cada.
