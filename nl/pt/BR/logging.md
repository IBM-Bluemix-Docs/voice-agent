---

copyright:
  years: 2018
lastupdated: "2018-11-12"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Visualizando o uso e chame logs
{: #logging}

É possível visualizar o histórico de uso e os logs de chamada para seus agentes de voz no painel {{site.data.keyword.Bluemix_notm}}.
{: shortdesc}

## Sobre a criação de log

A criação de log é automaticamente ativada para o {{site.data.keyword.iva_full}}. É possível visualizar os logs de chamada do agente de voz no painel _Uso_.

O painel _Uso_ mostra estatísticas rápidas sobre o uso do serviço e os recursos restantes disponíveis em seu plano. Essas informações incluem o número máximo de conexões simultâneas que são encontradas no mês atual e o número máximo de conexões
simultâneas disponíveis em seu plano. Na caixa _Minutos de chamada_, é possível ver o número de minutos gratuitos incluídos no plano e o número de minutos usados. A seção _Logs de chamada_ segue suas _Estatísticas rápidas_.

É possível filtrar _Logs de chamada_ e _Minutos de chamada_ por data e por nome ou número do agente de voz para reduzir o número de chamadas exibidas e isolar os logs de chamada específicos. Além disso, é possível filtrar _Logs de chamada_ para exibir apenas chamadas com falha.

Para saber mais sobre como criar e editar agentes de voz, consulte [Gerenciando agentes de voz](/docs/services/voice-agent?topic=voice-agent-managing).

##  Visualizando logs de chamada

1. De seu painel {{site.data.keyword.iva_short}}, navegue até o painel _Uso_ para visualizar as _Estatísticas rápidas_ e os _Logs de chamada_. Cada linha na tabela _Logs de chamada_ corresponde a uma chamada.

      Para cada chamada, é possível ver o nome e o número de telefone do seu agente de voz, os horários de início e término e a duração da chamada. É possível também ver o símbolo de aviso ao lado do nome do agente de voz, que indica que a chamada falhou.

1.  É possível filtrar a lista de chamadas visualizando chamadas em uma data específica e filtrando chamadas pelo nome ou número do agente de voz. Também é possível escolher exibir apenas chamadas com falha.

1. Para acessar os logs de falha de uma chamada individual, clique nos pontos na coluna **Ações** dessa chamada para expandir o menu. Em seguida, escolha **Logs de falha**. Essa opção aparece apenas para chamadas com falha.

1. É possível examinar a lista detalhada de logs de mensagens na nova visualização usando os seguintes métodos:
  * Procure a falha logs
  * Filtre as mensagens com base no tipo de log, **Erro** ou **Aviso**
  * Faça download do seu conjunto de dados
  * Classifique os logs de falha por registro de data e hora crescente ou decrescente

1. Para visualizar qualquer mensagem de log de falha em detalhes, clique na seta no início da linha na qual você está
interessado para expandir a visualização. É possível visualizar informações mais detalhadas sobre mensagens de log em [Mensagens do sistema Voice Gateway](https://www.ibm.com/support/knowledgecenter/SS4U29/messages.html){:new_window}.

1. Clique na seta para voltar no início da página para retornar ao painel _Uso_.

## Links relacionados
Leia informações mais detalhadas sobre a criação de log em [Resolução de problemas](https://www.ibm.com/support/knowledgecenter/SS4U29/troubleshooting.html){:new_window}, na documentação do IBM Voice Gateway.
