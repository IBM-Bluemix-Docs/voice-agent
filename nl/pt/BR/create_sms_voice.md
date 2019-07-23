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

# Criando um agente de voz ativado por SMS
{: #sms_voice_config_instance}

Após você ter criado o seu serviço do {{site.data.keyword.iva_full}}, será possível criar agentes de voz individuais com funcionalidade do SMS ou agentes de voz com somente recursos do SMS, por meio do painel _Gerenciar_. É possível configurar o seu {{site.data.keyword.iva_full}} para receber chamadas de voz de entrada e responder com mensagens de saída do SMS, dependendo do comando de voz recebido pelo usuário. Para configurar, inclua um nó e um intento em seu serviço do {{site.data.keyword.conversationshort}}.
{: shortdesc}


1. Acesse a guia _Agentes de voz_ no painel _Gerenciar_ e clique em **Criar um agente de voz**.

1. Para **Tipo de agente**, selecione _Voice + SMS_.

1. Siga as instruções em [criando um agente de voz](/docs/services/voice-agent?topic=voice-agent-config_instance).

1. Marque a caixa **Iniciar conversação por meio de mensagens de entrada** para permitir que os usuários iniciem uma sessão do SMS com o seu agente do SMS.

1. Marque **Notificar sobre o tempo limite de sessão** para que o seu agente do SMS envie uma mensagem do SMS para o usuário, alertando-o de que o agente não recebeu uma resposta em algum momento e agora atingirá o tempo limite. 

   - Consulte [Opções avançadas](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_advanced) para obter mais informações sobre as **Opções avançadas** disponíveis para o seu agente do SMS, como configurar um tempo customizado para a sessão atingir o tempo limite.

1. Siga as instruções em [criando um agente do SMS](/docs/services/voice-agent?topic=voice-agent-sms_config_instance) para criar um agente do SMS.

1. _**NOTA:**_ para que um agente tenha a integração de Voz e SMS, como receber entrada de Voz e enviar de volta uma mensagem de saída do SMS para uma resposta, você **deverá** usar um de seus números de **voz** para o agente do **SMS**.

### Configurando o Watson Assistant para integração de voz e de SMS
{: #sms_outbound}

1. No painel {{site.data.keyword.Bluemix_notm}}, selecione a instância do {{site.data.keyword.conversationshort}} que seu agente de voz usa.

1. Crie um **intento do SMS de saída** no painel.

1. Inclua um **nó do SMS de saída** no painel.

1. Na seção _Se o assistente reconhecer:_, selecione o atributo **outbound SMS intent** que você criou anteriormente.

1. Inclua a resposta no nó. Copie e cole o fragmento de código a seguir para substituir o código no campo.

    ```json
        {
            "output": {
                "text": {
                "values": [
                    "Okay. I will send you a text message now."
                ],
     "selection_policy": "sequential"
                },
                "vgwActionSequence": [
                {
                    "command": "vgwActSendSMS",
                    "parameters": {
                    "message": "This is a test message from Watson Assistant"
                    }
                },
                {
                    "command": "vgwActPlayText"
                }
                ]
            }
        }
    ```
    {: codeblock}


1. Chame o seu agente e acione o nó para receber uma mensagem de texto no telefone do qual você está ligando. 

Para saber mais sobre como trabalhar no serviço {{site.data.keyword.conversationshort}}, consulte [Sobre o {{site.data.keyword.conversationshort}}](/docs/services/assistant?topic=assistant-index#indext).
