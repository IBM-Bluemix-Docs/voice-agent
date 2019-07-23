---

copyright:
  years: 2019
lastupdated: "2019-06-24"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Criando um agente de voz
{: #config_instance}

Depois de criar o serviço do {{site.data.keyword.iva_full}}, é possível criar agentes de voz individuais por meio do painel _Gerenciar_.
{: shortdesc}

Quando você cria um agente de voz, o {{site.data.keyword.iva_short}} procura automaticamente quaisquer instâncias de serviço do Watson disponíveis que possam ser usadas. Se nenhuma instância de serviço estiver disponível, será possível criar uma junto com o agente de voz ou se conectar aos serviços em uma conta do {{site.data.keyword.Bluemix_short}} diferente. Também é possível optar por conectar o agente de voz a uma instância do mecanismo de orquestração de serviço, do Google Speech-to-Text ou do Google Text-to-Speech.

1. Acesse a guia _Agentes de voz_ no painel _Gerenciar_ e clique em **Criar um agente de voz**.

1. Para **Tipo de agente**, selecione _Voice_.

1. Para o **Nome**, especifique um nome exclusivo para seu agente de voz. Por exemplo, `Suporte ao Cliente - América do Norte`. O nome pode incluir até 64 caracteres.

1. Para o **Número de telefone**, inclua o número do seu tronco SIP, incluindo os códigos de país e de área. Por exemplo, para um número 800 dos Estados Unidos, especifique o número de telefone como `18883334444`. O número do telefone pode ter um máximo de 30 caracteres, incluindo espaços e caracteres + ( ) -.

1. Por padrão, esse número do telefone será configurado como o **Número primário** para o serviço; este é simplesmente o primeiro número mostrado para você quando você tem uma lista de números e é somente para propósitos de exibição. Para mudar o seu Número primário, consulte [Configurando o número primário](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

1. Opcionalmente, use até 256 caracteres para descrever o seu agente de voz.

1. É possível incluir múltiplos números em um Voice Agent, clicando em **Gerenciar**, próximo a **Número do telefone**. Consulte [Configurando vários números de telefone
em uma instância do agente de voz](/docs/services/voice-agent?topic=voice-agent-multi_num) para obter informações sobre como configurar e associar vários números. Também é possível editar os números e incluir descrições para os números individuais na caixa de diálogo Gerenciar.
    
1. Como alternativa, para editar os números, clique no campo **Número do telefone** esmaecido ou clique em **Gerenciar**. Para obter mais informações, consulte [Editando um número e/ou uma descrição para múltiplos números](/docs/services/voice-agent?topic=voice-agent-multi_num#edit_num).
    
1. Para ativar a transferência de chamada, insira o URI de finalização para o seu **Destino de transferência padrão**. Consulte [Configurando a transferência de chamada](/docs/services/voice-agent?topic=voice-agent-call-transfer) para obter informações sobre como configurar um URI de terminação. Não use um número de telefone pessoal para o destino de transferência. O URI de terminação **Destino de transferência padrão** pode incluir até 256 caracteres.
    
1. Configure as conexões para as suas instâncias de serviço do Watson. É possível conectar múltiplas instâncias de serviço Watson configurando conexões para **Local 1** e **Local 2**. Ter conexões com múltiplas instâncias de serviço permite que seu agente de voz alterne para uma instância de serviço alternativa se ocorrer uma indisponibilidade. Consulte [Incluindo vários locais de serviço Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).
    
1. Em **Conversa**, configure a conexão com a instância de serviço do {{site.data.keyword.conversationshort}} clicando em **Local 1** ou em **Local 2** e ativando o local que você selecionou. É possível usar as instâncias do serviço {{site.data.keyword.conversationshort}} nas contas do {{site.data.keyword.Bluemix_notm}} que você ou outra pessoa possui. É possível também conectar-se a qualquer uma dessas opções por meio de um mecanismo de orquestração de serviços.
    
   * Se você estiver criando um agente de voz na região de Dallas ou Washington DC e não tiver uma instância de serviço do {{site.data.keyword.conversationshort}}, será possível criar uma no menu **Instância de serviço**.
   * Como alternativa, é possível se conectar a outras origens de um diálogo do {{site.data.keyword.conversationshort}} ou a um SOE, mudando o [**Tipo de serviço**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service).
   * Se você desejar configurar múltiplos locais de serviço, clique na opção **outra localização** e selecione **Ativar localização** para configurar a conexão com a sua outra instância do {{site.data.keyword.conversationshort}}. Para obter mais informações, consulte [Incluindo múltiplos locais de serviço do Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).
    
1. Em **{{site.data.keyword.speechtotextshort}}**, revise a configuração padrão para a instância de serviço do {{site.data.keyword.speechtotextshort}} selecionando **Localização 1** ou **Localização 2** e ativando esta localização. É possível customizar a configuração com o seguinte.
   * Para conectar o agente de voz a uma instância existente como o seu **Tipo de serviço**, escolha **Minha instância de fala para texto**. Em seguida, para **Selecionar tipo de modelo**, escolha **Banda estreita**, **Banda larga** ou **Banda larga e banda estreita** e, depois, selecione o **Modelo** de idioma.
   * Se você estiver criando um agente de voz na região de Dallas ou Washington DC e não tiver uma instância de serviço do {{site.data.keyword.speechtotextshort}}, será possível criar uma no menu **Instância de serviço**.
   * Para o seu **Tipo de serviço**, é possível escolher [uma instância do {{site.data.keyword.speechtotextshort}} em uma área de trabalho do {{site.data.keyword.Bluemix_notm}} diferente](/docs/services/voice-agent?topic=voice-agent-other_service) ou um [serviço de fala para texto de terceiros](/docs/services/voice-agent?topic=voice-agent-third-party#third-party), como o Google Cloud Speech-to-Text.
   * Se você deseja configurar múltiplos locais de serviço, clique na outra opção de local e selecione
**Ativar local** para configurar a conexão com a sua outra instância do
{{site.data.keyword.speechtotextshort}}. Para obter mais informações, consulte [Incluindo múltiplos locais de serviço do Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery).
    
1. Em **{{site.data.keyword.texttospeechshort}}**, revise a configuração padrão para a instância de serviço do {{site.data.keyword.texttospeechshort}} clicando em **Localização 1** ou **Localização 2** e ativando esta localização. É possível customizar a configuração com o seguinte.
   * Se você estiver criando um agente de voz na região de Dallas ou Washington DC e não tiver uma instância de serviço do {{site.data.keyword.texttospeechshort}}, será possível criar uma no menu **Instância de serviço**.
   * Para o seu **Tipo de serviço**, é possível escolher uma [instância do {{site.data.keyword.texttospeechshort}} em uma área de trabalho do {{site.data.keyword.Bluemix_notm}} diferente](/docs/services/voice-agent?topic=voice-agent-other_service) ou um [serviço de texto para fala de
terceiros](/docs/services/voice-agent?topic=voice-agent-third-party), como o Google Cloud Text-to-Speech.
   * Se você deseja configurar múltiplos locais de serviço, clique na outra opção de local e selecione
**Ativar local** para configurar a conexão com a sua outra instância do
{{site.data.keyword.texttospeechshort}}. Consulte [Incluindo vários locais de serviço Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery).
      
1. Também é possível escolher ativar o encaminhamento de eventos para coletar informações sobre chamadas que são
manipuladas pelos seus agentes de voz em um {{site.data.keyword.cloudantfull}}. Consulte
[Ativando o encaminhamento de eventos para os agentes de voz](/docs/services/voice-agent?topic=voice-agent-event_forwarding). Para obter mais opções de
configuração, consulte [Configurando um agente de voz](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1. Clique em **Criar agente de voz** para criar seu agente de voz e quaisquer serviços novos.

Depois de criar o agente de voz, teste-o ligando para seu número de telefone. É possível visualizar detalhes sobre a sua interação no painel _Uso_. Para obter mais informações, consulte [Visualizando o uso e os logs](/docs/services/voice-agent?topic=voice-agent-logging).   
