---

copyright:
  years: 2018
lastupdated: "2018-12-05"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Conectando um tronco SIP
{: #connect}

É possível escolher o provedor de tronco SIP que você usa para que seja integrado ao {{site.data.keyword.iva_full}} na lista a seguir.
{: #shortdesc}

* [NetFoundry](#NetFoundry-setup)
* [Twilio](#twilio-setup)
* [AT & T e outros provedores](#att-other)
* [Peering com {{site.data.keyword.iva_short}}](#peering)
* [Solicitando Configuração](#request-setup)

## Criando um tronco SIP e um número de telefone do NetFoundry
{: #NetFoundry-setup}

**Nota:** criar uma conta requer um cartão de crédito, que é cobrado periodicamente com base em seu uso. Se você já tiver uma conta do NetFoundry, será possível usar a conta existente.

1. Crie uma conta no website do [NetFoundry![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson.netfoundry.io/watson-login){: new_window}.

1. Acesse a página principal _Conta do Watson_.

1. Selecione uma região da qual deseja que o número seja proveniente.

  **Nota:** verifique no website do NetFoundry as regiões disponíveis. Novas regiões são incluídos continuamente.

1. Clique em **Comprar** e siga as instruções na tela para concluir a compra.

1. Assim que o pagamento for processado com êxito, o número de telefone do seu tronco SIP será exibido em sua conta.

Esse número de telefone é necessário para configurar o seu agente de voz e a transferência de chamada, incluindo os códigos de país e de área. Consulte [Criando e conectando o seu agente de voz](getting-started.html#step3).


## Criando um tronco SIP Twilio
{: #twilio-setup}

**Nota:** criar uma conta do [Twilio ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.twilio.com/try-twilio){: new_window} requer um cartão de crédito, que é cobrado periodicamente com base no uso do tronco SIP que você configura. Se você já tiver uma conta do Twilio, será possível usar a conta existente.

  1. Crie uma conta do Twilio no [website do Twilio ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.twilio.com/try-twilio){: new_window}.

  1. Crie um tronco SIP com sua conta do Twilio.

  1. No website do Twilio, acesse o painel Entroncamento SIP Elástico.

  1. Selecione **Troncos** na barra de navegação e crie um tronco SIP. Se você já tiver um tronco SIP, clique no ícone **+**. Na caixa de diálogo resultante, insira um nome para seu tronco SIP e clique em **Criar**.

  1. Na página Troncos SIP Elásticos, selecione seu tronco SIP.

  1. Selecione **Origem** na barra de navegação para seu tronco SIP e configure o URI SIP de origem. É possível incluir vários nomes de host para evitar falhas de serviço selecionando o ícone **+**.

  O endereço IP ou o nome do host é o valor que você observou no painel _Introdução_ de sua instância de serviço {{site.data.keyword.iva_short}}. Quando você configura o URI de origem, ele deve estar no formato URI SIP, como `sip:us-south.voiceagent.cloud.ibm.com/`. Ao incluir múltiplos nomes de host ou endereços IP, se o primeiro terminal de host falhar ou estiver fora de serviço, o seu provedor de tronco SIP direcionará as chamadas para o próximo nome do host listado.

  1. Selecione **Números** na barra de navegação para seu tronco SIP. Em seguida, crie um número de telefone e designe-o ao seu tronco SIP.

  Na página Números, clique em **Comprar um número** ou, se já tiver um número, clique no ícone **+**. Um painel exibe onde você pode fornecer um novo número de telefone em sua região. Designe o número ao tronco SIP que você criou ao voltar para o tronco SIP e clicar no ícone Número.

  Esse número de telefone é necessário para configurar o seu agente de voz, incluindo os códigos de país e de área. Consulte [Criando e conectando o seu agente de voz](getting-started.html#step3).

## Peering com {{site.data.keyword.iva_short}}
{: #peering}

O {{site.data.keyword.iva_short}} suporta conexões peer, como um túnel IPSec. Para estar no mesmo nível do {{site.data.keyword.iva_short}}, é possível inserir os endereços IP na lista de desbloqueio de seus servidores.

1. Acesse o painel _Gerenciar_ e selecione a guia _Instância_.

1. Clique no ícone **Incluir um novo IP** para inserir um novo endereço IP na lista de desbloqueio.

1. Inclua um **Apelido de IP** e o **Endereço IP**.

## Conectando com o AT&T e outros provedores
{: #att-other}

O {{site.data.keyword.iva_short}} suporta conexões com o AT&T&reg; e outros provedores de entroncamento SIP. No entanto, essas conexões não são configuradas por autoatendimento e requerem assistência adicional. Consulte [Solicitando Configuração](#request-setup).

## Solicitando assistência de configuração
{: #request-setup}

É possível solicitar a configuração de rede assistida para se conectar ao AT&T e a outros provedores de entroncamento SIP, para peer com o {{site.data.keyword.iva_short}} ou para solicitar mais de 50 conexões simultâneas usando o processo a seguir.

1. Abra um novo [{{site.data.keyword.Bluemix_notm}} chamado de suporte](https://cloud.ibm.com/unifiedsupport/tickets/add)

1. Selecione **Técnico** para **Tipo de Registro**.

1. Escolha **Cloud Foundry** para **Selecionar um contexto de recurso**.

1. Para **Área técnica de suporte**, escolha **Application Services**.

1. Escolha a **Região**, a **Organização** e o **Espaço** para a sua instância do {{site.data.keyword.iva_short}}.

1. Selecione a sua instância de serviço do {{site.data.keyword.iva_short}} para **Recurso associado**.

1. Escolha **Severidade 4 - Impacto mínimo** para **Severidade**

1. Para **Assunto**, insira `{{site.data.keyword.iva_short}} assisted network setup`.

1. Na seção **Descrição breve**, descreva como pretende se conectar ao seu serviço {{site.data.keyword.iva_short}} ou solicitar mais de 50 conexões simultâneas ao seu agente de voz. A conexão peer está disponível para os usuários com planos _Padrão_ ou _Premium_. Se você alternar sua instância de um plano _Padrão_ ou _Premium_ para um plano _Lite_ ou se você excluir sua instância, a conexão peer será desativada.

  É possível se conectar usando um provedor de entroncamento SIP ou uma conexão peer, como um túnel IPSec. Em seu chamado, é possível anexar um diagrama de rede que descreve a topologia de sua rede em um formato PDF ou de imagem. Também é possível anexar quaisquer White Papers que descrevam em detalhes as competências de serviços que você deseja.

  Inclua as informações a seguir em sua **Descrição breve**:
  * Nome da Empresa
  * ID da conta {{site.data.keyword.Bluemix_notm}}
  * URL do seu painel de serviços do {{site.data.keyword.iva_short}}
  * Caso de Uso
  * Diagrama de rede com endereço IP ou informações do provedor de tronco SIP
