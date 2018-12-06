---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-11"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configurando múltiplas localizações de serviço
{: #disaster-recovery}

É possível conectar o agente de voz a múltiplos serviços em diferentes localizações para a redundância de serviço. A segunda localização não é um segundo agente de voz, ela age somente como um backup.
{: shortdesc}

Se você usar um plano _Lite_ para a instância do agente de voz, será possível conectar o tronco SIP a apenas um terminal, em que a instância do agente de voz é criada. Como o plano _Lite_ fornece conexões para apenas uma localização, é possível fornecer redundâncias para os serviços conectados, mas não para o agente de voz. Se ocorrer uma indisponibilidade de serviço na localização do agente de voz, as chamadas não poderão ser direcionadas para uma localização secundária.
{: tip}

## Incluindo serviços redundantes
{: #add_redundant}

É possível incluir uma localização de serviço do Watson ou de terceiro na configuração do agente de voz editando-o a qualquer momento.

1. Para incluir um serviço redundante em um agente de voz existente, navegue para a guia _Agentes de voz_ no painel _Gerenciar_. Clique em **Editar agente** para o agente de voz que deseja configurar.

1. Escolha **Localização 1** ou **Localização 2** para o serviço do {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} ou {{site.data.keyword.speechtotextshort}} que você deseja conectar e inclua as informações de configuração. É possível usar serviços de terceiro ou instâncias de serviço do Watson na sua área de trabalho ou em outras áreas de trabalho. Consulte [Usando instâncias de serviço em outras áreas de trabalho do {{site.data.keyword.Bluemix_notm}}](managing_other.html).

**Lembre-se**: para redundância de serviço, deve-se usar as instâncias de serviço do Watson em
diferentes regiões de serviço para diferentes locais.

É possível ativar ou desativar um local usando a caixa **Ativar local**. **Local 1** é
ativado por padrão e **Local 2** é desativado por padrão. Pelo menos um local deve ser ativado para cada serviço
do Watson.

## Incluindo vários serviços locais do Watson
{: #add_location}

O agente de voz usa as instâncias de serviço do Watson em ordem de distância geográfica. Por exemplo, é possível criar um agente de voz na região de Washington DC e os serviços do {{site.data.keyword.conversationshort}} em Dallas e Sydney, Austrália. O agente de voz usa a região de Dallas do {{site.data.keyword.conversationshort}} porque Dallas é geograficamente mais próxima de Washington DC do que Sydney. Ao se conectar a serviços do Watson em múltiplas regiões, se um serviço do Watson estiver off-line em um
local, o seu agente de voz poderá usar o serviço redundante.
