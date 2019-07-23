---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-15"
subcollection: "voice-agent"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Gerenciando as instâncias de serviço e os agentes de voz
{: #managing}

É possível usar o painel _Gerenciar_ para mudar as configurações da instância de serviço e criar, editar, clonar, configurar ou remover agentes de voz individuais. É possível ter vários agentes de voz em sua instância de serviço e cada agente de voz pode ter até 1.000 números e descrições exclusivos. No entanto, cada agente de voz deve ter um nome exclusivo e pelo menos um número de telefone.

* **NOTA**: uma única instância de serviço do {{site.data.keyword.iva_full}} pode ter até 150 agentes de voz.
{: shortdesc}

## Navegando para o painel de serviço Agente de voz
{: #navigate_manage}

É possível localizar o painel _Gerenciar_ por meio do painel de serviço do {{site.data.keyword.iva_short}}.

1. Acesse a sua lista de recursos da conta do [{{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/resources).

1. Na lista de **Serviços**, selecione a instância de serviço do **Agente de voz** para abrir o painel de serviço na guia _Gerenciar_.

## Resumo do agente de voz
{: #agent_summary}

Se você já tiver um agente de voz existente, será possível ver um resumo de todos os números, descrições e definições de configuração para o agente. Para ver o resumo, clique no botão de seta suspensa à esquerda do **Nome** do agente de voz. O resumo será expandido.

Embora o agente de voz possa conter vários números, no resumo do agente, somente o **Número primário** é selecionado para ser mostrado. Por padrão, ele é o primeiro número incluído no
agente de voz, é somente para exibição e não tem propósito funcional. Se você desejar exibir um número
diferente do agente de voz, consulte [Gerenciando vários números](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

É possível visualizar todos os números no agente de voz no resumo do agente. Depois que o resumo da configuração for expandido, clique no botão **Visualizar números** e uma lista de todos
os números aparecerá em uma nova caixa de diálogo **Gerenciar**. Consulte a página [Gerenciando vários números](/docs/services/voice-agent?topic=voice-agent-multi_num) para
obter mais informações sobre como trabalhar com a caixa de diálogo **Gerenciar**.

## Editando o máximo de conexões simultâneas para a instância de serviço
{: #edit_service}

Em todos os planos, você recebe duas conexões simultâneas gratuitamente. Se você usar os planos _Padrão_ ou _Premium_, será possível [mudar o número máximo de conexões simultâneas](/docs/services/voice-agent?topic=voice-agent-edit_concurrency) nas configurações padrão por meio da guia _Instâncias_.

## Criando um agente de voz
{: #create_va}

[Crie um novo agente de voz](/docs/services/voice-agent?topic=voice-agent-config_instance) na guia _Agentes de voz_ no painel _Gerenciar_.

## Editando um agente de voz
{: #edit_va}

É possível mudar os agentes de voz existentes editando-os na guia _Agentes de voz_ no painel _Gerenciar_. Para editar um agente de voz, clique em **Editar agente** na lista de opções para o agente de voz. Mude a configuração e salve as mudanças.

## Clonando um agente de voz
{: #clone_va}

Ao clonar um agente de voz, todas as configurações para os serviços do Watson são copiadas para um novo agente. Para clonar um agente de voz, clique em **Clonar agente** na lista de opções para o agente de voz. Dê ao seu agente de voz um nome e número de telefone exclusivos, mude as opções de configuração conforme necessário e salve as mudanças.

## Excluindo um agente de voz
{: #delete_va}

Você pode querer excluir um agente de voz para liberar o número de telefone. É possível ter somente um agente de voz por número do telefone. Para usar um número de telefone para um agente de voz diferente, primeiro você deverá excluir qualquer agente de voz que estiver usando o número de telefone.

Para excluir um agente de voz, acesse a guia _Agentes de voz_, clique em **Excluir agente** na lista de opções para o agente de voz e salve as mudanças. O agente de voz é removido da lista de agentes de voz.

## Procurando um agente de voz por número ou por descrição
{: #search}

É possível procurar os agentes de voz com base nos números ou nas descrições salvos no agente.

Na barra de _Procura_, é possível digitar um número ou uma descrição. Conforme você digita, os resultados da pesquisa serão atualizados automaticamente.  

## Configurando um agente de voz
{: #configure_va}

Ao criar, clonar ou editar um agente de voz, é possível fazer mudanças nas definições de configuração para o agente de voz e as conexões com os serviços relacionados.

* **[Configurando vários números de telefone](/docs/services/voice-agent?topic=voice-agent-multi_num):** é possível configurar o seu agente de voz para incluir vários números de telefone.
* **[Configurando múltiplas localizações de serviço](/docs/services/voice-agent?topic=voice-agent-disaster-recovery):** inclua múltiplas localizações de serviço para os serviços conectados para suportar a redundância de serviço.
* **[Conectando-se a serviços de fala e texto de terceiro](/docs/services/voice-agent?topic=voice-agent-third-party):** em vez de usar o {{site.data.keyword.texttospeechshort}} ou o {{site.data.keyword.speechtotextshort}}, é possível conectar o agente de voz às APIs de terceiro, como o Google Cloud Speech-to-Text.
* **[Usando serviços em outras áreas de trabalho do {{site.data.keyword.Bluemix_notm}}](/docs/services/voice-agent?topic=voice-agent-other_service):** é possível configurar o seu agente de voz para usar as instâncias de serviço do {{site.data.keyword.conversationshort}}, do {{site.data.keyword.speechtotextshort}} ou do {{site.data.keyword.speechtotextshort}} que pertencem a áreas de trabalho em outras contas do {{site.data.keyword.Bluemix_short}}.
* **[Configurando o Watson Assistant com um Service Orchestration Engine](/docs/services/voice-agent?topic=voice-agent-conversation_va):** é possível conectar-se a uma qualificação do {{site.data.keyword.conversationshort}}
por meio de um service orchestration engine (SOE). Um SOE intercepta mensagens para e do serviço para que seja possível modificá-las usando APIs de terceiros.
* **[Ativando o encaminhamento de eventos para os agentes de voz](/docs/services/voice-agent?topic=voice-agent-event_forwarding):** você pode desejar coletar e analisar os dados da chamada por meio do {{site.data.keyword.iva_short}} para melhorar a naturalidade da conversa para o responsável pela chamada. Cada agente de voz que você cria pode encaminhar relatórios de eventos para um {{site.data.keyword.cloudant_short_notm}} especificado que você gerencia.

## Configurando as opções avançadas do agente de voz
{: #config-advanced}

Ao criar ou clonar um agente de voz, é possível clicar em **Mostrar avançado** para visualizar as
opções de configuração avançada a seguir.

* **Tempo limite de leitura de conversa (opcional)**: essa opção configura o tempo, em segundos, que o Voice Agent aguarda por uma resposta do Watson Assistant. Se o tempo for excedido,
o Voice Agent tentará novamente entrar em contato com o Watson Assistant. Se o serviço ainda não puder ser atingido, a chamada falhará. Configure como cinco segundos por padrão.
* **Mensagem de resposta de falha do {{site.data.keyword.conversationshort}} (opcional)**:
a mensagem de resposta padrão que será enviada para o receptor da mensagem se a chamada não puder se conectar ao {{site.data.keyword.conversationshort}}. É possível inserir até 1.024 caracteres.
* **Transferir mensagem de resposta de falha (opcional)**: a mensagem de resposta
padrão que será transmitida ao responsável pela chamada se a transferência de chamada falhar. É possível inserir até 1.024 caracteres.
* **Cabeçalho SIP INVITE customizado (opcional)**: especifica o cabeçalho SIP customizado a ser extraído de solicitações de entrada SIP INVITE. É possível inserir até 1.024 caracteres.
* **Enviar resposta de toque provisório do {{site.data.keyword.iva_short}}**: envia uma
resposta `180 ringing` enquanto o {{site.data.keyword.iva_short}} processa uma chamada de entrada. Ativado por padrão.
* **Colocar o responsável pela chamada em espera na transferência**: coloca o responsável pela chamada
em espera durante a transferência. Ativado por padrão.
* **Desconectar chamada na falha de transferência**: determina se a chamada será ou não desconectada se
uma transferência de chamada falhar.  Ativado por padrão. Se a configuração estiver desativada e uma transferência de chamada falhar,
o {{site.data.keyword.iva_short}} iniciará um turno de conversa. Em seguida, o {{site.data.keyword.conversationshort}}
poderá desconectar a chamada ou transferi-la para um destino diferente, conforme configurado no diálogo.
* **Notificar o {{site.data.keyword.conversationshort}} sobre eventos da rede**: quando ativado, e
um erro de rede for detectado, o {{site.data.keyword.iva_short}} iniciará um turno
para o serviço {{site.data.keyword.conversationshort}} com o texto "vgwNetworkWarningMessage". A variável de estado
`vgwNetworkWarnings` conterá uma lista dos eventos de rede que ocorreram durante o turno atual. Se desativado, uma
lista dos eventos de rede que ocorreram durante o turno atual será enviada no próximo evento de turno na variável de estado `vgwNetworkWarning`s. Ativado por padrão.
