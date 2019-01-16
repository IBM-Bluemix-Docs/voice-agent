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


# Gerenciando as instâncias de serviço e os agentes de voz
{: #managing}

É possível usar o painel _Gerenciar_ para mudar as configurações da instância de serviço e criar, editar, clonar, configurar ou remover agentes de voz individuais. É possível ter múltiplos agentes de voz na instância de serviço, mas cada agente de voz deve ter um nome e um número de telefone exclusivos.
{: shortdesc}

## Navegando para o painel de serviço Agente de voz
{: #navigate_manage}

É possível localizar o painel _Gerenciar_ por meio do painel de serviço do {{site.data.keyword.iva_short}}.

1. Acesse a sua lista de recursos da conta do [{{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/resources).

1. Na lista de **Serviços**, selecione a instância de serviço do **Agente de voz** para abrir o painel de serviço na guia _Gerenciar_.

## Editando o máximo de conexões simultâneas para a instância de serviço
{: #edit_service}

Em todos os planos, você recebe duas conexões simultâneas gratuitamente. Se você usar os planos _Padrão_ ou _Premium_, será possível [mudar o número máximo de conexões simultâneas](managing_concurrency.html) nas configurações padrão por meio da guia _Instâncias_.

## Criando um agente de voz
{: #create_va}

[Crie um novo agente de voz](managing_create.html) na guia _Agentes de voz_ no painel _Gerenciar_.

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

## Configurando um agente de voz
{: #configure_va}

Ao criar, clonar ou editar um agente de voz, é possível fazer mudanças nas definições de configuração para o agente de voz e as conexões com os serviços relacionados.

* **[Configurando múltiplas localizações de serviço](managing_disaster_recovery.html):** inclua múltiplas localizações de serviço para os serviços conectados para suportar a redundância de serviço.
* **[Conectando-se a serviços de fala e texto de terceiro](managing_third_party.html):** em vez de usar o {{site.data.keyword.texttospeechshort}} ou o {{site.data.keyword.speechtotextshort}}, é possível conectar o agente de voz às APIs de terceiro, como o Google Cloud Speech-to-Text.
* **[Usando os serviços em outras áreas de trabalho do {{site.data.keyword.Bluemix_notm}}](managing_other.html):** é possível configurar o agente de voz para usar as instâncias de serviço do {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.speechtotextshort}} que pertencem a áreas de trabalho em outras contas do {{site.data.keyword.Bluemix_short}}.
* **[Configurando o Watson Assistant com um mecanismo de orquestração de serviço](managing_SOE.html):** é possível se conectar a uma área de trabalho do {{site.data.keyword.conversationshort}} por meio de um mecanismo de orquestração de serviço (SOE). Um SOE intercepta mensagens para e do serviço para que seja possível modificá-las usando APIs de terceiros.
* **[Ativando o encaminhamento de eventos para os agentes de voz](event-forwarding.html):** você pode desejar coletar e analisar os dados da chamada por meio do {{site.data.keyword.iva_short}} para melhorar a naturalidade da conversa para o responsável pela chamada. Cada agente de voz que você cria pode encaminhar relatórios de eventos para um {{site.data.keyword.cloudant_short_notm}} especificado que você gerencia.

## Configurando as opções avançadas do agente de voz
{: #config-advanced}

Ao criar ou clonar um agente de voz, é possível clicar em **Mostrar avançado** para visualizar as
opções de configuração avançada a seguir.

* **Mensagem de resposta de falha do {{site.data.keyword.conversationshort}} (opcional)**:
a mensagem de resposta padrão que será enviada para o receptor da mensagem se a chamada não puder se conectar ao {{site.data.keyword.conversationshort}}.
* **Transferir mensagem de resposta de falha (opcional)**: a mensagem de resposta
padrão que será transmitida ao responsável pela chamada se a transferência de chamada falhar.
* **Cabeçalho customizado SIP INVITE (opcional)**: especifica o cabeçalho SIP customizado para extração de solicitações SIP INVITE recebidas
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
