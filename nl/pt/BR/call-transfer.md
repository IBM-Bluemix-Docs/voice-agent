---

copyright:
  years: 2018
lastupdated: "2018-06-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configurando a transferência de chamada
{: #call-transfer}

É possível configurar a transferência de chamada para que, se um responsável pela chamada solicitar falar com um agente em tempo real durante uma conversa, o agente de voz transfira automaticamente a chamada.
{: shortdesc}

## Sobre a transferência de chamada
{: #about-ct}

Ao ativar a transferência de chamada, se um responsável pela chamada solicitar falar com um agente em tempo real durante a conversa, o agente de voz redirecionará a chamada. É possível ativar a transferência de chamada configurando um URI de finalização na configuração do provedor SIP. Em seguida, defina
o destino de transferência em uma ação de API em um nó de diálogo da instância do {{site.data.keyword.conversationshort}}. O seu destino de transferência é um URI do SIP que contém o URI de finalização e o número do telefone. Para obter mais informações sobre ações suportadas e a customização dos agentes de voz, consulte [Programando
agentes de voz usando a API](api.html).

## Etapa 1: Configurando o URI de finalização
{: #termination-setup}

### Configurando um URI de finalização no NetFoundry
{: #termination-netfoundry}

Anote o número do telefone em sua [conta do NetFoundry ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson.netfoundry.io/watson-login){: new_window} para o qual deseja transferir. Posteriormente, é possível especificar esse número do telefone e o URI de finalização como o destino de transferência em seu diálogo de {{site.data.keyword.conversationshort}}. Não use um número de telefone pessoal.

É possível copiar o URI de finalização do NetFoundry a seguir para usá-lo no destino de transferência.

```
Dal.watson-va.netfoundry.net
```
{: codeblock}

Não é necessário configurar manualmente o URI de finalização na sua conta do NetFoundry ao [Configurar o {{site.data.keyword.conversationshort}} para transferência de chamada](#conversation-setup).

### Configurando um URI de finalização no Twilio
{: #termination-Twilio}

1. Em sua conta do Twilio, navegue para o painel _Entroncamento SIP elástico_ e selecione **Troncos**.

1. Escolha o tronco no qual deseja incluir a transferência de chamada selecionando um tronco existente ou criando um novo clicando no ícone **+**.

  * Se você criar um novo tronco, será necessário configurar a _URI de Tronco SIP_ no painel **Origem**.  Para obter mais informações, consulte [Conectando um tronco SIP](connect-SIP.html).

1. Selecione **Finalização** na barra de navegação e insira um nome para o URI de finalização.

  * Os nomes de URI de Rescisão deve ser exclusivo. O Twilio verifica automaticamente o nome que você escolher quanto à disponibilidade. Consulte [Configurações de finalização do tronco SIP ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.twilio.com/docs/api/sip-trunking/getting-started#termination){: new_window} para obter mais detalhes sobre os serviços do Twilio.

1. Na seção _Autenticação_, clique no ícone **+** para incluir um endereço IP do agente de voz na lista Acessar IP de controle.

  Inclua ambos os endereços IP a seguir:
   * 169.60.154.134 (região de serviço do Sul dos EUA)
   * 169.61.86.179 (região de serviço do Leste dos EUA)

1. Clique em **Salvar** para concluir a configuração do seu URI de finalização.

Anote o número do telefone e o URI de finalização para o qual você deseja transferir. Certifique-se de que o número de telefone não é um número de telefone pessoal. É possível usar o número de telefone e o URI de finalização para especificar o destino de transferência no diálogo {{site.data.keyword.conversationshort}}.


## Etapa 2: Configurando o {{site.data.keyword.conversationshort}} para transferência de chamada
{: #conversation-setup}

Para saber mais sobre como trabalhar no serviço {{site.data.keyword.conversationshort}}, consulte [Sobre o {{site.data.keyword.conversationshort}}](../conversation/index.html#about).

1. No painel {{site.data.keyword.Bluemix_notm}}, selecione a instância do {{site.data.keyword.conversationshort}} que seu agente de voz usa.

1. No painel _Introdução_, clique no botão **Ativar ferramenta**.

1. Clique em **Introdução** na área de trabalho que deseja editar.

1. Clique em **Incluir intenção** e insira um nome para a intenção, como _Transferir_.

  É possível inserir informações mais detalhadas ou retornar posteriormente para editar e refinar a intenção.

1. Depois de criar a intenção de transferência de chamada, selecione a guia _Diálogo_.

1. Clique em **Incluir nó** e insira um nome para o nó, como _Transferência de Chamada_.

1. Na seção _Se o robô reconhecer:_, digite **Intenção de transferência de chamada** para localizar a intenção que você fez.

1. Para a seção _Em seguida, responda com:_, clique no ícone **&vellip;** e selecione **Abrir editor JSON**. Copie e cole o fragmento de código a seguir para substituir o código no campo.

```json
{
    "output": {
        "text": {
            "values": [ "Please hold on while I connect you with a live agent." ],
     "selection_policy": "sequential"
        },
   "vgwAction": {
            "command": "vgwActTransfer",
     "parameters": {
                "transferTarget": "sip:18889990000\\@dal.watson-va.netfoundry.net"
            }
        }
    }
}
```
{: codeblock}

**Nota**: o URI SIP do destino de transferência inclui um número de telefone e o URI de finalização criados. Não use um número de telefone pessoal no destino de transferência. Por exemplo, se o número de telefone for `18889990000` e seu URI de finalização for `mysiptrunk.pstn.twilio.com`, o URI SIP completo será `sip:18889990000\\@mysiptrunk.pstn.twilio.com`. Se você usar o NetFoundry e tiver um número de telefone do `18889990000`, o URI do SIP completo será `sip:18889990000\\@dal.watson-va.netfoundry.net`.

## Próximas etapas
{: #Next}

Teste o seu agente de voz ligando para o seu número de telefone associado e use os termos principais que você identificou em sua
intenção. Se seu agente de voz redirecionar você, então, funcionou!

Agora, é possível refinar e configurar a intenção **Transferir** e o diálogo para responder aos principais termos e frases de sua escolha.
