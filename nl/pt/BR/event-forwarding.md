---

copyright:
  years: 2019
lastupdated: "2019-01-30"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Ativando o encaminhamento de eventos para agentes de voz
{: #event_forwarding}

Também é possível escolher ativar o encaminhamento de eventos para coletar informações sobre chamadas que são manipuladas
pelos seus agentes de voz em um {{site.data.keyword.iva_full}} usando um serviço do banco de dados do {{site.data.keyword.cloudantfull}}.
{: shortdesc}

Talvez você queira coletar e analisar dados de chamada do {{site.data.keyword.iva_short}} para melhorar a naturalidade da conversa para o responsável pela chamada. Cada agente de voz que você cria pode encaminhar relatórios de eventos para um {{site.data.keyword.cloudant_short_notm}} especificado que você gerencia. Eventos relatados incluem os eventos do registro de detalhes da chamada (CDR), eventos de transcrição e relatórios de eventos de turnos. É possível aprender mais sobre os tipos de eventos que podem ser encaminhados em
[Eventos de relatório](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}.

Analisar dados desses eventos pode ajudá-lo a ajustar diálogos, refinar intenções e melhorar a experiência geral do responsável pela chamada.

Ao criar ou editar agentes de voz, é possível também escolher ativar o encaminhamento de eventos. Para obter mais detalhes sobre como criar e editar agentes de voz, consulte [Gerenciando agentes de voz](/docs/services/voice-agent?topic=voice-agent-managing). É necessário fornecer informações da conta do {{site.data.keyword.cloudant_short_notm}}, incluindo o nome e a senha da conta, para ativar o encaminhamento de eventos.

**Importante:** o CDR, a transcrição e os eventos de turnos incluem informações de seus usuários que podem potencialmente conter dados de Informação Protegida de Saúde (PHI), Informações Pessoalmente Identificáveis (PII) ou Padrão de Segurança de Dados PCI (PCI DSS). Para evitar a exposição de informações pessoais, deve-se assegurar que a instância do {{site.data.keyword.cloudant_short_notm}} proteja adequadamente as informações confidenciais que seus usuários compartilham na conversa ou durante a conversa. Consulte [Segurança de informações e privacidade de dados: encaminhamento de eventos](/docs/services/voice-agent?topic=voice-agent-infosec#event_forwarding) e [{{site.data.keyword.cloudant_short_notm}}: segurança](/docs/services/Cloudant/offerings?topic=cloudant-security#security).


## Ativando o encaminhamento de eventos
{: #enable-event-forwarding}

É possível ativar o encaminhamento de eventos quando você está criando ou editando seus agentes de voz no painel _Gerenciar_ no {{site.data.keyword.Bluemix_short}}.

1. Na seção **Encaminhamento de evento**, depois da seção de configuração para {{site.data.keyword.texttospeechshort}}, selecione **Ativar encaminhamento de evento**.

1. Selecione **Minha instância de serviço {{site.data.keyword.cloudant_short_notm}}** ou **Outra instância de serviço {{site.data.keyword.cloudant_short_notm}}**.
  * Se você estiver usando **Minha instância de serviço {{site.data.keyword.cloudant_short_notm}}**, selecione o nome da conta **{{site.data.keyword.cloudant_short_notm}} e o** nome de usuário nas listas.
  * Se você estiver criando um agente de voz na região de Dallas ou Washington DC e não tiver uma instância do serviço {{site.data.keyword.cloudant_short_notm}}, será possível criar uma no menu **Conta do Cloudant**.
  * Se você estiver usando **Outra instância de serviço do {{site.data.keyword.cloudant_short_notm}}**, insira o nome de usuário e a senha do {{site.data.keyword.cloudant_short_notm}} (com até 128 e 256 caracteres, respectivamente)
ou a chave de API para a conta (com até 64 caracteres).

1. Selecione **Ativar** para cada tipo de evento que você deseja encaminhar e, em seguida, escolha o banco de dados no qual deseja encaminhar os eventos.
  * Eventos do registro de detalhe de chamada (CDR)
  * Eventos de transcrição
  * Eventos de transformação

1. Visualize seu banco de dados para assegurar que o evento relate o encaminhamento corretamente.

## Links relacionados
{: #related-links-forwarding}
* [IBM Voice Gateway: Relatando eventos](https://www.ibm.com/support/knowledgecenter/SS4U29/reporting.html){:new_window}
* [Segurança de informações e privacidade de dados](/docs/services/voice-agent?topic=voice-agent-infosec)
* [{{site.data.keyword.cloudant_short_notm}}: segurança](/docs/services/Cloudant/offerings?topic=cloudant-security#security)
