---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Criando um agente de voz por meio do painel _Gerenciar_
{: #config_instance}

Depois de criar o serviço do {{site.data.keyword.iva_full}}, é possível criar agentes de voz individuais por meio do painel _Gerenciar_.
{: shortdesc}


## Criando um agente de voz
{: #create_instance}

Quando você cria um agente de voz, o {{site.data.keyword.iva_short}} procura automaticamente quaisquer instâncias de serviço do Watson disponíveis que possam ser usadas. Se um serviço não estiver disponível, será possível selecionar criá-los juntamente com o agente de voz ou conectar-se aos serviços em um espaço de conta {{site.data.keyword.Bluemix_short}} diferente. Também é possível optar por conectar o agente de voz a uma instância do mecanismo de orquestração de serviço, do Google Speech-to-Text ou do Google Text-to-Speech.

1. Acesse a guia _Agentes de voz_ no painel _Gerenciar_ e clique em **Criar um agente de voz**.

1. Para o **Nome**, especifique um nome exclusivo para seu agente de voz. Por exemplo, `Suporte ao Cliente - América do Norte`.

1. Para o **Número de telefone**, inclua o número do seu tronco SIP, incluindo os códigos de país e de área. Por exemplo, para um número 800 dos Estados Unidos, especifique o número de telefone como `18883334444`. O número de telefone pode ter espaços e os caracteres `+ ( ) -`.

1. Opcionalmente, descreva seu agente de voz.

1. Se desejar ativar a transferência de chamada, insira o URI de terminação para o **Destino padrão de transferência**. Consulte [Configurando a transferência de chamada](call-transfer.html) para obter informações sobre como configurar um URI de terminação. Não use um número de telefone pessoal para o destino de transferência.

1. Configure as conexões para as suas instâncias de serviço do Watson. É possível conectar múltiplas instâncias de serviço Watson configurando conexões para **Local 1** e **Local 2**. Ter conexões com múltiplas instâncias de serviço permite que seu agente de voz alterne para uma instância de serviço alternativa se ocorrer uma indisponibilidade. Consulte [Incluindo vários locais de serviço Watson](managing_disaster_recovery.html#add_location).

1. Em **{{site.data.keyword.conversationshort}}**, configure a conexão com a instância de serviço do {{site.data.keyword.conversationshort}} clicando em **Localização 1** ou **Localização 2** e ativando a localização selecionada. É possível usar as instâncias do {{site.data.keyword.conversationshort}} em contas do {{site.data.keyword.Bluemix_notm}} que você ou outra pessoa tem. É possível também conectar-se a qualquer uma dessas opções por meio de um mecanismo de orquestração de serviços.

   * Se você estiver criando um agente de voz na região de Dallas ou Washington DC e não tiver uma instância de serviço do {{site.data.keyword.conversationshort}}, será possível criar uma no menu **Instância de serviço**.
   * Como alternativa, é possível se conectar a outras origens de um diálogo do {{site.data.keyword.conversationshort}} ou se conectar a um SOE mudando o [**Tipo de serviço**](managing_other.html#other_service).
   * Se você deseja configurar múltiplos locais de serviço, clique na outra opção de local e selecione
**Ativar local** para configurar a conexão com a sua outra instância do
{{site.data.keyword.conversationshort}}. Consulte [Incluindo vários locais de serviço Watson](managing_disaster_recovery.html#add_location).

1. Em **{{site.data.keyword.speechtotextshort}}**, revise a configuração padrão para a instância de serviço do {{site.data.keyword.speechtotextshort}} selecionando **Localização 1** ou **Localização 2** e ativando esta localização. É possível customizar a configuração com o seguinte.
   * Para conectar o agente de voz a uma instância existente como o seu **Tipo de serviço**, escolha **Minha instância de fala para texto**. Em seguida, para **Selecionar tipo de modelo**, escolha **Banda estreita**, **Banda larga** ou **Banda larga e banda estreita** e, depois, selecione o **Modelo** de idioma.
   * Se você estiver criando um agente de voz na região de Dallas ou Washington DC e não tiver uma instância de serviço do {{site.data.keyword.speechtotextshort}}, será possível criar uma no menu **Instância de serviço**.
   * Para o **Tipo de serviço**, é possível escolher [ uma instância do {{site.data.keyword.speechtotextshort}} em uma área de trabalho diferente do {{site.data.keyword.Bluemix_notm}} ](managing_other.html) ou um [serviço de fala para texto de terceiro](managing_third_party.html), como o Google Cloud Speech-to-Text.
   * Se você deseja configurar múltiplos locais de serviço, clique na outra opção de local e selecione
**Ativar local** para configurar a conexão com a sua outra instância do
{{site.data.keyword.speechtotextshort}}. Consulte [Incluindo vários locais de serviço Watson](managing_disaster_recovery.html).

1. Em **{{site.data.keyword.texttospeechshort}}**, revise a configuração padrão para a instância de serviço do {{site.data.keyword.texttospeechshort}} clicando em **Localização 1** ou **Localização 2** e ativando esta localização. É possível customizar a configuração com o seguinte.
   * Se você estiver criando um agente de voz na região de Dallas ou Washington DC e não tiver uma instância de serviço do {{site.data.keyword.texttospeechshort}}, será possível criar uma no menu **Instância de serviço**.
   * Para o **Tipo de serviço**, é possível escolher uma instância do [{{site.data.keyword.texttospeechshort}} em uma área de trabalho diferente do {{site.data.keyword.Bluemix_notm}}](managing_other.html) ou um [serviço de texto para fala de terceiro](managing_third_party.html), como o Google Cloud Text-to-Speech.
   * Se você deseja configurar múltiplos locais de serviço, clique na outra opção de local e selecione
**Ativar local** para configurar a conexão com a sua outra instância do
{{site.data.keyword.texttospeechshort}}. Consulte [Incluindo vários locais de serviço Watson](managing_disaster_recovery.html).

1. Também é possível escolher ativar o encaminhamento de eventos para coletar informações sobre chamadas que são
manipuladas pelos seus agentes de voz em um {{site.data.keyword.cloudantfull}}. Consulte
[Ativando o encaminhamento de eventos para os agentes de voz](event-forwarding.html). Para obter mais opções de
configuração, consulte [Configurando um agente de voz](managing.html#configure_va).

1. Clique em **Criar agente de voz** para criar seu agente de voz e quaisquer serviços novos.

Depois de criar o agente de voz, teste-o ligando para seu número de telefone. É possível visualizar detalhes sobre seu telefonema no painel _Uso_.  
