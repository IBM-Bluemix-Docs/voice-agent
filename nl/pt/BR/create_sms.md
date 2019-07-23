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


# Criando um agente do SMS
{: #sms_config_instance}

Após você ter criado o seu serviço do {{site.data.keyword.iva_full}}, será possível criar agentes do sms individuais por meio do painel _Gerenciar_.
{: shortdesc}

1. Acesse a guia _Agentes de voz_ no painel _Gerenciar_ e clique em **Criar um agente de voz**.

1. Para **Tipo de agente**, selecione _SMS_.

1. Para o **Nome**, especifique um nome exclusivo para seu agente de voz. Por exemplo, `Suporte ao Cliente - América do Norte`. O nome pode incluir até 64 caracteres.

1. Para Número do telefone, inclua o número de seu tronco do SIP, incluindo os códigos de país e de área. Por exemplo, para um número 800 dos Estados Unidos, especifique o número de telefone como 18883334444. O número do telefone pode ter um máximo de 30 caracteres, incluindo espaços e caracteres + ( ) -. O SMS suporta apenas um número por usuário.

1. Sob **Provedor do SMS**, insira o nome do usuário, a senha e a URL de API para o seu provedor do SMS. Por exemplo, se estiver usando o _Twilio_, o nome de usuário será o seu **SID da conta**, a senha será o seu **Token de autenticação** e o seu provedor do SMS será `https://api.twilio.com`

1. Sob **Conversa**, configure a conexão com a sua instância de serviço do {{site.data.keyword.conversationshort}}. É possível usar as instâncias do serviço {{site.data.keyword.conversationshort}} nas contas do {{site.data.keyword.Bluemix_notm}} que você ou outra pessoa possui. Também é possível se conectar a qualquer uma dessas opções por meio de um mecanismo de orquestração de serviço (SOE).

   * Se você estiver criando um agente do SMS na região de Dallas ou Washington DC e não tiver uma instância de serviço do {{site.data.keyword.conversationshort}}, será possível criar uma no menu **Instância de serviço**.
   * Como alternativa, é possível se conectar a outras origens de um diálogo do {{site.data.keyword.conversationshort}} ou se conectar a um SOE mudando o [**Tipo de serviço**](/docs/services/voice-agent?topic=voice-agent-other_service#other_service).
   * Se você deseja configurar múltiplos locais de serviço, clique na outra opção de local e selecione
**Ativar local** para configurar a conexão com a sua outra instância do
{{site.data.keyword.conversationshort}}. Para obter mais informações, consulte [Incluindo múltiplos locais de serviço do Watson](/docs/services/voice-agent?topic=voice-agent-disaster-recovery#add_location).

1. Marque a caixa **Iniciar conversação por meio de mensagens de entrada** para permitir que os usuários iniciem uma sessão do SMS com o seu agente do SMS.

1. Marque a caixa **Notificar sobre o tempo limite de sessão** para que o seu agente do SMS envie uma mensagem do SMS para o usuário, alertando-o de que o agente não recebeu uma resposta em algum momento e agora atingirá o tempo limite. 

    - Consulte [Opções avançadas](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) para obter mais informações sobre as **Opções avançadas** disponíveis para o seu agente do SMS, como configurar um tempo customizado para a sessão atingir o tempo limite.
    - Marque a caixa somente se você desejar ser notificado quando uma sessão atingir o tempo limite.

1. Também é possível escolher ativar o encaminhamento de eventos para coletar informações sobre chamadas que são
manipuladas pelos seus agentes de voz em um {{site.data.keyword.cloudantfull}}. Para obter mais informações, consulte [Ativando o encaminhamento de eventos para os agentes de voz](/docs/services/voice-agent?topic=voice-agent-event_forwarding). Para obter mais opções de
configuração, consulte [Configurando um agente de voz](/docs/services/voice-agent?topic=voice-agent-managing#configure_va).

1.  Clique em **Criar agente de voz** para criar o seu agente do SMS e quaisquer serviços novos.

1. Siga [as instruções](/docs/services/voice-agent?topic=voice-agent-connect-sms) para se conectar a um provedor do SMS.

Após você criar o agente do SMS, teste o seu agente do SMS enviando mensagens de texto para o seu número do telefone. É possível visualizar detalhes sobre a sua interação no painel _Uso_. Consulte [Visualizando o uso e os logs](/docs/services/voice-agent?topic=voice-agent-logging).

Para ativar o sistema de mensagens do SMS entre clientes e um agente de voz durante uma chamada de voz, o número do SMS deverá corresponder ao número de voz.
{: tip}

Antes de você criar um agente do SMS ou incluir a funcionalidade do SMS em seu agente de voz, **deverá** ter as credenciais adequadas configuradas e gerar uma chave de API para programar para o seu número do SMS. Para obter mais informações, consulte [Gerando uma chave de API e Configurando credenciais](/docs/services/voice-agent?topic=voice-agent-connect-sms#sms_access).

Também **deve-se** configurar o seu tronco do SIP para a funcionalidade do SMS. Consulte as instruções do seu provedor, por exemplo, o Twilio. Se você não tiver um número do telefone do Twilio, consulte [Criando um tronco do SIP do Twilio](/docs/services/voice-agent?topic=voice-agent-connect#twilio-setup).

Assim que você tiver um número do Twilio, será necessário configurá-lo para a funcionalidade do SMS. Para obter mais informações, consulte [Configurando o Twilio para o SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

Se você tiver problemas ao criar credenciais, entre em contato com o seu administrador da instância de serviço para conceder-lhe acesso de *Gerenciador* ou *Gravador*.
{: tip}

## Opções avançadas para agentes do SMS
{: #sms_advanced}

Clique em **Mostrar avançado** após o campo **Número do telefone**.

1. Configure um valor de **Tempo limite de leitura de conversação** opcional. Esse é o tempo, em segundos, que o SMS Gateway espera por uma resposta do Watson Assistant. Se o tempo for excedido, o SMS Gateway fará novas tentativas de contatar o Watson Assistant. Se o serviço ainda não puder ser atingido, a mensagem de SMS/MMS falhará. Configure para 30 segundos, por padrão.

1. Configure um **Tempo limite de sessão** opcional. Este é o tempo, em segundos, após o qual a sessão expirará se o SMS Gateway não receber uma resposta do usuário.

1. Configure uma **Mensagem de resposta de falha de conversação**. Esta é a mensagem de resposta padrão que será enviada se o Watson Assistant não puder ser atingido. Por padrão, ela é configurada para `We're sorry, but we can't respond to your message.`.

### Configurando o SMS Agent para finalizar a sessão
{: #sms_terminate}

O agente do SMS do {{site.data.keyword.iva_full}} finaliza uma sessão com base no valor para o tempo limite de sessão, que é configurável e configurado para 30 segundos por padrão. 

Também é possível incluir um nó em seu serviço do {{site.data.keyword.conversationshort}} para responder a um comando de sessão de encerramento do usuário. 

1. No painel {{site.data.keyword.Bluemix_notm}}, selecione a instância do {{site.data.keyword.conversationshort}} que seu agente de voz usa.

1. Crie uma **Finalização de intento do SMS** no painel. Como alternativa, é possível modificar um intento existente que você já usa para o agente de voz, como _Finalizar a chamada_.

1. Inclua uma **Finalização do nó do SMS** no painel.

1. Na seção _Se o assistente reconhecer:_, inclua o atributo **Terminate SMS intent** que você criou anteriormente.

1. Inclua a resposta no nó. Copie e cole o fragmento de código a seguir para substituir o código no campo.

    ```json
        {
            "output": {
                 "text": {
                    "values": [
                        "Thank you for using the service. Goodbye!"
                    ],
                    "selection_policy”: “sequential"
                },
                "smsAction": {
                    "command": "terminateSession"
                }
            }
        }
    ```
    {: codeblock}

Após você criar o agente de voz, teste o seu agente de voz ligando ou enviando mensagens de texto para o seu número do telefone com base em seu tipo. É possível visualizar detalhes sobre a sua interação no painel _Uso_. Consulte [Visualizando o uso e os logs](/docs/services/voice-agent?topic=voice-agent-logging).
