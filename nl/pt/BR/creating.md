---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Criando o serviço

{: shortdesc}
É possível criar uma instância de serviço do {{site.data.keyword.iva_full}} usando o
catálogo do {{site.data.keyword.Bluemix_short}} ou um comando `ibmcloud` do {{site.data.keyword.Bluemix_notm}}.

## Criando o serviço a partir do catálogo
{: #catalog_create}

1. Acesse o [{{site.data.keyword.iva_short}} página do catálogo](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

   A página do catálogo possui informações sobre o serviço e seus planos de precificação. É possível mudar o valor **Nome do serviço**.

2. Clique em **Criar**.

## Criando o serviço da linha de comandos
{: #command_create}

1. [Instale a CLI do {{site.data.keyword.Bluemix_notm}}](../../cli/reference/bluemix_cli/get_started.html).

2. Execute o [comando `ibmcloud`
](../../cli/reference/bluemix_cli/bx_cli.html#bluemix_cli) que cria a sua instância do serviço VoiceAgent com o plano de Experiência:

   ```
   ibmcloud service create VoiceAgent _Trial_ "My Voice Agent Service"
   ```
   {: codeblock}

## Próximas etapas
{: #next}

Criar o agente de voz pelo painel _Gerenciar_. Consulte [Gerenciando agentes de voz](managing.html).
