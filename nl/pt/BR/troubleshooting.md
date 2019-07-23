---

copyright:
  years: 2017, 2018
lastupdated: "2018-06-14"
subcollection: "voice-agent"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Resolução de Problemas e Suporte
{: #troubleshooting}

Tendo problemas com {{site.data.keyword.iva_full}}? Revise as dicas de resolução de problemas para problemas comuns e chegue até a comunidade com quaisquer perguntas.
{: shortdesc}

## Como resolver {{site.data.keyword.iva_short}}
{: #how-to}

Para solucionar problemas com os seus agentes de voz, é possível utilizar a criação de log, o uso e o encaminhamento de
eventos para localizar registros de erros e falhas. Esses registros podem ajudá-lo a diagnosticar e resolver problemas com os seus
agentes de voz. Se você estiver tendo problemas com o {{site.data.keyword.iva_short}}, tente as etapas a seguir.

1. Quando uma chamada falhar, o turno final do {{site.data.keyword.conversationshort}} poderá explicar a falha.

1. Logs de uso mostram quaisquer erros que possam ter ocorrido durante uma chamada específica. Consulte [Visualizando logs de uso e de chamada](/docs/services/voice-agent?topic=voice-agent-logging).

1. Verifique os logs do provedor de serviços para erros de sinalização. Por exemplo, o Twilio fornece logs para cada tronco SIP
que hospeda.

1. Ao [ativar o encaminhamento de eventos para os agentes de voz](/docs/services/voice-agent?topic=voice-agent-event_forwarding), é possível
configurar o seu agente de voz para encaminhar os registros de detalhe de chamada (CDRs) para um banco de dados do
Cloudant e então determinar por que uma chamada falhou. Outros eventos, como os eventos de turno do
{{site.data.keyword.conversationshort}} podem fornecer detalhes sobre cada turno de conversa dentro de uma chamada.

**Importante:** o CDR, a transcrição e os eventos de turnos incluem informações de seus usuários que podem potencialmente conter dados de Informação Protegida de Saúde (PHI), Informações Pessoalmente Identificáveis (PII) ou Padrão de Segurança de Dados PCI (PCI DSS). Para evitar a exposição de informações pessoais, deve-se assegurar que a instância do {{site.data.keyword.cloudant_short_notm}} proteja adequadamente as informações confidenciais que seus usuários compartilham na conversa ou durante a conversa.


## Obtendo ajuda
{: #help}

Se você precisar de ajuda, associe-se à nossa comunidade do desenvolvedor postando as suas perguntas ou comentários em
qualquer um dos lugares a seguir, que são todos monitorados ativamente.

* Poste no [fórum dwAnswers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/topics/voice-agent/) com a tag `voice-agent`
* Poste no [StackOverflow ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://stackoverflow.com/questions/tagged/voice-agent){: new_window} com a tag `voice-agent`
* Encontre-nos no Slack na equipe do [IBM Cloud Technology ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://slack-invite-ibm-cloud-tech.mybluemix.net/) no canal `#ibmvoicegateway`

**Lembre-se**: antes de postar quaisquer logs ou registros de chamadas, remova todas as informações pessoais
que os responsáveis pela chamada e os usuários podem ter compartilhado durante a conversa.

## Dicas de resolução de problemas
{: #troubleshooting-tips}

### Por que eu não recebo uma resposta no telefone quando ligo para meu agente de voz?

Sua chamada provavelmente não se conectou aos serviços. Esse problema ocorre quando a instância de serviço {{site.data.keyword.iva_short}} não está configurada corretamente. Verifique as configurações do agente de voz a seguir:

* Verifique se o número do telefone no painel _Gerenciar_ do agente de voz é o mesmo número do telefone do
seu provedor de entroncamento SIP, como NetFoundry ou Twilio.

   **Nota:** deve-se incluir o código de país e de área ao especificar o número do telefone no
painel _Gerenciar_ do agente de voz. Por exemplo, `18884253968`.

* Verifique se as credenciais de serviço do Watson, as URLs e o ID da área de trabalho do {{site.data.keyword.conversationshort}} são todas válidas.
* Verifique se o diálogo em sua qualificação do {{site.data.keyword.conversationshort}} foi criado corretamente.
  * É possível importar a [conversa de amostra ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/WASdev/sample.voice.gateway/blob/master/conversation/voice-gateway-conversation-en.json) do GitHub para obter uma qualificação pré-construída. Consulte a [Etapa 3 no *Tutorial de introdução*](/docs/services/voice-agent?topic=voice-agent-getting-started#step3) para obter detalhes sobre como salvar a conversa de amostra como um arquivo JSON e, em seguida, importar o arquivo como uma qualificação na ferramenta {{site.data.keyword.conversationshort}}.
  * Se você criou o seu próprio diálogo {{site.data.keyword.conversationshort}}, verifique se o diálogo
contém um nó com a condição `conversation_start` e um nó com uma resposta padrão. Para obter instruções detalhadas, consulte [Construindo um diálogo](/docs/services/assistant?topic=assistant-getting-started#getting-started-build-dialog) na documentação do {{site.data.keyword.conversationshort}}.
* Veja se seu telefonema está listado no painel _Uso_ do agente de voz. Se você vir um item para seu telefonema, então, seu agente de voz conectou ao serviço do Watson.

### Por que eu não posso especificar um número de telefone quando crio um agente de voz?

Veja se o número do telefone especificado é usado por um agente de voz existente. É possível ter apenas um agente de voz para um número de telefone. É possível fornecer outro número de telefone do seu provedor de entroncamento SIP e usá-lo para criar outro agente de voz. Ou [exclua o agente de voz existente no painel _Gerenciar_](/docs/services/voice-agent?topic=voice-agent-managing#delete_va) para liberar o número do telefone e, em seguida, crie um novo agente de voz.

### Por que meus telefonemas falhando frequentemente?

Os agentes de voz podem ter problemas quando as chamadas falham porque um mecanismo de orquestração de serviço (SOE) inicia uma
transação longa e não responde ao seu agente de voz em tempo hábil. Se uma transação exceder o tempo limite padrão do
{{site.data.keyword.conversationshort}}, a chamada falhará. Para evitar falhas de chamada, o SOE pode modificar o
tempo limite padrão do {{site.data.keyword.conversationshort}} usando a variável de estado `vgwConversationResponseTimeout`. Consulte [Variáveis configuradas no {{site.data.keyword.conversationshort}} diálogo](https://www.ibm.com/support/knowledgecenter/SS4U29/api.html#variables-conv).


### Várias limitações

* É possível criar novas instâncias de serviço do Watson diretamente por meio do painel _Criar um agente de voz_ para as regiões **Dallas** ou **Washington DC**. Para conectar o seu agente de voz aos serviços do Watson em outras regiões, crie
os seus serviços do Watson antes de criar um agente de voz no painel _Gerenciar_.

* Apenas conexões com a rede de telefonia comutada pública (PSTN) são suportadas.

* Todas as configurações do agente de voz devem ser especificadas no serviço do {{site.data.keyword.conversationshort}} que usa a API.
