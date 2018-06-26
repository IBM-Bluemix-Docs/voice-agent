---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Gerenciando agentes de voz
{: #managing}

É possível criar, editar, clonar, configurar e remover agentes de voz no painel _Gerenciar_. É possível ter vários agentes de voz, mas cada um deles deve ter um nome e número de telefone exclusivos.
{: shortdesc}

<!-- Title should be task oriented and descriptive-->

## Criando um agente de voz
{: #config_instance}

Quando você cria um agente de voz, o {{site.data.keyword.iva_short}} procura automaticamente quaisquer instâncias de serviço do Watson disponíveis que possam ser usadas. Se um serviço não estiver disponível, será possível selecionar criá-los juntamente com o agente de voz ou conectar-se aos serviços em um espaço de conta {{site.data.keyword.Bluemix_short}} diferente.

1. Clique em **Criar um agente de voz**.

1. Para o **Nome**, especifique um nome exclusivo para seu agente de voz. Por exemplo, `Suporte ao Cliente - América do Norte`.

1. Para o **Número de telefone**, inclua o número do seu tronco SIP, incluindo os códigos de país e de área. Por exemplo, para um número 800 dos Estados Unidos, especifique o número de telefone como `18883334444`. O número de telefone pode ter espaços e os caracteres `+ ( ) -`.

1. Opcionalmente, descreva seu agente de voz.

1. Configure as conexões para as suas instâncias de serviço do Watson. É possível se conectar a múltiplas instâncias de serviços
do Watson configurando conexões para o **Local 1** e o **Local 2**. Ter conexões com
múltiplas instâncias de serviço permite que o seu agente de voz alterne para uma instância de serviço alternativa se uma
indisponibilidade ocorrer. Consulte [Incluindo vários locais de serviço Watson](#add_location).

**Importante**: as contas de _Avaliação_ e _Lite_ podem se conectar apenas ao
local em que a sua instância do serviço {{site.data.keyword.iva_short}} é criada. O seu segundo local não é um
segundo agente de voz. Ele atua apenas como um backup para recuperação de desastre.

1. Em **{{site.data.keyword.conversationshort}}**, configure a conexão com a sua instância de
serviço do {{site.data.keyword.conversationshort}} clicando em **Ativar local 1** ou
**Ativar local 2**. É possível usar instâncias do {{site.data.keyword.conversationshort}} ou
instâncias do {{site.data.keyword.virtualagentfull}} em contas do {{site.data.keyword.Bluemix_notm}} que pertençam a
você ou a outra pessoa. É possível também conectar-se a qualquer uma dessas opções por meio de um mecanismo de orquestração de serviços.

    * Se você estiver criando um agente de voz na região sul dos EUA e não tiver uma instância do serviço
{{site.data.keyword.conversationshort}}, poderá criar uma no menu **Instância de serviço**.
    * Como alternativa, é possível conectar-se a outras fontes de um diálogo {{site.data.keyword.conversationshort}} mudando o [**Tipo de serviço**](#other_service).
    * Se você deseja configurar múltiplos locais de serviço, clique na outra opção de local e selecione
**Ativar local** para configurar a conexão com a sua outra instância do
{{site.data.keyword.conversationshort}}. Consulte [Incluindo vários locais de serviço Watson](#add_location).

1. Em **{{site.data.keyword.speechtotextshort}}**, revise a configuração padrão para a sua instância
do serviço {{site.data.keyword.speechtotextshort}} clicando em **Ativar local 1** ou **Ativar
local 2**. Se você estiver criando um agente de voz na região sul dos EUA e não tiver uma instância do serviço
{{site.data.keyword.speechtotextshort}}, crie uma no menu **Instância de serviço**. Ou, é possível conectar seu agente de voz a uma instância {{site.data.keyword.speechtotextshort}} em um espaço de conta {{site.data.keyword.Bluemix_notm}} diferente mudando o [**Tipo de serviço**](#other_service). {{site.data.keyword.iva_short}} suporta apenas modelos estreita.

    Se você deseja configurar múltiplos locais de serviço, clique na outra opção de local e selecione
**Ativar local** para configurar a conexão com a sua outra instância do
{{site.data.keyword.speechtotextshort}}. Consulte [Incluindo vários locais de serviço Watson](#add_location).

1. Em **{{site.data.keyword.texttospeechshort}}**, revise a configuração padrão para a sua instância
do serviço {{site.data.keyword.texttospeechshort}} clicando em **Ativar local 1** ou **Ativar
local 2**. Se você estiver criando um agente de voz na região sul dos EUA e não tiver uma instância do serviço
{{site.data.keyword.texttospeechshort}}, poderá criar uma no menu **Instância de serviço**. Ou, é possível conectar seu agente de voz a uma instância {{site.data.keyword.texttospeechshort}} em um espaço de conta {{site.data.keyword.Bluemix_notm}} diferente mudando o [**Tipo de serviço**](#other_service).

    Se você deseja configurar múltiplos locais de serviço, clique na outra opção de local e selecione
**Ativar local** para configurar a conexão com a sua outra instância do
{{site.data.keyword.texttospeechshort}}. Consulte [Incluindo vários locais de serviço Watson](#add_location).

1. Também é possível escolher ativar o encaminhamento de eventos para coletar informações sobre chamadas que são
manipuladas pelos seus agentes de voz em um {{site.data.keyword.cloudantfull}}. Consulte
[Ativando o encaminhamento de eventos para os agentes de voz](event-forwarding.html). Para obter mais opções de
configuração, consulte [Configurando um agente de voz](#configure_va).

1. Clique em **Criar agente de voz** para criar seu agente de voz e quaisquer serviços novos.

Depois de criar o agente de voz, teste-o ligando para seu número de telefone. É possível visualizar detalhes sobre seu telefonema no painel _Uso_.  

## Editando o máximo de conexões simultâneas
{: #edit_concurrency}

Se você usar o plano _Padrão_, poderá mudar o número máximo de conexões simultâneas das configurações
padrão. Em todos os planos, você recebe duas conexões simultâneas gratuitamente. Para obter mais informações, consulte os
[Planos de precificação](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

No painel _Gerenciar_, é possível ver o número máximo de conexões simultâneas que são permitidas em seu
plano listado em **Máximo de conexões simultâneas**. Também é possível ver o número máximo de conexões simultâneas
que são usadas por seus agentes de voz durante o mês atual em **Máximo de conexões simultâneas usadas**.

Se você deseja mudar o número máximo de conexões simultâneas em seu plano, clique no ícone **Editar**. Na
janela _Editar máximo de conexões simultâneas_, escolha o número máximo de conexões simultâneas e clique em **Salvar**. 
O número mínimo de conexões simultâneas que pode ser configurado por meio de autoatendimento é 10 e o máximo é 50. Se você precisar
de mais de 50 conexões simultâneas para o seu agente de voz, consulte [Solicitando
configuração de rede assistida](connect-SIP.html#request-setup).

### Informações de conexão simultânea
{: #concurrent-charge}

  * Os planos _Lite_, _Avaliação_ e _Padrão_ incluem duas conexões simultâneas
gratuitamente.
  * Os planos _Premium_ são customizados por instância.
  * Em uma conta _Padrão_, você tem uma capacidade mínima de 10 conexões simultâneas.
  * O uso de conexão simultânea é rateado por mês. Se você usar mais de duas conexões simultâneas em um dia, uma
taxa diária será cobrada.
  * Se você tiver um plano _Padrão_ ou _Premium_, será possível comprar uma maior
capacidade de conexão simultânea.
  * Uma taxa diária é cobrada para a capacidade máxima de conexões simultâneas usadas em um dia. Por exemplo, como o seu
plano suporta duas conexões simultâneas gratuitas e você configura um limite máximo de 12 conexões, se você usar apenas cinco em um
dia, você será cobrado por três.

Para obter mais informações sobre planos, taxas e recursos, consulte
[Planos de precificação](https://console.bluemix.net/catalog/services/voice-agent-with-watson).

## Editando um agente de voz
{: #edit_va}

É possível mudar agentes de voz existentes editando-os. Para editar um agente de voz, clique em **Editar agente** na lista de opções para o agente de voz. Mude a configuração e salve as mudanças.

## Clonando um agente de voz
{: #clone_va}

Ao clonar um agente de voz, todas as configurações para os serviços do Watson são copiadas para um novo agente. Para clonar um agente de voz, clique em **Clonar agente** na lista de opções para o agente de voz. Dê ao seu agente de voz um nome e número de telefone exclusivos, mude as opções de configuração conforme necessário e salve as mudanças.

## Excluindo um agente de voz
{: #delete_va}

Você pode querer excluir um agente de voz para liberar o número de telefone. É possível ter apenas um agente de voz para um número de telefone. Para usar um número de telefone para um agente de voz diferente, primeiro você deverá excluir qualquer agente de voz que estiver usando o número de telefone.

Para excluir um agente de voz, clique em **Excluir agente** na lista de opções para o agente de voz e salve as mudanças. O agente de voz é removido da lista de agentes de voz.

## Configurando um agente de voz
{: #configure_va}

### Configurando opções avançadas
{: #config-advanced}

Ao criar ou clonar um agente de voz, é possível clicar em **Mostrar avançado** para visualizar as
opções de configuração avançada a seguir.

* **Mensagem de resposta de falha do {{site.data.keyword.conversationshort}} (opcional)**:
a mensagem de resposta padrão que será enviada para o receptor da mensagem se a chamada não puder se conectar ao {{site.data.keyword.conversationshort}}.
* **Transferir mensagem de resposta de falha (opcional)**: a mensagem de resposta
padrão que será transmitida ao responsável pela chamada se a transferência de chamada falhar.
* **Enviar resposta de toque provisório do {{site.data.keyword.iva_short}}**: envia uma
resposta `180 ringing` enquanto o {{site.data.keyword.iva_short}} processa uma chamada de entrada. Ativado por padrão.
* **Colocar o responsável pela chamada em espera na transferência**: coloca o responsável pela chamada
em espera durante a transferência. Ativado por padrão.
* **Desconectar chamada na falha de transferência**: determina se a chamada será ou não desconectada se
uma transferência de chamada falhar. Ativado por padrão. Se a configuração estiver desativada e uma transferência de chamada falhar,
o {{site.data.keyword.iva_short}} iniciará um turno de conversa. Em seguida, o {{site.data.keyword.conversationshort}}
poderá desconectar a chamada ou transferi-la para um destino diferente, conforme configurado no diálogo.
* **Notificar o {{site.data.keyword.conversationshort}} sobre eventos da rede**: quando ativado, e
um erro de rede for detectado, o {{site.data.keyword.iva_short}} iniciará um turno
para o serviço {{site.data.keyword.conversationshort}} com o texto "vgwNetworkWarningMessage". A variável de estado
`vgwNetworkWarnings` conterá uma lista dos eventos de rede que ocorreram durante o turno atual. Se desativado, uma
lista dos eventos de rede que ocorreram durante o turno atual será enviada no próximo evento de turno na variável de estado `vgwNetworkWarning`s. Ativado por padrão.

### Incluindo vários serviços locais do Watson
{: #add_location}

Se você tiver uma conta _Padrão_ ou _Premium_, será possível conectar o seu agente de voz a
múltiplos serviços do Watson em diferentes locais para redundância de serviço. As contas _Avaliação_ e
_Lite_ podem se conectar apenas ao local em que a sua instância do serviço {{site.data.keyword.iva_short}} é
criada. O seu segundo local não é um segundo agente de voz. Ele atua apenas como um backup para recuperação de desastre.

O agente de voz usa as instâncias de serviço do Watson em ordem de distância geográfica. Por exemplo, é possível criar um
agente de voz na região leste dos EUA e os seus serviços {{site.data.keyword.conversationshort}} no sul dos EUA
e em Sydney, Austrália. O seu agente de voz usa a região sul dos EUA do {{site.data.keyword.conversationshort}} porque ela é
geograficamente mais próxima do leste dos EUA do que Sydney. Ao se conectar a serviços do Watson em múltiplas regiões, se um serviço do Watson estiver off-line em um
local, o seu agente de voz poderá usar o serviço redundante.

É possível incluir um local de serviço do Watson na configuração do seu agente de voz a qualquer momento. Para obter
informações sobre como conectar múltiplas instâncias do local de serviço ao criar o seu agente de voz, consulte
[Criando um agente de voz](#creating).

Para incluir um local de serviço do Watson para um agente de voz existente, clique em **Editar agente**
para o agente de voz que você deseja configurar. Escolha **Local 1** ou **Local 2** para a
instância do {{site.data.keyword.conversationshort}}, {{site.data.keyword.texttospeechshort}} ou
{{site.data.keyword.speechtotextshort}} à qual deseja se conectar e inclua as informações da sua configuração. É possível
usar a instância de serviço do Watson em sua área de trabalho ou em outras áreas de trabalho. Consulte
[Usando instâncias de serviço em outras áreas de trabalho do {{site.data.keyword.Bluemix_notm}}](#other_services).

**Lembre-se**: para redundância de serviço, deve-se usar as instâncias de serviço do Watson em
diferentes regiões de serviço para diferentes locais.

É possível ativar ou desativar um local usando a caixa **Ativar local**. **Local 1** é
ativado por padrão e **Local 2** é desativado por padrão. Pelo menos um local deve ser ativado para cada serviço
do Watson.

### Usando instâncias de serviço em outras áreas de trabalho do {{site.data.keyword.Bluemix_notm}}
{: #other_service}

É possível configurar seu agente de voz para usar instâncias de serviço {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} ou {{site.data.keyword.speechtotextshort}} que pertencem a áreas de trabalho em outras contas do {{site.data.keyword.Bluemix_short}}. Para conectar o seu agente de voz a outras instâncias de serviço, é possível utilizar o nome de usuário e as credenciais de senha
ou uma chave API para as suas instâncias de serviço.

1. Selecione o seu **Tipo de serviço** e a sua **Região**.

1. Escolha um **Nome de usuário e senha** ou **Chave API** e insira as suas credenciais de
serviço.
  Para localizar esses valores, acesse a instância de serviço que você deseja configurar e selecione **Credenciais de serviço** e, em seguida, **Visualizar credenciais**.

  * **Nome de usuário e senha**: nos campos **URL**, **Nome do
usuário** e **Senha**, configure as credenciais para as suas instâncias de serviço do {{site.data.keyword.conversationshort}},
do {{site.data.keyword.speechtotextshort}} ou do {{site.data.keyword.texttospeechshort}}.
  * **Chave API**: nos campos **URL** e **Chave API**, configure as
credenciais para as suas instâncias de serviço do {{site.data.keyword.conversationshort}}, do
{{site.data.keyword.speechtotextshort}} ou do {{site.data.keyword.texttospeechshort}}.

  As credenciais não são seu nome de usuário e senha do {{site.data.keyword.Bluemix_notm}}, mas credenciais criptografadas para a instância de serviço específica.
  {:tip}

1. Digite as informações da instância de serviço.

  * **{{site.data.keyword.conversationshort}}:** No campo **ID da área de trabalho**, insira o ID da área de trabalho que deseja usar com seu agente de voz. Para localizar o ID da área de trabalho, ative a ferramenta e, na área de trabalho que você deseja integrar, clique no ícone Ações (**&vellip;**) e selecione **Visualizar detalhes**.

  * **{{site.data.keyword.speechtotextshort}}:** No campo **Modelo**, selecione o idioma da fala e o formato para seu serviço. {{site.data.keyword.iva_short}} suporta apenas modelos estreita.

  * **{{site.data.keyword.texttospeechshort}}:** No campo **Voz**, selecione o idioma e a voz que seu serviço usa. Deve-se especificar uma voz para o seu serviço.

**Lembre-se:** para que seu agente de voz funcione, deve-se configurar seu {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} e {{site.data.keyword.texttospeechshort}} para o mesmo idioma. Consulte [Idiomas suportados](about.html#supported-languages).

### Configurando o {{site.data.keyword.conversationshort}} para o seu agente de voz
{: #conversation_va}

Como uma alternativa para configurar uma instância de serviço {{site.data.keyword.conversationshort}}, é possível conectar-se a um mecanismo de orquestração de serviços (SOE) ou Watson {{site.data.keyword.virtualagentshort}}.

* **Mecanismo de orquestração de serviço**: conecte-se a uma área de trabalho {{site.data.keyword.conversationshort}} ou {{site.data.keyword.virtualagentshort}} por meio de um [mecanismo de orquestração de serviços (SOE)](about.html#arch-soe). Um SOE intercepta mensagens para e do serviço para que seja possível modificá-las usando APIs de terceiros.

  No campo **URL**, insira a URL completa para sua área de trabalho SOE, por exemplo `https://iva-soesample.myorg.net/SOE/myWorkspace`. Se seu SOE exigir autenticação (recomendado), insira o nome de usuário e a senha nos respectivos campos.

* **Watson {{site.data.keyword.virtualagentshort}}**: conecte-se a um robô de bate-papo {{site.data.keyword.virtualagentshort}} em vez de uma área de trabalho {{site.data.keyword.conversationshort}}. [{{site.data.keyword.virtualagentshort}}](../virtual-agent/getting-started.html#getting-started) é construído no serviço {{site.data.keyword.conversationshort}}, mas fornece recursos pré-treinados para que você possa começar com zero de experiência no aprendizado com máquina.

  No campo **URL**, insira a credencial da URL para {{site.data.keyword.virtualagentshort}}, como `https://api.ibm.com/virtualagent/run/api`. Para os campos **ID do cliente** e **Segredo do cliente**, insira as chaves de autenticação, que mapeiam para os campos de cabeçalho `X-IBM-Client-Id` e `X-IBM-Client-Secret` para chamadas API. No campo **ID do robô**, insira o ID para o robô usar para esse agente de voz. Para obter mais informações sobre como localizar esses valores, consulte [Publicando o
agente](../virtual-agent/publish.html) na documentação do {{site.data.keyword.virtualagentshort}}.
