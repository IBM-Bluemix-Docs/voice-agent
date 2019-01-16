---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-03"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Criando o serviço

É possível criar uma instância de serviço do {{site.data.keyword.iva_full}} usando o catálogo do {{site.data.keyword.Bluemix_short}} ou com um comando `ibmcloud` do {{site.data.keyword.Bluemix_notm}}.
{: shortdesc}


## Criando o serviço a partir do catálogo
{: #catalog_create}

1. Acesse o [{{site.data.keyword.iva_short}} página do catálogo](https://cloud.ibm.com/catalog/services/voice-agent-with-watson).

   A página do catálogo possui informações sobre o serviço e seus planos de precificação. É possível mudar o valor **Nome do serviço**.

2. Clique em **Criar** para [criar um agente de voz por meio do painel _Gerenciar_](managing_create.html#config_instance).

## Criando o serviço da linha de comandos
{: #command_create}

1. [Instale o {{site.data.keyword.Bluemix_notm}} CLI](../cli/index.html#overview).

2. Execute o comando [`ibmcloud` ](../cli/idt/commands.html#idt-cli) que cria a instância de serviço do Agente de voz com o plano _Lite_:

   ```
   ibmcloud service create VoiceAgent _Lite_ "My Voice Agent Service"
   ```
   {: codeblock}
