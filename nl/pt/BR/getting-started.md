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

# Tutorial de introdução
{{site.data.keyword.iva_full}} ajuda a integrar um conjunto de serviços do Watson orquestrados com a rede telefônica usando o Protocolo de Inicialização de Sessão (SIP). Este tutorial descreve como configurar um agente cognitivo de voz que pode ser chamado em qualquer telefone.
{: shortdesc}

Assista a uma demonstração de como criar seu primeiro agente de voz neste tutorial do [{{site.data.keyword.iva_full_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/tv/building-voice-enabled-cognitive-applications-with-watson/).
{: tip}

## Antes de começar
{: #prereqs}

Crie uma nova conta ou efetue login em sua conta existente no [{{site.data.keyword.Bluemix_short}}](https://cloud.ibm.com/).

## Etapa 1: criando uma instância de serviço do {{site.data.keyword.iva_short}} no {{site.data.keyword.Bluemix_notm}}
{: #step1}

Na página do catálogo do [{{site.data.keyword.iva_short}}](https://cloud.ibm.com/catalog/services/voice-agent-with-watson), revise as informações de serviço e, então, clique em **Criar**.

Depois de criar o serviço, anote o terminal do agente de voz no painel _Introdução_. O URI SIP do terminal é necessário para a configuração do tronco SIP.

## Etapa 2: criando um tronco SIP para encaminhar chamadas para o {{site.data.keyword.iva_short}}
{: #step2}

1. Crie um tronco SIP por meio de qualquer um dos provedores suportados a seguir. Em seguida, associe um número de telefone ao seu
tronco SIP.

  * [NetFoundry](connect-SIP.html#NetFoundry-setup)
  * [Twilio](connect-SIP.html#twilio-setup)
  * [AT&T e outros provedores de entroncamento SIP](connect-SIP.html#att-other)
  * [Peering com {{site.data.keyword.iva_short}}](connect-SIP.html#peering)

## Etapa 3: criando e conectando o seu agente de voz
{: #step3}

1. Acesse o painel _Gerenciar_ no painel {{site.data.keyword.iva_short}} e clique em **Criar um agente de voz**.

2. Insira as configurações básicas para seu agente de voz:
  * **Nome:** um nome exclusivo para seu agente de voz, como `Suporte ao cliente`
  * **Número do telefone:** o número do telefone completo que você associou ao seu tronco SIP, incluindo
os códigos de país e de área. Por exemplo, para um número 800 dos Estados Unidos, especifique o número de telefone como 18883334444. O número do telefone pode ter espaços e caracteres + ( ) -.
  * **Descrição:** uma descrição opcional de seu uso
  * **Destino de transferência padrão:** um URI de terminação opcional para o qual as chamadas podem ser transferidas.

3. Crie as instâncias de serviço {{site.data.keyword.conversationshort}}, {{site.data.keyword.speechtotextshort}} e {{site.data.keyword.texttospeechshort}} para seu agente de voz. Você pode optar por criar um agente de voz com qualquer um dos métodos a seguir:
  * Clique em **Criar um agente de voz** para criar todos os serviços e um agente de voz com a configuração padrão em uma única etapa.
  * Ou clique em cada um dos nomes de serviço para criar os serviços sozinho. Em seguida, retorne para
o {{site.data.keyword.iva_short}} e crie um agente de voz separadamente.

   Se você criou manualmente uma instância de serviço {{site.data.keyword.conversationshort}}, inclua um diálogo para que seja possível testar seu agente de voz.  Para iniciar rapidamente, clone a [conversa de amostra ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) do GitHub e, em seguida, [importe a amostra](../conversation/configure-workspace.html#creating-workspaces) como uma área de trabalho:

   1. Na página GitHub de conversa de amostra, clique no número da linha `1` e selecione **... > Copiar linha**. Cole o texto copiado em um arquivo e salve-o como um arquivo JSON, como `voice-gateway-conversation-en.json`.
   2. Ative a ferramenta {{site.data.keyword.conversationshort}}. Na página _Áreas de trabalho_, clique
no ícone ![Importar área de trabalho](../conversation/images/workspace_import.png) e importe o arquivo JSON.

  Como alternativa, é possível [construir seu próprio diálogo](../conversation/dialog-build.html) para simular o ambiente de produção. No mínimo, seu diálogo deve conter um nó com a condição `conversation_start` e um nó com uma resposta padrão.


## Próximas etapas
{: #next}

Teste seu agente de voz ligando para seu número de telefone associado. Se você ouvir uma resposta, seu agente de voz está ativo!

Se você não ouvir uma resposta, poderá examinar seus logs de chamada e o uso do agente de voz no painel _Uso_. Consulte [Visualizando logs de uso e de chamada](logging.html).

É possível editar as configurações para o seu agente de voz, criar ou remover agentes de voz e incluir múltiplos locais de
serviço do Watson no seu agente de voz do painel _Gerenciar_. Para obter mais informações, consulte [Gerenciando agentes de voz](managing.html).

Também é possível definir configurações avançadas, como proteger sua conexão SIP de sua conta do Twilio. Consulte [Protegendo Conexões](secure-trunking.html).
