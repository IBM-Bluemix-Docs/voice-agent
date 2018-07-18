---

copyright:
  years: 2018
lastupdated: "2018-06-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Protegendo Conexões
{: #securing}

É possível ativar o Protocolo de Transporte em Tempo Real Seguro (SRTP) e a criptografia utilizando a Segurança da
Camada de Transporte (TLS) para os seus troncos SIP para proteger as conexões que são feitas com o
{{site.data.keyword.iva_full}}.

## Configurando SRTP no Twilio
{: #SRTP}

**Nota:** se você ativar o SRTP, as mensagens SIP também serão criptografadas. Não é necessário ativar a
criptografia de mensagem SRTP e SIP separadamente.

1. Em sua conta do Twilio, navegue para o painel _Entroncamento SIP elástico_ e selecione **Troncos**.

1. Escolha o tronco que você deseja proteger com o SRTP selecionando um tronco existente ou criando um novo clicando no ícone
**+**.

  * Se você criar um novo tronco, será necessário configurar a _URI de Tronco SIP_ no painel **Origem**.  Para obter mais informações, consulte [Conectando um tronco SIP](connect-SIP.html).

1. No painel _Geral_, localize a seção _Entroncamento seguro_. Clique em
**Desativado** para mudar a configuração de entroncamento seguro para **Ativado** e salve
as suas mudanças.

## Ativando a criptografia somente para as mensagens de SIP usando o TLS no Twilio
{: #TLS}

Se você quiser criptografar apenas as mensagens de SIP no {{site.agent.keyword.iva_short}} sem o SRTP, será possível
selecionar um terminal URI que use a Segurança da Camada de Transporte (TLS) no Twilio.

1. Em sua conta do Twilio, navegue para o painel _Entroncamento SIP elástico_ e selecione **Troncos**.

1. Escolha o tronco no qual deseja incluir a transferência de chamada selecionando um tronco existente ou criando um novo clicando no ícone **+**.

1. Selecione **Origem** no menu e insira os seguintes URIs de origem segura, um de cada vez. Ao incluir múltiplos nomes de host ou endereços IP, se o primeiro terminal de host falhar ou estiver fora de serviço, o seu
provedor de tronco SIP direcionará as chamadas para o próximo nome do host listado.

```
Sip:us-south.voiceagent.cloud.ibm.com; transporte = tls
```
{:codeblock}

Ou

```
Sip:us-east.voiceagent.cloud.ibm.com; transporte = tls
```
{:codeblock}
