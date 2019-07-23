---

copyright:
  years: 2019
lastupdated: "2019-06-21"
subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"_}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Conectando-se a Provedores do SMS
{: #connect-sms}

É possível escolher o provedor do SMS que você usa para integrar com o {{site.data.keyword.iva_full}} na lista a seguir.
{: #shortdesc}

* [Twilio](#twilio-setup)

## Gerando uma chave de API e Configurando credenciais
{: #sms_access}

Será possível criar credenciais somente para funções que já estiverem ativas em sua conta. Para os agentes do SMS e do Voice + SMS, deve-se ter a função *Gravador* ou *Gerenciador* designada. Consulte [Etapa 9 de Convidar os usuários e designar o acesso inicial](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. No *Painel* de sua instância do {{site.data.keyword.iva_short}}, clique em **Nova credencial (+)**. 
2. Na nova caixa de diálogo que aparece por pop-up, insira um **Nome** e sob o menu suspenso **Função**, selecione *Gravador* ou *Gerenciador*. 
    - **NOTA:** para qualquer funcionalidade relacionada ao SMS, **_deve-se_** selecionar a função *Gravador* ou *Gerenciador*. 
3. Clique em  ** Incluir **.
4. Próximo às suas credenciais recém-criadas, clique em **Visualizar credenciais**. Tome nota do valor para `APIKEY` no script de JSON para uso em [Configurando o Twilio para o SMS](/docs/services/voice-agent?topic=voice-agent-connect-sms#twilio-setup).

## Configurando o Twilio para o SMS
{: #twilio-setup}

1. Acesse os seus números de telefone do Twilio, localizados [aqui](https://www.twilio.com/console/phone-numbers/) e selecione o número do telefone que está designado para o seu agente do _SMS_ ou _Voice + SMS_. 

1. Role para baixo até a seção **Sistema de mensagens**. No campo _CONFIGURAR COM_, selecione **Webhooks, TwiML Bins, Functions, Studio ou Proxy** no menu suspenso.

1. No campo _UMA MENSAGEM É FORNECIDA EM_, selecione**Webhook** no menu suspenso.

1. No campo de URL vazio ao lado de **Webhook**, siga as instruções com base na região de seu agente. 

    - Se o agente que você criou for baseado na região de Washington, escreva `https://apikey:YOUR_API_KEY@sms-east.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` no campo.
    - Se o agente que você criou for baseado na região de Dallas, escreva `https://apikey:YOUR_API_KEY@sms-south.voiceagent.cloud.ibm.com/sms.receiver/SmsRecv` no campo.
    - Substitua `YOUR_API_KEY` na URL anterior pela `APIKEY` da credencial que você criou anteriormente. Consulte [Gerando uma chave de API e Configurando credenciais](/docs/services/voice-agent?topic=voice-agent-sms_config_instance#sms_access). 

1. Clique em **Salvar (Save)**. 
